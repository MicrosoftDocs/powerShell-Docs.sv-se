---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Skapa en pipeline för kontinuerlig integrering och kontinuerlig distribution med DSC
ms.openlocfilehash: 012057a32ccf85b0d15e76a332cadda4b226180a
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687267"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="6e9b2-103">Skapa en pipeline för kontinuerlig integrering och kontinuerlig distribution med DSC</span><span class="sxs-lookup"><span data-stu-id="6e9b2-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="6e9b2-104">Det här exemplet visar hur du skapar en pipeline för kontinuerlig integrering/kontinuerlig distribution (CI/CD) med hjälp av PowerShell, DSC, Pester och Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="6e9b2-105">När pipelinen har skapats och konfigurerats, du kan använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och tillhörande värdposter.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="6e9b2-106">Den här processen simulerar den första delen av en pipeline som skulle användas i en utvecklingsmiljö.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="6e9b2-107">En automatiserad CI/CD-pipeline kan du uppdatera programvara snabbare och mer tillförlitligt att säkerställa att all kod har testats och att det är en aktuell version av din kod vid alla tidpunkter.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="6e9b2-108">Förutsättningar</span><span class="sxs-lookup"><span data-stu-id="6e9b2-108">Prerequisites</span></span>

<span data-ttu-id="6e9b2-109">Om du vill använda det här exemplet, bör du känna till följande:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="6e9b2-110">CI-CD-begrepp.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-110">CI-CD concepts.</span></span> <span data-ttu-id="6e9b2-111">En bra referens finns på [The Release Pipeline modellen](http://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-111">A good reference can be found at [The Release Pipeline Model](http://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="6e9b2-112">[Git](https://git-scm.com/) källkontroll</span><span class="sxs-lookup"><span data-stu-id="6e9b2-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="6e9b2-113">Den [Pester](https://github.com/pester/Pester) xcuitest</span><span class="sxs-lookup"><span data-stu-id="6e9b2-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="6e9b2-114">Team Foundation Server</span><span class="sxs-lookup"><span data-stu-id="6e9b2-114">Team Foundation Server</span></span>](https://www.visualstudio.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="6e9b2-115">Vad du behöver</span><span class="sxs-lookup"><span data-stu-id="6e9b2-115">What you will need</span></span>

<span data-ttu-id="6e9b2-116">Om du vill skapa och köra det här exemplet, behöver du en miljö med flera datorer och/eller virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="6e9b2-117">Klient</span><span class="sxs-lookup"><span data-stu-id="6e9b2-117">Client</span></span>

<span data-ttu-id="6e9b2-118">Det här är den dator där du ska göra allt arbete som konfigurerar och kör exemplet.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="6e9b2-119">Klientdatorn måste vara en Windows-dator med följande installerat:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="6e9b2-120">Git</span><span class="sxs-lookup"><span data-stu-id="6e9b2-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="6e9b2-121">en lokal git-lagringsplats som klonas från https://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="6e9b2-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="6e9b2-122">en textredigerare, till exempel [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="6e9b2-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="6e9b2-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="6e9b2-123">TFSSrv1</span></span>

<span data-ttu-id="6e9b2-124">Den dator som är värd för TFS-servern där du definierar din version och utgåva.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="6e9b2-125">Den här datorn måste ha [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installerad.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-125">This computer must have [Team Foundation Server 2017](https://www.visualstudio.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="6e9b2-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="6e9b2-126">BuildAgent</span></span>

<span data-ttu-id="6e9b2-127">Den dator som kör Windows Skapa agenten som bygger på projektet.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="6e9b2-128">Den här datorn måste ha en Windows Skapa agenten installerad och igång.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="6e9b2-129">Se [distribuerar en agent på Windows](/azure/devops/pipelines/agents/v2-windows) för instruktioner om hur du installerar och kör ett Windows Skapa agenten.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="6e9b2-130">Du måste också installera både den `xDnsServer` och `xNetworking` DSC-moduler på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="6e9b2-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="6e9b2-131">TestAgent1</span></span>

<span data-ttu-id="6e9b2-132">Det här är den dator som är konfigurerad som en DNS-server av DSC-konfigurationen i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="6e9b2-133">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="6e9b2-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="6e9b2-134">TestAgent2</span></span>

<span data-ttu-id="6e9b2-135">Det här är den dator som är värd för webbplatsen som det här exemplet konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="6e9b2-136">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="6e9b2-137">Lägg till kod till TFS</span><span class="sxs-lookup"><span data-stu-id="6e9b2-137">Add the code to TFS</span></span>

<span data-ttu-id="6e9b2-138">Vi börjar genom att skapa en Git-lagringsplats i TFS och importera koden från din lokala lagringsplats på klientdatorn.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="6e9b2-139">Om du inte redan har klonat lagringsplatsen Demo_CI till klientdatorn gör du nu genom att köra följande git-kommando:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="6e9b2-140">Navigera till TFS-servern i en webbläsare på din klientdator.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="6e9b2-141">I TFS, [skapa ett nytt grupprojekt](/azure/devops/organizations/projects/create-project) med namnet Demo_CI.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="6e9b2-142">Se till att **versionskontroll** är inställd på **Git**.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="6e9b2-143">Lägg till en fjärransluten i databasen som du skapade i TFS med följande kommando på klientdatorn:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="6e9b2-144">Där `<YourTFSRepoURL>` är URL-klonen i TFS-databasen som du skapade i föregående steg.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="6e9b2-145">Om du inte vet var du hittar den här URL: en kan se [klona en befintlig Git-lagringsplats](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="6e9b2-146">Skicka koden från din lokala lagringsplats till TFS-lagringsplatsen med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="6e9b2-147">TFS-databasen fylls med Demo_CI kod.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="6e9b2-148">Det här exemplet använder koden i den `ci-cd-example` grenen av Git-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="6e9b2-149">Se till att ange den här grenen som standardgren i TFS-projektet och för CI/CD-utlösare som du skapar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="6e9b2-150">Så här fungerar koden</span><span class="sxs-lookup"><span data-stu-id="6e9b2-150">Understanding the code</span></span>

<span data-ttu-id="6e9b2-151">Innan vi skapar bygg- och distributionsledningar ska vi titta på några av koden för att förstå vad som händer.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="6e9b2-152">På klientdatorn, öppna valfri textredigerare och navigera till roten i Demo_CI Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="6e9b2-153">DSC-konfiguration</span><span class="sxs-lookup"><span data-stu-id="6e9b2-153">The DSC configuration</span></span>

<span data-ttu-id="6e9b2-154">Öppna filen `DNSServer.ps1` (från roten för den lokala lagringsplatsen Demo_CI `./InfraDNS/Configs/DNSServer.ps1`).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="6e9b2-155">Den här filen innehåller den DSC-konfiguration som konfigurerar DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="6e9b2-156">Här är det i sin helhet:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="6e9b2-157">Observera den `Node` instruktionen:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="6e9b2-158">Detta söker efter alla noder som har definierats som har rollen `DNSServer` i den [konfigurationsdata](../configurations/configData.md), som skapas av den `DevEnv.ps1` skript.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="6e9b2-159">Du kan läsa mer om den `Where` -metod i [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span><span class="sxs-lookup"><span data-stu-id="6e9b2-159">You can read more about the `Where` method in [about_arrays](/powershell/reference/3.0/Microsoft.PowerShell.Core/About/about_Arrays.md)</span></span>

<span data-ttu-id="6e9b2-160">Det är viktigt att med konfigurationsdata för att definiera noder när du gör CI eftersom nodinformation troligen kommer att förändras mellan miljöer och använder konfigurationsdata kan du enkelt göra ändringar i noden information utan att ändra konfigurationskoden.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="6e9b2-161">I det första resource blocket konfigurationen anropar den **WindowsFeature** så att DNS-funktionen är aktiverad.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="6e9b2-162">Resurs-block som följer anrop resurser från den [xDnsServer](https://github.com/PowerShell/xDnsServer) modul för att konfigurera primär zon och DNS-poster.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="6e9b2-163">Observera att två `xDnsRecord` block är omslutna i `foreach` slingor gå igenom matriser i konfigurationsdata.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="6e9b2-164">Igen, konfigurationsdata har skapats av den `DevEnv.ps1` skript som vi ska titta på Nästa.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="6e9b2-165">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="6e9b2-165">Configuration data</span></span>

<span data-ttu-id="6e9b2-166">Den `DevEnv.ps1` fil (från roten för den lokala lagringsplatsen Demo_CI `./InfraDNS/DevEnv.ps1`) anger miljöspecifika konfigurationsdata i en hash-tabell och skickar den hash-tabellen till ett anrop till den `New-DscConfigurationDataDocument` som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="6e9b2-167">Den `DevEnv.ps1` fil:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-167">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="6e9b2-168">Den `New-DscConfigurationDataDocument` funktion (definieras i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmässigt skapar en konfigurationsdokumentet data från den hash-tabell (noddata) och matrisen (icke-noden data) som skickas som den `RawEnvData` och `OtherEnvData` parametrar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="6e9b2-169">I vårt fall bara i `RawEnvData` parametern används.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="6e9b2-170">Build-skriptet psake</span><span class="sxs-lookup"><span data-stu-id="6e9b2-170">The psake build script</span></span>

<span data-ttu-id="6e9b2-171">Den [psake](https://github.com/psake/psake) skapa skript som definierats i `Build.ps1` (från roten för lagringsplatsen Demo_CI `./InfraDNS/Build.ps1`) definierar uppgifter som ingår i versionen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="6e9b2-172">Den definierar även vilka uppgifter som varje aktivitet beror på.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="6e9b2-173">När anropats skriptet psake säkerställer att den angivna aktiviteten (eller aktiviteten `Default` om inget anges) körs och att alla beroenden även kör (detta är rekursiv, så att beroenden för beroenden körs, och så vidare).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="6e9b2-174">I det här exemplet på `Default` uppgift definieras som:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="6e9b2-175">Den `Default` uppgiften har ingen implementering själva, men har ett beroende på den `CompileConfigs` uppgift.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="6e9b2-176">Den resulterande kedjan av aktivitetsberoenden säkerställer att alla aktiviteter i build-skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="6e9b2-177">I det här exemplet skriptet psake startas av ett anrop till `Invoke-PSake` i den `Initiate.ps1` filen (som finns i roten för lagringsplatsen Demo_CI):</span><span class="sxs-lookup"><span data-stu-id="6e9b2-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="6e9b2-178">När vi skapar byggesdefinition i vårt exempel i TFS, ska vi ange vår psake skriptfilen som den `fileName` parameter för det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="6e9b2-179">Build-skriptet definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="6e9b2-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="6e9b2-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="6e9b2-181">Körningar `DevEnv.ps1`, vilket genererar konfigurationsdatafilen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="6e9b2-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="6e9b2-182">InstallModules</span></span>

<span data-ttu-id="6e9b2-183">Installerar moduler som krävs av konfigurationen `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="6e9b2-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="6e9b2-184">ScriptAnalysis</span></span>

<span data-ttu-id="6e9b2-185">Anropar den [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="6e9b2-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="6e9b2-186">UnitTests</span></span>

<span data-ttu-id="6e9b2-187">Körs den [Pester](https://github.com/pester/Pester/wiki) enhetstester.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="6e9b2-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="6e9b2-188">CompileConfigs</span></span>

<span data-ttu-id="6e9b2-189">Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med hjälp av configuration-data som genereras av den `GenerateEnvironmentFiles` uppgift.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="6e9b2-190">Rensa</span><span class="sxs-lookup"><span data-stu-id="6e9b2-190">Clean</span></span>

<span data-ttu-id="6e9b2-191">Skapar de mappar som ska användas för det här exemplet och tar bort alla testresultat och konfigurationsdatafiler moduler från tidigare körningar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="6e9b2-192">Psake distribuera skriptet</span><span class="sxs-lookup"><span data-stu-id="6e9b2-192">The psake deploy script</span></span>

<span data-ttu-id="6e9b2-193">Den [psake](https://github.com/psake/psake) distributionsskriptet som definierats i `Deploy.ps1` (från roten för lagringsplatsen Demo_CI `./InfraDNS/Deploy.ps1`) definierar uppgifter som att distribuera och kör sedan konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="6e9b2-194">`Deploy.ps1` definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="6e9b2-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="6e9b2-195">DeployModules</span></span>

<span data-ttu-id="6e9b2-196">Startar en PowerShell-session på `TestAgent1` och installerar de moduler som innehåller DSC-resurser som krävs för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="6e9b2-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="6e9b2-197">DeployConfigs</span></span>

<span data-ttu-id="6e9b2-198">Anropar den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet för att köra konfigurationen på `TestAgent1`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="6e9b2-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="6e9b2-199">IntegrationTests</span></span>

<span data-ttu-id="6e9b2-200">Körs den [Pester](https://github.com/pester/Pester/wiki) integreringstester.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="6e9b2-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="6e9b2-201">AcceptanceTests</span></span>

<span data-ttu-id="6e9b2-202">Körs den [Pester](https://github.com/pester/Pester/wiki) acceptanstester.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="6e9b2-203">Rensa</span><span class="sxs-lookup"><span data-stu-id="6e9b2-203">Clean</span></span>

<span data-ttu-id="6e9b2-204">Tar bort alla moduler som installerats i tidigare körningar och ser till att testa resultatet mappen finns.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="6e9b2-205">Testa skript</span><span class="sxs-lookup"><span data-stu-id="6e9b2-205">Test scripts</span></span>

<span data-ttu-id="6e9b2-206">Godkännande, Integration och enhet tester har definierats i skripten i den `Tests` mapp (från roten för lagringsplatsen Demo_CI `./InfraDNS/Tests`), var och en i filer med namnet `DNSServer.tests.ps1` i sina respektive mappar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="6e9b2-207">Testet skript använder [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="6e9b2-208">Enhetstester</span><span class="sxs-lookup"><span data-stu-id="6e9b2-208">Unit tests</span></span>

<span data-ttu-id="6e9b2-209">Testa DSC-konfigurationer själva så att konfigurationerna som kommer att göra vad som förväntas när de kör jednotek.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="6e9b2-210">Skriptet använder enhetstestar [Pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="6e9b2-211">Integreringstester</span><span class="sxs-lookup"><span data-stu-id="6e9b2-211">Integration tests</span></span>

<span data-ttu-id="6e9b2-212">Integreringstester testa konfigurationen av systemet för att se till att när du har integrerat med andra komponenter i systemet konfigureras som förväntat.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="6e9b2-213">De här testerna körs på målnoden när den har konfigurerats med DSC.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="6e9b2-214">Testskriptet integration använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="6e9b2-215">Acceptanstester</span><span class="sxs-lookup"><span data-stu-id="6e9b2-215">Acceptance tests</span></span>

<span data-ttu-id="6e9b2-216">Acceptanstester testa systemet för att säkerställa att det fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="6e9b2-217">Till exempel tester för att säkerställa att en webbsida returnerar rätt information när en förfrågan.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="6e9b2-218">De här testerna körs via en fjärranslutning från målnoden för att testa verkliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="6e9b2-219">Testskriptet integration använder en blandning av [Pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="6e9b2-220">Definiera versionen</span><span class="sxs-lookup"><span data-stu-id="6e9b2-220">Define the build</span></span>

<span data-ttu-id="6e9b2-221">Nu när vi har överfört vår kod till TFS och tittat på vad det gör vi definiera vår build.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="6e9b2-222">Här kan upp vi endast byggsteg som du lägger till i bygget.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="6e9b2-223">Mer information om hur du skapar en byggesdefinition i TFS, finns i [skapa och kön en byggesdefinition](/azure/devops/pipelines/get-started-designer).</span><span class="sxs-lookup"><span data-stu-id="6e9b2-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/get-started-designer).</span></span>

<span data-ttu-id="6e9b2-224">Skapa en ny build-definition (Välj den **tom** mall) med namnet ”InfraDNS”.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="6e9b2-225">Lägg till följande steg för att du build-definition:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="6e9b2-226">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="6e9b2-226">PowerShell Script</span></span>
- <span data-ttu-id="6e9b2-227">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-227">Publish Test Results</span></span>
- <span data-ttu-id="6e9b2-228">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="6e9b2-228">Copy Files</span></span>
- <span data-ttu-id="6e9b2-229">Publicera artefakter</span><span class="sxs-lookup"><span data-stu-id="6e9b2-229">Publish Artifact</span></span>

<span data-ttu-id="6e9b2-230">När du lägger till dessa bygg steg, redigera egenskaperna för varje steg på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="6e9b2-231">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="6e9b2-231">PowerShell Script</span></span>

1. <span data-ttu-id="6e9b2-232">Ange den **typ** egenskap `File Path`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="6e9b2-233">Ange den **skriptets sökväg** egenskap `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="6e9b2-234">Lägg till `-fileName build` till den **argument** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="6e9b2-235">Det här steget för att bygga körs den `initiate.ps1` -fil som anropar psake build-skriptet.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="6e9b2-236">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-236">Publish Test Results</span></span>

1. <span data-ttu-id="6e9b2-237">Ange **testa Resultatformatet** till `NUnit`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="6e9b2-238">Ange **Test resulterar filer** till `InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="6e9b2-239">Ange **testa kör rubrik** till `Unit`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="6e9b2-240">Se till att **alternativ för åtkomstkontroll** **aktiverad** och **körs alltid** är båda har valt.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="6e9b2-241">Det här steget för att bygga körs enhetstesterna i skriptet Pester vi tittade på tidigare och lagrar resultatet i den `InfraDNS/Tests/Results/*.xml` mapp.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="6e9b2-242">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="6e9b2-242">Copy Files</span></span>

1. <span data-ttu-id="6e9b2-243">Lägg till var och en av följande rader till **innehållet**:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="6e9b2-244">Ange **TargetFolder** till `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="6e9b2-245">Det här steget kopierar bygga och testa skript för att uppsamlingskatalogen så som de kan publiceras bygger artefakter med nästa steg.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="6e9b2-246">Publicera artefakter</span><span class="sxs-lookup"><span data-stu-id="6e9b2-246">Publish Artifact</span></span>

1. <span data-ttu-id="6e9b2-247">Ange **sökvägen till publicera** till `$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="6e9b2-248">Ange **Artefaktnamn** till `Deploy`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="6e9b2-249">Ange **Artefakttypen** till `Server`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="6e9b2-250">Välj `Enabled` i **styra alternativ**</span><span class="sxs-lookup"><span data-stu-id="6e9b2-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="6e9b2-251">Aktivera kontinuerlig integrering</span><span class="sxs-lookup"><span data-stu-id="6e9b2-251">Enable continuous integration</span></span>

<span data-ttu-id="6e9b2-252">Nu vi ställer in en utlösare som gör att projektet att skapa helst en ändring har checkats in till den `ci-cd-example` grenen av git-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="6e9b2-253">I TFS, klickar du på den **Build & Release** fliken</span><span class="sxs-lookup"><span data-stu-id="6e9b2-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="6e9b2-254">Välj den `DNS Infra` build-definition klicka sedan på **redigera**</span><span class="sxs-lookup"><span data-stu-id="6e9b2-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="6e9b2-255">Klicka på den **utlösare** fliken</span><span class="sxs-lookup"><span data-stu-id="6e9b2-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="6e9b2-256">Välj **kontinuerlig integrering (CI)**, och välj `refs/heads/ci-cd-example` i listrutan gren</span><span class="sxs-lookup"><span data-stu-id="6e9b2-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="6e9b2-257">Klicka på **spara** och sedan **OK**</span><span class="sxs-lookup"><span data-stu-id="6e9b2-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="6e9b2-258">Nu ändras något i TFS git-lagringsplats utlösare en automatisk build.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="6e9b2-259">Skapa versionsdefinitionen</span><span class="sxs-lookup"><span data-stu-id="6e9b2-259">Create the release definition</span></span>

<span data-ttu-id="6e9b2-260">Nu ska vi skapa en versionsdefinition så att projektet har distribuerats till utvecklingsmiljö med varje checkar in ny kod.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="6e9b2-261">Gör detta genom att lägga till en ny versionsdefinition som är associerade med den `InfraDNS` build-definition som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="6e9b2-262">Se till att välja **kontinuerlig distribution** så att en ny version utlöses varje gång en ny version är klar.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="6e9b2-263">([Vad är releaser? ](/azure/devops/pipelines/release/what-is-release-management)) och konfigurera den på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-263">([What are release pipelines?](/azure/devops/pipelines/release/what-is-release-management)) and configure it as follows:</span></span>

<span data-ttu-id="6e9b2-264">Lägg till följande versionsdefinitionen:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="6e9b2-265">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="6e9b2-265">PowerShell Script</span></span>
- <span data-ttu-id="6e9b2-266">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-266">Publish Test Results</span></span>
- <span data-ttu-id="6e9b2-267">Publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-267">Publish Test Results</span></span>

<span data-ttu-id="6e9b2-268">Redigera stegen på följande sätt:</span><span class="sxs-lookup"><span data-stu-id="6e9b2-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="6e9b2-269">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="6e9b2-269">PowerShell Script</span></span>

1. <span data-ttu-id="6e9b2-270">Ange den **skriptets sökväg** fältet `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="6e9b2-271">Ange den **argument** fältet `-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="6e9b2-272">Först publicera testresultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-272">First Publish Test Results</span></span>

1. <span data-ttu-id="6e9b2-273">Välj `NUnit` för den **Test Resultatformatet** fält</span><span class="sxs-lookup"><span data-stu-id="6e9b2-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="6e9b2-274">Ange den **resultatet Testfiler** fältet `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="6e9b2-275">Ange den **testa kör rubrik** till `Integration`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="6e9b2-276">Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**</span><span class="sxs-lookup"><span data-stu-id="6e9b2-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="6e9b2-277">Andra publicera resultaten</span><span class="sxs-lookup"><span data-stu-id="6e9b2-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="6e9b2-278">Välj `NUnit` för den **Test Resultatformatet** fält</span><span class="sxs-lookup"><span data-stu-id="6e9b2-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="6e9b2-279">Ange den **resultatet Testfiler** fältet `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="6e9b2-280">Ange den **testa kör rubrik** till `Acceptance`</span><span class="sxs-lookup"><span data-stu-id="6e9b2-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="6e9b2-281">Under **alternativ för åtkomstkontroll**, kontrollera **körs alltid**</span><span class="sxs-lookup"><span data-stu-id="6e9b2-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="6e9b2-282">Kontrollera dina resultat</span><span class="sxs-lookup"><span data-stu-id="6e9b2-282">Verify your results</span></span>

<span data-ttu-id="6e9b2-283">Nu vill du skicka ändringar den `ci-cd-example` startar gren till TFS, en ny version.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="6e9b2-284">Om versionen är klar utlöses en ny distribution.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="6e9b2-285">Du kan kontrollera resultatet av distributionen genom att öppna en webbläsare på klientdatorn och gå till `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="6e9b2-286">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="6e9b2-286">Next steps</span></span>

<span data-ttu-id="6e9b2-287">Det här exemplet konfigurerar DNS-servern `TestAgent1` så att URL: en `www.contoso.com` motsvarar `TestAgent2`, men det inte att distribuera en webbplats.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="6e9b2-288">Stommen för att göra det har angetts i lagringsplatsen under den `WebApp` mapp.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="6e9b2-289">Du kan använda platshållare som hjälper för att skapa psake skript, Pester tester och DSC-konfigurationer för att distribuera din egen webbplats.</span><span class="sxs-lookup"><span data-stu-id="6e9b2-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
