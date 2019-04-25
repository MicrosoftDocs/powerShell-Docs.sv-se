---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Snabbstart – skapa en webbplats med DSC
ms.openlocfilehash: d98607939ccd3cc5e660936d8c0a6d54fce7d65f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079131"
---
> <span data-ttu-id="3cda4-103">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="3cda4-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="quickstart---create-a-website-with-dsc"></a><span data-ttu-id="3cda4-104">Snabbstart – skapa en webbplats med DSC</span><span class="sxs-lookup"><span data-stu-id="3cda4-104">Quickstart - Create a website with DSC</span></span>

<span data-ttu-id="3cda4-105">Den här övningen visar hur du skapar och tillämpar en konfiguration med Desired State Configuration (DSC) från början till slut.</span><span class="sxs-lookup"><span data-stu-id="3cda4-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="3cda4-106">Exemplet använder vi ser till att en server har den `Web-Server` (IIS)-funktionen aktiverad och som innehållet för en enkel ”Hello World”-webbplats finns i den `inetpub\wwwroot` katalogen i den här servern.</span><span class="sxs-lookup"><span data-stu-id="3cda4-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="3cda4-107">En översikt över vad DSC är och hur det fungerar, se [Desired State Configuration-översikt för beslutsfattare](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="3cda4-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="3cda4-108">Krav</span><span class="sxs-lookup"><span data-stu-id="3cda4-108">Requirements</span></span>

<span data-ttu-id="3cda4-109">Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="3cda4-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="3cda4-110">Skriva och placera filen index.htm</span><span class="sxs-lookup"><span data-stu-id="3cda4-110">Write and place the index.htm file</span></span>

<span data-ttu-id="3cda4-111">Först ska vi skapa HTML-fil som ska användas som webbplatsens innehåll.</span><span class="sxs-lookup"><span data-stu-id="3cda4-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="3cda4-112">Skapa en mapp med namnet i din rotmapp `test`.</span><span class="sxs-lookup"><span data-stu-id="3cda4-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="3cda4-113">Skriv följande text i en textredigerare:</span><span class="sxs-lookup"><span data-stu-id="3cda4-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="3cda4-114">Spara den som `index.htm` i den `test` mappen som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="3cda4-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="3cda4-115">Skriva konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3cda4-115">Write the configuration</span></span>

<span data-ttu-id="3cda4-116">En [DSC-konfiguration](../configurations/configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="3cda4-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="3cda4-117">Skriv följande i PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="3cda4-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="3cda4-118">Spara filen som `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="3cda4-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="3cda4-119">Du kan se att det ser ut som en PowerShell-funktion med hjälp av nyckelordet **Configuration** använde före namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="3cda4-120">Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.</span><span class="sxs-lookup"><span data-stu-id="3cda4-120">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="3cda4-121">Konfigurationen anropar två [resurser](../resources/resources.md), **WindowsFeature** och **filen**.</span><span class="sxs-lookup"><span data-stu-id="3cda4-121">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="3cda4-122">Resurser som utför arbete för att säkerställa en som Målnoden är i tillståndet som definieras av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-122">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="3cda4-123">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3cda4-123">Compile the configuration</span></span>

<span data-ttu-id="3cda4-124">För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="3cda4-124">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="3cda4-125">Om du vill göra detta måste köra du konfigurationen som en funktion.</span><span class="sxs-lookup"><span data-stu-id="3cda4-125">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="3cda4-126">Navigera till mappen där du sparade din konfiguration och kör följande kommandon för att kompilera konfigurationen till en MOF-fil i en PowerShell-konsol:</span><span class="sxs-lookup"><span data-stu-id="3cda4-126">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="3cda4-127">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="3cda4-127">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="3cda4-128">Den första raden gör configuration-funktionen som är tillgängliga i konsolen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-128">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="3cda4-129">Den andra raden kör konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-129">The second line runs the configuration.</span></span>
<span data-ttu-id="3cda4-130">Resultatet är att en ny mapp med namnet `WebsiteTest` skapas som en undermapp i den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-130">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="3cda4-131">Den `WebsiteTest` mappen innehåller en fil med namnet `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="3cda4-131">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="3cda4-132">Det är den här filen som sedan kan tillämpas på målnoden.</span><span class="sxs-lookup"><span data-stu-id="3cda4-132">It is this file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="3cda4-133">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3cda4-133">Apply the configuration</span></span>

<span data-ttu-id="3cda4-134">Nu när du har den kompilerade MOF, du kan tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3cda4-134">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="3cda4-135">Den `Start-DscConfiguration` cmdlet visar den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), vilket är motorn i DSC att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-135">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="3cda4-136">LCM fungerar för att anropa DSC-resurser för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="3cda4-136">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="3cda4-137">I PowerShell-konsolen, gå till mappen där du sparade din konfiguration och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="3cda4-137">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="3cda4-138">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="3cda4-138">Test the configuration</span></span>

<span data-ttu-id="3cda4-139">Du kan anropa den [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet för att se om konfigurationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="3cda4-139">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="3cda4-140">Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="3cda4-140">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="3cda4-141">Du bör se ”Hello World” HTML-sidan som du skapade som ett första steg i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="3cda4-141">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="3cda4-142">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="3cda4-142">Next steps</span></span>

- <span data-ttu-id="3cda4-143">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="3cda4-143">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="3cda4-144">Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="3cda4-144">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="3cda4-145">Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="3cda4-145">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
