---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: 171068acb51f44e31c81e63f6640222ef71bee38
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093702"
---
# <a name="dsc-configurations"></a><span data-ttu-id="1aaf4-103">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="1aaf4-103">DSC Configurations</span></span>

> <span data-ttu-id="1aaf4-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="1aaf4-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="1aaf4-105">DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktionen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="1aaf4-106">För att definiera en konfiguration, använder du nyckelordet PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

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

<span data-ttu-id="1aaf4-107">Spara skriptet som en .ps1-fil.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="1aaf4-108">Syntax för konfiguration</span><span class="sxs-lookup"><span data-stu-id="1aaf4-108">Configuration syntax</span></span>

<span data-ttu-id="1aaf4-109">Ett konfigurationsskript består av följande delar:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="1aaf4-110">Den **Configuration** block.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-110">The **Configuration** block.</span></span> <span data-ttu-id="1aaf4-111">Det här är det yttersta skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-111">This is the outermost script block.</span></span> <span data-ttu-id="1aaf4-112">Du kan definiera den med hjälp av den **Configuration** nyckelord och att ange ett namn.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="1aaf4-113">I det här fallet är namnet på konfigurationen ”MyDscConfiguration”.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="1aaf4-114">En eller flera **noden** block.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-114">One or more **Node** blocks.</span></span> <span data-ttu-id="1aaf4-115">De definierar noderna (datorer eller virtuella datorer) som du konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="1aaf4-116">I konfigurationen ovan finns en **noden** block som riktar sig mot en dator med namnet ”TEST-PC1”.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="1aaf4-117">En eller flera resurs-block.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-117">One or more resource blocks.</span></span> <span data-ttu-id="1aaf4-118">Det här är där konfigurationen anger egenskaperna för de resurser som den konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="1aaf4-119">Det finns i det här fallet två resurs-block, som anropar ”WindowsFeature”-resurs.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="1aaf4-120">Inom en **Configuration** block, du kan göra allt som du normalt skulle kunna i en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="1aaf4-121">Till exempel i exemplet ovan om du inte vill hårt code namnet på måldatorn i konfigurationen, du kan lägga till en parameter för namnet på noden:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {
    param(
        [string[]]$ComputerName='localhost'
    )
    Node $ComputerName {
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
MyDscConfiguration -ComputerName $ComputerName
```

<span data-ttu-id="1aaf4-122">I det här exemplet anger du namnet på noden genom att skicka det som den **ComputerName** parameter när du kompilera konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="1aaf4-123">Namnet som standard ”localhost”.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="1aaf4-124">Kompilera konfigurationen</span><span class="sxs-lookup"><span data-stu-id="1aaf4-124">Compiling the configuration</span></span>

<span data-ttu-id="1aaf4-125">Innan du kan införa en konfiguration, har du kompilera den till en MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="1aaf4-126">Du kan göra detta genom att anropa konfigurationen som du vill anropa en funktion för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="1aaf4-127">Den sista raden i exempel som endast anger namnet på konfigurationen, anropar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

> [!NOTE]
> <span data-ttu-id="1aaf4-128">För att anropa en konfiguration, måste funktionen vara i global omfattning (precis som med alla andra PowerShell-funktion).</span><span class="sxs-lookup"><span data-stu-id="1aaf4-128">To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
> <span data-ttu-id="1aaf4-129">Du kan göra det här utförs antingen av ”dot-källa” skriptet, eller genom att köra konfigurationsskriptet genom att välja F5 eller klicka på den **kör skript** knappen i ISE.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
> <span data-ttu-id="1aaf4-130">Till dot-källa skriptet, kör du kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skriptfil som innehåller din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="1aaf4-131">När du anropar konfigurationen, det:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="1aaf4-132">Matchar alla variabler</span><span class="sxs-lookup"><span data-stu-id="1aaf4-132">Resolves all variables</span></span>
- <span data-ttu-id="1aaf4-133">Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="1aaf4-134">Skapar en fil med namnet _nodnamn_.mof i den nya katalogen där _nodnamn_ är namnet på målnoden av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
  <span data-ttu-id="1aaf4-135">Om det finns flera noder, skapas en MOF-fil för varje nod.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

> [!NOTE]
> <span data-ttu-id="1aaf4-136">MOF-filen innehåller alla konfigurationsinformation för målnoden.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-136">The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="1aaf4-137">Därför är det viktigt att skydda den.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-137">Because of this, it’s important to keep it secure.</span></span>
> <span data-ttu-id="1aaf4-138">Mer information finns i [skydda MOF-filen](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="1aaf4-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="1aaf4-139">Kompilera den första konfigurationen ovan resulterar i följande mappstrukturen:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="1aaf4-140">Om konfigurationen tar en parameter, som i det andra exemplet som måste anges vid kompilering.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="1aaf4-141">Här är hur som ser ut:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="1aaf4-142">Med hjälp av DependsOn</span><span class="sxs-lookup"><span data-stu-id="1aaf4-142">Using DependsOn</span></span>

<span data-ttu-id="1aaf4-143">Ett användbart DSC-nyckelord är **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="1aaf4-144">Vanligtvis (dock inte nödvändigtvis), DSC gäller resurserna i den ordning som de visas i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="1aaf4-145">Dock **DependsOn** anger vilken resurser är beroende av andra resurser och LCM säkerställer att tillämpas de i rätt ordning, oavsett den ordning i vilken resurs som instanser har definierats.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="1aaf4-146">En konfiguration kan till exempel ange att en instans av den **användaren** resource beror på förekomsten av en **grupp** instans:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = 'Present'
            GroupName = 'TestGroup'
        }

        User UserExample {
            Ensure = 'Present'
            UserName = 'TestUser'
            FullName = 'TestUser'
            DependsOn = '[Group]GroupExample'
        }
    }
}
```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="1aaf4-147">Med nya resurser i din konfiguration</span><span class="sxs-lookup"><span data-stu-id="1aaf4-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="1aaf4-148">Om du har kört i föregående exempel kanske du har märkt att du har en varning att du använder en resurs utan att uttryckligen importera den.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="1aaf4-149">Idag, DSC levereras med 12 resurserna som en del av modulen PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="1aaf4-150">Andra resurser i externa moduler måste placeras i `$env:PSModulePath` för att kunna identifieras av LCM.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="1aaf4-151">En ny cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), kan användas för att avgöra vilka resurser som är installerade i systemet och tillgängliga för användning av LCM.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="1aaf4-152">När dessa moduler har placerats i `$env:PSModulePath` och kan identifieras av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), de behöver för att läsas in i din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="1aaf4-153">**Import-DscResource** är en dynamisk nyckelord som kan endast identifieras inom en **Configuration** block (dvs. det inte är en cmdlet).</span><span class="sxs-lookup"><span data-stu-id="1aaf4-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="1aaf4-154">**Import-DscResource** stöder två parametrar:</span><span class="sxs-lookup"><span data-stu-id="1aaf4-154">**Import-DscResource** supports two parameters:</span></span>

- <span data-ttu-id="1aaf4-155">**ModuleName** är det rekommendera sättet att använda **Import-DscResource**.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="1aaf4-156">Den godkänner namnet på den modul som innehåller resurser som ska importeras (samt en strängmatris Modulnamnen).</span><span class="sxs-lookup"><span data-stu-id="1aaf4-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="1aaf4-157">**Namn på** är namnet på resursen att importera.</span><span class="sxs-lookup"><span data-stu-id="1aaf4-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="1aaf4-158">Detta är inte det egna namnet som ”Name” som returneras av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), men Klassnamnet används när definiera resursschemat (returneras som **ResourceType** av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="1aaf4-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="1aaf4-159">Se även</span><span class="sxs-lookup"><span data-stu-id="1aaf4-159">See Also</span></span>

- [<span data-ttu-id="1aaf4-160">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="1aaf4-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
- [<span data-ttu-id="1aaf4-161">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="1aaf4-161">DSC Resources</span></span>](resources.md)
- [<span data-ttu-id="1aaf4-162">Konfigurera den lokala Konfigurationshanteraren</span><span class="sxs-lookup"><span data-stu-id="1aaf4-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)