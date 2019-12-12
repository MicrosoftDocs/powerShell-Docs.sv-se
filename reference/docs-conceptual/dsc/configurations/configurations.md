---
ms.date: 12/12/2018
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: d7749ec88f9cca3e29c6b38d61fb73776af7ceb4
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942330"
---
# <a name="dsc-configurations"></a><span data-ttu-id="d00a5-103">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="d00a5-103">DSC Configurations</span></span>

> <span data-ttu-id="d00a5-104">Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0</span><span class="sxs-lookup"><span data-stu-id="d00a5-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="d00a5-105">DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktion.</span><span class="sxs-lookup"><span data-stu-id="d00a5-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="d00a5-106">Om du vill definiera en konfiguration använder du nyckelords **konfigurationen**för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d00a5-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="d00a5-107">Spara skriptet som en `.ps1`-fil.</span><span class="sxs-lookup"><span data-stu-id="d00a5-107">Save the script as a `.ps1` file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="d00a5-108">Konfigurationssyntax</span><span class="sxs-lookup"><span data-stu-id="d00a5-108">Configuration syntax</span></span>

<span data-ttu-id="d00a5-109">Ett konfigurations skript består av följande delar:</span><span class="sxs-lookup"><span data-stu-id="d00a5-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="d00a5-110">**Konfigurations** blocket.</span><span class="sxs-lookup"><span data-stu-id="d00a5-110">The **Configuration** block.</span></span> <span data-ttu-id="d00a5-111">Detta är det yttersta skript blocket.</span><span class="sxs-lookup"><span data-stu-id="d00a5-111">This is the outermost script block.</span></span> <span data-ttu-id="d00a5-112">Du definierar den genom att använda nyckelordet **konfiguration** och ange ett namn.</span><span class="sxs-lookup"><span data-stu-id="d00a5-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="d00a5-113">I det här fallet är namnet på konfigurationen "MyDscConfiguration".</span><span class="sxs-lookup"><span data-stu-id="d00a5-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="d00a5-114">Ett eller flera **Node** -block.</span><span class="sxs-lookup"><span data-stu-id="d00a5-114">One or more **Node** blocks.</span></span> <span data-ttu-id="d00a5-115">Dessa definierar de noder (datorer eller virtuella datorer) som du konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="d00a5-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="d00a5-116">I ovanstående konfiguration finns ett **Node** -block som är riktat mot en dator med namnet "test-PC1".</span><span class="sxs-lookup"><span data-stu-id="d00a5-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span> <span data-ttu-id="d00a5-117">Node-blocket kan acceptera flera dator namn.</span><span class="sxs-lookup"><span data-stu-id="d00a5-117">The Node block can accept multiple computer names.</span></span>
- <span data-ttu-id="d00a5-118">Ett eller flera resurs block.</span><span class="sxs-lookup"><span data-stu-id="d00a5-118">One or more resource blocks.</span></span> <span data-ttu-id="d00a5-119">Det är här som konfigurationen anger egenskaperna för de resurser som konfigureras.</span><span class="sxs-lookup"><span data-stu-id="d00a5-119">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="d00a5-120">I det här fallet finns det två resurs block som anropar "WindowsFeature"-resursen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-120">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="d00a5-121">I ett **konfigurations** block kan du göra allt som du normalt kan i en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="d00a5-121">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="d00a5-122">I föregående exempel, om du inte vill hårdkoda namnet på mål datorn i konfigurationen, kan du lägga till en parameter för nodnamnet:</span><span class="sxs-lookup"><span data-stu-id="d00a5-122">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

<span data-ttu-id="d00a5-123">I det här exemplet anger du namnet på noden genom att skicka den som parametern **computername** när du kompilerar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-123">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="d00a5-124">Namnet är som standard "localhost".</span><span class="sxs-lookup"><span data-stu-id="d00a5-124">The name defaults to "localhost".</span></span>

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

<span data-ttu-id="d00a5-125">**Node** -blocket kan också acceptera flera dator namn.</span><span class="sxs-lookup"><span data-stu-id="d00a5-125">The **Node** block can also accept multiple computer names.</span></span> <span data-ttu-id="d00a5-126">I exemplet ovan kan du antingen använda `-ComputerName` parameter eller skicka en kommaavgränsad lista med datorer direkt till **Node** -blocket.</span><span class="sxs-lookup"><span data-stu-id="d00a5-126">In the above example, you can either use the `-ComputerName` parameter, or pass a comma-separated list of computers directly to the **Node** block.</span></span>

```powershell
MyDscConfiguration -ComputerName "localhost", "Server01"
```

<span data-ttu-id="d00a5-127">När du anger en lista över datorer i **Node** -blocket, från en konfiguration, måste du använda mat ris notation.</span><span class="sxs-lookup"><span data-stu-id="d00a5-127">When specifying a list of computers to the **Node** block, from within a Configuration, you need to use array-notation.</span></span>

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

## <a name="compiling-the-configuration"></a><span data-ttu-id="d00a5-128">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="d00a5-128">Compiling the configuration</span></span>

<span data-ttu-id="d00a5-129">Innan du kan använda en konfiguration måste du kompilera den till ett MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="d00a5-129">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="d00a5-130">Du gör detta genom att anropa konfigurationen precis som du anropar en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="d00a5-130">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="d00a5-131">Den sista raden i exemplet som bara innehåller namnet på konfigurationen och anropar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-131">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="d00a5-132">För att anropa en konfiguration måste funktionen vara i globalt omfång (precis som med andra PowerShell-funktioner).</span><span class="sxs-lookup"><span data-stu-id="d00a5-132">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="d00a5-133">Du kan göra detta med hjälp av "punkt-källa"-skriptet eller genom att köra konfigurations skriptet genom att använda F5 eller klicka på knappen **Kör skript** i ISE.</span><span class="sxs-lookup"><span data-stu-id="d00a5-133">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="d00a5-134">Kör kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skript fil som innehåller konfigurationen för att köra skriptet med punkt källa.</span><span class="sxs-lookup"><span data-stu-id="d00a5-134">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="d00a5-135">När du anropar konfigurationen:</span><span class="sxs-lookup"><span data-stu-id="d00a5-135">When you call the configuration, it:</span></span>

- <span data-ttu-id="d00a5-136">Matchar alla variabler</span><span class="sxs-lookup"><span data-stu-id="d00a5-136">Resolves all variables</span></span>
- <span data-ttu-id="d00a5-137">Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-137">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="d00a5-138">Skapar en fil med namnet _nodnamn_. MOF i den nya katalogen där _nodnamn_ är namnet på mål-noden i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-138">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="d00a5-139">Om det finns fler än en nod skapas en MOF-fil för varje nod.</span><span class="sxs-lookup"><span data-stu-id="d00a5-139">If there is more than one node, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="d00a5-140">MOF-filen innehåller all konfigurations information för målnoden.</span><span class="sxs-lookup"><span data-stu-id="d00a5-140">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="d00a5-141">Därför är det viktigt att skydda det.</span><span class="sxs-lookup"><span data-stu-id="d00a5-141">Because of this, it's important to keep it secure.</span></span>
> <span data-ttu-id="d00a5-142">Mer information finns i [skydda MOF-filen](../pull-server/secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="d00a5-142">For more information, see [Securing the MOF file](../pull-server/secureMOF.md).</span></span>

<span data-ttu-id="d00a5-143">Att kompilera den första konfigurationen ovan resulterar i följande mappstruktur:</span><span class="sxs-lookup"><span data-stu-id="d00a5-143">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="d00a5-144">Om konfigurationen tar en parameter, som i det andra exemplet, som måste tillhandahållas vid kompilering.</span><span class="sxs-lookup"><span data-stu-id="d00a5-144">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="d00a5-145">Så här ser det ut:</span><span class="sxs-lookup"><span data-stu-id="d00a5-145">Here's how that would look:</span></span>

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

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="d00a5-146">Använda nya resurser i konfigurationen</span><span class="sxs-lookup"><span data-stu-id="d00a5-146">Using new resources in Your configuration</span></span>

<span data-ttu-id="d00a5-147">Om du körde föregående exempel kanske du har märkt att du har fått en varning om att du använde en resurs utan att importera den direkt.</span><span class="sxs-lookup"><span data-stu-id="d00a5-147">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="d00a5-148">Idag levereras DSC med 12 resurser som en del av PSDesiredStateConfiguration-modulen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-148">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>

<span data-ttu-id="d00a5-149">Cmdleten [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)kan användas för att avgöra vilka resurser som är installerade i systemet och som är tillgängliga för användning av LCM.</span><span class="sxs-lookup"><span data-stu-id="d00a5-149">The cmdlet, [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="d00a5-150">När de här modulerna har placerats i `$env:PSModulePath` och identifieras korrekt av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), måste de fortfarande läsas in i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="d00a5-150">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), they still need to be loaded within your configuration.</span></span>

<span data-ttu-id="d00a5-151">**Import-dscresource Keyword Supports** är ett dynamiskt nyckelord som bara kan identifieras i ett **konfigurations** block, men det är inte en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="d00a5-151">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block, it is not a cmdlet.</span></span>
<span data-ttu-id="d00a5-152">**Import-dscresource Keyword Supports** stöder två parametrar:</span><span class="sxs-lookup"><span data-stu-id="d00a5-152">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="d00a5-153">**Modulnamn** är det rekommenderade sättet att använda **import-dscresource Keyword Supports**.</span><span class="sxs-lookup"><span data-stu-id="d00a5-153">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="d00a5-154">Den accepterar namnet på modulen som innehåller de resurser som ska importeras (samt en sträng mat ris med Modulnamn).</span><span class="sxs-lookup"><span data-stu-id="d00a5-154">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="d00a5-155">**Namn** är namnet på den resurs som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="d00a5-155">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="d00a5-156">Detta är inte det egna namnet som returneras som "name" av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), men det klass namn som används för att definiera resurs schema (returnerat som **resourcetype** av [Get-dscresource Keyword Supports](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span><span class="sxs-lookup"><span data-stu-id="d00a5-156">This is not the friendly name returned as "Name" by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](/powershell/module/PSDesiredStateConfiguration/Get-DscResource)).</span></span>

<span data-ttu-id="d00a5-157">Mer information om hur du använder `Import-DSCResource`finns i [using import-dscresource Keyword Supports](import-dscresource.md)</span><span class="sxs-lookup"><span data-stu-id="d00a5-157">For more information on using `Import-DSCResource`, see [Using Import-DSCResource](import-dscresource.md)</span></span>

## <a name="powershell-v4-and-v5-differences"></a><span data-ttu-id="d00a5-158">Skillnader mellan PowerShell v4 och v5</span><span class="sxs-lookup"><span data-stu-id="d00a5-158">PowerShell v4 and v5 differences</span></span>

<span data-ttu-id="d00a5-159">Det finns skillnader i var DSC-resurser måste lagras i PowerShell 4,0.</span><span class="sxs-lookup"><span data-stu-id="d00a5-159">There are differences in where DSC resources need to be stored in PowerShell 4.0.</span></span> <span data-ttu-id="d00a5-160">Mer information finns i [resurs plats](import-dscresource.md#resource-location).</span><span class="sxs-lookup"><span data-stu-id="d00a5-160">For more information, see [Resource location](import-dscresource.md#resource-location).</span></span>

## <a name="see-also"></a><span data-ttu-id="d00a5-161">Se även</span><span class="sxs-lookup"><span data-stu-id="d00a5-161">See Also</span></span>

- [<span data-ttu-id="d00a5-162">Översikt över önskad tillstånds konfiguration i Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="d00a5-162">Windows PowerShell Desired State Configuration Overview</span></span>](../overview/overview.md)
- [<span data-ttu-id="d00a5-163">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="d00a5-163">DSC Resources</span></span>](../resources/resources.md)
- [<span data-ttu-id="d00a5-164">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="d00a5-164">Configuring The Local Configuration Manager</span></span>](../managing-nodes/metaConfig.md)
