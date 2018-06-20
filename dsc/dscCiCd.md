---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skapa en kontinuerlig integrering och kontinuerlig distribution pipeline med DSC
ms.openlocfilehash: ce0f2ed79f5f96a1c38e0beaf32529aba7538963
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34190561"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Skapa en kontinuerlig integrering och kontinuerlig distribution pipeline med DSC

Det här exemplet visar hur du skapar en pipeline för kontinuerlig Integration/kontinuerlig distribution (CI/CD) med hjälp av PowerShell, DSC, Pester och Visual Studio Team Foundation Server (TFS).

När pipelinen har skapats och konfigurerats, du kan använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och tillhörande värdposter.
Den här processen simulerar den första delen av en pipeline som ska användas i en utvecklingsmiljö.

En automatisk CI/CD-pipeline kan du uppdatera programvara snabbare och mer tillförlitligt säkerställer att all kod testas och att det finns en aktuell version av din kod vid alla tidpunkter.

## <a name="prerequisites"></a>Förutsättningar

Om du vill använda det här exemplet, bör du känna till följande:

- CI-CD begrepp. En bra referens finns på [den versionen Pipeline modellen](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) datakälla
- Den [Pester](https://github.com/pester/Pester) testning framework
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Vad du behöver

Om du vill skapa och köra det här exemplet, behöver du en miljö med flera datorer och/eller virtuella datorer.

### <a name="client"></a>Klient

Detta är den dator där du ska göra allt arbete att installera och köra exemplet.

Klientdatorn måste vara en Windows-dator med följande installerat:
- [Git](https://git-scm.com/)
- en lokal git-lagringsplatsen klonad från https://github.com/PowerShell/Demo_CI
- en textredigerare, t.ex [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Den dator som värd för TFS-servern där du definierar din version och utgåva.
Datorn måste ha [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installerad.

### <a name="buildagent"></a>BuildAgent

Den dator som kör Windows Skapa agenten som bygger projektet.
Den här datorn måste ha en Windows Skapa agent installerad och körs.
Se [distribuerar en agent på Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) för instruktioner om hur du installerar och kör ett Windows Skapa agenten.

Du måste också installera både den `xDnsServer` och `xNetworking` DSC-moduler på den här datorn.

### <a name="testagent1"></a>TestAgent1

Detta är den dator som har konfigurerats som en DNS-server av DSC-konfigurationen i det här exemplet.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Detta är den dator som är värd för webbplatsen för det här exemplet konfigureras.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Lägg till kod till TFS

Vi börjar genom att skapa en Git-lagringsplats i TFS och importera koden från din lokala lagringsplats på klientdatorn.
Om du inte redan har klona Demo_CI databasen till en klientdator, gör du nu genom att köra följande kommando i git:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigera till TFS-servern i en webbläsare på klientdatorn.
1. I TFS, [skapa ett nytt grupprojekt](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) med namnet Demo_CI.

    Se till att **versionskontroll** är inställd på **Git**.
1. Lägg till en fjärransluten i databasen som du skapade i TFS med följande kommando på klientdatorn:

    `git remote add tfs <YourTFSRepoURL>`

    Där `<YourTFSRepoURL>` är klon-URL: en till TFS-databasen som du skapade i föregående steg.

    Om du inte vet var du hittar den här URL: en kan se [klona en befintlig Git-lagringsplatsen](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).
1. Skicka koden från din lokala lagringsplatsen till lagringsplatsen för TFS med följande kommando:

    `git push tfs --all`
1. TFS-databasen fylls med Demo_CI kod.

>**Obs:** det här exemplet används koden i den `ci-cd-example` grenen av Git-lagringsplatsen.
>Se till att ange den här grenen som standardförgrening i TFS-projektet och för CI/CD-utlösare som du skapar.

## <a name="understanding-the-code"></a>Förstå koden

Innan vi skapar bygg- och distributionsprocessen pipelines ska vi titta på några av kod för att förstå vad som händer.
På klientdatorn, öppna valfri textredigerare och navigera till roten i Demo_CI Git-lagringsplatsen.

### <a name="the-dsc-configuration"></a>DSC-konfigurationen

Öppna filen `DNSServer.ps1` (från roten för den lokala Demo_CI lagringsplatsen `./InfraDNS/Configs/DNSServer.ps1`).

Den här filen innehåller DSC-konfigurationen som ställer in DNS-servern. Det är här i sin helhet:

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

Observera den `Node` instruktionen:

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

Detta hittar de noder som har definierats som en roll `DNSServer` i den [konfigurationsdata](configData.md), som skapas av den `DevEnv.ps1` skript.

Med data för att definiera noder är viktigt när du gör CI eftersom noden informationen ändras troligen mellan miljöer och använder konfigurationsdata kan du enkelt göra ändringar i noden information utan att ändra konfigurationskoden.

I det första resurs blocket konfigurationen anropar den [WindowsFeature](windowsFeatureResource.md) så att DNS-funktionen är aktiverad.
Resurs-block som följer anropet resurser från den [xDnsServer](https://github.com/PowerShell/xDnsServer) modul för att konfigurera primär zon och DNS-poster.

Observera att två `xDnsRecord` block placeras i `foreach` slingor gå igenom matriser i konfigurationsdata.
Igen, konfigurationsdata skapas av den `DevEnv.ps1` skript som vi ska titta på Nästa.

### <a name="configuration-data"></a>Konfigurationsdata

Den `DevEnv.ps1` fil (från roten för den lokala Demo_CI lagringsplatsen `./InfraDNS/DevEnv.ps1`) anger miljö-specifika konfigurationsdata i en hash-tabell och skickar sedan den hash-tabellen till ett anrop till den `New-DscConfigurationDataDocument` funktion, som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Den `DevEnv.ps1` filen:

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

Den `New-DscConfigurationDataDocument` funktion (definieras i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmässigt skapar ett configuration datadokument från hashtable (noden data) och matris (data-nod) som skickas av `RawEnvData` och `OtherEnvData` parametrar.

I vårt fall bara i `RawEnvData` parametern används.

### <a name="the-psake-build-script"></a>Skriptet psake build

Den [psake](https://github.com/psake/psake) skapa skript som definierats i `Build.ps1` (från roten av lagringsplatsen Demo_CI `./InfraDNS/Build.ps1`) definierar uppgifter som ingår i versionen.
Den definierar också vilka aktiviteter som varje uppgift beror på.
När den anropas, skriptet psake garanterar att den angivna aktiviteten (eller aktiviteten `Default` om inget anges) körs och att alla beroenden även kör (detta är rekursiv, så att det körs beroenden av beroenden, och så vidare).

I detta exempel på `Default` aktivitet har definierats som:

```powershell
Task Default -depends UnitTests
```

Den `Default` aktiviteten har ingen implementering sig själv, men har ett beroende på den `CompileConfigs` aktivitet.
Den resulterande kedjan av beroenden för aktiviteten säkerställer att alla aktiviteter i build-skript körs.

I det här exemplet anropas skriptet psake av ett anrop till `Invoke-PSake` i den `Initiate.ps1` filen (som finns i roten på Demo_CI databasen):

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

När vi skapar build-definition i vårt exempel i TFS, levererar vi vårt psake skriptfilen som den `fileName` parametern för det här skriptet.

Build-skriptet definierar följande uppgifter:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Kör `DevEnv.ps1`, vilket genererar data konfigurationsfilen.

#### <a name="installmodules"></a>InstallModules

Installerar de moduler som krävs för konfigurationen `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Anrop av [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Kör den [Pester](https://github.com/pester/Pester/wiki) kontroller.

#### <a name="compileconfigs"></a>CompileConfigs

Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med konfigurationsdata som genererats av den `GenerateEnvironmentFiles` aktivitet.

#### <a name="clean"></a>Rensa

Skapar de mappar som ska användas för exemplet och tar bort alla testresultat och konfigurationsfiler för data moduler tidigare körs.

### <a name="the-psake-deploy-script"></a>Psake distribuera skriptet

Den [psake](https://github.com/psake/psake) distributionsskriptet som definierats i `Deploy.ps1` (från roten av lagringsplatsen Demo_CI `./InfraDNS/Deploy.ps1`) definierar uppgifter som att distribuera och kör sedan konfigurationen.

`Deploy.ps1` definierar följande uppgifter:

#### <a name="deploymodules"></a>DeployModules

Startar en PowerShell-session på `TestAgent1` och installerar de moduler som innehåller DSC-resurser som krävs för konfigurationen.

#### <a name="deployconfigs"></a>DeployConfigs

Anrop av [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) för att köra konfigurationen på `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Kör den [Pester](https://github.com/pester/Pester/wiki) integrering tester.

#### <a name="acceptancetests"></a>AcceptanceTests

Kör den [Pester](https://github.com/pester/Pester/wiki) godkännande tester.

#### <a name="clean"></a>Rensa

Tar bort alla moduler som installerats i föregående körs och ser till att testa resultatet mappen finns.

### <a name="test-scripts"></a>Testa skript

Godkännande, Integration och enheten tester definieras i skript i den `Tests` mapp (från roten av lagringsplatsen Demo_CI `./InfraDNS/Tests`), varje i filer med namnet `DNSServer.tests.ps1` i sina respektive mappar.

Testet skript använder [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

#### <a name="unit-tests"></a>Kontroller

Enheten testar test av DSC-konfigurationer själva så att konfigurationerna som kommer att göra vad som förväntas när de körs.
Enheten Testa skriptet använder [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integration tester

Integration testerna testa konfigurationen av systemet så att när du har integrerat med andra komponenter, systemet är konfigurerat som förväntat. Dessa tester köras på målnoden när den har konfigurerats med DSC.
Testa integrationsskriptet använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

#### <a name="acceptance-tests"></a>Godkännande tester

Godkännande testerna testar system för att säkerställa att den fungerar som förväntat.
Till exempel tester för att säkerställa en webbsida returnerar rätt information när en förfrågan.
Dessa tester fjärrköra från målnoden för att testa verkliga scenarier.
Testa integrationsskriptet använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

## <a name="define-the-build"></a>Definiera bygga

Nu när vi har överfört vår kod till TFS och tittar på syfte, definiera våra build.

Här kan rapporterar vi bara de build steg som du lägger till i versionen. Anvisningar om hur du skapar en build-definition i TFS finns [skapa och kön en definition av build](https://www.visualstudio.com/en-us/docs/build/define/create).

Skapa en ny build-definition (Välj den **tom** mall) med namnet ”InfraDNS”.
Lägg till följande steg ska du skapa definition:

- PowerShell-skript
- Publicera testresultat
- Kopiera filer
- Publicera artefakt

När du lägger till dessa steg skapa, redigera egenskaperna för varje steg på följande sätt:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange den **typen** egenskapen `File Path`.
1. Ange den **skriptsökvägen** egenskapen `initiate.ps1`.
1. Lägg till `-fileName build` till den **argument** egenskapen.

Det här build-steget körs den `initiate.ps1` -fil, som anropar psake build-skript.

### <a name="publish-test-results"></a>Publicera testresultat

1. Ange **testa Resultatformatet** till `NUnit`
1. Ange **Test resulterar filer** till `InfraDNS/Tests/Results/*.xml`
1. Ange **testa kör rubrik** till `Unit`.
1. Kontrollera att **alternativ för åtkomstkontroll** **aktiverad** och **körs alltid** är båda markerade.

Det här steget build körs testerna enhet i skriptet Pester vi har tittat på tidigare och lagrar resultatet i den `InfraDNS/Tests/Results/*.xml` mapp.

### <a name="copy-files"></a>Kopiera filer

1. Lägg till följande rader till **innehållet**:

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. Ange **TargetFolder** till `$(Build.ArtifactStagingDirectory)\`

Det här steget kopierar bygga och testa skript i uppsamlingskatalogen så som de kan publiceras som skapa artefakter med nästa steg.

### <a name="publish-artifact"></a>Publicera artefakt

1. Ange **sökvägen till publicera** till `$(Build.ArtifactStagingDirectory)\`
1. Ange **artefakt namnet** till `Deploy`
1. Ange **typ av artefakt** till `Server`
1. Välj `Enabled` i **alternativ**

## <a name="enable-continuous-integration"></a>Aktivera kontinuerlig integration

Nu vi ställer in en utlösare som orsakar projektet för att skapa varje gång en ändring har checkats in till den `ci-cd-example` grenen av git-lagringsplats.

1. I TFS, klickar du på den **Skapa & släpper** fliken
1. Välj den `DNS Infra` skapa definition, och klicka på **redigera**
1. Klicka på den **utlösare** fliken
1. Välj **kontinuerlig integration (KO)**, och välj `refs/heads/ci-cd-example` i listrutan gren
1. Klicka på **spara** och sedan **OK**

Nu ändras något i TFS git-lagringsplatsen utlösare en automatiserad version.

## <a name="create-the-release-definition"></a>Skapa en definition för versionen

Nu ska vi skapa en definition av versionen så att projektet har distribuerats till utvecklingsmiljö med varje kod incheckning.

För att göra detta, lägger du till en ny version som är associerade med den `InfraDNS` skapa definition som du skapade tidigare.
Se till att välja **kontinuerlig distribution** så att en ny version ska utlösas när en ny version har slutförts.
([Så här: arbeta med definitioner av versionen](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) och konfigurera den på följande sätt:

Lägg till följande steg i definitionen för versionen:

- PowerShell-skript
- Publicera testresultat
- Publicera testresultat

Redigera stegen på följande sätt:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange den **skriptsökvägen** till `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ange den **argument** till `-fileName Deploy`

### <a name="first-publish-test-results"></a>Publicera testresultat

1. Välj `NUnit` för den **Test Resultatformatet** fält
1. Ange den **resultatet Testfiler** till `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ange den **testa kör rubrik** till `Integration`
1. Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**

### <a name="second-publish-test-results"></a>Andra publicera testresultat

1. Välj `NUnit` för den **Test Resultatformatet** fält
1. Ange den **resultatet Testfiler** till `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ange den **testa kör rubrik** till `Acceptance`
1. Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**

## <a name="verify-your-results"></a>Kontrollera resultatet

Nu när du trycker på ändringar den `ci-cd-example` startar gren till TFS, en ny version.
Om versionen har slutförts, utlöses en ny distribution.

Du kan kontrollera resultatet av distributionen genom att öppna en webbläsare på klientdatorn och gå till `www.contoso.com`.

## <a name="next-steps"></a>Nästa steg

Det här exemplet konfigureras DNS-servern `TestAgent1` så att URL: en `www.contoso.com` matchar `TestAgent2`, men det inte att distribuera en webbplats.
Stommen för att göra det tillhandahålls i lagringsplatsen under den `WebApp` mapp.
Du kan använda stub-rutiner som hjälper för att skapa psake skript, Pester testerna och DSC-konfigurationer för att distribuera din egen webbplats.