---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-Snabbstart
ms.openlocfilehash: eb7572f39f7a2710c82f132f42c3502b15c48d0f
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219053"
---
> <span data-ttu-id="19f74-103">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="19f74-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="desired-state-configuration-quick-start"></a><span data-ttu-id="19f74-104">Desired State Configuration-Snabbstart</span><span class="sxs-lookup"><span data-stu-id="19f74-104">Desired State Configuration Quick Start</span></span>

<span data-ttu-id="19f74-105">Den här övningen går igenom hur du skapar och använda en önskad tillstånd Configuration DSC ()-konfiguration från början till slut.</span><span class="sxs-lookup"><span data-stu-id="19f74-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="19f74-106">Exemplet använder vi garanterar att en server har den `Web-Server` (IIS)-funktionen aktiverad och att innehållet för en enkel ”Hello World”-webbplats finns i den `intepub\wwwroot` på servern.</span><span class="sxs-lookup"><span data-stu-id="19f74-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `intepub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="19f74-107">En översikt över DSC är och hur det fungerar, se [Desired Configuration översikt över för beslutsfattare](decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="19f74-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="19f74-108">Krav</span><span class="sxs-lookup"><span data-stu-id="19f74-108">Requirements</span></span>

<span data-ttu-id="19f74-109">Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="19f74-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="19f74-110">Skriva och placera filen index.htm</span><span class="sxs-lookup"><span data-stu-id="19f74-110">Write and place the index.htm file</span></span>

<span data-ttu-id="19f74-111">Först ska vi skapa HTML-fil som vi ska använda som webbplatsens innehåll.</span><span class="sxs-lookup"><span data-stu-id="19f74-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="19f74-112">Skapa en mapp med namnet i din rotmapp `test`.</span><span class="sxs-lookup"><span data-stu-id="19f74-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="19f74-113">Skriv följande text i en textredigerare:</span><span class="sxs-lookup"><span data-stu-id="19f74-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="19f74-114">Spara den som `index.htm` i den `test` mappen som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="19f74-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="19f74-115">Skriva konfigurationen</span><span class="sxs-lookup"><span data-stu-id="19f74-115">Write the configuration</span></span>

<span data-ttu-id="19f74-116">En [DSC-konfigurationen](configurations.md) är en särskild funktion i PowerShell som definierar hur du vill konfigurera en eller flera datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="19f74-116">A [DSC configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="19f74-117">Skriv följande i PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="19f74-117">In the PowerShell ISE, type the following:</span></span>

```powershell
Configuration WebsiteTest {

    # Import the module that contains the resources we're using.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets this configuration will be applied to.
    Node 'localhost' {

        # The first resource block ensures that the Web-Server (IIS) feature is enabled.
        WindowsFeature WebServer {
            Ensure = "Present"
            Name   = "Web-Server"
        }

        # The second resource block ensures that the website content copied to the website root folder.
        File WebsiteContent {
            Ensure = 'Present'
            SourcePath = 'c:\test\index.htm'
            DestinationPath = 'c:\inetpub\wwwroot'
        }
    }
}
```

<span data-ttu-id="19f74-118">Spara filen som `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="19f74-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="19f74-119">Du kan se att det ser ut som en PowerShell-funktionen med nyckelordet **Configuration** använde före namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="19f74-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="19f74-120">Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.</span><span class="sxs-lookup"><span data-stu-id="19f74-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="19f74-121">Konfigurationen anropar två [resurser](resources.md), [WindowsFeature](windowsFeatureResource.md) och [filen](fileResource.md).</span><span class="sxs-lookup"><span data-stu-id="19f74-121">The configuration calls two [resources](resources.md), [WindowsFeature](windowsFeatureResource.md) and [File](fileResource.md).</span></span>
<span data-ttu-id="19f74-122">Resurser som arbetar för att säkerställa som Målnoden är i tillståndet enligt konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="19f74-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="19f74-123">Kompilera konfiguration</span><span class="sxs-lookup"><span data-stu-id="19f74-123">Compile the configuration</span></span>

<span data-ttu-id="19f74-124">För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="19f74-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="19f74-125">Om du vill göra detta måste köra du konfigurationen som en funktion.</span><span class="sxs-lookup"><span data-stu-id="19f74-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="19f74-126">Navigera till samma mapp där du sparade konfigurationen i PowerShell-konsolen och kör följande kommandon för att kompilera konfiguration till en MOF-fil:</span><span class="sxs-lookup"><span data-stu-id="19f74-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="19f74-127">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="19f74-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="19f74-128">Den första raden gör configuration-funktionen i konsolen.</span><span class="sxs-lookup"><span data-stu-id="19f74-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="19f74-129">Den andra raden körs konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="19f74-129">The second line runs the configuration.</span></span>
<span data-ttu-id="19f74-130">Resultatet är att en ny mapp med namnet `WebsiteTest` skapas en undermapp i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="19f74-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="19f74-131">Den `WebsiteTest` mappen innehåller en fil med namnet `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="19f74-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="19f74-132">Det är den här filen som sedan kan tillämpas på målnoden.</span><span class="sxs-lookup"><span data-stu-id="19f74-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="19f74-133">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="19f74-133">Apply the configuration</span></span>

<span data-ttu-id="19f74-134">Nu när du har den kompilerade MOF kan du tillämpa konfigurationen till målnoden (i det här fallet den lokala datorn) genom att anropa den [Start DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="19f74-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/reference/5.1/PSDesiredStateConfiguration/Start-DscConfiguration) cmdlet.</span></span>

<span data-ttu-id="19f74-135">Den `Start-DscConfiguration` cmdlet talar om den [lokala Configuration Manager (MGM)](metaConfig.md), som är motorn för DSC att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="19f74-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="19f74-136">MGM är den anropar DSC-resurser för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="19f74-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="19f74-137">Navigera till samma mapp där du sparade konfigurationen i PowerShell-konsolen och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="19f74-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="19f74-138">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="19f74-138">Test the configuration</span></span>

<span data-ttu-id="19f74-139">Du kan anropa den [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) för att se om konfigurationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="19f74-139">You can call the [Get-DscConfigurationStatus](/reference/5.1/PSDesiredStateConfiguration/Get-DscConfigurationStatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="19f74-140">Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="19f74-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="19f74-141">Du bör se ”Hello World” HTML-sidan som du skapade som ett första steg i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="19f74-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="19f74-142">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="19f74-142">Next steps</span></span>

- <span data-ttu-id="19f74-143">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="19f74-143">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="19f74-144">Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC resurser](resources.md).</span><span class="sxs-lookup"><span data-stu-id="19f74-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](resources.md).</span></span>
- <span data-ttu-id="19f74-145">Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="19f74-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>