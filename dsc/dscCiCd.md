---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Skapa en kontinuerlig integrering och kontinuerlig distribution pipeline med DSC
ms.openlocfilehash: 5f7583fb93b69bbe4103b34b79b3a859c9cee8a9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="8ff1b-103">Skapa en kontinuerlig integrering och kontinuerlig distribution pipeline med DSC</span><span class="sxs-lookup"><span data-stu-id="8ff1b-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="8ff1b-104">Det här exemplet visar hur du skapar en pipeline för kontinuerlig Integration/kontinuerlig distribution (CI/CD) med hjälp av PowerShell, DSC, Pester och Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="8ff1b-105">När pipelinen har skapats och konfigurerats, du kan använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och tillhörande värdposter.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span> <span data-ttu-id="8ff1b-106">Den här processen simulerar den första delen av en pipeline som ska användas i en utvecklingsmiljö.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="8ff1b-107">En automatisk CI/CD-pipeline kan du uppdatera programvara snabbare och mer tillförlitligt säkerställer att all kod testas och att det finns en aktuell version av din kod vid alla tidpunkter.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="8ff1b-108">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="8ff1b-108">Prerequisites</span></span>

<span data-ttu-id="8ff1b-109">Om du vill använda det här exemplet, bör du känna till följande:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="8ff1b-110">CI-CD begrepp.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-110">CI-CD concepts.</span></span> <span data-ttu-id="8ff1b-111">En bra referens finns på [den versionen Pipeline modellen](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="8ff1b-112">[Git](https://git-scm.com/) datakälla</span><span class="sxs-lookup"><span data-stu-id="8ff1b-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="8ff1b-113">Den [Pester](https://github.com/pester/Pester) testning framework</span><span class="sxs-lookup"><span data-stu-id="8ff1b-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="8ff1b-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="8ff1b-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="8ff1b-115">Vad du behöver</span><span class="sxs-lookup"><span data-stu-id="8ff1b-115">What you will need</span></span>

<span data-ttu-id="8ff1b-116">Om du vill skapa och köra det här exemplet, behöver du en miljö med flera datorer och/eller virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="8ff1b-117">Klient</span><span class="sxs-lookup"><span data-stu-id="8ff1b-117">Client</span></span>

<span data-ttu-id="8ff1b-118">Detta är den dator där du ska göra allt arbete att installera och köra exemplet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="8ff1b-119">Klientdatorn måste vara en Windows-dator med följande installerat:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-119">The client computer must be a Windows computer with the following installed:</span></span>
- [<span data-ttu-id="8ff1b-120">Git</span><span class="sxs-lookup"><span data-stu-id="8ff1b-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="8ff1b-121">en lokal git-lagringsplatsen klonad från https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="8ff1b-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="8ff1b-122">en textredigerare, t.ex [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="8ff1b-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="8ff1b-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="8ff1b-123">TFSSrv1</span></span>

<span data-ttu-id="8ff1b-124">Den dator som värd för TFS-servern där du definierar din version och utgåva.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="8ff1b-125">Datorn måste ha [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installerad.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="8ff1b-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="8ff1b-126">BuildAgent</span></span>

<span data-ttu-id="8ff1b-127">Den dator som kör Windows Skapa agenten som bygger projektet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="8ff1b-128">Den här datorn måste ha en Windows Skapa agent installerad och körs.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="8ff1b-129">Se [distribuerar en agent på Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) för instruktioner om hur du installerar och kör ett Windows Skapa agenten.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-129">See [Deploy an agent on Windows](https://www.visualstudio.com/en-us/docs/build/actions/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="8ff1b-130">Du måste också installera både den `xDnsServer` och `xNetworking` DSC-moduler på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="8ff1b-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="8ff1b-131">TestAgent1</span></span>

<span data-ttu-id="8ff1b-132">Detta är den dator som har konfigurerats som en DNS-server av DSC-konfigurationen i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="8ff1b-133">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="8ff1b-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="8ff1b-134">TestAgent2</span></span>

<span data-ttu-id="8ff1b-135">Detta är den dator som är värd för webbplatsen för det här exemplet konfigureras.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="8ff1b-136">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span> 

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="8ff1b-137">Lägg till kod till TFS</span><span class="sxs-lookup"><span data-stu-id="8ff1b-137">Add the code to TFS</span></span>

<span data-ttu-id="8ff1b-138">Vi börjar genom att skapa en Git-lagringsplats i TFS och importera koden från din lokala lagringsplats på klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="8ff1b-139">Om du inte redan har klona Demo_CI databasen till en klientdator, gör du nu genom att köra följande kommando i git:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="8ff1b-140">Navigera till TFS-servern i en webbläsare på klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="8ff1b-141">I TFS, [skapa ett nytt grupprojekt](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) med namnet Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-141">In TFS, [Create a new team project](https://www.visualstudio.com/en-us/docs/setup-admin/create-team-project) named Demo_CI.</span></span>

    <span data-ttu-id="8ff1b-142">Se till att **versionskontroll** är inställd på **Git**.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="8ff1b-143">Lägg till en fjärransluten i databasen som du skapade i TFS med följande kommando på klientdatorn:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

    `git remote add tfs <YourTFSRepoURL>`

    <span data-ttu-id="8ff1b-144">Där `<YourTFSRepoURL>` är klon-URL: en till TFS-databasen som du skapade i föregående steg.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

    <span data-ttu-id="8ff1b-145">Om du inte vet var du hittar den här URL: en kan se [klona en befintlig Git-lagringsplatsen](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-145">If you don't know where to find this URL, see [Clone an existing Git repo](https://www.visualstudio.com/en-us/docs/git/tutorial/clone).</span></span>
1. <span data-ttu-id="8ff1b-146">Skicka koden från din lokala lagringsplatsen till lagringsplatsen för TFS med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

    `git push tfs --all`
1. <span data-ttu-id="8ff1b-147">TFS-databasen fylls med Demo_CI kod.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-147">The TFS repository will be populated with the Demo_CI code.</span></span>

><span data-ttu-id="8ff1b-148">**Obs:** det här exemplet används koden i den `ci-cd-example` grenen av Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-148">**Note:** This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
><span data-ttu-id="8ff1b-149">Se till att ange den här grenen som standardförgrening i TFS-projektet och för CI/CD-utlösare som du skapar.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="8ff1b-150">Förstå koden</span><span class="sxs-lookup"><span data-stu-id="8ff1b-150">Understanding the code</span></span>

<span data-ttu-id="8ff1b-151">Innan vi skapar bygg- och distributionsprocessen pipelines ska vi titta på några av kod för att förstå vad som händer.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="8ff1b-152">På klientdatorn, öppna valfri textredigerare och navigera till roten i Demo_CI Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="8ff1b-153">DSC-konfigurationen</span><span class="sxs-lookup"><span data-stu-id="8ff1b-153">The DSC configuration</span></span>

<span data-ttu-id="8ff1b-154">Öppna filen `DNSServer.ps1` (från roten för den lokala Demo_CI lagringsplatsen `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="8ff1b-155">Den här filen innehåller DSC-konfigurationen som ställer in DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="8ff1b-156">Det är här i sin helhet:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="8ff1b-157">Observera den `Node` instruktionen:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="8ff1b-158">Detta hittar de noder som har definierats som en roll `DNSServer` i den [konfigurationsdata](configData.md), som skapas av den `DevEnv.ps1` skript.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="8ff1b-159">Med data för att definiera noder är viktigt när du gör CI eftersom noden informationen ändras troligen mellan miljöer och använder konfigurationsdata kan du enkelt göra ändringar i noden information utan att ändra konfigurationskoden.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-159">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="8ff1b-160">I det första resurs blocket konfigurationen anropar den [WindowsFeature](windowsFeatureResource.md) så att DNS-funktionen är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-160">In the first resource block, the configuration calls the [WindowsFeature](windowsFeatureResource.md) to ensure that the DNS feature is enabled.</span></span> <span data-ttu-id="8ff1b-161">Resurs-block som följer anropet resurser från den [xDnsServer](https://github.com/PowerShell/xDnsServer) modul för att konfigurera primär zon och DNS-poster.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-161">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="8ff1b-162">Observera att två `xDnsRecord` block placeras i `foreach` slingor gå igenom matriser i konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-162">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="8ff1b-163">Igen, konfigurationsdata skapas av den `DevEnv.ps1` skript som vi ska titta på Nästa.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-163">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="8ff1b-164">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="8ff1b-164">Configuration data</span></span>

<span data-ttu-id="8ff1b-165">Den `DevEnv.ps1` fil (från roten för den lokala Demo_CI lagringsplatsen `./InfraDNS/DevEnv.ps1`) anger miljö-specifika konfigurationsdata i en hash-tabell och skickar sedan den hash-tabellen till ett anrop till den `New-DscConfigurationDataDocument` funktion, som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-165">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="8ff1b-166">Den `DevEnv.ps1` filen:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-166">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="8ff1b-167">Den `New-DscConfigurationDataDocument` funktion (definieras i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmässigt skapar ett configuration datadokument från hashtable (noden data) och matris (data-nod) som skickas av `RawEnvData` och `OtherEnvData` parametrar.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-167">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="8ff1b-168">I vårt fall bara i `RawEnvData` parametern används.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-168">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="8ff1b-169">Skriptet psake build</span><span class="sxs-lookup"><span data-stu-id="8ff1b-169">The psake build script</span></span>

<span data-ttu-id="8ff1b-170">Den [psake](https://github.com/psake/psake) skapa skript som definierats i `Build.ps1` (från roten av lagringsplatsen Demo_CI `./InfraDNS/Build.ps1`) definierar uppgifter som ingår i versionen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-170">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="8ff1b-171">Den definierar också vilka aktiviteter som varje uppgift beror på.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-171">It also defines which other tasks each task depends on.</span></span> <span data-ttu-id="8ff1b-172">När den anropas, skriptet psake garanterar att den angivna aktiviteten (eller aktiviteten `Default` om inget anges) körs och att alla beroenden även kör (detta är rekursiv, så att det körs beroenden av beroenden, och så vidare).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-172">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="8ff1b-173">I detta exempel på `Default` aktivitet har definierats som:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-173">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="8ff1b-174">Den `Default` aktiviteten har ingen implementering sig själv, men har ett beroende på den `CompileConfigs` aktivitet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-174">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="8ff1b-175">Den resulterande kedjan av beroenden för aktiviteten säkerställer att alla aktiviteter i build-skript körs.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-175">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="8ff1b-176">I det här exemplet anropas skriptet psake av ett anrop till `Invoke-PSake` i den `Initiate.ps1` filen (som finns i roten på Demo_CI databasen):</span><span class="sxs-lookup"><span data-stu-id="8ff1b-176">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="8ff1b-177">När vi skapar build-definition i vårt exempel i TFS, levererar vi vårt psake skriptfilen som den `fileName` parametern för det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-177">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="8ff1b-178">Build-skriptet definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-178">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="8ff1b-179">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="8ff1b-179">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="8ff1b-180">Kör `DevEnv.ps1`, vilket genererar data konfigurationsfilen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-180">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="8ff1b-181">InstallModules</span><span class="sxs-lookup"><span data-stu-id="8ff1b-181">InstallModules</span></span>

<span data-ttu-id="8ff1b-182">Installerar de moduler som krävs för konfigurationen `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-182">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="8ff1b-183">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="8ff1b-183">ScriptAnalysis</span></span>

<span data-ttu-id="8ff1b-184">Anrop av [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-184">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="8ff1b-185">UnitTests</span><span class="sxs-lookup"><span data-stu-id="8ff1b-185">UnitTests</span></span>

<span data-ttu-id="8ff1b-186">Kör den [Pester](https://github.com/pester/Pester/wiki) kontroller.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-186">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="8ff1b-187">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="8ff1b-187">CompileConfigs</span></span>

<span data-ttu-id="8ff1b-188">Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med konfigurationsdata som genererats av den `GenerateEnvironmentFiles` aktivitet.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-188">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="8ff1b-189">Rensa</span><span class="sxs-lookup"><span data-stu-id="8ff1b-189">Clean</span></span>

<span data-ttu-id="8ff1b-190">Skapar de mappar som ska användas för exemplet och tar bort alla testresultat och konfigurationsfiler för data moduler tidigare körs.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-190">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="8ff1b-191">Psake distribuera skriptet</span><span class="sxs-lookup"><span data-stu-id="8ff1b-191">The psake deploy script</span></span>

<span data-ttu-id="8ff1b-192">Den [psake](https://github.com/psake/psake) distributionsskriptet som definierats i `Deploy.ps1` (från roten av lagringsplatsen Demo_CI `./InfraDNS/Deploy.ps1`) definierar uppgifter som att distribuera och kör sedan konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-192">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="8ff1b-193">`Deploy.ps1`definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-193">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="8ff1b-194">DeployModules</span><span class="sxs-lookup"><span data-stu-id="8ff1b-194">DeployModules</span></span>

<span data-ttu-id="8ff1b-195">Startar en PowerShell-session på `TestAgent1` och installerar de moduler som innehåller DSC-resurser som krävs för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-195">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="8ff1b-196">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="8ff1b-196">DeployConfigs</span></span>

<span data-ttu-id="8ff1b-197">Anrop av [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) för att köra konfigurationen på `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-197">Calls the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration.md) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="8ff1b-198">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="8ff1b-198">IntegrationTests</span></span>

<span data-ttu-id="8ff1b-199">Kör den [Pester](https://github.com/pester/Pester/wiki) integrering tester.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-199">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="8ff1b-200">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="8ff1b-200">AcceptanceTests</span></span>

<span data-ttu-id="8ff1b-201">Kör den [Pester](https://github.com/pester/Pester/wiki) godkännande tester.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-201">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="8ff1b-202">Rensa</span><span class="sxs-lookup"><span data-stu-id="8ff1b-202">Clean</span></span>

<span data-ttu-id="8ff1b-203">Tar bort alla moduler som installerats i föregående körs och ser till att testa resultatet mappen finns.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-203">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="8ff1b-204">Testa skript</span><span class="sxs-lookup"><span data-stu-id="8ff1b-204">Test scripts</span></span>

<span data-ttu-id="8ff1b-205">Godkännande, Integration och enheten tester definieras i skript i den `Tests` mapp (från roten av lagringsplatsen Demo_CI `./InfraDNS/Tests`), varje i filer med namnet `DNSServer.tests.ps1` i sina respektive mappar.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-205">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="8ff1b-206">Testet skript använder [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-206">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="8ff1b-207">Kontroller</span><span class="sxs-lookup"><span data-stu-id="8ff1b-207">Unit tests</span></span>

<span data-ttu-id="8ff1b-208">Enheten testar test av DSC-konfigurationer själva så att konfigurationerna som kommer att göra vad som förväntas när de körs.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-208">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="8ff1b-209">Enheten Testa skriptet använder [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-209">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="8ff1b-210">Integration tester</span><span class="sxs-lookup"><span data-stu-id="8ff1b-210">Integration tests</span></span>

<span data-ttu-id="8ff1b-211">Integration testerna testa konfigurationen av systemet så att när du har integrerat med andra komponenter, systemet är konfigurerat som förväntat.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-211">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="8ff1b-212">Dessa tester köras på målnoden när den har konfigurerats med DSC.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-212">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="8ff1b-213">Testa integrationsskriptet använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-213">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="8ff1b-214">Godkännande tester</span><span class="sxs-lookup"><span data-stu-id="8ff1b-214">Acceptance tests</span></span>

<span data-ttu-id="8ff1b-215">Godkännande testerna testar system för att säkerställa att den fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-215">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="8ff1b-216">Till exempel tester för att säkerställa en webbsida returnerar rätt information när en förfrågan.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-216">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="8ff1b-217">Dessa tester fjärrköra från målnoden för att testa verkliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-217">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="8ff1b-218">Testa integrationsskriptet använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-218">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="8ff1b-219">Definiera bygga</span><span class="sxs-lookup"><span data-stu-id="8ff1b-219">Define the build</span></span>

<span data-ttu-id="8ff1b-220">Nu när vi har överfört vår kod till TFS och tittar på syfte, definiera våra build.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-220">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="8ff1b-221">Här kan rapporterar vi bara de build steg som du lägger till i versionen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-221">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="8ff1b-222">Anvisningar om hur du skapar en build-definition i TFS finns [skapa och kön en definition av build](https://www.visualstudio.com/en-us/docs/build/define/create).</span><span class="sxs-lookup"><span data-stu-id="8ff1b-222">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](https://www.visualstudio.com/en-us/docs/build/define/create).</span></span>

<span data-ttu-id="8ff1b-223">Skapa en ny build-definition (Välj den **tom** mall) med namnet ”InfraDNS”.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-223">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="8ff1b-224">Lägg till följande steg ska du skapa definition:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-224">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="8ff1b-225">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="8ff1b-225">PowerShell Script</span></span>
- <span data-ttu-id="8ff1b-226">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-226">Publish Test Results</span></span>
- <span data-ttu-id="8ff1b-227">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="8ff1b-227">Copy Files</span></span>
- <span data-ttu-id="8ff1b-228">Publicera artefakt</span><span class="sxs-lookup"><span data-stu-id="8ff1b-228">Publish Artifact</span></span>

<span data-ttu-id="8ff1b-229">När du lägger till dessa steg skapa, redigera egenskaperna för varje steg på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-229">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="8ff1b-230">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="8ff1b-230">PowerShell Script</span></span>

1. <span data-ttu-id="8ff1b-231">Ange den **typen** egenskapen `File Path`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-231">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="8ff1b-232">Ange den **skriptsökvägen** egenskapen `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-232">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="8ff1b-233">Lägg till `-fileName build` till den **argument** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-233">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="8ff1b-234">Det här build-steget körs den `initiate.ps1` -fil, som anropar psake build-skript.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-234">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="8ff1b-235">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-235">Publish Test Results</span></span>

1. <span data-ttu-id="8ff1b-236">Ange **testa Resultatformatet** till`NUnit`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-236">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="8ff1b-237">Ange **Test resulterar filer** till`InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-237">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="8ff1b-238">Ange **testa kör rubrik** till `Unit`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-238">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="8ff1b-239">Kontrollera att **alternativ för åtkomstkontroll** **aktiverad** och **körs alltid** är båda markerade.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-239">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="8ff1b-240">Det här steget build körs testerna enhet i skriptet Pester vi har tittat på tidigare och lagrar resultatet i den `InfraDNS/Tests/Results/*.xml` mapp.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-240">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="8ff1b-241">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="8ff1b-241">Copy Files</span></span>

1. <span data-ttu-id="8ff1b-242">Lägg till följande rader till **innehållet**:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-242">Add each of the following lines to **Contents**:</span></span>

    ```
    initiate.ps1
    **\deploy.ps1
    **\Acceptance\**
    **\Integration\**
    ```

1. <span data-ttu-id="8ff1b-243">Ange **TargetFolder** till`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-243">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="8ff1b-244">Det här steget kopierar bygga och testa skript i uppsamlingskatalogen så som de kan publiceras som skapa artefakter med nästa steg.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-244">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="8ff1b-245">Publicera artefakt</span><span class="sxs-lookup"><span data-stu-id="8ff1b-245">Publish Artifact</span></span>

1. <span data-ttu-id="8ff1b-246">Ange **sökvägen till publicera** till`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-246">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="8ff1b-247">Ange **artefakt namnet** till`Deploy`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-247">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="8ff1b-248">Ange **typ av artefakt** till`Server`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-248">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="8ff1b-249">Välj `Enabled` i **alternativ**</span><span class="sxs-lookup"><span data-stu-id="8ff1b-249">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="8ff1b-250">Aktivera kontinuerlig integration</span><span class="sxs-lookup"><span data-stu-id="8ff1b-250">Enable continuous integration</span></span>

<span data-ttu-id="8ff1b-251">Nu vi ställer in en utlösare som orsakar projektet för att skapa varje gång en ändring har checkats in till den `ci-cd-example` grenen av git-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-251">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="8ff1b-252">I TFS, klickar du på den **Skapa & släpper** fliken</span><span class="sxs-lookup"><span data-stu-id="8ff1b-252">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="8ff1b-253">Välj den `DNS Infra` skapa definition, och klicka på **redigera**</span><span class="sxs-lookup"><span data-stu-id="8ff1b-253">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="8ff1b-254">Klicka på den **utlösare** fliken</span><span class="sxs-lookup"><span data-stu-id="8ff1b-254">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="8ff1b-255">Välj **kontinuerlig integration (KO)**, och välj `refs/heads/ci-cd-example` i listrutan gren</span><span class="sxs-lookup"><span data-stu-id="8ff1b-255">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="8ff1b-256">Klicka på **spara** och sedan **OK**</span><span class="sxs-lookup"><span data-stu-id="8ff1b-256">Click **Save** and then **OK**</span></span>

<span data-ttu-id="8ff1b-257">Nu ändras något i TFS git-lagringsplatsen utlösare en automatiserad version.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-257">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="8ff1b-258">Skapa en definition för versionen</span><span class="sxs-lookup"><span data-stu-id="8ff1b-258">Create the release definition</span></span>

<span data-ttu-id="8ff1b-259">Nu ska vi skapa en definition av versionen så att projektet har distribuerats till utvecklingsmiljö med varje kod incheckning.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-259">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="8ff1b-260">För att göra detta, lägger du till en ny version som är associerade med den `InfraDNS` skapa definition som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-260">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="8ff1b-261">Se till att välja **kontinuerlig distribution** så att en ny version ska utlösas när en ny version har slutförts.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-261">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="8ff1b-262">([Så här: arbeta med definitioner av versionen](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) och konfigurera den på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-262">([How to: Work with release definitions](https://www.visualstudio.com/en-us/docs/build/actions/work-with-release-definitions)) and configure it as follows:</span></span>

<span data-ttu-id="8ff1b-263">Lägg till följande steg i definitionen för versionen:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-263">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="8ff1b-264">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="8ff1b-264">PowerShell Script</span></span>
- <span data-ttu-id="8ff1b-265">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-265">Publish Test Results</span></span>
- <span data-ttu-id="8ff1b-266">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-266">Publish Test Results</span></span>

<span data-ttu-id="8ff1b-267">Redigera stegen på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="8ff1b-267">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="8ff1b-268">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="8ff1b-268">PowerShell Script</span></span>

1. <span data-ttu-id="8ff1b-269">Ange den **skriptsökvägen** till`$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-269">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="8ff1b-270">Ange den **argument** till`-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-270">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="8ff1b-271">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-271">First Publish Test Results</span></span>

1. <span data-ttu-id="8ff1b-272">Välj `NUnit` för den **Test Resultatformatet** fält</span><span class="sxs-lookup"><span data-stu-id="8ff1b-272">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="8ff1b-273">Ange den **resultatet Testfiler** till`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-273">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="8ff1b-274">Ange den **testa kör rubrik** till`Integration`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-274">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="8ff1b-275">Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**</span><span class="sxs-lookup"><span data-stu-id="8ff1b-275">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="8ff1b-276">Andra publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="8ff1b-276">Second Publish Test Results</span></span>

1. <span data-ttu-id="8ff1b-277">Välj `NUnit` för den **Test Resultatformatet** fält</span><span class="sxs-lookup"><span data-stu-id="8ff1b-277">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="8ff1b-278">Ange den **resultatet Testfiler** till`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-278">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="8ff1b-279">Ange den **testa kör rubrik** till`Acceptance`</span><span class="sxs-lookup"><span data-stu-id="8ff1b-279">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="8ff1b-280">Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**</span><span class="sxs-lookup"><span data-stu-id="8ff1b-280">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="8ff1b-281">Kontrollera resultatet</span><span class="sxs-lookup"><span data-stu-id="8ff1b-281">Verify your results</span></span>

<span data-ttu-id="8ff1b-282">Nu när du trycker på ändringar den `ci-cd-example` startar gren till TFS, en ny version.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-282">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="8ff1b-283">Om versionen har slutförts, utlöses en ny distribution.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-283">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="8ff1b-284">Du kan kontrollera resultatet av distributionen genom att öppna en webbläsare på klientdatorn och gå till `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-284">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="8ff1b-285">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="8ff1b-285">Next steps</span></span>

<span data-ttu-id="8ff1b-286">Det här exemplet konfigureras DNS-servern `TestAgent1` så att URL: en `www.contoso.com` matchar `TestAgent2`, men det inte att distribuera en webbplats.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-286">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="8ff1b-287">Stommen för att göra det tillhandahålls i lagringsplatsen under den `WebApp` mapp.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-287">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="8ff1b-288">Du kan använda stub-rutiner som hjälper för att skapa psake skript, Pester testerna och DSC-konfigurationer för att distribuera din egen webbplats.</span><span class="sxs-lookup"><span data-stu-id="8ff1b-288">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>







