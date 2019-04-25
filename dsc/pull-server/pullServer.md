---
ms.date: 03/04/2019
keywords: DSC, powershell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: 3cb2ca09111100f39589072a0d8e7010f9188efb
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079412"
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration-hämtningstjänsten

> [!IMPORTANT]
> Pull-servern (Windows-funktionen *DSC-tjänst*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Rekommenderar vi att du påbörjar övergången hanterade klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver Pull-servern på Windows Server) eller en av community-lösningar visas [här](pullserver.md#community-solutions-for-pull-service).

Lokal konfigurationshanterare kan hanteras centralt av en Pull-tjänst-lösning.
När du använder den här metoden, är den nod som hanteras registrerat med en tjänst och tilldelad en konfiguration i LCM inställningar.
Konfigurationen och alla DSC-resurser som behövs som beroenden för konfigurationen hämtas till datorn och används av LCM för att hantera konfigurationen.
Information om tillståndet för den datorn hanteras har överförts till tjänsten för rapportering.
Detta kallas för ”hämtningstjänsten”.

De aktuella alternativ för pull-tjänsten är:

- Azure Automation Desired State Configuration-tjänsten
- En pull-tjänst som körs på Windows Server
- Community underhålls lösningar med öppen källkod
- En SMB-resurs

**Den rekommenderade lösningen**, och alternativet med de funktioner som är tillgänglig, är [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Azure-tjänsten kan hantera noder på plats i privat Datacenter eller i offentliga moln, till exempel Azure och AWS.
Överväg att begränsa utgående trafik till endast publicerade Azure IP-intervall för privata miljöer där servrarna inte kan ansluta direkt till Internet, (se [Azure Datacenter IP-intervall](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Funktioner i tjänsten online som inte är för närvarande tillgängliga i pull-tjänsten på Windows Server:

- Alla data krypteras vid överföring och i vila
- Klientcertifikat skapas och hanteras automatiskt
- Hemligheter lagra för att centralt hantera [lösenord/autentiseringsuppgifterna](/azure/automation/automation-credentials), eller [variabler](/azure/automation/automation-variables) , till exempel servernamn eller anslutningssträngar
- Centralt hantera nod [LCM konfiguration](../managing-nodes/metaConfig.md#basic-settings)
- Tilldela centralt konfigurationer till klientnoder
- Versionen konfigurationen ändras till ”kontrollvärde grupper” för att testa innan de når produktionen
- Grafisk rapportering
  - Statusinformation om på DSC-resurs granularitetsnivån
  - Utförlig felmeddelanden från klientdatorer för felsökning
- [Integrering med Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) för avisering, automatiserade uppgifter Android/iOS-app för rapportering och aviseringar

## <a name="dsc-pull-service-in-windows-server"></a>DSC-hämtningstjänsten i Windows Server

Det är möjligt att konfigurera en pull-tjänsten ska köras på Windows Server.
Vara bäst att pull-tjänst-lösning som ingår i Windows Server innehåller endast funktioner för att lagra konfigurationer och moduler för att ladda ned och samla in rapportdata i databasen.
Den innehåller inte alla funktioner som erbjuds av tjänsten i Azure och därför är inte ett bra verktyg för att utvärdera hur tjänsten används.

Pull-tjänsten som erbjuds i Windows Server är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillgängliggöra DSC-konfigurationsfilerna till målnoder när de noderna som ber om.

Krav för att använda en pull-server:

- En server som kör:
  - WMF/PowerShell 4.0 eller senare
  - IIS-serverrollen
  - DSC-tjänsten
- Vi rekommenderar några innebär att generera ett certifikat att skydda autentiseringsuppgifterna som skickas till den lokala Configuration Manager (LCM) på målnoder

Det bästa sättet att konfigurera Windows Server till pull värdtjänsten är att använda en DSC-konfiguration.
Ett exempelskript finns nedan.

### <a name="supported-database-systems"></a>Stöds databassystem

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (standard), MDB |ESENT (standard), MDB|ESENT (standard), SQLServer, MDB

Från och med versionen 17090 av [Windows Server, Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server är ett alternativ som stöds för Pull-tjänsten (Windows-funktionen *DSC-tjänst*). Detta ger ett nytt alternativ för att skala stora DSC-miljöer som inte har migrerat till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> Stöd för SQL Server kommer inte att lägga till tidigare versioner av WMF 5.1 (eller tidigare) och är endast tillgängligt på Windows Server-versioner som är större än eller lika med 17090.

Om du vill konfigurera pull-servern för att använda SQL Server, ange **SqlProvider** till `$true` och **SqlConnectionString** till en giltig anslutningssträng i SQL Server. Mer information finns i [SqlClient anslutningssträngar](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Ett exempel på konfiguration av SQL Server med **xDscWebService**, läsa [använder resursen som xDscWebService](#using-the-xdscwebservice-resource) och granska [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 på GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Med hjälp av xDscWebService-resurs

Det enklaste sättet att konfigurera en webbpullserver är att använda den **xDscWebService** resursmängd som ingår i den **xPSDesiredStateConfiguration** modulen.
Följande steg beskriver hur du använder resursen i en konfiguration som konfigurerar webbtjänsten.

1. Anropa den [Install-Module](/powershell/module/PowershellGet/Install-Module) cmdlet för att installera den **xPSDesiredStateConfiguration** modulen.
   > [!NOTE]
   > **Install-Module** ingår i den **PowerShellGet** modulen, som ingår i PowerShell 5.0. Du kan ladda ned den **PowerShellGet** -modulen för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler förhandsversion](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
2. Hämta ett SSL-certifikat för DSC-hämtningsservern från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet. Certifikatet som togs emot från utfärdaren är vanligtvis i PFX-format.
3. Installera certifikatet på den nod som blir DSC-hämtningsservern på standardplatsen, vilket ska vara `CERT:\LocalMachine\My`.
   - Anteckna tumavtrycket för certifikatet.
4. Välj ett GUID som ska användas som nyckel för tjänstregistrering. För att generera en med hjälp av PowerShell anger du följande i PS-Kommandotolken och tryck på RETUR: `[guid]::newGuid()` eller `New-Guid`. Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen. Mer information finns i avsnittet registreringsnyckel nedan.
5. I PowerShell ISE starta (F5) följande konfigurationsskript (ingår i exempel-mappen på den **xPSDesiredStateConfiguration** modulen som `Sample_xDscWebServiceRegistration.ps1`). Det här skriptet ställer in hämtningsservern.

    ```powershell
    configuration Sample_xDscWebServiceRegistration
    {
        param
        (
            [string[]]$NodeName = 'localhost',

            [ValidateNotNullOrEmpty()]
            [string] $certificateThumbPrint,

            [Parameter(HelpMessage='This should be a string with enough entropy (randomness) to protect the registration of clients to the pull server.  We will use new GUID by default.')]
            [ValidateNotNullOrEmpty()]
            [string] $RegistrationKey   # A guid that clients use to initiate conversation with pull server
        )

        Import-DSCResource -ModuleName PSDesiredStateConfiguration
        Import-DSCResource -ModuleName xPSDesiredStateConfiguration

        Node $NodeName
        {
            WindowsFeature DSCServiceFeature
            {
                Ensure = "Present"
                Name   = "DSC-Service"
            }

            xDscWebService PSDSCPullServer
            {
                Ensure                  = "Present"
                EndpointName            = "PSDSCPullServer"
                Port                    = 8080
                PhysicalPath            = "$env:SystemDrive\inetpub\PSDSCPullServer"
                CertificateThumbPrint   = $certificateThumbPrint
                ModulePath              = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules"
                ConfigurationPath       = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration"
                State                   = "Started"
                DependsOn               = "[WindowsFeature]DSCServiceFeature"
                RegistrationKeyPath     = "$env:PROGRAMFILES\WindowsPowerShell\DscService"
                AcceptSelfSignedCertificates = $true
                UseSecurityBestPractices     = $true
                Enable32BitAppOnWin64   = $false
            }

            File RegistrationKeyFile
            {
                Ensure          = 'Present'
                Type            = 'File'
                DestinationPath = "$env:ProgramFiles\WindowsPowerShell\DscService\RegistrationKeys.txt"
                Contents        = $RegistrationKey
            }
        }
    }
    ```

6. Kör sedan konfigurationen skicka tumavtrycket för SSL-certifikat som den **certificateThumbPrint** parameter och en GUID-registrering nyckel som den **RegistrationKey** parameter:

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Nyckel för tjänstregistrering

För att tillåta noder som ska registreras på servern så att de kan använda namnen i stället för ett ID, en registreringsnyckel som har skapats av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`. Nyckel för tjänstregistrering fungerar som en delad hemlighet som används under den första registreringen av klienten med pull-servern. Klienten genererar ett självsignerat certifikat som används för att autentisera till hämtningsservern unikt när registreringen är slutförd. Tumavtrycket för certifikatet lagras lokalt och som är associerade med pull-serverns URL.

> [!NOTE]
> Registreringsnycklar stöds inte i PowerShell 4.0.

Nyckel för tjänstregistrering måste finnas i metaconfiguration för alla målnoden som ska registreras med den här pull-servern för att kunna konfigurera en nod för autentisering med pull-servern. Observera att den **RegistrationKey** i metaconfiguration nedan tas bort när måldatorn har registrerats och som värdet måste matcha det värde som lagras i den `RegistrationKeys.txt` fil på hämtningsservern (” 140a952b-b9d6-406b-b416-e0f759c9c0e4 ”i det här exemplet). Behandla alltid registrering nyckelvärdet på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn för att registreras på pull-servern.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to set up pull server in previous configuration

        [ValidateNotNullOrEmpty()]
        [string] $ServerName = 'localhost' #node name of the pull server, same as $NodeName used in previous configuration
    )

    Node $NodeName
    {
        Settings
        {
            RefreshMode        = 'Pull'
        }

        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey    = $RegistrationKey
            ConfigurationNames = @('ClientConfig')
        }

        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = "https://$ServerName`:8080/PSDSCPullServer.svc" # notice it is https
            RegistrationKey = $RegistrationKey
        }
    }
}

Sample_MetaConfigurationToRegisterWithLessSecurePullServer -RegistrationKey $RegistrationKey -OutputPath c:\Configs\TargetNodes
```

> [!NOTE]
> Den **ReportServerWeb** avsnittet kan rapporterar data som ska skickas till den pull-servern.

Bristen på den **ConfigurationID** egenskap i filen metaconfiguration innebär den pull-servern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs.
Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server ska användas och det finns ingen registrering-bearbetning.

> [!NOTE]
> I ett pushscenario finns en bugg i den aktuella versionen som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metaconfiguration för noder som aldrig har registrerat med en pull-server. Detta tvinga V1-Hämtningsserver-protokollet och undvika felmeddelanden för registrering.

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

Efter pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du placerar moduler och konfigurationer som ska vara tillgängliga för målnoder att hämta.
De här filerna måste vara i ett visst format i för pull-servern ska kunna bearbetas korrekt.

### <a name="dsc-resource-module-package-format"></a>DSC resursformatet modulen paket

Varje Resursmodul måste zippade och med namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.

Till exempel en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 heta `xWebAdministration_3.2.1.0.zip`.
Varje version av en modul måste finnas i en enda zip-fil.
Eftersom det finns endast en version av en resurs i varje zip-filen, stöds inte formatet modulen har lagts till i WMF 5.0 med stöd för flera modulversionerna i en enskild katalog.
Det innebär att innan du packa upp DSC-resurs-moduler för användning med hämtningsservern du måste göra små ändringar i katalogstrukturen.
Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\`.
Innan du paketering för hämtningsservern, ta bort den **{Modulversion}** mapp så blir sökvägen `{Module Folder}\DscResources\{DSC Resource Folder}\`.
Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.

Använd `New-DscChecksum {module zip file}` att skapa en kontrollsumma-fil för den nya modulen.

### <a name="configuration-mof-format"></a>Konfigurationen MOF-format

En MOF-konfigurationsfilen måste kopplas till en kontrollsumma-fil så att en LCM på målnoden verifiera konfigurationen.
Om du vill skapa en kontrollsumma, anropa den [New DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.
Cmdlet: en tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.
Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på mof-konfigurationsfilen.
Om det finns flera olika konfigurationer MOF-filer i en angiven mapp, skapas en kontrollsumma för varje konfiguration i mappen.
Placera MOF-filer och deras associerade kontrollsumma filer i den **ConfigurationPath** mapp.

> [!NOTE]
> Om du ändrar MOF-konfigurationsfilen på något sätt, måste du också återskapa filen kontrollsumma.

### <a name="tooling"></a>Verktyg

För att kunna utgör inställningen verifiera och hantera hämtningsservern enklare, följande verktyg ingår som exempel i den senaste versionen av modulen xPSDesiredStateConfiguration:

1. En modul som hjälper med paketering moduler för DSC-resurs och konfigurationsfiler för användning på hämtningsservern.
   [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1).
   Exemplen nedan:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Ett skript som kontrollerar pull-servern är korrekt konfigurerad. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-lösningar för Pull-tjänsten

DSC-communityn har skapat flera lösningar för att implementera protokollet pull-tjänsten.
För lokala miljöer erbjuder dessa pull service-funktionerna och en möjlighet att bidra till community med inkrementell förbättringar.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Pull-klientkonfiguration

I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:

- [Konfigurera en DSC-pullklient med konfigurations-ID](pullClientConfigID.md)
- [Konfigurera en DSC-hämtningsklient med konfigurationsnamn](pullClientConfigNames.md)
- [Partiella konfigurationer](partialConfigs.md)

## <a name="see-also"></a>Se även

- [Windows PowerShell Desired State Configuration-översikt](../overview/overview.md)
- [Tillämpa konfigurationer](enactingConfigurations.md)
- [Använd en DSC-rapportserver](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration protokollet för Pull-modell](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Pull-modellen protokollet rättelser](https://msdn.microsoft.com/library/mt612824.aspx)
