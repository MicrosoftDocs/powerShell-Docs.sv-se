---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Snabb start – skapa en webbplats med DSC
ms.openlocfilehash: 08ca25604998ce8c913ef8112b5342f2e0216b6e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75416136"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="13371-103">Snabb start – skapa en webbplats med önskad tillstånds konfiguration (DSC)</span><span class="sxs-lookup"><span data-stu-id="13371-103">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="13371-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="13371-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="13371-105">Den här övningen beskriver hur du skapar och tillämpar en Desired State Configuration (DSC)-konfiguration från början till slut.</span><span class="sxs-lookup"><span data-stu-id="13371-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="13371-106">Exemplet som vi ska använda säkerställer att en server har `Web-Server` (IIS) funktionen aktive rad och att innehållet för en enkel "Hello World"-webbplats finns i `inetpub\wwwroot` katalogen på den servern.</span><span class="sxs-lookup"><span data-stu-id="13371-106">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="13371-107">En översikt över vad DSC är och hur det fungerar finns i [Översikt över önskad tillstånds konfiguration för besluts fattare](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="13371-107">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="13371-108">Krav</span><span class="sxs-lookup"><span data-stu-id="13371-108">Requirements</span></span>

<span data-ttu-id="13371-109">Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="13371-109">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="13371-110">Skriv och placera filen index. htm</span><span class="sxs-lookup"><span data-stu-id="13371-110">Write and place the index.htm file</span></span>

<span data-ttu-id="13371-111">Först skapar vi HTML-filen som vi ska använda som webbplats innehåll.</span><span class="sxs-lookup"><span data-stu-id="13371-111">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="13371-112">Skapa en mapp med namnet `test`i rotmappen.</span><span class="sxs-lookup"><span data-stu-id="13371-112">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="13371-113">Skriv följande text i en text redigerare:</span><span class="sxs-lookup"><span data-stu-id="13371-113">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="13371-114">Spara det som `index.htm` i `test` mappen som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="13371-114">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="13371-115">Skriv konfigurationen</span><span class="sxs-lookup"><span data-stu-id="13371-115">Write the configuration</span></span>

<span data-ttu-id="13371-116">En [DSC-konfiguration](../configurations/configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera mål datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="13371-116">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="13371-117">Skriv följande i PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="13371-117">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="13371-118">Spara filen som `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="13371-118">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="13371-119">Du kan se att det ser ut som en PowerShell-funktion, med tillägg av den nyckelords **konfiguration** som används före namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="13371-119">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="13371-120">**Node** -blocket anger den målnod som ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="13371-120">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="13371-121">I det här fallet `localhost`.</span><span class="sxs-lookup"><span data-stu-id="13371-121">In this case, `localhost`.</span></span>

<span data-ttu-id="13371-122">Konfigurationen anropar två [resurser](../resources/resources.md), **WindowsFeature** och **fil**.</span><span class="sxs-lookup"><span data-stu-id="13371-122">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File**.</span></span>
<span data-ttu-id="13371-123">Resurser gör jobbet för att säkerställa att målnoden är i det tillstånd som definieras av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="13371-123">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="13371-124">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="13371-124">Compile the configuration</span></span>

<span data-ttu-id="13371-125">För att en DSC-konfiguration ska tillämpas på en nod måste den först kompileras till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="13371-125">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="13371-126">Det gör du genom att köra konfigurationen som en funktion.</span><span class="sxs-lookup"><span data-stu-id="13371-126">To do this, you run the configuration like a function.</span></span>
<span data-ttu-id="13371-127">I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommandon för att kompilera konfigurationen till en MOF-fil:</span><span class="sxs-lookup"><span data-stu-id="13371-127">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="13371-128">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="13371-128">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="13371-129">Den första raden gör konfigurations funktionen tillgänglig i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="13371-129">The first line makes the configuration function available in the console.</span></span>
<span data-ttu-id="13371-130">Den andra raden kör-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="13371-130">The second line runs the configuration.</span></span>
<span data-ttu-id="13371-131">Resultatet är att en ny mapp som heter `WebsiteTest` skapas som en undermapp till den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="13371-131">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span>
<span data-ttu-id="13371-132">`WebsiteTest` Mappen innehåller en fil med namnet `localhost.mof`.</span><span class="sxs-lookup"><span data-stu-id="13371-132">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span>
<span data-ttu-id="13371-133">Detta är den fil som sedan kan användas på målnoden.</span><span class="sxs-lookup"><span data-stu-id="13371-133">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="13371-134">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="13371-134">Apply the configuration</span></span>

<span data-ttu-id="13371-135">Nu när du har kompilerat MOF kan du tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="13371-135">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="13371-136">`Start-DscConfiguration` Cmdleten talar om för [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), som är motorn för DSC, för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="13371-136">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="13371-137">LCM fungerar som att anropa DSC-resurserna för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="13371-137">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="13371-138">För att DSC ska kunna köras måste Windows konfigureras för att ta emot PowerShell-fjärrkommandon, även när du `localhost` kör en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="13371-138">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="13371-139">För att enkelt konfigurera din miljö på rätt sätt `Set-WsManQuickConfig -Force` kan du bara köra i en upphöjd PowerShell-Terminal.</span><span class="sxs-lookup"><span data-stu-id="13371-139">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="13371-140">I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="13371-140">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="13371-141">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="13371-141">Test the configuration</span></span>

<span data-ttu-id="13371-142">Du kan anropa cmdleten [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) för att se om konfigurationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="13371-142">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="13371-143">Du kan också testa resultaten direkt, i det här fallet genom att bläddra `http://localhost/` till i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="13371-143">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span>
<span data-ttu-id="13371-144">Du bör se HTML-sidan Hello World som du skapade som första steg i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="13371-144">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="13371-145">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="13371-145">Next steps</span></span>

- <span data-ttu-id="13371-146">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="13371-146">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="13371-147">Se vilka DSC-resurser som är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="13371-147">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="13371-148">Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="13371-148">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
