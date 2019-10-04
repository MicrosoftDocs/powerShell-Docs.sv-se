---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Skapa en kontinuerlig integrering och en pipeline för kontinuerlig distribution med DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71942148"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Skapa en kontinuerlig integrering och en pipeline för kontinuerlig distribution med DSC

Det här exemplet visar hur du skapar en pipeline för kontinuerlig integrering/distribution (CI/CD) med hjälp av PowerShell, DSC, pester och Visual Studio Team Foundation Server (TFS).

När pipelinen har skapats och kon figurer ATS kan du använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och associerade värd poster.
Den här processen simulerar den första delen av en pipeline som används i en utvecklings miljö.

En automatiserad CI/CD-pipeline hjälper dig att uppdatera program vara snabbare och mer tillförlitligt, se till att all kod testas och att en aktuell version av din kod är tillgänglig hela tiden.

## <a name="prerequisites"></a>Förutsättningar

För att kunna använda det här exemplet bör du vara bekant med följande:

- CI-CD-koncept. En lämplig referens finns i [modell för versions pipeline](https://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) -datakälla
- [Pester](https://github.com/pester/Pester) test Framework
- [Team Foundation-Server](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a>Vad du behöver

För att skapa och köra det här exemplet behöver du en miljö med flera datorer och/eller virtuella datorer.

### <a name="client"></a>Klient

Det här är den dator där du utför all arbets inställning och kör exemplet.

Klient datorn måste vara en Windows-dator med följande installerat:

- [Git](https://git-scm.com/)
- en lokal git-lagrings platsen klonas från https://github.com/PowerShell/Demo_CI
- en text redigerare, till exempel [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Datorn som är värd för TFS-servern där du definierar build och version.
Den här datorn måste ha [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installerat.

### <a name="buildagent"></a>BuildAgent

Datorn som kör Windows build-agenten som bygger projektet.
Datorn måste ha en Windows build-agent installerad och igång.
Se [distribuera en agent i Windows](/azure/devops/pipelines/agents/v2-windows) för instruktioner om hur du installerar och kör en Windows build-agent.

Du måste också installera både `xDnsServer`-och `xNetworking` DSC-moduler på den här datorn.

### <a name="testagent1"></a>TestAgent1

Detta är den dator som är konfigurerad som en DNS-server av DSC-konfigurationen i det här exemplet.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Detta är den dator som är värd för webbplatsen som exemplet konfigurerar.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Lägg till koden i TFS

Vi börjar med att skapa en git-lagringsplats i TFS och importera koden från din lokala lagrings plats på klient datorn.
Om du inte redan har klonat Demo_CI-lagringsplatsen till klient datorn gör du det nu genom att köra följande git-kommando:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigera till din TFS-server i en webbläsare på klient datorn.
1. I TFS [skapar du ett nytt grup projekt](/azure/devops/organizations/projects/create-project) med namnet Demo_CI.

   Kontrol lera att **versions kontroll** är inställt på **git**.
1. På klient datorn lägger du till en fjärr anslutning till den lagrings plats som du nyss skapade i TFS med följande kommando:

   `git remote add tfs <YourTFSRepoURL>`

   Där `<YourTFSRepoURL>` är klon-URL: en till TFS-lagringsplatsen som du skapade i föregående steg.

   Om du inte vet var du hittar den här URL: en kan du läsa [klona en befintlig git-lagrings platsen](/azure/devops/repos/git/clone).
1. Skicka koden från din lokala lagrings plats till TFS-lagringsplatsen med följande kommando:

   `git push tfs --all`
1. TFS-lagringsplatsen fylls med Demo_CI-koden.

> [!NOTE]
> I det här exemplet används koden i `ci-cd-example`-grenen för git-lagrings platsen.
> Se till att ange den här grenen som standard gren i ditt TFS-projekt och för de CI/CD-utlösare som du skapar.

## <a name="understanding-the-code"></a>Förstå koden

Innan vi skapar pipelinen build och Deployment kan vi titta på en del av koden för att förstå vad som händer.
Öppna din favorit text redigerare på klient datorn och gå till roten för din Demo_CI git-lagringsplats.

### <a name="the-dsc-configuration"></a>DSC-konfigurationen

Öppna filen `DNSServer.ps1` (från roten i den lokala Demo_CI-lagringsplatsen `./InfraDNS/Configs/DNSServer.ps1`).

Den här filen innehåller DSC-konfigurationen som konfigurerar DNS-servern. Här är dess helhet:

```powershell
configuration DNSServer
{
    Import-DscResource -module 'xDnsServer','xNetworking', 'PSDesiredStateConfiguration'

    Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
    {
        WindowsFeature DNS
        {
            Ensure  = 'Present'
            Name    = 'DNS'
        }

        xDnsServerPrimaryZone $Node.zone
        {
            Ensure    = 'Present'
            Name      = $Node.Zone
            DependsOn = '[WindowsFeature]DNS'
        }

        foreach ($ARec in $Node.ARecords.keys) {
            xDnsRecord $ARec
            {
                Ensure    = 'Present'
                Name      = $ARec
                Zone      = $Node.Zone
                Type      = 'ARecord'
                Target    = $Node.ARecords[$ARec]
                DependsOn = '[WindowsFeature]DNS'
            }
        }

        foreach ($CName in $Node.CNameRecords.keys) {
            xDnsRecord $CName
            {
                Ensure    = 'Present'
                Name      = $CName
                Zone      = $Node.Zone
                Type      = 'CName'
                Target    = $Node.CNameRecords[$CName]
                DependsOn = '[WindowsFeature]DNS'
            }
        }
    }
}
```

Observera `Node`-satsen:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Detta hittar alla noder som har definierats som en roll för `DNSServer` i [konfigurations data](../configurations/configData.md), som skapas av `DevEnv.ps1`-skriptet.

Du kan läsa mer om metoden `Where` i [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)

Att använda konfigurations data för att definiera noder är viktigt när du använder CI eftersom Node-information troligen kommer att ändras mellan miljöer, och med hjälp av konfigurations data kan du enkelt göra ändringar i Node-informationen utan att ändra konfigurations koden.

I det första resurs blocket anropar konfigurationen **WindowsFeature** för att se till att DNS-funktionen är aktive rad.
Resurs blocken som följer anrops resurser från [xDnsServer](https://github.com/PowerShell/xDnsServer) -modulen för att konfigurera den primära zonen och DNS-poster.

Observera att de två `xDnsRecord`-blocken är omslutna i `foreach`-slingor som itererar genom matriser i konfigurations data.
Sedan skapas konfigurations data av skriptet `DevEnv.ps1`, som vi ska titta på härnäst.

### <a name="configuration-data"></a>Konfigurationsdata

@No__t-0-filen (från roten i den lokala Demo_CI-lagringsplatsen `./InfraDNS/DevEnv.ps1`) anger miljödefinierade konfigurations data i en hash-hash och skickar sedan den hash-tabellen till ett anrop till funktionen `New-DscConfigurationDataDocument`, som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Filen `DevEnv.ps1`:

```powershell
param(
    [parameter(Mandatory=$true)]
    [string]
    $OutputPath
)

Import-Module $PSScriptRoot\..\Assets\DscPipelineTools\DscPipelineTools.psd1 -Force

# Define Unit Test Environment
$DevEnvironment = @{
    Name                        = 'DevEnv';
    Roles = @(
        @{  Role                = 'DNSServer';
            VMName              = 'TestAgent1';
            Zone                = 'Contoso.com';
            ARecords            = @{'TFSSrv1'= '10.0.0.10';'Client'='10.0.0.15';'BuildAgent'='10.0.0.30';'TestAgent1'='10.0.0.40';'TestAgent2'='10.0.0.50'};
            CNameRecords        = @{'DNS' = 'TestAgent1.contoso.com'};
        }
    )
}

Return New-DscConfigurationDataDocument -RawEnvData $DevEnvironment -OutputPath $OutputPath
```

Funktionen `New-DscConfigurationDataDocument` (definieras i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) skapar program mässigt ett konfigurations data dokument från hash-tabellen (Node data) och matrisen (icke-Node-data) som skickas som `RawEnvData`-och `OtherEnvData`-parametrar.

I vårt fall används endast parametern `RawEnvData`.

### <a name="the-psake-build-script"></a>Psake build-skriptet

[Psake](https://github.com/psake/psake) build-skriptet som definieras i `Build.ps1` (från roten i Demo_CI-lagringsplatsen `./InfraDNS/Build.ps1`) definierar uppgifter som ingår i versionen.
Den definierar också vilka andra aktiviteter varje aktivitet är beroende av.
När det anropas, ser psake-skriptet till att den angivna aktiviteten (eller aktiviteten med namnet `Default` om inget anges) körs, och att alla beroenden också körs (detta är rekursivt, så att beroenden av beroenden körs, och så vidare).

I det här exemplet definieras aktiviteten `Default` som:

```powershell
Task Default -depends UnitTests
```

Aktiviteten `Default` har ingen implementering, men har ett beroende av aktiviteten @no__t 1.
Den resulterande kedjan med aktivitets beroenden säkerställer att alla aktiviteter i build-skriptet körs.

I det här exemplet anropas psake-skriptet av ett anrop till `Invoke-PSake` i `Initiate.ps1`-filen (finns i roten av Demo_CI-lagringsplatsen):

```powershell
param(
    [parameter()]
    [ValidateSet('Build','Deploy')]
    [string]
    $fileName
)

#$Error.Clear()

Invoke-PSake $PSScriptRoot\InfraDNS\$fileName.ps1

<#if($Error.count)
{
    Throw "$fileName script failed. Check logs for failure details."
}
#>
```

När vi skapar build-definitionen för vårt exempel i TFS, kommer vi att ange vår psake-skriptfil som parametern `fileName` för det här skriptet.

Bygg skriptet definierar följande uppgifter:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Kör `DevEnv.ps1`, vilket genererar konfigurations data filen.

#### <a name="installmodules"></a>InstallModules

Installerar modulerna som krävs av konfigurationen `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Anropar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Kör [pester](https://github.com/pester/Pester/wiki) Unit-tester.

#### <a name="compileconfigs"></a>CompileConfigs

Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med hjälp av konfigurations data som genererats av aktiviteten @no__t 1.

#### <a name="clean"></a>Rensa

Skapar mapparna som används för exemplet och tar bort alla test resultat, konfigurationsfiler för data och moduler från tidigare körningar.

### <a name="the-psake-deploy-script"></a>Skript för psake-distribution

Det [psake](https://github.com/psake/psake) distributions skript som definierats i `Deploy.ps1` (från roten i Demo_CI-lagringsplatsen `./InfraDNS/Deploy.ps1`) definierar aktiviteter som distribuerar och kör konfigurationen.

`Deploy.ps1` definierar följande uppgifter:

#### <a name="deploymodules"></a>DeployModules

Startar en PowerShell-session på `TestAgent1` och installerar de moduler som innehåller de DSC-resurser som krävs för konfigurationen.

#### <a name="deployconfigs"></a>DeployConfigs

Anropar cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) för att köra konfigurationen på `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Kör [pester](https://github.com/pester/Pester/wiki) -integrations test.

#### <a name="acceptancetests"></a>AcceptanceTests

Kör testerna för [pester](https://github.com/pester/Pester/wiki) -godkännande.

#### <a name="clean"></a>Rensa

Tar bort alla moduler som är installerade i tidigare körningar och ser till att mappen test resultat finns.

### <a name="test-scripts"></a>Test skript

Godkännande-, integrations-och enhets test definieras i skript i mappen `Tests` (från roten i Demo_CI-lagringsplatsen `./InfraDNS/Tests`), var och en i filer med namnet `DNSServer.tests.ps1` i respektive mapp.

Test skripten använder syntaxen [pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) .

#### <a name="unit-tests"></a>Enhets tester

Enhets testerna testar själva DSC-konfigurationen för att se till att konfigurationerna kommer att göra vad som förväntas när de körs.
Enhets test skriptet använder [pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integrations test

Integrerings testerna testar systemets konfiguration för att säkerställa att när det är integrerat med andra komponenter, konfigureras systemet som förväntat. De här testerna körs på målnoden när den har kon figurer ATS med DSC.
Integrations test skriptet använder en blandning av [pester](https://github.com/pester/Pester/wiki) -och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxen.

#### <a name="acceptance-tests"></a>Acceptans test

Test av godkännande testar systemet för att se till att det fungerar som förväntat.
Till exempel testar den för att se till att en webb sida returnerar rätt information när den efter frågas.
De här testerna körs på distans från målnoden för att kunna testa verkliga scenarier.
Integrations test skriptet använder en blandning av [pester](https://github.com/pester/Pester/wiki) -och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxen.

## <a name="define-the-build"></a>Definiera versionen

Nu när vi har laddat upp vår kod till TFS och tittat på vad det gör kan vi definiera vår version.

Här kommer vi bara att se de build-steg som du kommer att lägga till i versionen. Instruktioner för hur du skapar en bygge-definition i TFS finns i [skapa och köa en build-definition](/azure/devops/pipelines/create-first-pipeline).

Skapa en ny Bygg definition (Välj den **tomma** mallen) med namnet "InfraDNS".
Lägg till följande steg i bygg definitionen:

- PowerShell-skript
- Publicera Testresultat
- Kopiera filer
- Publicera artefakt

När du har lagt till dessa build-steg redigerar du egenskaperna för varje steg enligt följande:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange egenskapen **Type** till `File Path`.
1. Ange egenskapen för **skript Sök vägen** till `initiate.ps1`.
1. Lägg till `-fileName build` i egenskapen **arguments** .

Det här build-steget Kör filen `initiate.ps1`, som anropar psake build-skriptet.

### <a name="publish-test-results"></a>Publicera Testresultat

1. Ange **test resultat format** till `NUnit`
1. Ange **testresultat-filer** till `InfraDNS/Tests/Results/*.xml`
1. Ange `Unit` för **testets körnings rubrik** .
1. Kontrol lera att **kontroll alternativen** **är aktiverade** och att **alltid körs** båda är markerade.

Det här build-steget Kör enhets testerna i pester-skriptet som vi såg tidigare och lagrar resultaten i mappen `InfraDNS/Tests/Results/*.xml`.

### <a name="copy-files"></a>Kopiera filer

1. Lägg till var och en av följande rader i **innehållet**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Ange **TargetFolder** till `$(Build.ArtifactStagingDirectory)\`

I det här steget kopieras bygg-och test skript till uppsamlings katalogen så att kan publiceras som build-artefakter i nästa steg.

### <a name="publish-artifact"></a>Publicera artefakt

1. Ange **sökväg för att publicera** till `$(Build.ArtifactStagingDirectory)\`
1. Ange **artefakt namn** till `Deploy`
1. Ange **artefakt typ** till `Server`
1. Välj `Enabled` i **kontroll alternativ**

## <a name="enable-continuous-integration"></a>Aktivera kontinuerlig integrering

Nu ska vi konfigurera en utlösare som gör att projektet skapas varje gång en ändring checkas in i `ci-cd-example`-grenen av Git-lagringsplatsen.

1. I TFS klickar du på fliken **Build & version**
1. Välj build-definitionen `DNS Infra` och klicka på **Redigera**
1. Klicka på fliken **utlösare**
1. Välj **kontinuerlig integrering (CI)** och välj `refs/heads/ci-cd-example` i list rutan gren
1. Klicka på **Spara** och sedan på **OK**

Nu utlöser alla ändringar i TFS git-lagringsplatsen en automatiserad version.

## <a name="create-the-release-definition"></a>Skapa versions definitionen

Nu ska vi skapa en versions definition så att projektet distribueras till utvecklings miljön med varje kod incheckning.

Det gör du genom att lägga till en ny versions definition som är associerad med den `InfraDNS` Build-definition som du skapade tidigare.
Se till att välja **kontinuerlig distribution** så att en ny version utlöses när en ny version har slutförts.
([Vad är Frisläpp pipelines?](/azure/devops/pipelines/release/)) och konfigurera det enligt följande:

Lägg till följande steg i versions definitionen:

- PowerShell-skript
- Publicera Testresultat
- Publicera Testresultat

Redigera stegen enligt följande:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange fältet **skript Sök väg** till `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ange **argument** fältet till `-fileName Deploy`

### <a name="first-publish-test-results"></a>Första publicerings Testresultat

1. Välj `NUnit` för fältet **test resultat format**
1. Ange fältet **test resultat** till `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ställ in **testets körnings titel** på `Integration`
1. Under **kontroll alternativ**markerar du **Kör alltid**

### <a name="second-publish-test-results"></a>Andra publicerings Testresultat

1. Välj `NUnit` för fältet **test resultat format**
1. Ange fältet **test resultat** till `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ställ in **testets körnings titel** på `Acceptance`
1. Under **kontroll alternativ**markerar du **Kör alltid**

## <a name="verify-your-results"></a>Verifiera dina resultat

Nu när du push-överför ändringar i `ci-cd-example`-grenen till TFS, kommer en ny version att starta.
Om skapandet har slutförts utlöses en ny distribution.

Du kan kontrol lera resultatet av distributionen genom att öppna en webbläsare på klient datorn och gå till `www.contoso.com`.

## <a name="next-steps"></a>Nästa steg

I det här exemplet konfigureras DNS-servern `TestAgent1` så att URL: en `www.contoso.com` matchar `TestAgent2`, men den distribuerar inte en webbplats.
Skeleton för att göra detta finns i mappen lagrings platsen under mappen `WebApp`.
Du kan använda de tillhandahållna stub-skripten för att skapa psake-skript, pester-tester och DSC-konfigurationer för att distribuera din egen webbplats.
