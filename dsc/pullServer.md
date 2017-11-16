---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Ställer in en pull webbserver DSC"
ms.openlocfilehash: 03d4d148c87854b146091aa0e8d815b8c35def72
ms.sourcegitcommit: 4102ecc35d473211f50a453f6ae3fbea31cb3428
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/31/2017
---
# <a name="setting-up-a-dsc-web-pull-server"></a>Ställer in en pull webbserver DSC

> Gäller för: Windows PowerShell 5.0

En pull-DSC webbserver är en webbtjänst i IIS som använder ett OData-gränssnitt för att tillhandahålla DSC konfigurationsfiler målnoder när de noderna som ber om.

Krav för att använda en pull-server:

* En server som kör:
  - WMF/PowerShell 5.0 eller senare
  - IIS-serverrollen
  - DSC-tjänsten
* Vi rekommenderar vissa innebär genererar ett certifikat för säker autentiseringsuppgifter som angavs till den lokala Configuration Manager (MGM) på målnoder

Du kan lägga till IIS-serverrollen och DSC-tjänsten med guiden Lägg till roller och funktioner i Serverhanteraren eller med hjälp av PowerShell. Exempelskript som ingår i det här avsnittet kommer att hantera dessa steg du också.

## <a name="using-the-xdscwebservice-resource"></a>Resursnamnet xDSCWebService
Det enklaste sättet att konfigurera en pull-webbserver är att använda resursen xWebService ingår i modulen xPSDesiredStateConfiguration. Följande steg förklarar hur du använder resursen i en konfiguration som ställer in webbtjänsten.

1. Anropa den [installera modulen](https://technet.microsoft.com/en-us/library/dn807162.aspx) för att installera den **xPSDesiredStateConfiguration** modul. **Obs**: **installera modulen** ingår i den **PowerShellGet** module, som ingår i PowerShell 5.0. Du kan hämta den **PowerShellGet** -modul för PowerShell 3.0 och 4.0 på [PackageManagement PowerShell-moduler Preview](https://www.microsoft.com/en-us/download/details.aspx?id=49186). 
1. Hämta ett SSL-certifikat för DSC Pull-server från en betrodd certifikatutfärdare, antingen inom din organisation eller en offentlig myndighet. Certifikatet som togs emot från myndigheten är vanligtvis i PFX-format. Installera certifikatet på den nod som blir DSC Pull-servern i standardplatsen som ska vara CERT: \LocalMachine\My. Anteckna tumavtrycket för certifikatet.
1. Välj ett GUID som ska användas som nyckel för tjänstregistrering. Skapa ett med hjälp av PowerShell Skriv följande i PS-Kommandotolken och tryck på RETUR: '``` [guid]::newGuid()```'eller'```New-Guid```'. Den här nyckeln används av klientnoder som en delad nyckel för autentisering under registreringen. Mer information finns i avsnittet registreringsnyckel nedan.
1. I PowerShell ISE start (F5) följande konfigurationsskript (ingår i mappen exempel i den **xPSDesiredStateConfiguration** modulen som Sample_xDscWebService.ps1). Det här skriptet konfigurerar pull-server.
  
    ```powershell
    configuration Sample_xDscPullServer
    { 
        param  
        ( 
                [string[]]$NodeName = 'localhost', 

                [ValidateNotNullOrEmpty()] 
                [string] $certificateThumbPrint,

                [Parameter(Mandatory)]
                [ValidateNotNullOrEmpty()]
                [string] $RegistrationKey 
         ) 
         
         Import-DSCResource -ModuleName xPSDesiredStateConfiguration
         Import-DSCResource –ModuleName PSDesiredStateConfiguration

         Node $NodeName 
         { 
             WindowsFeature DSCServiceFeature 
             { 
                 Ensure = 'Present'
                 Name   = 'DSC-Service'             
             } 

             xDscWebService PSDSCPullServer 
             { 
                 Ensure                   = 'Present' 
                 EndpointName             = 'PSDSCPullServer' 
                 Port                     = 8080 
                 PhysicalPath             = "$env:SystemDrive\inetpub\PSDSCPullServer" 
                 CertificateThumbPrint    = $certificateThumbPrint          
                 ModulePath               = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Modules" 
                 ConfigurationPath        = "$env:PROGRAMFILES\WindowsPowerShell\DscService\Configuration" 
                 State                    = 'Started'
                 DependsOn                = '[WindowsFeature]DSCServiceFeature'     
                 UseSecurityBestPractices = $false
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

## <a name="registration-key"></a>Nyckel för tjänstregistrering
Så att klienten noder som ska registreras på servern så att de kan använda konfigurationsnamn i stället för ett konfigurations-ID, en registreringsnyckel som skapats av ovanstående konfiguration sparas i en fil med namnet `RegistrationKeys.txt` i `C:\Program Files\WindowsPowerShell\DscService`. Registreringsnyckeln som fungerar som en delad hemlighet som används under registreringen av klienten med pull-servern. Klienten genererar ett självsignerat certifikat som används för att autentisera unikt till den pull-servern när registreringen är slutförd. Tumavtrycket för certifikatet lagras lokalt och som är kopplade till URL-Adressen till den pull-servern.
> **Obs**: registreringsnycklar stöds inte i PowerShell 4.0. 

Nyckeln måste vara i metakonfigurationen för varje målnod i som ska registreras med den här pull-servern för att kunna konfigurera en nod för att autentisera med hämtningsservern i registreringen. Observera att den **RegistrationKey** i metakonfigurationen nedan tas bort när måldatorn har registrerats och att värdet '140a952b-b9d6-406b-b416-e0f759c9c0e4' måste matcha det värde som lagras i den RegistrationKeys.txt fil på hämtningsservern. Behandla alltid nyckelvärdet registrering på ett säkert sätt, eftersom att känna till det tillåter alla måldatorn registreras på pull-servern.

```powershell
[DSCLocalConfigurationManager()]
configuration PullClientConfigID
{
    Node localhost
    {
        Settings
        {
            RefreshMode          = 'Pull'
            RefreshFrequencyMins = 30 
            RebootNodeIfNeeded   = $true
        }
        
        ConfigurationRepositoryWeb CONTOSO-PullSrv
        {
            ServerURL          = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey    = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
            ConfigurationNames = @('ClientConfig')
        }   
        
        ReportServerWeb CONTOSO-PullSrv
        {
            ServerURL       = 'https://CONTOSO-PullSrv:8080/PSDSCPullServer.svc'
            RegistrationKey = '140a952b-b9d6-406b-b416-e0f759c9c0e4'
        }
    }
}

PullClientConfigID -OutputPath c:\Configs\TargetNodes
```
> **Obs**: den **ReportServerWeb** avsnittet kan rapportera data skickas till den pull-servern. 

Bristen på den **ConfigurationID** egenskapen i filen metakonfigurationen innebär att hämtningsservern stöder version 2 av protokollet för pull-server så att en inledande registrering krävs. Däremot förekomsten av en **ConfigurationID** innebär att V1-version av protokollet för pull-server används och det finns ingen registrering bearbetning.

>**Obs**: I en PUSH-scenariot ett programfel finns i den aktuella slutgiltiga som gör det nödvändigt att definiera en ConfigurationID-egenskap i filen metakonfigurationen för noder som aldrig har registrerats med en pull-server. Detta tvingar protokollet V1 Pull-Server och undvika fel registreringsmeddelanden.

## <a name="placing-configurations-and-resources"></a>Placera konfigurationer och resurser

När pull serverinstallationen är klar måste de mappar som definieras av den **ConfigurationPath** och **ModulePath** egenskaper i pull-serverkonfiguration är där du kan placera moduler och konfigurationer som ska vara tillgängliga för målnoder och hämtar. Filerna måste vara i ett specifikt format för pull-servern att bearbeta dem korrekt. 

### <a name="dsc-resource-module-package-format"></a>DSC resursformatet modulen paketet

Varje Resursmodul behöver zippade och namnet enligt följande mönster `{Module Name}_{Module Version}.zip`. Till exempel namnet en modul med namnet xWebAdminstration med en Modulversion av 3.1.2.0 'xWebAdministration_3.2.1.0.zip'. Varje version av en modul måste finnas i en enda zip-fil. Eftersom det finns endast en version av en resurs i formatet modulen lades till i WMF 5.0 med varje zip-filen stöds inte stöd för flera modulversioner i en katalog. Detta innebär att innan paketering in DSC resurs moduler för användning med pull-server behöver du göra en mindre ändring i katalogstrukturen. Moduler som innehåller DSC-resurs i WMF 5.0 standardformatet är ' {modulen mappen}\{Modulversion} \DscResources\{DSC resursmapp}\'. Innan paketering för pull-server bara ta bort den **{Modulversion}** mapp så blir sökvägen ' {modulen mappen} \DscResources\{DSC resursmapp}\'. Med den här ändringen zip-mappen som beskrivs ovan och placera dessa zip-filer i den **ModulePath** mapp.

Använd `new-dscchecksum {module zip file}` att skapa en kontrollsumma fil för modulen nyligen tillagda.

### <a name="configuration-mof-format"></a>Konfigurationen MOF-format 
En konfiguration MOF-fil måste kombineras med en fil kontrollsummor så att en MGM på målnoden kan validera konfigurationen. Om du vill skapa en kontrollsumma anropa den [ny DSCCheckSum](https://technet.microsoft.com/en-us/library/dn521622.aspx) cmdlet. Cmdlet tar en **sökväg** parameter som anger den mapp där konfigurationen MOF finns. Cmdleten skapar en kontrollsumma-fil med namnet `ConfigurationMOFName.mof.checksum`, där `ConfigurationMOFName` är namnet på konfigurationens mof-fil. Om det finns mer än en konfiguration MOF-filer i den angivna mappen, skapas en kontrollsumma för varje konfiguration i mappen. Placera MOF-filer och deras associerade kontrollsumma filer i den den **ConfigurationPath** mapp.

>**Obs**: Om du ändrar konfigurationen MOF-filen på något sätt, måste du också återskapa filen kontrollsumma.

## <a name="tooling"></a>Tooling
För att kunna utgör inställningen verifiera och hantera den pull-servern som är enklare, följande verktyg ingår som exemplen i den senaste versionen av modulen xPSDesiredStateConfiguration:
1. En modul som kan hjälpa dig i Paketera DSC resurs moduler och konfigurationsfilerna för användning på pull-server. [PublishModulesAndMofsToPullServer.psm1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PublishModulesAndMofsToPullServer.psm1). Exemplen nedan:

    ```powershell
        # Example 1 - Package all versions of given modules installed locally and MOF files are in c:\LocalDepot
         $moduleList = @("xWebAdministration", "xPhp") 
         Publish-DSCModuleAndMof -Source C:\LocalDepot -ModuleNameList $moduleList 

         # Example 2 - Package modules and mof documents from c:\LocalDepot
         Publish-DSCModuleAndMof -Source C:\LocalDepot -Force
    ```

1. Ett skript som kontrollerar pull-servern är korrekt konfigurerad. [PullServerSetupTests.ps1](https://github.com/PowerShell/xPSDesiredStateConfiguration/blob/dev/DSCPullServerSetup/PullServerDeploymentVerificationTest/PullServerSetupTests.ps1).


## <a name="pull-client-configuration"></a>Pull-klientkonfiguration 
I följande avsnitt beskrivs hur du konfigurerar pull-klienter i detalj:

* [Ställa in en DSC pull-klient som använder ett konfigurations-ID](pullClientConfigID.md)
* [Ställa in en DSC pull-klient med konfigurationsnamn](pullClientConfigNames.md)
* [Partiell konfigurationer](partialConfigs.md)


## <a name="see-also"></a>Se även
* [Windows PowerShell Desired State Configuration-översikt](overview.md)
* [Anta konfigurationer](enactingConfigurations.md)
* [Med hjälp av en DSC-rapportserver](reportServer.md)

