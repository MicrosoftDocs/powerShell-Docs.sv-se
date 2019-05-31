---
ms.date: 12/12/2018
keywords: DSC, powershell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: 6af27f442de3080facd65892c713c989d0e388c5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62080188"
---
# <a name="dsc-configurations"></a><span data-ttu-id="c2a3b-103">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="c2a3b-103">DSC Configurations</span></span>

> <span data-ttu-id="c2a3b-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="c2a3b-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="c2a3b-105">DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktionen.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="c2a3b-106">För att definiera en konfiguration, använder du nyckelordet PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {
    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = 'Present'
            Name = 'RSAT'
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}
MyDscConfiguration
```

<span data-ttu-id="c2a3b-107">Spara skriptet som en `.ps1` fil.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="c2a3b-108">Syntax för konfiguration</span><span class="sxs-lookup"><span data-stu-id="c2a3b-108">Configuration syntax</span></span>

<span data-ttu-id="c2a3b-109">Ett konfigurationsskript består av följande delar:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="c2a3b-110">Den **Configuration** block.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-110">The **Configuration** block.</span></span> <span data-ttu-id="c2a3b-111">Det här är det yttersta skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-111">This is the outermost script block.</span></span> <span data-ttu-id="c2a3b-112">Du kan definiera den med hjälp av den **Configuration** nyckelord och att ange ett namn.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="c2a3b-113">I det här fallet är namnet på konfigurationen ”MyDscConfiguration”.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="c2a3b-114">En eller flera **noden** block.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-114">One or more **Node** blocks.</span></span> <span data-ttu-id="c2a3b-115">De definierar noderna (datorer eller virtuella datorer) som du konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="c2a3b-116">I konfigurationen ovan finns en **noden** block som riktar sig mot en dator med namnet ”TEST-PC1”.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="c2a3b-117">Noden blocket kan acceptera flera datornamn.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="c2a3b-118">En eller flera resurs-block.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-118">One or more resource blocks.</span></span> <span data-ttu-id="c2a3b-119">Det här är där konfigurationen anger egenskaperna för de resurser som den konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="c2a3b-120">Det finns i det här fallet två resurs-block, som anropar ”WindowsFeature”-resurs.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="c2a3b-121">Inom en **Configuration** block, du kan göra allt som du normalt skulle kunna i en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="c2a3b-122">Till exempel i exemplet ovan om du inte vill hårt code namnet på måldatorn i konfigurationen, du kan lägga till en parameter för namnet på noden:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="c2a3b-123">I det här exemplet anger du namnet på noden genom att skicka det som den **ComputerName** parameter när du kompilera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="c2a3b-124">Namnet som standard ”localhost”.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-124">The name defaults to "localhost".</span></span>

```powershell
Configuration MyDscConfiguration
{
    param
    (
        [string[]]$ComputerName='localhost'
    )

    Node $ComputerName
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

<span data-ttu-id="c2a3b-125">Den **noden** block kan också acceptera flera datornamn.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="c2a3b-126">I exemplet ovan kan du antingen genom att använda den `-ComputerName` parameter eller pass som en kommaavgränsad lista med datorer direkt till den **noden** block.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="c2a3b-127">När du anger en lista med datorer till den **noden** block, måste du använda matris-notation i en konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

```powershell
Configuration MyDscConfiguration
{
    Node @('localhost', 'Server01')
    {
        WindowsFeature MyFeatureInstance
        {
            Ensure = 'Present'
            Name = 'RSAT'
        }

        WindowsFeature My2ndFeatureInstance
        {
            Ensure = 'Present'
            Name = 'Bitlocker'
        }
    }
}

MyDscConfiguration
```

## <a name="compiling-the-configuration"></a><span data-ttu-id="c2a3b-128">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="c2a3b-128">Compiling the configuration</span></span>

<span data-ttu-id="c2a3b-129">Innan du kan införa en konfiguration, har du kompilera den till en MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="c2a3b-130">Du kan göra detta genom att anropa konfigurationen som du vill anropa en funktion för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="c2a3b-131">Den sista raden i exempel som endast anger namnet på konfigurationen, anropar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a3b-132">För att anropa en konfiguration, måste funktionen vara i global omfattning (precis som med alla andra PowerShell-funktion).</span><span class="sxs-lookup"><span data-stu-id="c2a3b-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="c2a3b-133">Du kan göra det här utförs antingen av ”dot-källa” skriptet, eller genom att köra konfigurationsskriptet genom att välja F5 eller klicka på den **kör skript** knappen i ISE.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="c2a3b-134">Till dot-källa skriptet, kör du kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skriptfil som innehåller din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="c2a3b-135">När du anropar konfigurationen, det:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="c2a3b-136">Matchar alla variabler</span><span class="sxs-lookup"><span data-stu-id="c2a3b-136">Resolves all variables</span></span>
- <span data-ttu-id="c2a3b-137">Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="c2a3b-138">Skapar en fil med namnet _nodnamn_.mof i den nya katalogen där _nodnamn_ är namnet på målnoden av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="c2a3b-139">Om det finns fler än en nod, skapas en MOF-fil för varje nod.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="c2a3b-140">MOF-filen innehåller alla konfigurationsinformation för målnoden.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="c2a3b-141">Därför är det viktigt att skydda den.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-141">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="c2a3b-142">Mer information finns i [skydda MOF-filen](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="c2a3b-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="c2a3b-143">Kompilera den första konfigurationen ovan resulterar i följande mappstrukturen:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-143">Compiling the first configuration above results in the following folder structure:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 localhost.mof
```

<span data-ttu-id="c2a3b-144">Om konfigurationen tar en parameter, som i det andra exemplet som måste anges vid kompilering.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="c2a3b-145">Här är hur som ser ut:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-145">Here's how that would look:</span></span>

```powershell
. .\MyDscConfiguration.ps1
MyDscConfiguration -ComputerName 'MyTestNode'
```

```
    Directory: C:\users\default\Documents\DSC Configurations\MyDscConfiguration
Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----       10/23/2015   4:32 PM           2842 MyTestNode.mof
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="c2a3b-146">Med nya resurser i din konfiguration</span><span class="sxs-lookup"><span data-stu-id="c2a3b-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="c2a3b-147">Om du har kört i föregående exempel kanske du har märkt att du har en varning att du använder en resurs utan att uttryckligen importera den.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="c2a3b-148">Idag, DSC levereras med 12 resurserna som en del av modulen PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="c2a3b-149">Cmdlet: en [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), kan användas för att avgöra vilka resurser som är installerade i systemet och tillgängliga för användning av LCM.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="c2a3b-150">När dessa moduler har placerats i `$env:PSModulePath` och kan identifieras av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), de behöver för att läsas in i din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="c2a3b-151">**Import-DscResource** är en dynamisk nyckelord som kan endast identifieras inom en **Configuration** block, det är inte en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="c2a3b-152">**Import-DscResource** stöder två parametrar:</span><span class="sxs-lookup"><span data-stu-id="c2a3b-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="c2a3b-153">**ModuleName** är det rekommendera sättet att använda **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="c2a3b-154">Den godkänner namnet på den modul som innehåller resurser som ska importeras (samt en strängmatris Modulnamnen).</span><span class="sxs-lookup"><span data-stu-id="c2a3b-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="c2a3b-155">**Namn på** är namnet på resursen att importera.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="c2a3b-156">Detta är inte det egna namnet som ”Name” som returneras av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), men Klassnamnet används när definiera resursschemat (returneras som **ResourceType** av [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="c2a3b-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="c2a3b-157">Mer information om hur du använder `Import-DSCResource`, se [med Import-DSCResource](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="c2a3b-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="c2a3b-158">V4 och v5 skillnader i PowerShell</span><span class="sxs-lookup"><span data-stu-id="c2a3b-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="c2a3b-159">Det finns skillnader i där DSC-resurser måste vara lagrad i PowerShell 4.0.</span><span class="sxs-lookup"><span data-stu-id="c2a3b-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="c2a3b-160">Mer information finns i [resursplats](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="c2a3b-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="c2a3b-161">Se även</span><span class="sxs-lookup"><span data-stu-id="c2a3b-161">See Also</span></span>

- [<span data-ttu-id="c2a3b-162">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="c2a3b-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="c2a3b-163">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="c2a3b-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="c2a3b-164">Konfigurera den lokala Konfigurationshanteraren</span><span class="sxs-lookup"><span data-stu-id="c2a3b-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
