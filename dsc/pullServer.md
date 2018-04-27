---
ms.date: 04/11/2018
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: 075487be68de82074750e5344a24d6d4c2f2bec5
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2018
---
# <a name="desired-state-configuration-pull-service"></a>Desired State Configuration Pull-tjänsten

> Gäller för: Windows PowerShell 5.0

> [!IMPORTANT]
> Pull-Server (Windows-funktionen *DSC-Service*) är en stöds komponent i Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att börja övergång hanteras klienter [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (omfattar funktioner utöver Pull-Server på Windows Server) eller någon av community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Local Configuration Manager kan hanteras centralt av en Pull-tjänst-lösning.
När du använder den här metoden är noden som hanteras registrerats med en tjänst och tilldelad en konfiguration i MGM inställningar.
Konfigurationen och alla DSC-resurser som behövs som beroenden för konfigurationen laddas ned till datorn och används av MGM för att hantera konfigurationen.
Information om tillståndet för den datorn hanteras har överförts till tjänsten för rapportering.
Detta kallas för ”pull-tjänst”.

Aktuella alternativ för pull-tjänsten är:

- Azure Automation önskade tillstånd konfigurationstjänsten
- En pull-tjänst som körs på Windows Server
- Gemenskapen underhålls öppen källkod
- En SMB-resurs

**Den rekommenderade lösningen**, och alternativet med de funktioner som är tillgängliga, är [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

Azure-tjänsten kan hantera noder lokalt i privat Datacenter eller i offentliga moln, till exempel Azure och AWS.
Överväg att begränsa utgående trafik till endast publicerade Azure IP-adressintervall för privata miljöer där servrarna inte kan ansluta direkt till Internet, (se [IP-intervall för Azure-Datacenter](https://www.microsoft.com/en-us/download/details.aspx?id=41653)).

Tjänsten online-funktioner som inte är tillgängliga i pull-tjänsten på Windows Server inkluderar:
- Krypteras alla data under överföring och i vila
- Klientcertifikat skapas och hanteras automatiskt
- Hemligheter lagra för att centralt hantera [lösenord/autentiseringsuppgifterna](/azure/automation/automation-credentials), eller [variabler](/azure/automation/automation-variables) , till exempel servernamn eller anslutningssträngar
- Centralt hantera nod [MGM konfiguration](metaConfig.md#basic-settings)
- Tilldela centralt konfigurationer till klientnoder
- Versionen konfiguration ändras till ”Kanarieöarna grupper” för att testa innan det nådde produktion
- Grafisk rapportering
  - Information om status på nivån för DSC-resurs i granularitet
  - Detaljerade felmeddelanden från klientdatorer för felsökning
- [Integrering med Azure logganalys](/azure/automation/automation-dsc-diagnostics) för aviseringar, automatiserade åtgärder Android/iOS-app för rapportering och aviseringar

## <a name="dsc-pull-service-in-windows-server"></a>DSC pull-tjänsten i Windows Server

Det är möjligt att konfigurera en pull-tjänsten körs på Windows Server.
Vara medveten om att pull-tjänsten-lösningen som ingår i Windows Server innehåller endast funktioner för lagring av konfigurationer och moduler för att ladda ned och samlar in rapportdata i databasen.
Den innehåller inte många av funktionerna som erbjuds av tjänst i Azure och är alltså inte en bra verktyg för att utvärdera hur tjänsten skulle användas.

Pull-tjänsten erbjuds i Windows Server är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillhandahålla DSC konfigurationsfiler målnoder när de noderna som ber om.

Krav för att använda en pull-server:

- En server som kör:
  - WMF/PowerShell 5.0 eller senare
  - IIS-serverrollen
  - DSC-tjänsten
- Vi rekommenderar vissa innebär genererar ett certifikat för säker autentiseringsuppgifter som angavs till den lokala Configuration Manager (MGM) på målnoder

Det bästa sättet att konfigurera Windows Server till pull-värdtjänsten är att använda en DSC-konfigurationen.
Ett exempelskript finns nedan.

### <a name="supported-database-systems"></a>System som stöds

|WMF 4.0   |WMF 5.0  |WMF 5.1 |WMF 5.1 (Windows Server Insider Preview 17090)|
|---------|---------|---------|---------|
|MDB     |ESENT (standard), MDB |ESENT (standard), MDB|ESENT (standard), SQLServer, MDB

Från och med att släppa 17090 av [Windows Server, Insider Preview](https://www.microsoft.com/en-us/software-download/windowsinsiderpreviewserver), SQL Server är ett alternativ som stöds för Pull-tjänsten (Windows-funktionen *DSC-Service*).  Detta ger ett nytt alternativ för skalning stora DSC-miljöer som inte har migrerat till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> **Obs**: stöd för SQL Server kommer inte att lägga till tidigare versioner av WMF 5.1 (eller tidigare) och kan bara användas på Windows Server-versionerna större än eller lika med 17090.

För att konfigurera pull-server för att använda SQL Server, ange **SqlProvider** till `$true` och **SqlConnectionString** till en giltig anslutningssträng i SQL Server.  Mer information finns i [SqlClient-anslutningssträngar](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Ett exempel på konfiguration av SQL Server med **xDscWebService**, läsa [resursnamnet xDscWebService](#using-the-xdscwebservice-resource) och granska sedan [Sample_xDscWebServiceRegistration_ UseSQLProvider.ps1 på GitHub](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Resursnamnet xDscWebService

Det enklaste sättet att konfigurera en pull-webbserver är att använda den **xDscWebService** resurs, som ingår i den **xPSDesiredStateConfiguration** modul.
Följande steg förklarar hur du använder resursen i en konfiguration som ställer in webbtjänsten.

1. Anropa den [installera modulen](/powershell/module/PowershellGet/Install-Module) för att installera den **xPSDesiredStateConfiguration** modul. **Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0. Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186).
1. Hämta ett SSL-certifikat för DSC Pull-server från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet. Certifikatet som togs emot från myndigheten är vanligtvis i PFX-format. Installera certifikatet på den nod som blir DSC hämtningsservern på standardplatsen bör vara CERT: \LocalMachine\My. Anteckna tumavtrycket för certifikatet.
1. Välj ett GUID som ska användas som nyckel för tjänstregistrering. Skapa ett med hjälp av PowerShell Skriv följande i PS-Kommandotolken och tryck på RETUR: '``` [guid]::newGuid()```'eller'```New-Guid```'. Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen. Mer information finns i avsnittet registreringsnyckel nedan.
1. I PowerShell ISE start (F5) följande konfigurationsskript (ingår i mappen exempel i den **xPSDesiredStateConfiguration** modulen som Sample_xDscWebServiceRegistration.ps1). Det här skriptet konfigurerar pull-server.

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

1. Kör sedan konfigurationen skicka tumavtrycket för SSL-certifikat som den **certificateThumbPrint** parameter och en GUID-registrering nyckel som den **RegistrationKey** parameter:

```powershell
# To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
# and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
dir Cert:\LocalMachine\my

# Then include this thumbprint when running the configuration
Sample_xDSCPullServer -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

# Run the compiled configuration to make the target node a DSC Pull Server
Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
```

#### <a name="registration-key"></a>Nyckel för tjänstregistrering

Så att klienten noder som ska registreras på servern så att de kan använda konfigurationsnamn i stället för ett konfigurations-ID, en registreringsnyckel som skapades av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`. Registreringsnyckeln som fungerar som en delad hemlighet som används under registreringen av klienten med pull-servern. Klienten genererar ett självsignerat certifikat som används för att autentisera unikt till den pull-servern när registreringen är slutförd. Tumavtrycket för certifikatet lagras lokalt och som är kopplade till URL-Adressen till den pull-servern.
> **Obs**: registreringsnycklar stöds inte i PowerShell 4.0.

Registreringsnyckeln måste vara i metakonfigurationen för varje målnod i som ska registreras med den här pull-servern för att kunna konfigurera en nod för autentisering med pull-servern. Observera att den **RegistrationKey** i metakonfigurationen nedan tas bort när måldatorn har registrerats och att värdet '140a952b-b9d6-406b-b416-e0f759c9c0e4' måste matcha det värde som lagras i den RegistrationKeys.txt fil på hämtningsservern. Behandla alltid nyckelvärdet registrering på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn registreras på pull-servern.

```powershell
[DSCLocalConfigurationManager()]
configuration Sample_MetaConfigurationToRegisterWithLessSecurePullServer
{
    param
    (
        [ValidateNotNullOrEmpty()]
        [string] $NodeName = 'localhost',

        [ValidateNotNullOrEmpty()]
        [string] $RegistrationKey, #same as the one used to setup pull server in previous configuration

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

> **Obs**: den **ReportServerWeb** avsnittet kan rapportera data skickas till den pull-servern.

Bristen på den **ConfigurationID** egenskapen i filen metakonfigurationen innebär att hämtningsservern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs.
Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server används och det finns ingen registrering bearbetning.

>**Obs**: I en PUSH-scenariot ett programfel finns i den aktuella versionen som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metakonfigurationen för noder som aldrig har registrerats med en pull-server. Detta tvingar protokollet V1 Pull-Server och undvika fel registreringsmeddelanden.

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

När pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du kan placera moduler och konfigurationer som ska vara tillgängliga för målnoder och hämtar.
Filerna måste vara i ett specifikt format för pull-servern att bearbeta dem korrekt.

### <a name="dsc-resource-module-package-format"></a>DSC resursformatet modulen paketet

Varje Resursmodul behöver zippade och namnet enligt följande mönster `{Module Name}_{Module Version}.zip`.
Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'.
Varje version av en modul måste finnas i en enda zip-fil.
Eftersom endast en version av en resurs i varje zip-filen stöds inte formatet modulen lades till i WMF 5.0 med stöd för flera modulversioner i en katalog.
Detta innebär att innan paketering in DSC resurs moduler för användning med pull-server behöver du göra en mindre ändring i katalogstrukturen.
Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'.
Innan du paketering för pull-servern, ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'.
Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.

Använd `New-DscChecksum {module zip file}` att skapa en kontrollsumma fil för modulen nytillagda.

### <a name="configuration-mof-format"></a>Konfigurationen MOF-format

En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen.
Om du vill skapa en kontrollsumma anropa den [ny DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DscChecksum) cmdlet.
Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns.
Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil.
Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen.
Placera MOF-filer och deras associerade kontrollsumma filer i den **ConfigurationPath** mapp.

>**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.

### <a name="tooling"></a>Tooling

För att kunna utgör inställningen verifiera och hantera den pull-servern som är enklare, följande verktyg ingår som exemplen i den senaste versionen av modulen xPSDesiredStateConfiguration:

1. En modul som kan hjälpa dig i Paketera DSC resurs moduler och konfigurationsfilerna för användning på pull-server. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemplen nedan:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Ett skript som kontrollerar pull-servern är korrekt konfigurerad. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/master/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-lösningar för Pull-tjänsten

DSC-gruppen har skapats på flera lösningar för att implementera protokollet pull-tjänsten.
För lokala miljöer erbjuder dessa funktioner pull och möjlighet att bidra till community med inkrementell förbättringar.

- [Tug](https://github.com/powershellorg/tug)
- [DSC-TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Pull-klientkonfiguration

I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:

- [Ställa in en DSC pull-klient som använder ett konfigurations-ID](pullClientConfigID.md)
- [Ställa in en DSC pull-klient med konfigurationsnamn](pullClientConfigNames.md)
- [Partiell konfigurationer](partialConfigs.md)

## <a name="see-also"></a>Se även

- [Windows PowerShell Desired State Configuration-översikt](overview.md)
- [Tillämpa konfigurationer](enactingConfigurations.md)
- [Använd en DSC-rapportserver](reportServer.md)
- [[MS-DSCPM]: Desired State Configuration Pull modellen protokoll](https://msdn.microsoft.com/library/dn393548.aspx)
- [[MS-DSCPM]: Desired State Configuration Pull modellen protokollet rättelser](https://msdn.microsoft.com/library/mt612824.aspx)