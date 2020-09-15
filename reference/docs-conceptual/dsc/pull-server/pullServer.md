---
ms.date: 01/08/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-hämtningstjänsten
ms.openlocfilehash: c4e725569db776fe0dbd5395b2f0f8b8e70cbbeb
ms.sourcegitcommit: 105c69ecedfe5180d8c12e8015d667c5f1a71579
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/02/2020
ms.locfileid: "85837485"
---
# <a name="desired-state-configuration-pull-service"></a>Mottagar tjänst för önskad tillstånds konfiguration

> [!IMPORTANT]
> Hämtnings servern (Windows Feature *DSC-tjänst*) är en komponent som stöds av Windows Server men det finns inga planer på att erbjuda nya funktioner eller funktioner. Vi rekommenderar att du börjar överföra hanterade klienter till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started) (inklusive funktioner utöver hämtnings servern på Windows Server) eller någon av de community-lösningar som anges [här](pullserver.md#community-solutions-for-pull-service).

Lokala Configuration Manager (LCM) kan hanteras centralt av en pull service-lösning. När du använder den här metoden registreras noden som hanteras med en tjänst och tilldelas en konfiguration i LCM-inställningar. Konfigurationen och alla DSC-resurser som krävs som beroenden för konfigurationen laddas ned till datorn och används av LCM för att hantera konfigurationen. Information om statusen för den dator som hanteras överförs till tjänsten för rapportering. Det här begreppet kallas "pull-tjänst".

De aktuella alternativen för pull service är:

- Azure Automation tjänst för önskad tillstånds konfiguration
- En pull-tjänst som körs på Windows Server
- Community-underhållna lösningar med öppen källkod
- En SMB-resurs

Den rekommenderade skalningen för varje lösning är följande:

|                   Lösning                   |              Klient-noder              |
| -------------------------------------------- | -------------------------------------- |
| Windows pull-server med hjälp av MDB/ESENT-databas | Upp till 500 noder                        |
| Windows pull-server med SQL Database       | Upp till 3500 noder                       |
| Azure Automation DSC                         | Både små och stora miljöer      |

**Den rekommenderade lösningen**och alternativet med de mest tillgängliga funktionerna är [Azure Automation DSC](/azure/automation/automation-dsc-getting-started). En övre gräns för antalet noder per Automation-konto har inte identifierats.

Azure-tjänsten kan hantera noder lokalt i privata data Center eller i offentliga moln, till exempel Azure och AWS. För privata miljöer där servrar inte kan ansluta direkt till Internet bör du överväga att begränsa utgående trafik till endast det publicerade Azure IP-intervallet (se [Azure datacenter IP-intervall](https://www.microsoft.com/download/details.aspx?id=41653)).

Funktioner i online tjänsten som inte är tillgängliga i pull-tjänsten på Windows Server inkluderar:

- Alla data krypteras under överföring och i vila
- Klient certifikat skapas och hanteras automatiskt
- Hemligheter för central hantering av [lösen ord/autentiseringsuppgifter](/azure/automation/automation-credentials), eller [variabler](/azure/automation/automation-variables) som server namn eller anslutnings strängar
- Centralt hantera [konfiguration av LCM](../managing-nodes/metaConfig.md#basic-settings) -noden
- Centralt tilldela konfigurationer till klient-noder
- Frisläpp konfigurations ändringar till "Kanarie Groups" för testning innan du når produktion
- Grafisk rapportering
  - Statusinformation på DSC-resursens nivå för granularitet
  - Utförliga fel meddelanden från klient datorer för fel sökning
- [Integrering med Azure Log Analytics](/azure/automation/automation-dsc-diagnostics) för aviseringar, automatiserade uppgifter, Android/iOS-app för rapportering och aviseringar

## <a name="dsc-pull-service-in-windows-server"></a>DSC-pull-tjänst i Windows Server

Det är möjligt att konfigurera en pull-tjänst för att köras på Windows Server. Vi rekommenderar att lösningen för pull-tjänster som ingår i Windows Server bara innehåller funktioner för att lagra konfigurationer/moduler för att hämta och samla in rapport data i en databas. Det innehåller inte många av de funktioner som erbjuds av tjänsten i Azure och är därför inte ett lämpligt verktyg för att utvärdera hur tjänsten används.

Pull-tjänsten som erbjuds i Windows Server är en webb tjänst i IIS som använder ett OData-gränssnitt för att göra DSC-konfigurationsfiler tillgängliga för mål noder när noderna begär det.

Krav för att använda en hämtnings Server:

- En server som kör:
  - WMF/PowerShell 4,0 eller senare
  - IIS-serverrollen
  - DSC-tjänst
- Det bästa är att skapa ett certifikat för att skydda autentiseringsuppgifter som skickas till den lokala Configuration Manager (LCM) på målnoden

Det bästa sättet att konfigurera Windows Server som värd för pull-tjänst är att använda en DSC-konfiguration. Ett exempel skript anges nedan.

### <a name="supported-database-systems"></a>Databas system som stöds

| WMF 4,0 |       WMF 5.0        |       WMF 5.1        | WMF 5,1 (Windows Server Insider Preview 17090) |
| ------- | -------------------- | -------------------- | ---------------------------------------------- |
| MDB     | ESENT (standard), MDB | ESENT (standard), MDB | ESENT (standard), SQL Server, MDB               |

Från och med version 17090 av Windows Server är SQL Server ett alternativ som stöds för pull-tjänsten (Windows Feature *DSC-service*). Detta ger ett nytt alternativ för skalning av stora DSC-miljöer som inte har migrerats till [Azure Automation DSC](/azure/automation/automation-dsc-getting-started).

> [!NOTE]
> SQL Server-stöd kommer inte att läggas till i tidigare versioner av WMF 5,1 (eller tidigare) och är bara tillgängliga på Windows Server-versioner som är större än eller lika med 17090.

Konfigurera hämtnings servern för att använda SQL Server genom att ange **SqlProvider** till `$true` och **SqlConnectionString** till en giltig SQL Server anslutnings sträng. Mer information finns i [anslutnings strängar för SqlClient](/dotnet/framework/data/adonet/connection-string-syntax#sqlclient-connection-strings).
Ett exempel på SQL Server konfiguration med **xDscWebService**får du först läsa [med xDscWebService-resursen](#using-the-xdscwebservice-resource) och sedan granska [Sample_xDscWebServiceRegistration_UseSQLProvider.ps1 på GitHub](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Examples/Sample_xDscWebServiceRegistration_UseSQLProvider.ps1).

### <a name="using-the-xdscwebservice-resource"></a>Använda xDscWebService-resursen

Det enklaste sättet att konfigurera en webb hämtnings Server är att använda **xDscWebService** -resursen, som ingår i **xPSDesiredStateConfiguration** -modulen. Följande steg beskriver hur du använder resursen i en `Configuration` som konfigurerar webb tjänsten.

1. Anropa cmdleten [install-module](/powershell/module/PowerShellGet/Install-Module) för att installera **xPSDesiredStateConfiguration** -modulen.

   > [!NOTE]
   > `Install-Module` ingår i **PowerShellGet** -modulen, som ingår i PowerShell 5,0 och högre.

1. Hämta ett SSL-certifikat för DSC-pull-servern från en betrodd certifikat utfärdare, antingen inom organisationen eller en offentlig myndighet. Certifikatet som togs emot från utfärdaren är vanligt vis i PFX-format.
1. Installera certifikatet på den nod som ska bli DSC-pull-server på standard platsen, vilket ska vara `CERT:\LocalMachine\My` .
   - Anteckna tumavtryck för certifikatet.
1. Välj en GUID som ska användas som registrerings nyckel. Om du vill generera en med PowerShell anger du följande vid PS-prompten och trycker på RETUR: `[guid]::newGuid()` eller `New-Guid` . Den här nyckeln används av-klient noder som en delad nyckel för att autentisera vid registreringen. Mer information finns i avsnittet registrerings nyckel nedan.
1. I PowerShell ISE startar du (<kbd>F5</kbd>) följande konfigurations skript (ingår i mappen i **xPSDesiredStateConfiguration** -modulen som `Sample_xDscWebServiceRegistration.ps1` ). Det här skriptet konfigurerar hämtnings servern.

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

1. Kör konfigurationen och skicka tumavtrycket för SSL-certifikatet som parametern **certificateThumbPrint** och en GUID-registrerings nyckel som parametern **RegistrationKey** :

    ```powershell
    # To find the Thumbprint for an installed SSL certificate for use with the pull server list all certificates in your local store
    # and then copy the thumbprint for the appropriate certificate by reviewing the certificate subjects
    dir Cert:\LocalMachine\my

    # Then include this thumbprint when running the configuration
    Sample_xDscWebServiceRegistration -certificateThumbprint 'A7000024B753FA6FFF88E966FD6E19301FAE9CCC' -RegistrationKey '140a952b-b9d6-406b-b416-e0f759c9c0e4' -OutputPath c:\Configs\PullServer

    # Run the compiled configuration to make the target node a DSC Pull Server
    Start-DscConfiguration -Path c:\Configs\PullServer -Wait -Verbose
    ```

#### <a name="registration-key"></a>Registrerings nyckel

Om du vill tillåta att klusternoder registreras på servern så att de kan använda konfigurations namn i stället för ett konfigurations-ID, sparas en registrerings nyckel som har skapats av konfigurationen ovan i en fil med namnet `RegistrationKeys.txt` `C:\Program Files\WindowsPowerShell\DscService` . Registrerings nyckeln fungerar som en delad hemlighet som används under den inledande registreringen av klienten med hämtnings servern. Klienten genererar ett självsignerat certifikat som används för att autentisera till pull-servern när registreringen är slutförd. Tumavtrycket för det här certifikatet lagras lokalt och associeras med URL: en för pull-servern.

> [!NOTE]
> Registrerings nycklar stöds inte i PowerShell 4,0.

För att du ska kunna konfigurera en nod att autentisera med hämtnings servern måste registrerings nyckeln finnas i metaconfiguration för alla målnod som ska registreras med den här hämtnings servern. Observera att **RegistrationKey** i metaconfiguration nedan tas bort när mål datorn har registrerats och att värdet måste matcha det värde som lagras i `RegistrationKeys.txt` filen på hämtnings servern ("140a952b-b9d6-406b-b416-e0f759c9c0e4" i det här exemplet). Behandla alltid registrerings nyckel svärdet på ett säkert sätt, eftersom du vet att alla mål datorer kan registreras på hämtnings servern.

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
> I avsnittet **ReportServerWeb** kan du skicka rapporterings data till hämtnings servern.

Avsaknad av egenskapen **ConfigurationID** i metaconfiguration-filen innebär implicit att hämtnings servern har stöd för v2-versionen av protokollet för pull-server, så att en inledande registrering krävs. Förekomsten av en **ConfigurationID** innebär däremot att v1-versionen av pull server-protokollet används och att det inte finns någon registrerings bearbetning.

> [!NOTE]
> I ett PUSH-scenario finns en bugg i den aktuella versionen som gör det nödvändigt att definiera en ConfigurationID-egenskap i metaconfiguration-filen för noder som aldrig har registrerats med en pull-server. Detta tvingar v1 pull server-protokollet och undvika meddelanden om registrerings fel.

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

När installationen av hämtnings servern är klar är mapparna som definieras av egenskaperna **ConfigurationPath** och **ModulePath** i hämtnings Server konfigurationen där du kommer att placera moduler och konfigurationer som är tillgängliga för målnoden att hämta. Filerna måste vara i ett särskilt format för att hämtnings servern ska kunna bearbeta dem på rätt sätt.

### <a name="dsc-resource-module-package-format"></a>Paket format för DSC-resurs

Varje resurs-modul måste vara zippad och namngiven enligt följande mönster `{Module Name}_{Module Version}.zip` .

Till exempel skulle en modul med namnet **xWebAdminstration** med en modul version av 3.1.2.0 namnges `xWebAdministration_3.1.2.0.zip` . Varje version av en modul måste finnas i en enda zip-fil.
Eftersom det bara finns en enda version av en resurs i varje zip-fil stöds inte modulfönstret som lagts till i WMF 5,0 med stöd för flera versioner i en enda katalog. Det innebär att innan du packar upp DSC-resurspooler för användning med pull-server måste du göra en liten ändring i katalog strukturen. Standardformat för moduler som innehåller DSC-resurser i WMF 5,0 är `{Module Folder}\{Module Version}\DscResources\{DSC Resource Folder}\` . Innan du packar upp för pull-servern tar du bort mappen **{module version}** så att sökvägen blir `{Module Folder}\DscResources\{DSC Resource Folder}\` . Med den här ändringen zip-mappen enligt beskrivningen ovan och placera dessa zip-filer i mappen **ModulePath** .

Används `New-DscChecksum {module zip file}` för att skapa en kontroll Summa fil för den nyligen tillagda modulen.

### <a name="configuration-mof-format"></a>MOF-format för konfiguration

En konfigurations-MOF-fil måste kombineras med en kontroll Summa fil så att en LCM på en målnod kan verifiera konfigurationen. Om du vill skapa en kontroll Summa anropar du cmdleten [New-DscChecksum](/powershell/module/PSDesiredStateConfiguration/New-DSCCheckSum) . Cmdlet: en använder en **Sök vägs** parameter som anger den mapp där MOF-konfigurationsfilen finns. Cmdleten skapar en kontroll Summa fil med namnet `ConfigurationMOFName.mof.checksum` , där `ConfigurationMOFName` är namnet på MOF-konfigurationsfilen. Om det finns fler än en konfigurations-MOF-fil i den angivna mappen skapas en kontroll summa för varje konfiguration i mappen. Placera MOF-filerna och deras associerade kontroll Summa filer i mappen **ConfigurationPath** .

> [!NOTE]
> Om du ändrar konfigurations-MOF-filen på valfritt sätt måste du också återskapa kontroll Summa filen.

### <a name="tooling"></a>Verktyg

Följande verktyg ingår som exempel i den senaste versionen av xPSDesiredStateConfiguration-modulen för att göra det enklare att konfigurera, verifiera och hantera hämtnings servern:

1. En modul som hjälper till att paketera DSC-resurspooler och konfigurationsfiler för användning på hämtnings servern.
   [PublishModulesAndMofsToPullServer. psm1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetup.psm1).
   Exempel nedan:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @('xWebAdministration', 'xPhp')
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Ett skript som verifierar hämtnings servern är korrekt konfigurerat. [PullServerSetupTests.ps1](https://github.com/dsccommunity/xPSDesiredStateConfiguration/blob/master/source/Modules/DscPullServerSetup/DscPullServerSetupTest/DscPullServerSetupTest.ps1).

## <a name="community-solutions-for-pull-service"></a>Community-lösningar för pull-tjänst

DSC-communityn har skapat flera lösningar för att implementera protokollet för pull-protokollet. För lokala miljöer erbjuder dessa funktioner för pull-tjänster och en möjlighet att bidra tillbaka till communityn med stegvisa förbättringar.

- [Tug](https://github.com/powershellorg/tug)
- [DSC – TRÆK](https://github.com/powershellorg/dsc-traek)

## <a name="pull-client-configuration"></a>Hämta klient konfiguration

I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:

- [Konfigurera en DSC-pull-klient med ett konfigurations-ID](pullClientConfigID.md)
- [Konfigurera en DSC-pull-klient med hjälp av konfigurations namn](pullClientConfigNames.md)
- [Partiella konfigurationer](partialConfigs.md)

## <a name="see-also"></a>Se även

- [Översikt över önskad tillstånds konfiguration i Windows PowerShell](../overview/overview.md)
- [Tillämpa konfigurationer](enactingConfigurations.md)
- [Använda en DSC-rapportserver](reportServer.md)
- [[MS-DSCP]: protokoll för Desired State Configuration pull-modell](/openspecs/windows_protocols/ms-dscpm/ea744c01-51a2-4000-9ef2-312711dcc8c9)
- [[MS-DSCP]: protokoll för önskad tillstånds konfiguration pull-errata](/openspecs/windows_protocols/ms-winerrata/f5fc7ae3-9172-41e8-ac6a-2a5a5b7bfaf5)
