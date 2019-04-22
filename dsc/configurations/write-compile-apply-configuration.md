---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, tjänst, inställning
title: Skriva, kompilera och tillämpa en konfiguration
ms.openlocfilehash: 947308efa165543571801c88a922daf44fa88be0
ms.sourcegitcommit: 17ce42f97e13e8b3286779dc3f583474b0357023
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/18/2019
ms.locfileid: "59506826"
---
> <span data-ttu-id="4e9ce-103">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="4e9ce-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="4e9ce-104">Skriva, kompilera och tillämpa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="4e9ce-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="4e9ce-105">Den här övningen visar hur du skapar och tillämpar en konfiguration med Desired State Configuration (DSC) från början till slut.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="4e9ce-106">I följande exempel lära du dig att skriva och tillämpa en väldigt enkel konfiguration.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="4e9ce-107">Konfigurationen garanterar en ”HelloWorld.txt”-fil finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="4e9ce-108">Om du tar bort filen DSC kommer att återskapa den nästa gång den uppdaterar.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="4e9ce-109">En översikt över vad DSC är och hur det fungerar, se [Desired State Configuration-översikt för utvecklare](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="4e9ce-110">Krav</span><span class="sxs-lookup"><span data-stu-id="4e9ce-110">Requirements</span></span>

<span data-ttu-id="4e9ce-111">Om du vill köra det här exemplet behöver du en dator med PowerShell 4.0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="4e9ce-112">Skriva konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4e9ce-112">Write the configuration</span></span>

<span data-ttu-id="4e9ce-113">En DSC [Configuration](configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="4e9ce-114">I PowerShell ISE eller andra PowerShell-redigerare, skriver du följande:</span><span class="sxs-lookup"><span data-stu-id="4e9ce-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

```powershell
Configuration HelloWorld {

    # Import the module that contains the File resource.
    Import-DscResource -ModuleName PsDesiredStateConfiguration

    # The Node statement specifies which targets to compile MOF files for, when this configuration is executed.
    Node 'localhost' {

        # The File resource can ensure the state of files, or copy them from a source to a destination with persistent updates.
        File HelloWorld {
            DestinationPath = "C:\Temp\HelloWorld.txt"
            Ensure = "Present"
            Contents   = "Hello World from DSC!"
        }
    }
}
```

<span data-ttu-id="4e9ce-115">Save the file as "HelloWorld.ps1".</span><span class="sxs-lookup"><span data-stu-id="4e9ce-115">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="4e9ce-116">Definiera en konfiguration är som definierar en funktion.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-116">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="4e9ce-117">Den **nod** block anger målnoden som ska konfigureras i det här fallet `localhost`.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-117">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="4e9ce-118">Konfigurationen anropar en [resurser](../resources/resources.md), `File` resurs.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-118">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="4e9ce-119">Resurser som utför arbete för att säkerställa en som Målnoden är i tillståndet som definieras av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-119">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="4e9ce-120">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4e9ce-120">Compile the configuration</span></span>

<span data-ttu-id="4e9ce-121">För en DSC-konfiguration som ska tillämpas på en nod måste du först kompilera den till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-121">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="4e9ce-122">Kör konfiguration, som en funktion ska kompilera en ”.mof”-fil för varje nod som definieras av den `Node` block.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-122">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="4e9ce-123">För att köra konfigurationen, måste du *dot-källa* ”HelloWorld.ps1” skriptet i den aktuella omfattningen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-123">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="4e9ce-124">Mer information finns i [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-124">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="4e9ce-125">*Dot-källa* ”HelloWorld.ps1” skriptet genom att skriva in sökvägen där du sparade den, efter den `. ` (punkt, utrymme).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-125">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="4e9ce-126">Du kan sedan köra konfigurationen genom att anropa den som en funktion.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-126">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="4e9ce-127">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="4e9ce-127">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="4e9ce-128">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4e9ce-128">Apply the configuration</span></span>

<span data-ttu-id="4e9ce-129">Nu när du har den kompilerade MOF, du kan tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-129">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="4e9ce-130">Den `Start-DscConfiguration` cmdlet visar den [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), motorn i DSC att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-130">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="4e9ce-131">LCM fungerar för att anropa DSC-resurser för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-131">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="4e9ce-132">Använda koden nedan för att köra den `Start-DSCConfiguration` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-132">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="4e9ce-133">Ange sökvägen till katalogen där din ”localhost.mof” lagras till det `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-133">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="4e9ce-134">Den `Start-DSCConfiguration` cmdlet genomsöks den katalog som anges för alla ”\<computername\>.mof” filer.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-134">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="4e9ce-135">Den `Start-DSCConfiguration` cmdlet försöker tillämpa varje ”.mof”-fil som hittas på datornamnet som anges av filnamnet (”localhost”, ”server01”, ”dc-02” osv.).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-135">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="4e9ce-136">Om den `-Wait` parametern inte anges `Start-DSCConfiguration` skapar ett bakgrundsjobb för att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-136">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="4e9ce-137">Anger den `-Verbose` parametern kan du titta på den **utförlig** resultatet av åtgärden.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-137">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="4e9ce-138">`-Wait`, och `-Verbose` är båda valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-138">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="4e9ce-139">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4e9ce-139">Test the configuration</span></span>

<span data-ttu-id="4e9ce-140">När den `Start-DSCConfiguration` cmdleten har slutförts, visas en ”HelloWorld.txt”-fil på den plats du angav.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-140">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="4e9ce-141">Du kan kontrollera innehållet med den [Get-innehåll](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-141">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="4e9ce-142">Du kan också *testa* aktuell status med [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-142">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="4e9ce-143">Utdata ska vara ”True” om noden är för närvarande är kompatibel med tillämpade konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-143">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

```powershell
Test-DSCConfiguration
```

```output
True
```

```powershell
Get-Content -Path C:\Temp\HelloWorld.txt
```

```output
Hello World from DSC!
```

## <a name="re-applying-the-configuration"></a><span data-ttu-id="4e9ce-144">Återanvänder konfigurationen</span><span class="sxs-lookup"><span data-stu-id="4e9ce-144">Re-applying the configuration</span></span>

<span data-ttu-id="4e9ce-145">Du kan ta bort textfilen som skapats av din konfiguration om du vill se din konfiguration tillämpas igen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-145">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="4e9ce-146">Användning de `Start-DSCConfiguration` cmdlet med den `-UseExisting` parametern.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-146">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="4e9ce-147">Den `-UseExisting` parametern instruerar `Start-DSCConfiguration` för att tillämpa igen filen ”current.mof”, som representerar de nyligen har tillämpat konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4e9ce-147">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="4e9ce-148">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="4e9ce-148">Next steps</span></span>

- <span data-ttu-id="4e9ce-149">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-149">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="4e9ce-150">Se vilka DSC-resurser är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-150">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="4e9ce-151">Hitta DSC-konfigurationer och resurser i den [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="4e9ce-151">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
