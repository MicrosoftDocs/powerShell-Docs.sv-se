---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skapa en pipeline för kontinuerlig integrering och kontinuerlig distribution med DSC
ms.openlocfilehash: c305d9bc7e0f8c659129b5a20d0b7e8b34d09ba8
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405248"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a>Skapa en pipeline för kontinuerlig integrering och kontinuerlig distribution med DSC

Det här exemplet visar hur du skapar en pipeline för kontinuerlig integrering/kontinuerlig distribution (CI/CD) med hjälp av PowerShell, DSC, Pester och Visual Studio Team Foundation Server (TFS).

När pipelinen har skapats och konfigurerats, du kan använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och tillhörande värdposter.
Den här processen simulerar den första delen av en pipeline som skulle användas i en utvecklingsmiljö.

En automatiserad CI/CD-pipeline kan du uppdatera programvara snabbare och mer tillförlitligt att säkerställa att all kod har testats och att det är en aktuell version av din kod vid alla tidpunkter.

## <a name="prerequisites"></a>Förutsättningar

Om du vill använda det här exemplet, bör du känna till följande:

- CI-CD-begrepp. En bra referens finns på [The Release Pipeline modellen](http://aka.ms/thereleasepipelinemodelpdf).
- [Git](https://git-scm.com/) källkontroll
- Den [Pester](https://github.com/pester/Pester) xcuitest
- [Team Foundation Server](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a>Vad du behöver

Om du vill skapa och köra det här exemplet, behöver du en miljö med flera datorer och/eller virtuella datorer.

### <a name="client"></a>Klient

Det här är den dator där du ska göra allt arbete som konfigurerar och kör exemplet.

Klientdatorn måste vara en Windows-dator med följande installerat:

- [Git](https://git-scm.com/)
- en lokal git-lagringsplats som klonas från https://github.com/PowerShell/Demo_CI
- en textredigerare, till exempel [Visual Studio Code](https://code.visualstudio.com/)

### <a name="tfssrv1"></a>TFSSrv1

Den dator som är värd för TFS-servern där du definierar din version och utgåva.
Den här datorn måste ha [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installerad.

### <a name="buildagent"></a>BuildAgent

Den dator som kör Windows Skapa agenten som bygger på projektet.
Den här datorn måste ha en Windows Skapa agenten installerad och igång.
Se [distribuerar en agent på Windows](/azure/devops/pipelines/agents/v2-windows) för instruktioner om hur du installerar och kör ett Windows Skapa agenten.

Du måste också installera både den `xDnsServer` och `xNetworking` DSC-moduler på den här datorn.

### <a name="testagent1"></a>TestAgent1

Det här är den dator som är konfigurerad som en DNS-server av DSC-konfigurationen i det här exemplet.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

### <a name="testagent2"></a>TestAgent2

Det här är den dator som är värd för webbplatsen som det här exemplet konfigurerar.
Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).

## <a name="add-the-code-to-tfs"></a>Lägg till kod till TFS

Vi börjar genom att skapa en Git-lagringsplats i TFS och importera koden från din lokala lagringsplats på klientdatorn.
Om du inte redan har klonat lagringsplatsen Demo_CI till klientdatorn gör du nu genom att köra följande git-kommando:

`git clone https://github.com/PowerShell/Demo_CI`

1. Navigera till TFS-servern i en webbläsare på din klientdator.
1. I TFS, [skapa ett nytt grupprojekt](/azure/devops/organizations/projects/create-project) med namnet Demo_CI.

   Se till att **versionskontroll** är inställd på **Git**.
1. Lägg till en fjärransluten i databasen som du skapade i TFS med följande kommando på klientdatorn:

   `git remote add tfs <YourTFSRepoURL>`

   Där `<YourTFSRepoURL>` är URL-klonen i TFS-databasen som du skapade i föregående steg.

   Om du inte vet var du hittar den här URL: en kan se [klona en befintlig Git-lagringsplats](/azure/devops/repos/git/clone).
1. Skicka koden från din lokala lagringsplats till TFS-lagringsplatsen med följande kommando:

   `git push tfs --all`
1. TFS-databasen fylls med Demo_CI kod.

> [!NOTE]
> Det här exemplet använder koden i den `ci-cd-example` grenen av Git-lagringsplats.
> Se till att ange den här grenen som standardgren i TFS-projektet och för CI/CD-utlösare som du skapar.

## <a name="understanding-the-code"></a>Så här fungerar koden

Innan vi skapar bygg- och distributionsledningar ska vi titta på några av koden för att förstå vad som händer.
På klientdatorn, öppna valfri textredigerare och navigera till roten i Demo_CI Git-lagringsplatsen.

### <a name="the-dsc-configuration"></a>DSC-konfiguration

Öppna filen `DNSServer.ps1` (från roten för den lokala lagringsplatsen Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).

Den här filen innehåller den DSC-konfiguration som konfigurerar DNS-servern. Här är det i sin helhet:

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

Detta söker efter alla noder som har definierats som har rollen `DNSServer` i den [konfigurationsdata](../configurations/configData.md), som skapas av den `DevEnv.ps1` skript.

Du kan läsa mer om den `Where` -metod i [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)

Det är viktigt att med konfigurationsdata för att definiera noder när du gör CI eftersom nodinformation troligen kommer att förändras mellan miljöer och använder konfigurationsdata kan du enkelt göra ändringar i noden information utan att ändra konfigurationskoden.

I det första resource blocket konfigurationen anropar den **WindowsFeature** så att DNS-funktionen är aktiverad.
Resurs-block som följer anrop resurser från den [xDnsServer](https://github.com/PowerShell/xDnsServer) modul för att konfigurera primär zon och DNS-poster.

Observera att två `xDnsRecord` block är omslutna i `foreach` slingor gå igenom matriser i konfigurationsdata.
Igen, konfigurationsdata har skapats av den `DevEnv.ps1` skript som vi ska titta på Nästa.

### <a name="configuration-data"></a>Konfigurationsdata

Den `DevEnv.ps1` fil (från roten för den lokala lagringsplatsen Demo_CI `./InfraDNS/DevEnv.ps1`) anger miljöspecifika konfigurationsdata i en hash-tabell och skickar den hash-tabellen till ett anrop till den `New-DscConfigurationDataDocument` som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).

Den `DevEnv.ps1` fil:

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

Den `New-DscConfigurationDataDocument` funktion (definieras i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmässigt skapar en konfigurationsdokumentet data från den hash-tabell (noddata) och matrisen (icke-noden data) som skickas som den `RawEnvData` och `OtherEnvData` parametrar.

I vårt fall bara i `RawEnvData` parametern används.

### <a name="the-psake-build-script"></a>Build-skriptet psake

Den [psake](https://github.com/psake/psake) skapa skript som definierats i `Build.ps1` (från roten för lagringsplatsen Demo_CI `./InfraDNS/Build.ps1`) definierar uppgifter som ingår i versionen.
Den definierar även vilka uppgifter som varje aktivitet beror på.
När anropats skriptet psake säkerställer att den angivna aktiviteten (eller aktiviteten `Default` om inget anges) körs och att alla beroenden även kör (detta är rekursiv, så att beroenden för beroenden körs, och så vidare).

I det här exemplet på `Default` uppgift definieras som:

```powershell
Task Default -depends UnitTests
```

Den `Default` uppgiften har ingen implementering själva, men har ett beroende på den `CompileConfigs` uppgift.
Den resulterande kedjan av aktivitetsberoenden säkerställer att alla aktiviteter i build-skriptet körs.

I det här exemplet skriptet psake startas av ett anrop till `Invoke-PSake` i den `Initiate.ps1` filen (som finns i roten för lagringsplatsen Demo_CI):

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

När vi skapar byggesdefinition i vårt exempel i TFS, ska vi ange vår psake skriptfilen som den `fileName` parameter för det här skriptet.

Build-skriptet definierar följande uppgifter:

#### <a name="generateenvironmentfiles"></a>GenerateEnvironmentFiles

Körningar `DevEnv.ps1`, vilket genererar konfigurationsdatafilen.

#### <a name="installmodules"></a>InstallModules

Installerar moduler som krävs av konfigurationen `DNSServer.ps1`.

#### <a name="scriptanalysis"></a>ScriptAnalysis

Anropar den [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).

#### <a name="unittests"></a>UnitTests

Körs den [Pester](https://github.com/pester/Pester/wiki) enhetstester.

#### <a name="compileconfigs"></a>CompileConfigs

Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med hjälp av configuration-data som genereras av den `GenerateEnvironmentFiles` uppgift.

#### <a name="clean"></a>Rensa

Skapar de mappar som ska användas för det här exemplet och tar bort alla testresultat och konfigurationsdatafiler moduler från tidigare körningar.

### <a name="the-psake-deploy-script"></a>Psake distribuera skriptet

Den [psake](https://github.com/psake/psake) distributionsskriptet som definierats i `Deploy.ps1` (från roten för lagringsplatsen Demo_CI `./InfraDNS/Deploy.ps1`) definierar uppgifter som att distribuera och kör sedan konfigurationen.

`Deploy.ps1` definierar följande uppgifter:

#### <a name="deploymodules"></a>DeployModules

Startar en PowerShell-session på `TestAgent1` och installerar de moduler som innehåller DSC-resurser som krävs för konfigurationen.

#### <a name="deployconfigs"></a>DeployConfigs

Anropar den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet för att köra konfigurationen på `TestAgent1`.

#### <a name="integrationtests"></a>IntegrationTests

Körs den [Pester](https://github.com/pester/Pester/wiki) integreringstester.

#### <a name="acceptancetests"></a>AcceptanceTests

Körs den [Pester](https://github.com/pester/Pester/wiki) acceptanstester.

#### <a name="clean"></a>Rensa

Tar bort alla moduler som installerats i tidigare körningar och ser till att testa resultatet mappen finns.

### <a name="test-scripts"></a>Testa skript

Godkännande, Integration och enhet tester har definierats i skripten i den `Tests` mapp (från roten för lagringsplatsen Demo_CI `./InfraDNS/Tests`), var och en i filer med namnet `DNSServer.tests.ps1` i sina respektive mappar.

Testet skript använder [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

#### <a name="unit-tests"></a>Enhetstester

Testa DSC-konfigurationer själva så att konfigurationerna som kommer att göra vad som förväntas när de kör jednotek.
Skriptet använder enhetstestar [Pester](https://github.com/pester/Pester/wiki).

#### <a name="integration-tests"></a>Integreringstester

Integreringstester testa konfigurationen av systemet för att se till att när du har integrerat med andra komponenter i systemet konfigureras som förväntat. De här testerna körs på målnoden när den har konfigurerats med DSC.
Testskriptet integration använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

#### <a name="acceptance-tests"></a>Acceptanstester

Acceptanstester testa systemet för att säkerställa att det fungerar som förväntat.
Till exempel tester för att säkerställa att en webbsida returnerar rätt information när en förfrågan.
De här testerna körs via en fjärranslutning från målnoden för att testa verkliga scenarier.
Testskriptet integration använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.

## <a name="define-the-build"></a>Definiera versionen

Nu när vi har överfört vår kod till TFS och tittat på vad det gör vi definiera vår build.

Här kan upp vi endast byggsteg som du lägger till i bygget. Mer information om hur du skapar en byggesdefinition i TFS, finns i [skapa och kön en byggesdefinition](/azure/devops/pipelines/get-started-designer).

Skapa en ny build-definition (Välj den **tom** mall) med namnet ”InfraDNS”.
Lägg till följande steg för att du build-definition:

- PowerShell-skript
- Publicera testresultat
- Kopiera filer
- Publicera artefakter

När du lägger till dessa bygg steg, redigera egenskaperna för varje steg på följande sätt:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange den **typ** egenskap `File Path`.
1. Ange den **skriptets sökväg** egenskap `initiate.ps1`.
1. Lägg till `-fileName build` till den **argument** egenskapen.

Det här steget för att bygga körs den `initiate.ps1` -fil som anropar psake build-skriptet.

### <a name="publish-test-results"></a>Publicera testresultat

1. Ange **testa Resultatformatet** till `NUnit`
1. Ange **Test resulterar filer** till `InfraDNS/Tests/Results/*.xml`
1. Ange **testa kör rubrik** till `Unit`.
1. Se till att **alternativ för åtkomstkontroll** **aktiverad** och **körs alltid** är båda har valt.

Det här steget för att bygga körs enhetstesterna i skriptet Pester vi tittade på tidigare och lagrar resultatet i den `InfraDNS/Tests/Results/*.xml` mapp.

### <a name="copy-files"></a>Kopiera filer

1. Lägg till var och en av följande rader till **innehållet**:

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. Ange **TargetFolder** till `$(Build.ArtifactStagingDirectory)\`

Det här steget kopierar bygga och testa skript för att uppsamlingskatalogen så som de kan publiceras bygger artefakter med nästa steg.

### <a name="publish-artifact"></a>Publicera artefakter

1. Ange **sökvägen till publicera** till `$(Build.ArtifactStagingDirectory)\`
1. Ange **Artefaktnamn** till `Deploy`
1. Ange **Artefakttypen** till `Server`
1. Välj `Enabled` i **styra alternativ**

## <a name="enable-continuous-integration"></a>Aktivera kontinuerlig integrering

Nu vi ställer in en utlösare som gör att projektet att skapa helst en ändring har checkats in till den `ci-cd-example` grenen av git-lagringsplats.

1. I TFS, klickar du på den **Build & Release** fliken
1. Välj den `DNS Infra` build-definition klicka sedan på **redigera**
1. Klicka på den **utlösare** fliken
1. Välj **kontinuerlig integrering (CI)**, och välj `refs/heads/ci-cd-example` i listrutan gren
1. Klicka på **spara** och sedan **OK**

Nu ändras något i TFS git-lagringsplats utlösare en automatisk build.

## <a name="create-the-release-definition"></a>Skapa versionsdefinitionen

Nu ska vi skapa en versionsdefinition så att projektet har distribuerats till utvecklingsmiljö med varje checkar in ny kod.

Gör detta genom att lägga till en ny versionsdefinition som är associerade med den `InfraDNS` build-definition som du skapade tidigare.
Se till att välja **kontinuerlig distribution** så att en ny version utlöses varje gång en ny version är klar.
([Så här: Arbeta med definitioner av versionen](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) och konfigurera den på följande sätt:

Lägg till följande versionsdefinitionen:

- PowerShell-skript
- Publicera testresultat
- Publicera testresultat

Redigera stegen på följande sätt:

### <a name="powershell-script"></a>PowerShell-skript

1. Ange den **skriptets sökväg** fältet `$(Build.DefinitionName)\Deploy\initiate.ps1"`
1. Ange den **argument** fältet `-fileName Deploy`

### <a name="first-publish-test-results"></a>Först publicera testresultat

1. Välj `NUnit` för den **Test Resultatformatet** fält
1. Ange den **resultatet Testfiler** fältet `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`
1. Ange den **testa kör rubrik** till `Integration`
1. Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**

### <a name="second-publish-test-results"></a>Andra publicera resultaten

1. Välj `NUnit` för den **Test Resultatformatet** fält
1. Ange den **resultatet Testfiler** fältet `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`
1. Ange den **testa kör rubrik** till `Acceptance`
1. Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**

## <a name="verify-your-results"></a>Kontrollera dina resultat

Nu vill du skicka ändringar den `ci-cd-example` startar gren till TFS, en ny version.
Om versionen är klar utlöses en ny distribution.

Du kan kontrollera resultatet av distributionen genom att öppna en webbläsare på klientdatorn och gå till `www.contoso.com`.

## <a name="next-steps"></a>Nästa steg

Det här exemplet konfigurerar DNS-servern `TestAgent1` så att URL: en `www.contoso.com` motsvarar `TestAgent2`, men det inte att distribuera en webbplats.
Stommen för att göra det har angetts i lagringsplatsen under den `WebApp` mapp.
Du kan använda platshållare som hjälper för att skapa psake skript, Pester tester och DSC-konfigurationer för att distribuera din egen webbplats.
