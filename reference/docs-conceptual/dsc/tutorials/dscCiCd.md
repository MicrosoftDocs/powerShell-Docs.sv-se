---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Skapa en kontinuerlig integrering och en pipeline för kontinuerlig distribution med DSC
ms.openlocfilehash: 2d049cd640f0df9b018a88ad106e59dbeed7bcee
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71942148"
---
# <a name="building-a-continuous-integration-and-continuous-deployment-pipeline-with-dsc"></a><span data-ttu-id="04f9e-103">Skapa en kontinuerlig integrering och en pipeline för kontinuerlig distribution med DSC</span><span class="sxs-lookup"><span data-stu-id="04f9e-103">Building a Continuous Integration and Continuous Deployment pipeline with DSC</span></span>

<span data-ttu-id="04f9e-104">Det här exemplet visar hur du skapar en pipeline för kontinuerlig integrering/distribution (CI/CD) med hjälp av PowerShell, DSC, pester och Visual Studio Team Foundation Server (TFS).</span><span class="sxs-lookup"><span data-stu-id="04f9e-104">This example demonstrates how to build a Continuous Integration/Continuous Deployment (CI/CD) pipeline by using PowerShell, DSC, Pester, and Visual Studio Team Foundation Server (TFS).</span></span>

<span data-ttu-id="04f9e-105">När pipelinen har skapats och kon figurer ATS kan du använda den för att fullständigt distribuera, konfigurera och testa en DNS-server och associerade värd poster.</span><span class="sxs-lookup"><span data-stu-id="04f9e-105">After the pipeline is built and configured, you can use it to fully deploy, configure and test a DNS server and associated host records.</span></span>
<span data-ttu-id="04f9e-106">Den här processen simulerar den första delen av en pipeline som används i en utvecklings miljö.</span><span class="sxs-lookup"><span data-stu-id="04f9e-106">This process simulates the first part of a pipeline that would be used in a development environment.</span></span>

<span data-ttu-id="04f9e-107">En automatiserad CI/CD-pipeline hjälper dig att uppdatera program vara snabbare och mer tillförlitligt, se till att all kod testas och att en aktuell version av din kod är tillgänglig hela tiden.</span><span class="sxs-lookup"><span data-stu-id="04f9e-107">An automated CI/CD pipeline helps you update software faster and more reliably, ensuring that all code is tested, and that a current build of your code is available at all times.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="04f9e-108">Krav</span><span class="sxs-lookup"><span data-stu-id="04f9e-108">Prerequisites</span></span>

<span data-ttu-id="04f9e-109">För att kunna använda det här exemplet bör du vara bekant med följande:</span><span class="sxs-lookup"><span data-stu-id="04f9e-109">To use this example, you should be familiar with the following:</span></span>

- <span data-ttu-id="04f9e-110">CI-CD-koncept.</span><span class="sxs-lookup"><span data-stu-id="04f9e-110">CI-CD concepts.</span></span> <span data-ttu-id="04f9e-111">En lämplig referens finns i [modell för versions pipeline](https://aka.ms/thereleasepipelinemodelpdf).</span><span class="sxs-lookup"><span data-stu-id="04f9e-111">A good reference can be found at [The Release Pipeline Model](https://aka.ms/thereleasepipelinemodelpdf).</span></span>
- <span data-ttu-id="04f9e-112">[Git](https://git-scm.com/) -datakälla</span><span class="sxs-lookup"><span data-stu-id="04f9e-112">[Git](https://git-scm.com/) source control</span></span>
- <span data-ttu-id="04f9e-113">[Pester](https://github.com/pester/Pester) test Framework</span><span class="sxs-lookup"><span data-stu-id="04f9e-113">The [Pester](https://github.com/pester/Pester) testing framework</span></span>
- [<span data-ttu-id="04f9e-114">Team Foundation-Server</span><span class="sxs-lookup"><span data-stu-id="04f9e-114">Team Foundation Server</span></span>](https://visualstudio.microsoft.com/tfs/)

## <a name="what-you-will-need"></a><span data-ttu-id="04f9e-115">Vad du behöver</span><span class="sxs-lookup"><span data-stu-id="04f9e-115">What you will need</span></span>

<span data-ttu-id="04f9e-116">För att skapa och köra det här exemplet behöver du en miljö med flera datorer och/eller virtuella datorer.</span><span class="sxs-lookup"><span data-stu-id="04f9e-116">To build and run this example, you will need an environment with several computers and/or virtual machines.</span></span>

### <a name="client"></a><span data-ttu-id="04f9e-117">Client</span><span class="sxs-lookup"><span data-stu-id="04f9e-117">Client</span></span>

<span data-ttu-id="04f9e-118">Det här är den dator där du utför all arbets inställning och kör exemplet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-118">This is the computer where you'll do all of the work setting up and running the example.</span></span>

<span data-ttu-id="04f9e-119">Klient datorn måste vara en Windows-dator med följande installerat:</span><span class="sxs-lookup"><span data-stu-id="04f9e-119">The client computer must be a Windows computer with the following installed:</span></span>

- [<span data-ttu-id="04f9e-120">Git</span><span class="sxs-lookup"><span data-stu-id="04f9e-120">Git</span></span>](https://git-scm.com/)
- <span data-ttu-id="04f9e-121">en lokal git-lagrings platsen klonad frånhttps://github.com/PowerShell/Demo_CI</span><span class="sxs-lookup"><span data-stu-id="04f9e-121">a local git repo cloned from https://github.com/PowerShell/Demo_CI</span></span>
- <span data-ttu-id="04f9e-122">en text redigerare, till exempel [Visual Studio Code](https://code.visualstudio.com/)</span><span class="sxs-lookup"><span data-stu-id="04f9e-122">a text editor, such as [Visual Studio Code](https://code.visualstudio.com/)</span></span>

### <a name="tfssrv1"></a><span data-ttu-id="04f9e-123">TFSSrv1</span><span class="sxs-lookup"><span data-stu-id="04f9e-123">TFSSrv1</span></span>

<span data-ttu-id="04f9e-124">Datorn som är värd för TFS-servern där du definierar build och version.</span><span class="sxs-lookup"><span data-stu-id="04f9e-124">The computer that hosts the TFS server where you will define your build and release.</span></span>
<span data-ttu-id="04f9e-125">Den här datorn måste ha [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installerat.</span><span class="sxs-lookup"><span data-stu-id="04f9e-125">This computer must have [Team Foundation Server 2017](https://visualstudio.microsoft.com/tfs/) installed.</span></span>

### <a name="buildagent"></a><span data-ttu-id="04f9e-126">BuildAgent</span><span class="sxs-lookup"><span data-stu-id="04f9e-126">BuildAgent</span></span>

<span data-ttu-id="04f9e-127">Datorn som kör Windows build-agenten som bygger projektet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-127">The computer that runs the Windows build agent that builds the project.</span></span>
<span data-ttu-id="04f9e-128">Datorn måste ha en Windows build-agent installerad och igång.</span><span class="sxs-lookup"><span data-stu-id="04f9e-128">This computer must have a Windows build agent installed and running.</span></span>
<span data-ttu-id="04f9e-129">Se [distribuera en agent i Windows](/azure/devops/pipelines/agents/v2-windows) för instruktioner om hur du installerar och kör en Windows build-agent.</span><span class="sxs-lookup"><span data-stu-id="04f9e-129">See [Deploy an agent on Windows](/azure/devops/pipelines/agents/v2-windows) for instructions on how to install and run a Windows build agent.</span></span>

<span data-ttu-id="04f9e-130">Du måste också installera både- `xDnsServer` och `xNetworking` DSC-modulerna på den här datorn.</span><span class="sxs-lookup"><span data-stu-id="04f9e-130">You also need to install both the `xDnsServer` and `xNetworking` DSC modules on this computer.</span></span>

### <a name="testagent1"></a><span data-ttu-id="04f9e-131">TestAgent1</span><span class="sxs-lookup"><span data-stu-id="04f9e-131">TestAgent1</span></span>

<span data-ttu-id="04f9e-132">Detta är den dator som är konfigurerad som en DNS-server av DSC-konfigurationen i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-132">This is the computer that is configured as a DNS server by the DSC configuration in this example.</span></span>
<span data-ttu-id="04f9e-133">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="04f9e-133">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

### <a name="testagent2"></a><span data-ttu-id="04f9e-134">TestAgent2</span><span class="sxs-lookup"><span data-stu-id="04f9e-134">TestAgent2</span></span>

<span data-ttu-id="04f9e-135">Detta är den dator som är värd för webbplatsen som exemplet konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="04f9e-135">This is the computer that hosts the website this example configures.</span></span>
<span data-ttu-id="04f9e-136">Datorn måste köra [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span><span class="sxs-lookup"><span data-stu-id="04f9e-136">The computer must be running [Windows Server 2016](https://www.microsoft.com/en-us/evalcenter/evaluate-windows-server-2016).</span></span>

## <a name="add-the-code-to-tfs"></a><span data-ttu-id="04f9e-137">Lägg till koden i TFS</span><span class="sxs-lookup"><span data-stu-id="04f9e-137">Add the code to TFS</span></span>

<span data-ttu-id="04f9e-138">Vi börjar med att skapa en git-lagringsplats i TFS och importera koden från din lokala lagrings plats på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="04f9e-138">We'll start out by creating a Git repository in TFS, and importing the code from your local repository on the client computer.</span></span>
<span data-ttu-id="04f9e-139">Om du inte redan har klonat Demo_CI-lagringsplatsen till klient datorn gör du det nu genom att köra följande git-kommando:</span><span class="sxs-lookup"><span data-stu-id="04f9e-139">If you have not already cloned the Demo_CI repository to your client computer, do so now by running the following git command:</span></span>

`git clone https://github.com/PowerShell/Demo_CI`

1. <span data-ttu-id="04f9e-140">Navigera till din TFS-server i en webbläsare på klient datorn.</span><span class="sxs-lookup"><span data-stu-id="04f9e-140">On your client computer, navigate to your TFS server in a web browser.</span></span>
1. <span data-ttu-id="04f9e-141">[Skapa ett nytt team projekt](/azure/devops/organizations/projects/create-project) med namnet DEMO_CI i TFS.</span><span class="sxs-lookup"><span data-stu-id="04f9e-141">In TFS, [Create a new team project](/azure/devops/organizations/projects/create-project) named Demo_CI.</span></span>

   <span data-ttu-id="04f9e-142">Kontrol lera att **versions kontroll** är inställt på **git**.</span><span class="sxs-lookup"><span data-stu-id="04f9e-142">Make sure that **Version control** is set to **Git**.</span></span>
1. <span data-ttu-id="04f9e-143">På klient datorn lägger du till en fjärr anslutning till den lagrings plats som du nyss skapade i TFS med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="04f9e-143">On your client computer, add a remote to the repository you just created in TFS with the following command:</span></span>

   `git remote add tfs <YourTFSRepoURL>`

   <span data-ttu-id="04f9e-144">Där `<YourTFSRepoURL>` är klon-URL: en till TFS-lagringsplatsen som du skapade i föregående steg.</span><span class="sxs-lookup"><span data-stu-id="04f9e-144">Where `<YourTFSRepoURL>` is the clone URL to the TFS repository you created in the previous step.</span></span>

   <span data-ttu-id="04f9e-145">Om du inte vet var du hittar den här URL: en kan du läsa [klona en befintlig git-lagrings platsen](/azure/devops/repos/git/clone).</span><span class="sxs-lookup"><span data-stu-id="04f9e-145">If you don't know where to find this URL, see [Clone an existing Git repo](/azure/devops/repos/git/clone).</span></span>
1. <span data-ttu-id="04f9e-146">Skicka koden från din lokala lagrings plats till TFS-lagringsplatsen med följande kommando:</span><span class="sxs-lookup"><span data-stu-id="04f9e-146">Push the code from your local repository to your TFS repository with the following command:</span></span>

   `git push tfs --all`
1. <span data-ttu-id="04f9e-147">TFS-lagringsplatsen fylls med Demo_CI koden.</span><span class="sxs-lookup"><span data-stu-id="04f9e-147">The TFS repository will be populated with the Demo_CI code.</span></span>

> [!NOTE]
> <span data-ttu-id="04f9e-148">I det här exemplet används koden i `ci-cd-example` grenen för git-lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-148">This example uses the code in the `ci-cd-example` branch of the Git repo.</span></span>
> <span data-ttu-id="04f9e-149">Se till att ange den här grenen som standard gren i ditt TFS-projekt och för de CI/CD-utlösare som du skapar.</span><span class="sxs-lookup"><span data-stu-id="04f9e-149">Be sure to specify this branch as the default branch in your TFS project, and for the CI/CD triggers you create.</span></span>

## <a name="understanding-the-code"></a><span data-ttu-id="04f9e-150">Förstå koden</span><span class="sxs-lookup"><span data-stu-id="04f9e-150">Understanding the code</span></span>

<span data-ttu-id="04f9e-151">Innan vi skapar pipelinen build och Deployment kan vi titta på en del av koden för att förstå vad som händer.</span><span class="sxs-lookup"><span data-stu-id="04f9e-151">Before we create the build and deployment pipelines, let's look at some of the code to understand what is going on.</span></span>
<span data-ttu-id="04f9e-152">Öppna din favorit text redigerare på klient datorn och gå till roten för din Demo_CI git-lagringsplats.</span><span class="sxs-lookup"><span data-stu-id="04f9e-152">On your client computer, open your favorite text editor and navigate to the root of your Demo_CI Git repository.</span></span>

### <a name="the-dsc-configuration"></a><span data-ttu-id="04f9e-153">DSC-konfigurationen</span><span class="sxs-lookup"><span data-stu-id="04f9e-153">The DSC configuration</span></span>

<span data-ttu-id="04f9e-154">Öppna filen `DNSServer.ps1` (från roten i den lokala Demo_CI `./InfraDNS/Configs/DNSServer.ps1`-lagringsplatsen).</span><span class="sxs-lookup"><span data-stu-id="04f9e-154">Open the file `DNSServer.ps1` (from the root of the local Demo_CI repository, `./InfraDNS/Configs/DNSServer.ps1`).</span></span>

<span data-ttu-id="04f9e-155">Den här filen innehåller DSC-konfigurationen som konfigurerar DNS-servern.</span><span class="sxs-lookup"><span data-stu-id="04f9e-155">This file contains the DSC configuration that sets up the DNS server.</span></span> <span data-ttu-id="04f9e-156">Här är dess helhet:</span><span class="sxs-lookup"><span data-stu-id="04f9e-156">Here it is in its entirety:</span></span>

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

<span data-ttu-id="04f9e-157">Lägg märke `Node` till instruktionen:</span><span class="sxs-lookup"><span data-stu-id="04f9e-157">Notice the `Node` statement:</span></span>

```powershell
Node $AllNodes.Where{$_.Role -eq 'DNSServer'}.NodeName
```

<span data-ttu-id="04f9e-158">Detta hittar alla noder som har definierats som en roll `DNSServer` i [konfigurations data](../configurations/configData.md), som skapas av `DevEnv.ps1` skriptet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-158">This finds any nodes that were defined as having a role of `DNSServer` in the [configuration data](../configurations/configData.md), which is created by the `DevEnv.ps1` script.</span></span>

<span data-ttu-id="04f9e-159">Du kan läsa mer om `Where` metoden i [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span><span class="sxs-lookup"><span data-stu-id="04f9e-159">You can read more about the `Where` method in [about_arrays](/powershell/module/microsoft.powershell.core/about/about_arrays)</span></span>

<span data-ttu-id="04f9e-160">Att använda konfigurations data för att definiera noder är viktigt när du använder CI eftersom Node-information troligen kommer att ändras mellan miljöer, och med hjälp av konfigurations data kan du enkelt göra ändringar i Node-informationen utan att ändra konfigurations koden.</span><span class="sxs-lookup"><span data-stu-id="04f9e-160">Using configuration data to define nodes is important when doing CI because node information will likely change between environments, and using configuration data allows you to easily make changes to node information without changing the configuration code.</span></span>

<span data-ttu-id="04f9e-161">I det första resurs blocket anropar konfigurationen **WindowsFeature** för att se till att DNS-funktionen är aktive rad.</span><span class="sxs-lookup"><span data-stu-id="04f9e-161">In the first resource block, the configuration calls the **WindowsFeature** to ensure that the DNS feature is enabled.</span></span>
<span data-ttu-id="04f9e-162">Resurs blocken som följer anrops resurser från [xDnsServer](https://github.com/PowerShell/xDnsServer) -modulen för att konfigurera den primära zonen och DNS-poster.</span><span class="sxs-lookup"><span data-stu-id="04f9e-162">The resource blocks that follow call resources from the [xDnsServer](https://github.com/PowerShell/xDnsServer) module to configure the primary zone and DNS records.</span></span>

<span data-ttu-id="04f9e-163">Observera att de två `xDnsRecord` blocken omsluts av `foreach` slingor som itererar genom matriser i konfigurations data.</span><span class="sxs-lookup"><span data-stu-id="04f9e-163">Notice that the two `xDnsRecord` blocks are wrapped in `foreach` loops that iterate through arrays in the configuration data.</span></span>
<span data-ttu-id="04f9e-164">Sedan skapas konfigurations data av `DevEnv.ps1` skriptet, som vi ska titta på härnäst.</span><span class="sxs-lookup"><span data-stu-id="04f9e-164">Again, the configuration data is created by the `DevEnv.ps1` script, which we'll look at next.</span></span>

### <a name="configuration-data"></a><span data-ttu-id="04f9e-165">Konfigurationsdata</span><span class="sxs-lookup"><span data-stu-id="04f9e-165">Configuration data</span></span>

<span data-ttu-id="04f9e-166">`DevEnv.ps1` Filen (från roten i `./InfraDNS/DevEnv.ps1`den lokala Demo_CI-lagringsplatsen) anger miljödefinierade konfigurations data i en hash-enhet och skickar sedan den hash-tabellen till ett anrop `New-DscConfigurationDataDocument` till funktionen, som definieras i `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span><span class="sxs-lookup"><span data-stu-id="04f9e-166">The `DevEnv.ps1` file (from the root of the local Demo_CI repository, `./InfraDNS/DevEnv.ps1`) specifies the environment-specific configuration data in a hashtable, and then passes that hashtable to a call to the `New-DscConfigurationDataDocument` function, which is defined in `DscPipelineTools.psm` (`./Assets/DscPipelineTools/DscPipelineTools.psm1`).</span></span>

<span data-ttu-id="04f9e-167">`DevEnv.ps1` Filen:</span><span class="sxs-lookup"><span data-stu-id="04f9e-167">The `DevEnv.ps1` file:</span></span>

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

<span data-ttu-id="04f9e-168">Funktionen (definierad i `\Assets\DscPipelineTools\DscPipelineTools.psm1`) skapar program mässigt ett konfigurations data dokument från hash-tabellen (Node data) och matrisen (data som inte finns på en `RawEnvData` nod) som skickas `OtherEnvData` som-och-parametrarna. `New-DscConfigurationDataDocument`</span><span class="sxs-lookup"><span data-stu-id="04f9e-168">The `New-DscConfigurationDataDocument` function (defined in `\Assets\DscPipelineTools\DscPipelineTools.psm1`) programmatically creates a configuration data document from the hashtable (node data) and array (non-node data) that are passed as the `RawEnvData` and `OtherEnvData` parameters.</span></span>

<span data-ttu-id="04f9e-169">I vårt fall används endast `RawEnvData` parametern.</span><span class="sxs-lookup"><span data-stu-id="04f9e-169">In our case, only the `RawEnvData` parameter is used.</span></span>

### <a name="the-psake-build-script"></a><span data-ttu-id="04f9e-170">Psake build-skriptet</span><span class="sxs-lookup"><span data-stu-id="04f9e-170">The psake build script</span></span>

<span data-ttu-id="04f9e-171">[Psake](https://github.com/psake/psake) build-skriptet som definieras `Build.ps1` i (från roten i Demo_CI `./InfraDNS/Build.ps1`-lagringsplatsen) definierar uppgifter som ingår i bygget.</span><span class="sxs-lookup"><span data-stu-id="04f9e-171">The [psake](https://github.com/psake/psake) build script defined in `Build.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Build.ps1`) defines tasks that are part of the build.</span></span>
<span data-ttu-id="04f9e-172">Den definierar också vilka andra aktiviteter varje aktivitet är beroende av.</span><span class="sxs-lookup"><span data-stu-id="04f9e-172">It also defines which other tasks each task depends on.</span></span>
<span data-ttu-id="04f9e-173">När det anropas ser psake-skriptet till att den angivna aktiviteten (eller aktiviteten som `Default` kallas om ingen anges) körs och att alla beroenden också körs (detta är rekursivt, så att beroenden av beroenden körs, och så vidare).</span><span class="sxs-lookup"><span data-stu-id="04f9e-173">When invoked, the psake script ensures that the specified task (or the task named `Default` if none is specified) runs, and that all dependencies also run (this is recursive, so that dependencies of dependencies run, and so on).</span></span>

<span data-ttu-id="04f9e-174">I det här exemplet definieras `Default` uppgiften som:</span><span class="sxs-lookup"><span data-stu-id="04f9e-174">In this example, the `Default` task is defined as:</span></span>

```powershell
Task Default -depends UnitTests
```

<span data-ttu-id="04f9e-175">`Default` Aktiviteten har ingen implementering, men har ett beroende av `CompileConfigs` uppgiften.</span><span class="sxs-lookup"><span data-stu-id="04f9e-175">The `Default` task has no implementation itself, but has a dependency on the `CompileConfigs` task.</span></span>
<span data-ttu-id="04f9e-176">Den resulterande kedjan med aktivitets beroenden säkerställer att alla aktiviteter i build-skriptet körs.</span><span class="sxs-lookup"><span data-stu-id="04f9e-176">The resulting chain of task dependencies ensures that all tasks in the build script are run.</span></span>

<span data-ttu-id="04f9e-177">I det här exemplet anropas psake-skriptet av ett anrop till `Invoke-PSake` i `Initiate.ps1` filen (som finns i roten i Demo_CI-lagringsplatsen):</span><span class="sxs-lookup"><span data-stu-id="04f9e-177">In this example, the psake script is invoked by a call to `Invoke-PSake` in the `Initiate.ps1` file (located at the root of the Demo_CI repository):</span></span>

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

<span data-ttu-id="04f9e-178">När vi skapar build-definitionen för vårt exempel i TFS, kommer vi att tillhandahålla vår psake-skriptfil som `fileName` parameter för det här skriptet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-178">When we create the build definition for our example in TFS, we will supply our psake script file as the `fileName` parameter for this script.</span></span>

<span data-ttu-id="04f9e-179">Bygg skriptet definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="04f9e-179">The build script defines the following tasks:</span></span>

#### <a name="generateenvironmentfiles"></a><span data-ttu-id="04f9e-180">GenerateEnvironmentFiles</span><span class="sxs-lookup"><span data-stu-id="04f9e-180">GenerateEnvironmentFiles</span></span>

<span data-ttu-id="04f9e-181">Körs `DevEnv.ps1`, vilket genererar konfigurations data filen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-181">Runs `DevEnv.ps1`, which generates the configuration data file.</span></span>

#### <a name="installmodules"></a><span data-ttu-id="04f9e-182">InstallModules</span><span class="sxs-lookup"><span data-stu-id="04f9e-182">InstallModules</span></span>

<span data-ttu-id="04f9e-183">Installerar de moduler som krävs för konfigurationen `DNSServer.ps1`.</span><span class="sxs-lookup"><span data-stu-id="04f9e-183">Installs the modules required by the configuration `DNSServer.ps1`.</span></span>

#### <a name="scriptanalysis"></a><span data-ttu-id="04f9e-184">ScriptAnalysis</span><span class="sxs-lookup"><span data-stu-id="04f9e-184">ScriptAnalysis</span></span>

<span data-ttu-id="04f9e-185">Anropar [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span><span class="sxs-lookup"><span data-stu-id="04f9e-185">Calls the [PSScriptAnalyzer](https://github.com/PowerShell/PSScriptAnalyzer).</span></span>

#### <a name="unittests"></a><span data-ttu-id="04f9e-186">UnitTests</span><span class="sxs-lookup"><span data-stu-id="04f9e-186">UnitTests</span></span>

<span data-ttu-id="04f9e-187">Kör [pester](https://github.com/pester/Pester/wiki) Unit-tester.</span><span class="sxs-lookup"><span data-stu-id="04f9e-187">Runs the [Pester](https://github.com/pester/Pester/wiki) unit tests.</span></span>

#### <a name="compileconfigs"></a><span data-ttu-id="04f9e-188">CompileConfigs</span><span class="sxs-lookup"><span data-stu-id="04f9e-188">CompileConfigs</span></span>

<span data-ttu-id="04f9e-189">Kompilerar konfigurationen (`DNSServer.ps1`) till en MOF-fil med hjälp av konfigurations data som genererats av `GenerateEnvironmentFiles` aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="04f9e-189">Compiles the configuration (`DNSServer.ps1`) into a MOF file, using the configuration data generated by the `GenerateEnvironmentFiles` task.</span></span>

#### <a name="clean"></a><span data-ttu-id="04f9e-190">Rensa</span><span class="sxs-lookup"><span data-stu-id="04f9e-190">Clean</span></span>

<span data-ttu-id="04f9e-191">Skapar mapparna som används för exemplet och tar bort alla test resultat, konfigurationsfiler för data och moduler från tidigare körningar.</span><span class="sxs-lookup"><span data-stu-id="04f9e-191">Creates the folders used for the example, and removes any test results, configuration data files, and modules from previous runs.</span></span>

### <a name="the-psake-deploy-script"></a><span data-ttu-id="04f9e-192">Skript för psake-distribution</span><span class="sxs-lookup"><span data-stu-id="04f9e-192">The psake deploy script</span></span>

<span data-ttu-id="04f9e-193">Det [psake](https://github.com/psake/psake) distributions skript som `Deploy.ps1` definierats i (från roten i Demo_CI `./InfraDNS/Deploy.ps1`-lagringsplatsen) definierar aktiviteter som distribuerar och kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-193">The [psake](https://github.com/psake/psake) deployment script defined in `Deploy.ps1` (from the root of the Demo_CI repository, `./InfraDNS/Deploy.ps1`) defines tasks that deploy and run the configuration.</span></span>

<span data-ttu-id="04f9e-194">`Deploy.ps1`definierar följande uppgifter:</span><span class="sxs-lookup"><span data-stu-id="04f9e-194">`Deploy.ps1` defines the following tasks:</span></span>

#### <a name="deploymodules"></a><span data-ttu-id="04f9e-195">DeployModules</span><span class="sxs-lookup"><span data-stu-id="04f9e-195">DeployModules</span></span>

<span data-ttu-id="04f9e-196">Startar en PowerShell-session `TestAgent1` på och installerar de moduler som innehåller de DSC-resurser som krävs för konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-196">Starts a PowerShell session on `TestAgent1` and installs the modules containing the DSC resources required for the configuration.</span></span>

#### <a name="deployconfigs"></a><span data-ttu-id="04f9e-197">DeployConfigs</span><span class="sxs-lookup"><span data-stu-id="04f9e-197">DeployConfigs</span></span>

<span data-ttu-id="04f9e-198">Anropar cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) för att köra konfigurationen `TestAgent1`på.</span><span class="sxs-lookup"><span data-stu-id="04f9e-198">Calls the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet to run the configuration on `TestAgent1`.</span></span>

#### <a name="integrationtests"></a><span data-ttu-id="04f9e-199">IntegrationTests</span><span class="sxs-lookup"><span data-stu-id="04f9e-199">IntegrationTests</span></span>

<span data-ttu-id="04f9e-200">Kör [pester](https://github.com/pester/Pester/wiki) -integrations test.</span><span class="sxs-lookup"><span data-stu-id="04f9e-200">Runs the [Pester](https://github.com/pester/Pester/wiki) integration tests.</span></span>

#### <a name="acceptancetests"></a><span data-ttu-id="04f9e-201">AcceptanceTests</span><span class="sxs-lookup"><span data-stu-id="04f9e-201">AcceptanceTests</span></span>

<span data-ttu-id="04f9e-202">Kör testerna för [pester](https://github.com/pester/Pester/wiki) -godkännande.</span><span class="sxs-lookup"><span data-stu-id="04f9e-202">Runs the [Pester](https://github.com/pester/Pester/wiki) acceptance tests.</span></span>

#### <a name="clean"></a><span data-ttu-id="04f9e-203">Rensa</span><span class="sxs-lookup"><span data-stu-id="04f9e-203">Clean</span></span>

<span data-ttu-id="04f9e-204">Tar bort alla moduler som är installerade i tidigare körningar och ser till att mappen test resultat finns.</span><span class="sxs-lookup"><span data-stu-id="04f9e-204">Removes any modules installed in previous runs, and ensures that the test result folder exists.</span></span>

### <a name="test-scripts"></a><span data-ttu-id="04f9e-205">Test skript</span><span class="sxs-lookup"><span data-stu-id="04f9e-205">Test scripts</span></span>

<span data-ttu-id="04f9e-206">Godkännande-, integrations-och enhets test definieras i skript `Tests` i mappen (från roten i Demo_CI-lagringsplatsen `./InfraDNS/Tests`), var och en i `DNSServer.tests.ps1` filer som heter i respektive mapp.</span><span class="sxs-lookup"><span data-stu-id="04f9e-206">Acceptance, Integration, and Unit tests are defined in scripts in the `Tests` folder (from the root of the Demo_CI repository, `./InfraDNS/Tests`), each in files named `DNSServer.tests.ps1` in their respective folders.</span></span>

<span data-ttu-id="04f9e-207">Test skripten använder syntaxen [pester](https://github.com/pester/Pester/wiki) och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) .</span><span class="sxs-lookup"><span data-stu-id="04f9e-207">The test scripts use [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="unit-tests"></a><span data-ttu-id="04f9e-208">Enhets tester</span><span class="sxs-lookup"><span data-stu-id="04f9e-208">Unit tests</span></span>

<span data-ttu-id="04f9e-209">Enhets testerna testar själva DSC-konfigurationen för att se till att konfigurationerna kommer att göra vad som förväntas när de körs.</span><span class="sxs-lookup"><span data-stu-id="04f9e-209">The unit tests test the DSC configurations themselves to ensure that the configurations will do what is expected when they run.</span></span>
<span data-ttu-id="04f9e-210">Enhets test skriptet använder [pester](https://github.com/pester/Pester/wiki).</span><span class="sxs-lookup"><span data-stu-id="04f9e-210">The unit test script uses [Pester](https://github.com/pester/Pester/wiki).</span></span>

#### <a name="integration-tests"></a><span data-ttu-id="04f9e-211">Integrations test</span><span class="sxs-lookup"><span data-stu-id="04f9e-211">Integration tests</span></span>

<span data-ttu-id="04f9e-212">Integrerings testerna testar systemets konfiguration för att säkerställa att när det är integrerat med andra komponenter, konfigureras systemet som förväntat.</span><span class="sxs-lookup"><span data-stu-id="04f9e-212">The integration tests test the configuration of the system to ensure that when integrated with other components, the system is configured as expected.</span></span> <span data-ttu-id="04f9e-213">De här testerna körs på målnoden när den har kon figurer ATS med DSC.</span><span class="sxs-lookup"><span data-stu-id="04f9e-213">These tests run on the target node after it has been configured with DSC.</span></span>
<span data-ttu-id="04f9e-214">Integrations test skriptet använder en blandning av [pester](https://github.com/pester/Pester/wiki) -och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-214">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

#### <a name="acceptance-tests"></a><span data-ttu-id="04f9e-215">Acceptans test</span><span class="sxs-lookup"><span data-stu-id="04f9e-215">Acceptance tests</span></span>

<span data-ttu-id="04f9e-216">Test av godkännande testar systemet för att se till att det fungerar som förväntat.</span><span class="sxs-lookup"><span data-stu-id="04f9e-216">Acceptance tests test the system to ensure that it behaves as expected.</span></span>
<span data-ttu-id="04f9e-217">Till exempel testar den för att se till att en webb sida returnerar rätt information när den efter frågas.</span><span class="sxs-lookup"><span data-stu-id="04f9e-217">For example, it tests to ensure a web page returns the right information when queried.</span></span>
<span data-ttu-id="04f9e-218">De här testerna körs på distans från målnoden för att kunna testa verkliga scenarier.</span><span class="sxs-lookup"><span data-stu-id="04f9e-218">These tests run remotely from the target node in order to test real world scenarios.</span></span>
<span data-ttu-id="04f9e-219">Integrations test skriptet använder en blandning av [pester](https://github.com/pester/Pester/wiki) -och [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) -syntaxen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-219">The integration test script uses a mixture of [Pester](https://github.com/pester/Pester/wiki) and [PoshSpec](https://github.com/Ticketmaster/poshspec/wiki/Introduction) syntax.</span></span>

## <a name="define-the-build"></a><span data-ttu-id="04f9e-220">Definiera versionen</span><span class="sxs-lookup"><span data-stu-id="04f9e-220">Define the build</span></span>

<span data-ttu-id="04f9e-221">Nu när vi har laddat upp vår kod till TFS och tittat på vad det gör kan vi definiera vår version.</span><span class="sxs-lookup"><span data-stu-id="04f9e-221">Now that we've uploaded our code to TFS and looked at what it does, let's define our build.</span></span>

<span data-ttu-id="04f9e-222">Här kommer vi bara att se de build-steg som du kommer att lägga till i versionen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-222">Here, we'll cover only the build steps that you'll add to the build.</span></span> <span data-ttu-id="04f9e-223">Instruktioner för hur du skapar en bygge-definition i TFS finns i [skapa och köa en build-definition](/azure/devops/pipelines/create-first-pipeline).</span><span class="sxs-lookup"><span data-stu-id="04f9e-223">For instructions on how to create a build definition in TFS, see [Create and queue a build definition](/azure/devops/pipelines/create-first-pipeline).</span></span>

<span data-ttu-id="04f9e-224">Skapa en ny Bygg definition (Välj den **tomma** mallen) med namnet "InfraDNS".</span><span class="sxs-lookup"><span data-stu-id="04f9e-224">Create a new build definition (select the **Empty** template) named "InfraDNS".</span></span>
<span data-ttu-id="04f9e-225">Lägg till följande steg i bygg definitionen:</span><span class="sxs-lookup"><span data-stu-id="04f9e-225">Add the following steps to you build definition:</span></span>

- <span data-ttu-id="04f9e-226">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="04f9e-226">PowerShell Script</span></span>
- <span data-ttu-id="04f9e-227">Publicera Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-227">Publish Test Results</span></span>
- <span data-ttu-id="04f9e-228">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="04f9e-228">Copy Files</span></span>
- <span data-ttu-id="04f9e-229">Publicera artefakt</span><span class="sxs-lookup"><span data-stu-id="04f9e-229">Publish Artifact</span></span>

<span data-ttu-id="04f9e-230">När du har lagt till dessa build-steg redigerar du egenskaperna för varje steg enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04f9e-230">After adding these build steps, edit the properties of each step as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="04f9e-231">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="04f9e-231">PowerShell Script</span></span>

1. <span data-ttu-id="04f9e-232">Ange egenskapen **Type** till `File Path`.</span><span class="sxs-lookup"><span data-stu-id="04f9e-232">Set the **Type** property to `File Path`.</span></span>
1. <span data-ttu-id="04f9e-233">Ange egenskapen för **skript Sök vägen** till `initiate.ps1`.</span><span class="sxs-lookup"><span data-stu-id="04f9e-233">Set the **Script Path** property to `initiate.ps1`.</span></span>
1. <span data-ttu-id="04f9e-234">Lägg `-fileName build` till i egenskapen **arguments** .</span><span class="sxs-lookup"><span data-stu-id="04f9e-234">Add `-fileName build` to the **Arguments** property.</span></span>

<span data-ttu-id="04f9e-235">Det här build-steget `initiate.ps1` kör filen som anropar psake build-skriptet.</span><span class="sxs-lookup"><span data-stu-id="04f9e-235">This build step runs the `initiate.ps1` file, which calls the psake build script.</span></span>

### <a name="publish-test-results"></a><span data-ttu-id="04f9e-236">Publicera Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-236">Publish Test Results</span></span>

1. <span data-ttu-id="04f9e-237">Ange **test resultat format** till`NUnit`</span><span class="sxs-lookup"><span data-stu-id="04f9e-237">Set **Test Result Format** to `NUnit`</span></span>
1. <span data-ttu-id="04f9e-238">Ange **testresultat filer** till`InfraDNS/Tests/Results/*.xml`</span><span class="sxs-lookup"><span data-stu-id="04f9e-238">Set **Test Results Files** to `InfraDNS/Tests/Results/*.xml`</span></span>
1. <span data-ttu-id="04f9e-239">Ange **körnings titel** för `Unit`test till.</span><span class="sxs-lookup"><span data-stu-id="04f9e-239">Set **Test Run Title** to `Unit`.</span></span>
1. <span data-ttu-id="04f9e-240">Kontrol lera att **kontroll alternativen** **är aktiverade** och att **alltid körs** båda är markerade.</span><span class="sxs-lookup"><span data-stu-id="04f9e-240">Make sure **Control Options** **Enabled** and **Always run** are both selected.</span></span>

<span data-ttu-id="04f9e-241">Det här build-steget Kör enhets testerna i pester-skriptet som vi såg tidigare och lagrar resultatet i `InfraDNS/Tests/Results/*.xml` mappen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-241">This build step runs the unit tests in the Pester script we looked at earlier, and stores the results in the `InfraDNS/Tests/Results/*.xml` folder.</span></span>

### <a name="copy-files"></a><span data-ttu-id="04f9e-242">Kopiera filer</span><span class="sxs-lookup"><span data-stu-id="04f9e-242">Copy Files</span></span>

1. <span data-ttu-id="04f9e-243">Lägg till var och en av följande rader i **innehållet**:</span><span class="sxs-lookup"><span data-stu-id="04f9e-243">Add each of the following lines to **Contents**:</span></span>

   ```
   initiate.ps1
   **\deploy.ps1
   **\Acceptance\**
   **\Integration\**
   ```

1. <span data-ttu-id="04f9e-244">Ange **TargetFolder** till`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="04f9e-244">Set **TargetFolder** to `$(Build.ArtifactStagingDirectory)\`</span></span>

<span data-ttu-id="04f9e-245">I det här steget kopieras bygg-och test skript till uppsamlings katalogen så att kan publiceras som build-artefakter i nästa steg.</span><span class="sxs-lookup"><span data-stu-id="04f9e-245">This step copies the build and test scripts to the staging directory so that the can be published as build artifacts by the next step.</span></span>

### <a name="publish-artifact"></a><span data-ttu-id="04f9e-246">Publicera artefakt</span><span class="sxs-lookup"><span data-stu-id="04f9e-246">Publish Artifact</span></span>

1. <span data-ttu-id="04f9e-247">Ange **sökväg för publicering** till`$(Build.ArtifactStagingDirectory)\`</span><span class="sxs-lookup"><span data-stu-id="04f9e-247">Set **Path to Publish** to `$(Build.ArtifactStagingDirectory)\`</span></span>
1. <span data-ttu-id="04f9e-248">Ange **artefakt namn** till`Deploy`</span><span class="sxs-lookup"><span data-stu-id="04f9e-248">Set **Artifact Name** to `Deploy`</span></span>
1. <span data-ttu-id="04f9e-249">Ange **artefakt typ** till`Server`</span><span class="sxs-lookup"><span data-stu-id="04f9e-249">Set **Artifact Type** to `Server`</span></span>
1. <span data-ttu-id="04f9e-250">Välj `Enabled` i **kontroll alternativ**</span><span class="sxs-lookup"><span data-stu-id="04f9e-250">Select `Enabled` in **Control Options**</span></span>

## <a name="enable-continuous-integration"></a><span data-ttu-id="04f9e-251">Aktivera kontinuerlig integrering</span><span class="sxs-lookup"><span data-stu-id="04f9e-251">Enable continuous integration</span></span>

<span data-ttu-id="04f9e-252">Nu ska vi konfigurera en utlösare som gör att projektet skapas när en ändring checkas in i `ci-cd-example` grenen av Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-252">Now we'll set up a trigger that causes the project to build any time a change is checked in to the `ci-cd-example` branch of the git repository.</span></span>

1. <span data-ttu-id="04f9e-253">I TFS klickar du på fliken **Build & version**</span><span class="sxs-lookup"><span data-stu-id="04f9e-253">In TFS, click the **Build & Release** tab</span></span>
1. <span data-ttu-id="04f9e-254">Välj `DNS Infra` build-definitionen och klicka på **Redigera**</span><span class="sxs-lookup"><span data-stu-id="04f9e-254">Select the `DNS Infra` build definition, and click **Edit**</span></span>
1. <span data-ttu-id="04f9e-255">Klicka på fliken **utlösare**</span><span class="sxs-lookup"><span data-stu-id="04f9e-255">Click the **Triggers** tab</span></span>
1. <span data-ttu-id="04f9e-256">Välj **kontinuerlig integrering (CI)** och välj `refs/heads/ci-cd-example` i list rutan gren</span><span class="sxs-lookup"><span data-stu-id="04f9e-256">Select **Continuous integration (CI)**, and select `refs/heads/ci-cd-example` in the branch drop-down list</span></span>
1. <span data-ttu-id="04f9e-257">Klicka på **Spara** och sedan på **OK**</span><span class="sxs-lookup"><span data-stu-id="04f9e-257">Click **Save** and then **OK**</span></span>

<span data-ttu-id="04f9e-258">Nu utlöser alla ändringar i TFS git-lagringsplatsen en automatiserad version.</span><span class="sxs-lookup"><span data-stu-id="04f9e-258">Now any change in the TFS git repository triggers an automated build.</span></span>

## <a name="create-the-release-definition"></a><span data-ttu-id="04f9e-259">Skapa versions definitionen</span><span class="sxs-lookup"><span data-stu-id="04f9e-259">Create the release definition</span></span>

<span data-ttu-id="04f9e-260">Nu ska vi skapa en versions definition så att projektet distribueras till utvecklings miljön med varje kod incheckning.</span><span class="sxs-lookup"><span data-stu-id="04f9e-260">Let's create a release definition so that the project is deployed to the development environment with every code check-in.</span></span>

<span data-ttu-id="04f9e-261">Det gör du genom att lägga till en ny versions definition `InfraDNS` som är associerad med build-definitionen som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="04f9e-261">To do this, add a new release definition associated with the `InfraDNS` build definition you created previously.</span></span>
<span data-ttu-id="04f9e-262">Se till att välja **kontinuerlig distribution** så att en ny version utlöses när en ny version har slutförts.</span><span class="sxs-lookup"><span data-stu-id="04f9e-262">Be sure to select **Continuous deployment** so that a new release will be triggered any time a new build is completed.</span></span>
<span data-ttu-id="04f9e-263">([Vad är Frisläpp pipelines?](/azure/devops/pipelines/release/)) och konfigurera det enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04f9e-263">([What are release pipelines?](/azure/devops/pipelines/release/)) and configure it as follows:</span></span>

<span data-ttu-id="04f9e-264">Lägg till följande steg i versions definitionen:</span><span class="sxs-lookup"><span data-stu-id="04f9e-264">Add the following steps to the release definition:</span></span>

- <span data-ttu-id="04f9e-265">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="04f9e-265">PowerShell Script</span></span>
- <span data-ttu-id="04f9e-266">Publicera Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-266">Publish Test Results</span></span>
- <span data-ttu-id="04f9e-267">Publicera Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-267">Publish Test Results</span></span>

<span data-ttu-id="04f9e-268">Redigera stegen enligt följande:</span><span class="sxs-lookup"><span data-stu-id="04f9e-268">Edit the steps as follows:</span></span>

### <a name="powershell-script"></a><span data-ttu-id="04f9e-269">PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="04f9e-269">PowerShell Script</span></span>

1. <span data-ttu-id="04f9e-270">Ange fältet **skript Sök väg** till`$(Build.DefinitionName)\Deploy\initiate.ps1"`</span><span class="sxs-lookup"><span data-stu-id="04f9e-270">Set the **Script Path** field to `$(Build.DefinitionName)\Deploy\initiate.ps1"`</span></span>
1. <span data-ttu-id="04f9e-271">Ange **argument** fältet till`-fileName Deploy`</span><span class="sxs-lookup"><span data-stu-id="04f9e-271">Set the **Arguments** field to `-fileName Deploy`</span></span>

### <a name="first-publish-test-results"></a><span data-ttu-id="04f9e-272">Första publicerings Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-272">First Publish Test Results</span></span>

1. <span data-ttu-id="04f9e-273">Välj `NUnit` för fältet **test resultat format**</span><span class="sxs-lookup"><span data-stu-id="04f9e-273">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="04f9e-274">Ange fältet **Testa resultat filer** till`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span><span class="sxs-lookup"><span data-stu-id="04f9e-274">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Integration*.xml`</span></span>
1. <span data-ttu-id="04f9e-275">Ställ in **testets körnings titel** på`Integration`</span><span class="sxs-lookup"><span data-stu-id="04f9e-275">Set the **Test Run Title** to `Integration`</span></span>
1. <span data-ttu-id="04f9e-276">Under **kontroll alternativ**markerar du **Kör alltid**</span><span class="sxs-lookup"><span data-stu-id="04f9e-276">Under **Control Options**, check **Always run**</span></span>

### <a name="second-publish-test-results"></a><span data-ttu-id="04f9e-277">Andra publicerings Testresultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-277">Second Publish Test Results</span></span>

1. <span data-ttu-id="04f9e-278">Välj `NUnit` för fältet **test resultat format**</span><span class="sxs-lookup"><span data-stu-id="04f9e-278">Select `NUnit` for the **Test Result Format** field</span></span>
1. <span data-ttu-id="04f9e-279">Ange fältet **Testa resultat filer** till`$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span><span class="sxs-lookup"><span data-stu-id="04f9e-279">Set the **Test Result Files** field to `$(Build.DefinitionName)\Deploy\InfraDNS\Tests\Results\Acceptance*.xml`</span></span>
1. <span data-ttu-id="04f9e-280">Ställ in **testets körnings titel** på`Acceptance`</span><span class="sxs-lookup"><span data-stu-id="04f9e-280">Set the **Test Run Title** to `Acceptance`</span></span>
1. <span data-ttu-id="04f9e-281">Under **kontroll alternativ**markerar du **Kör alltid**</span><span class="sxs-lookup"><span data-stu-id="04f9e-281">Under **Control Options**, check **Always run**</span></span>

## <a name="verify-your-results"></a><span data-ttu-id="04f9e-282">Verifiera dina resultat</span><span class="sxs-lookup"><span data-stu-id="04f9e-282">Verify your results</span></span>

<span data-ttu-id="04f9e-283">Nu kommer en ny version att starta när du `ci-cd-example` skickar ändringar i grenen till TFS.</span><span class="sxs-lookup"><span data-stu-id="04f9e-283">Now, any time you push changes in the `ci-cd-example` branch to TFS, a new build will start.</span></span>
<span data-ttu-id="04f9e-284">Om skapandet har slutförts utlöses en ny distribution.</span><span class="sxs-lookup"><span data-stu-id="04f9e-284">If the build completes successfully, a new deployment is triggered.</span></span>

<span data-ttu-id="04f9e-285">Du kan kontrol lera resultatet av distributionen genom att öppna en webbläsare på klient datorn och gå till `www.contoso.com`.</span><span class="sxs-lookup"><span data-stu-id="04f9e-285">You can check the result of the deployment by opening a browser on the client machine and navigating to `www.contoso.com`.</span></span>

## <a name="next-steps"></a><span data-ttu-id="04f9e-286">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="04f9e-286">Next steps</span></span>

<span data-ttu-id="04f9e-287">I det här exemplet konfigureras DNS `TestAgent1` -servern så att `www.contoso.com` URL: en matchar `TestAgent2`, men den distribuerar inte en webbplats.</span><span class="sxs-lookup"><span data-stu-id="04f9e-287">This example configures the DNS server `TestAgent1` so that the URL `www.contoso.com` resolves to `TestAgent2`, but it does not actually deploy a website.</span></span>
<span data-ttu-id="04f9e-288">Skeleton för att göra detta finns i `WebApp` mappen lagrings platsen under mappen.</span><span class="sxs-lookup"><span data-stu-id="04f9e-288">The skeleton for doing so is provided in the repo under the `WebApp` folder.</span></span>
<span data-ttu-id="04f9e-289">Du kan använda de tillhandahållna stub-skripten för att skapa psake-skript, pester-tester och DSC-konfigurationer för att distribuera din egen webbplats.</span><span class="sxs-lookup"><span data-stu-id="04f9e-289">You can use the stubs provided to create psake scripts, Pester tests, and DSC configurations to deploy your own website.</span></span>
