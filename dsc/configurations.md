---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-konfigurationer
ms.openlocfilehash: ffeb953048c0a65352618d2ab141ee10ead4c663
ms.sourcegitcommit: a9aa5e8d0fab0cbb3e4e6cff0e3ca8c0339ab4e6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/27/2018
---
# <a name="dsc-configurations"></a><span data-ttu-id="0cdd8-103">DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="0cdd8-103">DSC Configurations</span></span>

><span data-ttu-id="0cdd8-104">Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0</span><span class="sxs-lookup"><span data-stu-id="0cdd8-104">Applies To: Windows PowerShell 4.0, Windows PowerShell 5.0</span></span>

<span data-ttu-id="0cdd8-105">DSC-konfigurationer är PowerShell-skript som definierar en särskild typ av funktionen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-105">DSC configurations are PowerShell scripts that define a special type of function.</span></span>
<span data-ttu-id="0cdd8-106">Om du vill definiera en konfiguration, använder du nyckelordet PowerShell **Configuration**.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-106">To define a configuration, you use the PowerShell keyword **Configuration**.</span></span>

```powershell
Configuration MyDscConfiguration {

    Node "TEST-PC1" {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration

```

<span data-ttu-id="0cdd8-107">Spara skriptet som en .ps1-fil.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-107">Save the script as a .ps1 file.</span></span>

## <a name="configuration-syntax"></a><span data-ttu-id="0cdd8-108">Syntax för konfiguration</span><span class="sxs-lookup"><span data-stu-id="0cdd8-108">Configuration syntax</span></span>

<span data-ttu-id="0cdd8-109">Ett konfigurationsskript består av följande delar:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-109">A configuration script consists of the following parts:</span></span>

- <span data-ttu-id="0cdd8-110">Den **Configuration** block.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-110">The **Configuration** block.</span></span> <span data-ttu-id="0cdd8-111">Det här är det yttersta skriptblocket.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-111">This is the outermost script block.</span></span> <span data-ttu-id="0cdd8-112">Du kan definiera den med hjälp av den **Configuration** nyckelord och ange ett namn.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-112">You define it by using the **Configuration** keyword and providing a name.</span></span> <span data-ttu-id="0cdd8-113">I det här fallet är namnet på konfigurationen ”MyDscConfiguration”.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-113">In this case, the name of the configuration is "MyDscConfiguration".</span></span>
- <span data-ttu-id="0cdd8-114">En eller flera **nod** block.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-114">One or more **Node** blocks.</span></span> <span data-ttu-id="0cdd8-115">De definierar noderna (datorer eller virtuella datorer) som du konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-115">These define the nodes (computers or VMs) that you are configuring.</span></span> <span data-ttu-id="0cdd8-116">I konfigurationen ovan finns en **nod** block som riktar sig till en dator med namnet ”TEST-PC1”.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-116">In the above configuration, there is one **Node** block that targets a computer named "TEST-PC1".</span></span>
- <span data-ttu-id="0cdd8-117">En eller flera resurs-block.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-117">One or more resource blocks.</span></span> <span data-ttu-id="0cdd8-118">Detta är där konfigurationen anger egenskaperna för de resurser som den konfigurerar.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-118">This is where the configuration sets the properties for the resources that it is configuring.</span></span> <span data-ttu-id="0cdd8-119">I det här fallet finns två resurs-block, där varje anropa resursen ”WindowsFeature”.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-119">In this case, there are two resource blocks, each of which call the "WindowsFeature" resource.</span></span>

<span data-ttu-id="0cdd8-120">Inom en **Configuration** block, kan du göra allt som du normalt kan i ett PowerShell-funktionen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-120">Within a **Configuration** block, you can do anything that you normally could in a PowerShell function.</span></span> <span data-ttu-id="0cdd8-121">Till exempel i föregående exempel, om du inte vill hård code namnet på måldatorn i konfigurationen, du kan lägga till en parameter för nodnamnet på:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-121">For example, in the previous example, if you didn't want to hard code the name of the target computer in the configuration, you could add a parameter for the node name:</span></span>

```powershell
Configuration MyDscConfiguration {

    param(
        [string[]]$ComputerName="localhost"
    )
    Node $ComputerName {
        WindowsFeature MyFeatureInstance {
            Ensure = "Present"
            Name =  "RSAT"
        }
        WindowsFeature My2ndFeatureInstance {
            Ensure = "Present"
            Name = "Bitlocker"
        }
    }
}
MyDscConfiguration -ComputerName $ComputerName

```

<span data-ttu-id="0cdd8-122">I det här exemplet, ange namnet på noden genom att skicka den som den **ComputerName** parameter när du kompilerar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-122">In this example, you specify the name of the node by passing it as the **ComputerName** parameter when you compile the configuration.</span></span> <span data-ttu-id="0cdd8-123">Namnet som standard ”localhost”.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-123">The name defaults to "localhost".</span></span>

## <a name="compiling-the-configuration"></a><span data-ttu-id="0cdd8-124">Kompilera konfiguration</span><span class="sxs-lookup"><span data-stu-id="0cdd8-124">Compiling the configuration</span></span>

<span data-ttu-id="0cdd8-125">Innan du kan tillämpar en konfiguration som du behöver kompileras till en MOF-dokument.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-125">Before you can enact a configuration, you have to compile it into a MOF document.</span></span>
<span data-ttu-id="0cdd8-126">Det gör du genom att anropa konfigurationen som du vill anropa en PowerShell-funktion.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-126">You do this by calling the configuration like you would call a PowerShell function.</span></span>
<span data-ttu-id="0cdd8-127">Den sista raden i exemplet som innehåller namnet på konfigurationen, anropar konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-127">The last line of the example containing only the name of the configuration, calls the configuration.</span></span>

><span data-ttu-id="0cdd8-128">**Obs:** för att anropa en konfiguration, funktionen måste vara i globalt scope (precis som med andra PowerShell funktioner).</span><span class="sxs-lookup"><span data-stu-id="0cdd8-128">**Note:** To call a configuration, the function must be in global scope (as with any other PowerShell function).</span></span>
><span data-ttu-id="0cdd8-129">Du kan göra detta hända antingen av ”dot-källa” skriptet, eller genom att köra skriptet konfiguration genom att använda F5 eller klicka på den **kör skriptet** knappen i ISE.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-129">You can make this happen either by "dot-sourcing" the script, or by running the configuration script by using F5 or clicking on the **Run Script** button in the ISE.</span></span>
><span data-ttu-id="0cdd8-130">Till dot-källa skriptet, kör du kommandot `. .\myConfig.ps1` där `myConfig.ps1` är namnet på den skriptfil som innehåller din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-130">To dot-source the script, run the command `. .\myConfig.ps1` where `myConfig.ps1` is the name of the script file that contains your configuration.</span></span>

<span data-ttu-id="0cdd8-131">När du anropar konfigurationen, är det:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-131">When you call the configuration, it:</span></span>

- <span data-ttu-id="0cdd8-132">Matchar alla variabler</span><span class="sxs-lookup"><span data-stu-id="0cdd8-132">Resolves all variables</span></span>
- <span data-ttu-id="0cdd8-133">Skapar en mapp i den aktuella katalogen med samma namn som konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-133">Creates a folder in the current directory with the same name as the configuration.</span></span>
- <span data-ttu-id="0cdd8-134">Skapar en fil med namnet _NodeName_MOF i den nya katalogen där _nodnamn_ är namnet på målnoden av konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-134">Creates a file named _NodeName_.mof in the new directory, where _NodeName_ is the name of the target node of the configuration.</span></span>
    <span data-ttu-id="0cdd8-135">Om det finns flera noder, skapas en MOF-fil för varje nod.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-135">If there are more than one nodes, a MOF file will be created for each node.</span></span>

><span data-ttu-id="0cdd8-136">**Obs**: I MOF-filen innehåller all konfigurationsinformation för målnoden.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-136">**Note**: The MOF file contains all of the configuration information for the target node.</span></span> <span data-ttu-id="0cdd8-137">Därför är det viktigt att skydda den.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-137">Because of this, it’s important to keep it secure.</span></span>
><span data-ttu-id="0cdd8-138">Mer information finns i [skydda MOF-filen](secureMOF.md).</span><span class="sxs-lookup"><span data-stu-id="0cdd8-138">For more information, see [Securing the MOF file](secureMOF.md).</span></span>

<span data-ttu-id="0cdd8-139">Kompilera den första konfigurationen ovan resulterar i följande mappstrukturen:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-139">Compiling the first configuration above results in the following folder structure:</span></span>

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

<span data-ttu-id="0cdd8-140">Om konfigurationen tar en parameter i det andra exemplet som anges vid kompileringen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-140">If the configuration takes a parameter, as in the second example, that has to be provided at compile time.</span></span> <span data-ttu-id="0cdd8-141">Här är hur som ser ut:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-141">Here's how that would look:</span></span>

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

## <a name="using-dependson"></a><span data-ttu-id="0cdd8-142">Använder DependsOn</span><span class="sxs-lookup"><span data-stu-id="0cdd8-142">Using DependsOn</span></span>

<span data-ttu-id="0cdd8-143">Ett användbart DSC-nyckelord är **DependsOn**.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-143">A useful DSC keyword is **DependsOn**.</span></span> <span data-ttu-id="0cdd8-144">Vanligtvis (men inte nödvändigtvis), DSC gäller resurser i den ordning som de visas i konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-144">Typically (though not necessarily always), DSC applies the resources in the order that they appear within the configuration.</span></span>
<span data-ttu-id="0cdd8-145">Dock **DependsOn** anger vilken resurser är beroende av andra resurser och MGM säkerställer att tillämpas de i rätt ordning, oavsett ordningen i vilken resurs som instanser har definierats.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-145">However, **DependsOn** specifies which resources depend on other resources, and the LCM ensures that they are applied in the correct order, regardless of the order in which resource instances are defined.</span></span>
<span data-ttu-id="0cdd8-146">En konfiguration kan till exempel ange att en instans av den **användare** resurs beror på förekomsten av en **grupp** instans:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-146">For example, a configuration might specify that an instance of the **User** resource depends on the existence of a **Group** instance:</span></span>

```powershell
Configuration DependsOnExample {
    Node Test-PC1 {
        Group GroupExample {
            Ensure = "Present"
            GroupName = "TestGroup"
        }

        User UserExample {
            Ensure = "Present"
            UserName = "TestUser"
            FullName = "TestUser"
            DependsOn = "[Group]GroupExample"
        }
    }
}

```

## <a name="using-new-resources-in-your-configuration"></a><span data-ttu-id="0cdd8-147">Med nya resurser i din konfiguration</span><span class="sxs-lookup"><span data-stu-id="0cdd8-147">Using new resources in Your configuration</span></span>

<span data-ttu-id="0cdd8-148">Om du körde i föregående exempel kanske såg du att du har en varning att du använder en resurs utan att uttryckligen importera den.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-148">If you ran the previous examples, you might have noticed that you were warned that you were using a resource without explicitly importing it.</span></span>
<span data-ttu-id="0cdd8-149">Idag DSC levereras med 12 resurser som en del av modulen PSDesiredStateConfiguration.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-149">Today, DSC ships with 12 resources as part of the PSDesiredStateConfiguration module.</span></span>
<span data-ttu-id="0cdd8-150">Andra resurser i externa moduler måste placeras i `$env:PSModulePath` för att kunna identifieras av MGM.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-150">Other resources in external modules must be placed in `$env:PSModulePath` in order to be recognized by the LCM.</span></span>
<span data-ttu-id="0cdd8-151">En ny cmdlet [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), kan användas för att avgöra vilka resurser som är installerade i systemet och kan användas av MGM.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-151">A new cmdlet, [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), can be used to determine what resources are installed on the system and available for use by the LCM.</span></span>
<span data-ttu-id="0cdd8-152">När dessa moduler har placerats i `$env:PSModulePath` och kan identifieras av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), de behöver inte läsas in i din konfiguration.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-152">Once these modules have been placed in `$env:PSModulePath` and are properly recognized by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), they still need to be loaded within your configuration.</span></span>
<span data-ttu-id="0cdd8-153">**Importera DscResource** är en dynamisk nyckelord som kan endast identifieras inom en **Configuration** block (dvs. det inte är en cmdlet).</span><span class="sxs-lookup"><span data-stu-id="0cdd8-153">**Import-DscResource** is a dynamic keyword that can only be recognized within a **Configuration** block (i.e. it is not a cmdlet).</span></span>
<span data-ttu-id="0cdd8-154">**Importera DscResource** stöder två parametrar:</span><span class="sxs-lookup"><span data-stu-id="0cdd8-154">**Import-DscResource** supports two parameters:</span></span>
- <span data-ttu-id="0cdd8-155">**Modulnamn** är det rekommenderade sättet att använda **importera DscResource**.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-155">**ModuleName** is the recommended way of using **Import-DscResource**.</span></span> <span data-ttu-id="0cdd8-156">Namnet på den modul som innehåller resurser som ska importeras (samt en strängmatris Modulnamnen) accepteras.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-156">It accepts the name of the module that contains the resources to be imported (as well as a string array of module names).</span></span>
- <span data-ttu-id="0cdd8-157">**Namnet** är namnet på resursen som ska importeras.</span><span class="sxs-lookup"><span data-stu-id="0cdd8-157">**Name** is the name of the resource to import.</span></span> <span data-ttu-id="0cdd8-158">Detta är inte ett eget namn som ”namn” som returneras av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), men Klassnamnet används när definierar resursschemat (returneras som **ResourceType** av [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span><span class="sxs-lookup"><span data-stu-id="0cdd8-158">This is not the friendly name returned as "Name" by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx), but the class name used when defining the resource schema (returned as **ResourceType** by [Get-DscResource](https://technet.microsoft.com/library/dn521625.aspx)).</span></span>

## <a name="see-also"></a><span data-ttu-id="0cdd8-159">Se även</span><span class="sxs-lookup"><span data-stu-id="0cdd8-159">See Also</span></span>
* [<span data-ttu-id="0cdd8-160">Windows PowerShell Desired State Configuration-översikt</span><span class="sxs-lookup"><span data-stu-id="0cdd8-160">Windows PowerShell Desired State Configuration Overview</span></span>](overview.md)
* [<span data-ttu-id="0cdd8-161">DSC-resurser</span><span class="sxs-lookup"><span data-stu-id="0cdd8-161">DSC Resources</span></span>](resources.md)
* [<span data-ttu-id="0cdd8-162">Konfigurera den lokala Configuration Manager</span><span class="sxs-lookup"><span data-stu-id="0cdd8-162">Configuring The Local Configuration Manager</span></span>](metaConfig.md)
