---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Snabb start – skapa en webbplats med DSC
description: Den här snabb starten visar hur du skapar en ny webbplats med hjälp av en DSC-konfiguration.
ms.openlocfilehash: ece1ae964bce00a4102de4b13d99d6ee1259117a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650891"
---
# <a name="quickstart---create-a-website-with-desired-state-configuration-dsc"></a><span data-ttu-id="11b1c-104">Snabb start – skapa en webbplats med önskad tillstånds konfiguration (DSC)</span><span class="sxs-lookup"><span data-stu-id="11b1c-104">Quickstart - Create a website with Desired State Configuration (DSC)</span></span>

> <span data-ttu-id="11b1c-105">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="11b1c-105">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="11b1c-106">Den här övningen beskriver hur du skapar och tillämpar en Desired State Configuration (DSC)-konfiguration från början till slut.</span><span class="sxs-lookup"><span data-stu-id="11b1c-106">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span> <span data-ttu-id="11b1c-107">Exemplet som vi ska använda säkerställer att en server har `Web-Server` (IIS) funktionen aktive rad och att innehållet för en enkel "Hello World"-webbplats finns i `inetpub\wwwroot` katalogen på den servern.</span><span class="sxs-lookup"><span data-stu-id="11b1c-107">The example we'll use ensures that a server has the `Web-Server` (IIS) feature enabled, and that the content for a simple "Hello World" website is present in the `inetpub\wwwroot` directory of that server.</span></span>

<span data-ttu-id="11b1c-108">En översikt över vad DSC är och hur det fungerar finns i [Översikt över önskad tillstånds konfiguration för besluts fattare](../overview/decisionMaker.md).</span><span class="sxs-lookup"><span data-stu-id="11b1c-108">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Decision Makers](../overview/decisionMaker.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="11b1c-109">Krav</span><span class="sxs-lookup"><span data-stu-id="11b1c-109">Requirements</span></span>

<span data-ttu-id="11b1c-110">Om du vill köra det här exemplet behöver du en dator som kör Windows Server 2012 eller senare och PowerShell 4,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="11b1c-110">To run this example, you will need a computer running Windows Server 2012 or later and PowerShell 4.0 or later.</span></span>

## <a name="write-and-place-the-indexhtm-file"></a><span data-ttu-id="11b1c-111">Skriv och placera index.htm-filen</span><span class="sxs-lookup"><span data-stu-id="11b1c-111">Write and place the index.htm file</span></span>

<span data-ttu-id="11b1c-112">Först skapar vi HTML-filen som vi ska använda som webbplats innehåll.</span><span class="sxs-lookup"><span data-stu-id="11b1c-112">First, we'll create the HTML file that we will use as the website content.</span></span>

<span data-ttu-id="11b1c-113">Skapa en mapp med namnet i rotmappen `test` .</span><span class="sxs-lookup"><span data-stu-id="11b1c-113">In your root folder, create a folder named `test`.</span></span>

<span data-ttu-id="11b1c-114">Skriv följande text i en text redigerare:</span><span class="sxs-lookup"><span data-stu-id="11b1c-114">In a text editor, type the following text:</span></span>

```html
<head></head>
<body>
<p>Hello World!</p>
</body>
```

<span data-ttu-id="11b1c-115">Spara det som `index.htm` i `test` mappen som du skapade tidigare.</span><span class="sxs-lookup"><span data-stu-id="11b1c-115">Save this as `index.htm` in the `test` folder you created earlier.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="11b1c-116">Skriv konfigurationen</span><span class="sxs-lookup"><span data-stu-id="11b1c-116">Write the configuration</span></span>

<span data-ttu-id="11b1c-117">En [DSC-konfiguration](../configurations/configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera mål datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="11b1c-117">A [DSC configuration](../configurations/configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (nodes).</span></span>

<span data-ttu-id="11b1c-118">Skriv följande i PowerShell ISE:</span><span class="sxs-lookup"><span data-stu-id="11b1c-118">In the PowerShell ISE, type the following:</span></span>

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

<span data-ttu-id="11b1c-119">Spara filen som `WebsiteTest.ps1`.</span><span class="sxs-lookup"><span data-stu-id="11b1c-119">Save the file as `WebsiteTest.ps1`.</span></span>

<span data-ttu-id="11b1c-120">Du kan se att det ser ut som en PowerShell-funktion, med tillägg av den nyckelords **konfiguration** som används före namnet på funktionen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-120">You can see that it looks like a PowerShell function, with the addition of the keyword **Configuration** used before the name of the function.</span></span>

<span data-ttu-id="11b1c-121">**Node** -blocket anger den målnod som ska konfigureras.</span><span class="sxs-lookup"><span data-stu-id="11b1c-121">The **Node** block specifies the target node to be configured.</span></span> <span data-ttu-id="11b1c-122">I det här fallet `localhost` .</span><span class="sxs-lookup"><span data-stu-id="11b1c-122">In this case, `localhost`.</span></span>

<span data-ttu-id="11b1c-123">Konfigurationen anropar två [resurser](../resources/resources.md), **WindowsFeature** och **fil** .</span><span class="sxs-lookup"><span data-stu-id="11b1c-123">The configuration calls two [resources](../resources/resources.md), **WindowsFeature** and **File** .</span></span>
<span data-ttu-id="11b1c-124">Resurser gör jobbet för att säkerställa att målnoden är i det tillstånd som definieras av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-124">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="11b1c-125">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="11b1c-125">Compile the configuration</span></span>

<span data-ttu-id="11b1c-126">För att en DSC-konfiguration ska tillämpas på en nod måste den först kompileras till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="11b1c-126">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span> <span data-ttu-id="11b1c-127">Det gör du genom att köra konfigurationen som en funktion.</span><span class="sxs-lookup"><span data-stu-id="11b1c-127">To do this, you run the configuration like a function.</span></span> <span data-ttu-id="11b1c-128">I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommandon för att kompilera konfigurationen till en MOF-fil:</span><span class="sxs-lookup"><span data-stu-id="11b1c-128">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following commands to compile the configuration into a MOF file:</span></span>

```powershell
. .\WebsiteTest.ps1
WebsiteTest
```

<span data-ttu-id="11b1c-129">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="11b1c-129">This generates the following output:</span></span>

```
Directory: C:\ConfigurationTest\WebsiteTest


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

<span data-ttu-id="11b1c-130">Den första raden gör konfigurations funktionen tillgänglig i-konsolen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-130">The first line makes the configuration function available in the console.</span></span> <span data-ttu-id="11b1c-131">Den andra raden kör-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-131">The second line runs the configuration.</span></span> <span data-ttu-id="11b1c-132">Resultatet är att en ny mapp som heter `WebsiteTest` skapas som en undermapp till den aktuella mappen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-132">The result is that a new folder, named `WebsiteTest` is created as a subfolder of the current folder.</span></span> <span data-ttu-id="11b1c-133">`WebsiteTest`Mappen innehåller en fil med namnet `localhost.mof` .</span><span class="sxs-lookup"><span data-stu-id="11b1c-133">The `WebsiteTest` folder contains a file named `localhost.mof`.</span></span> <span data-ttu-id="11b1c-134">Detta är den fil som sedan kan användas på målnoden.</span><span class="sxs-lookup"><span data-stu-id="11b1c-134">This is the file that can then be applied to the target node.</span></span>

## <a name="apply-the-configuration"></a><span data-ttu-id="11b1c-135">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="11b1c-135">Apply the configuration</span></span>

<span data-ttu-id="11b1c-136">Nu när du har kompilerat MOF kan du tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="11b1c-136">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="11b1c-137">`Start-DscConfiguration`Cmdleten talar om för [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), som är motorn för DSC, för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-137">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), which is the engine of DSC, to apply the configuration.</span></span> <span data-ttu-id="11b1c-138">LCM fungerar som att anropa DSC-resurserna för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="11b1c-138">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="11b1c-139">För att DSC ska kunna köras måste Windows konfigureras för att ta emot PowerShell-fjärrkommandon, även när du kör en `localhost` konfiguration.</span><span class="sxs-lookup"><span data-stu-id="11b1c-139">To allow DSC to run, Windows needs to be configured to receive PowerShell remote commands, even when you're running a `localhost` configuration.</span></span> <span data-ttu-id="11b1c-140">För att enkelt konfigurera din miljö på rätt sätt kan du bara köra `Set-WsManQuickConfig -Force` i en upphöjd PowerShell-Terminal.</span><span class="sxs-lookup"><span data-stu-id="11b1c-140">To easily configure your environment correctly, just run `Set-WsManQuickConfig -Force` in an elevated PowerShell Terminal.</span></span>

<span data-ttu-id="11b1c-141">I en PowerShell-konsol navigerar du till samma mapp där du sparade konfigurationen och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="11b1c-141">In a PowerShell console, navigate to the same folder where you saved your configuration and run the following command:</span></span>

```powershell
Start-DscConfiguration .\WebsiteTest
```

## <a name="test-the-configuration"></a><span data-ttu-id="11b1c-142">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="11b1c-142">Test the configuration</span></span>

<span data-ttu-id="11b1c-143">Du kan anropa cmdleten [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) för att se om konfigurationen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="11b1c-143">You can call the [Get-DscConfigurationStatus](/powershell/module/psdesiredstateconfiguration/get-dscconfigurationstatus) cmdlet to see whether the configuration succeeded.</span></span>

<span data-ttu-id="11b1c-144">Du kan också testa resultaten direkt, i det här fallet genom att bläddra till `http://localhost/` i en webbläsare.</span><span class="sxs-lookup"><span data-stu-id="11b1c-144">You can also test the results directly, in this case by browsing to `http://localhost/` in a web browser.</span></span> <span data-ttu-id="11b1c-145">Du bör se HTML-sidan Hello World som du skapade som första steg i det här exemplet.</span><span class="sxs-lookup"><span data-stu-id="11b1c-145">You should see the "Hello World" HTML page you created as the first step in this example.</span></span>

## <a name="next-steps"></a><span data-ttu-id="11b1c-146">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="11b1c-146">Next steps</span></span>

- <span data-ttu-id="11b1c-147">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](../configurations/configurations.md).</span><span class="sxs-lookup"><span data-stu-id="11b1c-147">Find out more about DSC configurations at [DSC configurations](../configurations/configurations.md).</span></span>
- <span data-ttu-id="11b1c-148">Se vilka DSC-resurser som är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="11b1c-148">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="11b1c-149">Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="11b1c-149">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
