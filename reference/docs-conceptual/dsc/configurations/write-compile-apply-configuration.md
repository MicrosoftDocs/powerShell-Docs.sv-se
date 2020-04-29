---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, tjänst, installation
title: Skriva, kompilera och tillämpa en konfiguration
ms.openlocfilehash: eb61e518762b9f13e617ecd4711bfef7a86814ec
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "76818166"
---
> <span data-ttu-id="741f7-103">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="741f7-103">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

# <a name="write-compile-and-apply-a-configuration"></a><span data-ttu-id="741f7-104">Skriva, kompilera och tillämpa en konfiguration</span><span class="sxs-lookup"><span data-stu-id="741f7-104">Write, Compile, and Apply a Configuration</span></span>

<span data-ttu-id="741f7-105">Den här övningen beskriver hur du skapar och tillämpar en Desired State Configuration (DSC)-konfiguration från början till slut.</span><span class="sxs-lookup"><span data-stu-id="741f7-105">This exercise walks through creating and applying a Desired State Configuration (DSC) configuration from start to finish.</span></span>
<span data-ttu-id="741f7-106">I följande exempel får du lära dig hur du skriver och använder en mycket enkel konfiguration.</span><span class="sxs-lookup"><span data-stu-id="741f7-106">In the following example, you will learn how to write and apply a very simple Configuration.</span></span> <span data-ttu-id="741f7-107">Konfigurationen ser till att filen "HelloWorld. txt" finns på den lokala datorn.</span><span class="sxs-lookup"><span data-stu-id="741f7-107">The Configuration will ensure a "HelloWorld.txt" file exists on your local machine.</span></span> <span data-ttu-id="741f7-108">Om du tar bort filen kommer DSC att återskapa den nästa gången den uppdateras.</span><span class="sxs-lookup"><span data-stu-id="741f7-108">If you delete the file, DSC will recreate it the next time it updates.</span></span>

<span data-ttu-id="741f7-109">En översikt över vad DSC är och hur det fungerar finns i [Översikt över önskad tillstånds konfiguration för utvecklare](../overview/overview.md).</span><span class="sxs-lookup"><span data-stu-id="741f7-109">For an overview of what DSC is and how it works, see [Desired State Configuration Overview for Developers](../overview/overview.md).</span></span>

## <a name="requirements"></a><span data-ttu-id="741f7-110">Krav</span><span class="sxs-lookup"><span data-stu-id="741f7-110">Requirements</span></span>

<span data-ttu-id="741f7-111">Om du vill köra det här exemplet behöver du en dator som kör PowerShell 4,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="741f7-111">To run this example, you will need a computer running PowerShell 4.0 or later.</span></span>

## <a name="write-the-configuration"></a><span data-ttu-id="741f7-112">Skriv konfigurationen</span><span class="sxs-lookup"><span data-stu-id="741f7-112">Write the configuration</span></span>

<span data-ttu-id="741f7-113">En DSC- [konfiguration](configurations.md) är en särskild PowerShell-funktion som definierar hur du vill konfigurera en eller flera mål datorer (noder).</span><span class="sxs-lookup"><span data-stu-id="741f7-113">A DSC [Configuration](configurations.md) is a special PowerShell function that defines how you want to configure one or more target computers (Nodes).</span></span>

<span data-ttu-id="741f7-114">I PowerShell ISE eller andra PowerShell-redigerare skriver du följande:</span><span class="sxs-lookup"><span data-stu-id="741f7-114">In the PowerShell ISE, or other PowerShell editor, type the following:</span></span>

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

> <span data-ttu-id="741f7-115">! Viktiga i mer avancerade scenarier där flera moduler måste importeras så att du kan arbeta med många DSC-resurser i samma konfiguration, se till att varje modul placeras i en separat rad med hjälp `Import-DscResource`av.</span><span class="sxs-lookup"><span data-stu-id="741f7-115">!Important In more advanced scenarios where multiple modules need to be imported so you can work with many DSC Resources in the same configuration, make sure to put each module in a separate line using `Import-DscResource`.</span></span>
> <span data-ttu-id="741f7-116">Detta är enklare att underhålla i käll kontroll och krävs när du arbetar med DSC i Azure-tillstånds konfiguration.</span><span class="sxs-lookup"><span data-stu-id="741f7-116">This is easier to maintain in source control and required when working with DSC in Azure State Configuration.</span></span>
>
> ```powershell
>  Configuration HelloWorld {
>
>   # Import the module that contains the File resource.
>   Import-DscResource -ModuleName PsDesiredStateConfiguration
>   Import-DscResource -ModuleName xWebAdministration
>
> ```

<span data-ttu-id="741f7-117">Spara filen som "HelloWorld. ps1".</span><span class="sxs-lookup"><span data-stu-id="741f7-117">Save the file as "HelloWorld.ps1".</span></span>

<span data-ttu-id="741f7-118">Att definiera en konfiguration är som att definiera en funktion.</span><span class="sxs-lookup"><span data-stu-id="741f7-118">Defining a Configuration is like defining a Function.</span></span> <span data-ttu-id="741f7-119">**Node** -blocket anger den målnod som ska konfigureras i det här `localhost`fallet.</span><span class="sxs-lookup"><span data-stu-id="741f7-119">The **Node** block specifies the target node to be configured, in this case `localhost`.</span></span>

<span data-ttu-id="741f7-120">Konfigurationen `File` anropar en [resurs](../resources/resources.md), resursen.</span><span class="sxs-lookup"><span data-stu-id="741f7-120">The configuration calls one [resources](../resources/resources.md), the `File` resource.</span></span> <span data-ttu-id="741f7-121">Resurser gör jobbet för att säkerställa att målnoden är i det tillstånd som definieras av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="741f7-121">Resources do the work of ensuring that the target node is in the state defined by the configuration.</span></span>

## <a name="compile-the-configuration"></a><span data-ttu-id="741f7-122">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="741f7-122">Compile the configuration</span></span>

<span data-ttu-id="741f7-123">För att en DSC-konfiguration ska tillämpas på en nod måste den först kompileras till en MOF-fil.</span><span class="sxs-lookup"><span data-stu-id="741f7-123">For a DSC configuration to be applied to a node, it must first be compiled into a MOF file.</span></span>
<span data-ttu-id="741f7-124">Genom att köra konfigurationen som en funktion kompileras en ". MOF"-fil för varje nod som definieras av `Node` blocket.</span><span class="sxs-lookup"><span data-stu-id="741f7-124">Running the configuration, like a function, will compile one ".mof" file for every Node defined by the `Node` block.</span></span>
<span data-ttu-id="741f7-125">För att kunna köra konfigurationen måste du *dot* -skriptet "HelloWorld. ps1" i det aktuella omfånget.</span><span class="sxs-lookup"><span data-stu-id="741f7-125">In order to run the configuration, you need to *dot source* your "HelloWorld.ps1" script into the current scope.</span></span>
<span data-ttu-id="741f7-126">Mer information finns i [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span><span class="sxs-lookup"><span data-stu-id="741f7-126">For more information, see [about_Scripts](/powershell/module/microsoft.powershell.core/about/about_scripts?view=powershell-6#script-scope-and-dot-sourcing).</span></span>

<!-- markdownlint-disable MD038 -->
<span data-ttu-id="741f7-127">*Dot-källa* ditt "HelloWorld. ps1"-skript genom att skriva in sökvägen där du sparade den, `. ` efter (punkt, blank steg).</span><span class="sxs-lookup"><span data-stu-id="741f7-127">*Dot source* your "HelloWorld.ps1" script by typing in the path where you stored it, after the `. ` (dot, space).</span></span> <span data-ttu-id="741f7-128">Sedan kan du köra konfigurationen genom att anropa den som en funktion.</span><span class="sxs-lookup"><span data-stu-id="741f7-128">You may then, run your configuration by calling it like a Function.</span></span>
<!-- markdownlint-enable MD038 -->

```powershell
. C:\Scripts\HelloWorld.ps1
HelloWorld
```

<span data-ttu-id="741f7-129">Detta genererar följande utdata:</span><span class="sxs-lookup"><span data-stu-id="741f7-129">This generates the following output:</span></span>

```output
Directory: C:\Scripts\HelloWorld


Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----        3/13/2017   5:20 PM           2746 localhost.mof
```

## <a name="apply-the-configuration"></a><span data-ttu-id="741f7-130">Tillämpa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="741f7-130">Apply the configuration</span></span>

<span data-ttu-id="741f7-131">Nu när du har kompilerat MOF kan du tillämpa konfigurationen på målnoden (i det här fallet den lokala datorn) genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .</span><span class="sxs-lookup"><span data-stu-id="741f7-131">Now that you have the compiled MOF, you can apply the configuration to the target node (in this case, the local computer) by calling the [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.</span></span>

<span data-ttu-id="741f7-132">`Start-DscConfiguration` Cmdleten talar om för [lokala Configuration Manager (LCM)](../managing-nodes/metaConfig.md), motorn för DSC, för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="741f7-132">The `Start-DscConfiguration` cmdlet tells the [Local Configuration Manager (LCM)](../managing-nodes/metaConfig.md), the engine of DSC, to apply the configuration.</span></span>
<span data-ttu-id="741f7-133">LCM fungerar som att anropa DSC-resurserna för att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="741f7-133">The LCM does the work of calling the DSC resources to apply the configuration.</span></span>

<span data-ttu-id="741f7-134">Använd koden nedan för att köra `Start-DSCConfiguration` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="741f7-134">Use the code below to execute the `Start-DSCConfiguration` cmdlet.</span></span> <span data-ttu-id="741f7-135">Ange sökvägen till katalogen där din "localhost. MOF" lagras till- `-Path` parametern.</span><span class="sxs-lookup"><span data-stu-id="741f7-135">Specify the directory path where your "localhost.mof" is stored to the `-Path` parameter.</span></span> <span data-ttu-id="741f7-136">`Start-DSCConfiguration` Cmdleten söker igenom katalogen som anges för alla "\<ComputerName\>. MOF"-filer.</span><span class="sxs-lookup"><span data-stu-id="741f7-136">The `Start-DSCConfiguration` cmdlet looks through the directory specified for any "\<computername\>.mof" files.</span></span> <span data-ttu-id="741f7-137">`Start-DSCConfiguration` Cmdleten försöker tillämpa varje ". MOF"-fil som hittas av det ComputerName som anges av fil namnet ("localhost", "Server01", "DC-02" osv.).</span><span class="sxs-lookup"><span data-stu-id="741f7-137">The `Start-DSCConfiguration` cmdlet attempts to apply each ".mof" file it finds to the computername specified by the filename ("localhost", "server01", "dc-02", etc.).</span></span>

> [!NOTE]
> <span data-ttu-id="741f7-138">Om `-Wait` parametern inte anges `Start-DSCConfiguration` skapas ett bakgrunds jobb för att utföra åtgärden.</span><span class="sxs-lookup"><span data-stu-id="741f7-138">If the `-Wait` parameter is not specified, `Start-DSCConfiguration` creates a background job to perform the operation.</span></span> <span data-ttu-id="741f7-139">Genom att `-Verbose` ange parametern kan du se **utförlig** utdata för åtgärden.</span><span class="sxs-lookup"><span data-stu-id="741f7-139">Specifying the `-Verbose` parameter allows you to watch the **Verbose** output of the operation.</span></span> <span data-ttu-id="741f7-140">`-Wait`och `-Verbose` är båda valfria parametrar.</span><span class="sxs-lookup"><span data-stu-id="741f7-140">`-Wait`, and `-Verbose` are both optional parameters.</span></span>

```powershell
Start-DscConfiguration -Path C:\Scripts\HelloWorld -Verbose -Wait
```

## <a name="test-the-configuration"></a><span data-ttu-id="741f7-141">Testa konfigurationen</span><span class="sxs-lookup"><span data-stu-id="741f7-141">Test the configuration</span></span>

<span data-ttu-id="741f7-142">När `Start-DSCConfiguration` cmdleten har slutförts bör du se filen "HelloWorld. txt" på den plats som du har angett.</span><span class="sxs-lookup"><span data-stu-id="741f7-142">Once the `Start-DSCConfiguration` cmdlet is complete, you should see a "HelloWorld.txt" file in the location you specified.</span></span> <span data-ttu-id="741f7-143">Du kan kontrol lera innehållet med cmdleten [Get-Content](/powershell/module/microsoft.powershell.management/get-content) .</span><span class="sxs-lookup"><span data-stu-id="741f7-143">You can verify the contents with the [Get-Content](/powershell/module/microsoft.powershell.management/get-content) cmdlet.</span></span>

<span data-ttu-id="741f7-144">Du kan också *testa* den aktuella statusen med hjälp av [test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span><span class="sxs-lookup"><span data-stu-id="741f7-144">You can also *test* the current status using [Test-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/Test-DSCConfiguration).</span></span>

<span data-ttu-id="741f7-145">Utdata ska vara "true" om noden för närvarande är kompatibel med den tillämpade konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="741f7-145">The output should be "True" if the Node is currently compliant with the applied Configuration.</span></span>

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

## <a name="re-applying-the-configuration"></a><span data-ttu-id="741f7-146">Tillämpar konfigurationen igen</span><span class="sxs-lookup"><span data-stu-id="741f7-146">Re-applying the configuration</span></span>

<span data-ttu-id="741f7-147">Om du vill se hur konfigurationen tillämpas igen kan du ta bort text filen som skapats av din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="741f7-147">To see your configuration get applied again, you can remove the text file created by your Configuration.</span></span> <span data-ttu-id="741f7-148">Använd `Start-DSCConfiguration` cmdleten med `-UseExisting` parametern.</span><span class="sxs-lookup"><span data-stu-id="741f7-148">The use the `Start-DSCConfiguration` cmdlet with the `-UseExisting` parameter.</span></span> <span data-ttu-id="741f7-149">`-UseExisting` Parametern instruerar `Start-DSCConfiguration` att tillämpa den aktuella. MOF-filen igen som representerar den senast tillämpade konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="741f7-149">The `-UseExisting` parameter instructs `Start-DSCConfiguration` to re-apply the "current.mof" file, which represents the most recently successfully applied configuration.</span></span>

```powershell
Remove-Item -Path C:\Temp\HelloWorld.txt
```

## <a name="next-steps"></a><span data-ttu-id="741f7-150">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="741f7-150">Next steps</span></span>

- <span data-ttu-id="741f7-151">Lär dig mer om DSC-konfigurationer på [DSC-konfigurationer](configurations.md).</span><span class="sxs-lookup"><span data-stu-id="741f7-151">Find out more about DSC configurations at [DSC configurations](configurations.md).</span></span>
- <span data-ttu-id="741f7-152">Se vilka DSC-resurser som är tillgängliga och hur du skapar anpassade DSC-resurser på [DSC-resurser](../resources/resources.md).</span><span class="sxs-lookup"><span data-stu-id="741f7-152">See what DSC resources are available, and how to create custom DSC resources at [DSC resources](../resources/resources.md).</span></span>
- <span data-ttu-id="741f7-153">Hitta DSC-konfigurationer och-resurser i [PowerShell-galleriet](https://www.powershellgallery.com/).</span><span class="sxs-lookup"><span data-stu-id="741f7-153">Find DSC configurations and resources in the [PowerShell Gallery](https://www.powershellgallery.com/).</span></span>
