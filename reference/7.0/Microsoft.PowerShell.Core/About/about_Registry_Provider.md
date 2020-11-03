---
description: Register
keywords: powershell,cmdlet
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register leverantör
ms.openlocfilehash: efed68c42d46d5a44864af6b8892413c680c6b4e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270255"
---
# <a name="registry-provider"></a><span data-ttu-id="7fffc-104">Register leverantör</span><span class="sxs-lookup"><span data-stu-id="7fffc-104">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="7fffc-105">Providernamn</span><span class="sxs-lookup"><span data-stu-id="7fffc-105">Provider name</span></span>

<span data-ttu-id="7fffc-106">Register</span><span class="sxs-lookup"><span data-stu-id="7fffc-106">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="7fffc-107">Enheter</span><span class="sxs-lookup"><span data-stu-id="7fffc-107">Drives</span></span>

<span data-ttu-id="7fffc-108">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="7fffc-108">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="7fffc-109">Funktioner</span><span class="sxs-lookup"><span data-stu-id="7fffc-109">Capabilities</span></span>

<span data-ttu-id="7fffc-110">**ShouldProcess** , **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="7fffc-110">**ShouldProcess** , **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="7fffc-111">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="7fffc-111">Short description</span></span>

<span data-ttu-id="7fffc-112">Ger åtkomst till register nycklar, poster och värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fffc-112">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="7fffc-113">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="7fffc-113">Detailed description</span></span>

<span data-ttu-id="7fffc-114">Med PowerShell- **registerposten** kan du hämta, lägga till, ändra, rensa och ta bort register nycklar, poster och värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="7fffc-114">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="7fffc-115">**Register** enheterna är ett hierarkiskt namn område som innehåller register nycklar och under nycklar på din dator.</span><span class="sxs-lookup"><span data-stu-id="7fffc-115">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="7fffc-116">Register poster och värden är inte komponenter i den hierarkin.</span><span class="sxs-lookup"><span data-stu-id="7fffc-116">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="7fffc-117">De är i stället egenskaper för var och en av nycklarna.</span><span class="sxs-lookup"><span data-stu-id="7fffc-117">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="7fffc-118">**Registry** -providern stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="7fffc-118">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="7fffc-119">Get-location</span><span class="sxs-lookup"><span data-stu-id="7fffc-119">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="7fffc-120">Ange plats</span><span class="sxs-lookup"><span data-stu-id="7fffc-120">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="7fffc-121">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-121">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="7fffc-122">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="7fffc-122">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="7fffc-123">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-123">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="7fffc-124">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-124">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="7fffc-125">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-125">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="7fffc-126">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-126">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="7fffc-127">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-127">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="7fffc-128">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-128">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="7fffc-129">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-129">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="7fffc-130">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-130">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="7fffc-131">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="7fffc-131">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="7fffc-132">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="7fffc-132">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="7fffc-133">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="7fffc-133">Types exposed by this provider</span></span>

<span data-ttu-id="7fffc-134">Register nycklar representeras som instanser av klassen [Microsoft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) .</span><span class="sxs-lookup"><span data-stu-id="7fffc-134">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="7fffc-135">Register poster representeras som instanser av klassen [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .</span><span class="sxs-lookup"><span data-stu-id="7fffc-135">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="7fffc-136">Navigera i register enheterna</span><span class="sxs-lookup"><span data-stu-id="7fffc-136">Navigating the Registry drives</span></span>

<span data-ttu-id="7fffc-137">**Register** leverantören exponerar data lagret som två standard enheter.</span><span class="sxs-lookup"><span data-stu-id="7fffc-137">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="7fffc-138">Register platsen HKEY_LOCAL_MACHINE mappas till `HKLM:` enheten och HKEY_CURRENT_USER mappas till `HKCU:` enheten.</span><span class="sxs-lookup"><span data-stu-id="7fffc-138">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="7fffc-139">Om du vill arbeta med registret kan du ändra platsen till `HKLM:` enheten med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="7fffc-139">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="7fffc-140">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="7fffc-140">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="7fffc-141">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="7fffc-141">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="7fffc-142">Du kan också arbeta med **registrerings** leverantören från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="7fffc-142">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="7fffc-143">Om du vill referera till en register nyckel från en annan plats använder du enhets namnet ( `HKLM:` , `HKCU:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="7fffc-143">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="7fffc-144">Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange en nivå för **register** enheten.</span><span class="sxs-lookup"><span data-stu-id="7fffc-144">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="7fffc-145">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-145">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="7fffc-146">Kommandon som `dir` och är `ls` nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location)och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="7fffc-146">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="7fffc-147">I det sista exemplet visas en annan sökväg för sökvägen som du kan använda för att navigera i **register** leverantören.</span><span class="sxs-lookup"><span data-stu-id="7fffc-147">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="7fffc-148">Den här syntaxen använder Providerns namn, följt av två kolon `::` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-148">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="7fffc-149">Med den här syntaxen kan du använda det fullständiga HIVE-namnet i stället för namnet på den mappade enheten `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-149">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="7fffc-150">Visar innehållet i register nycklar</span><span class="sxs-lookup"><span data-stu-id="7fffc-150">Displaying the contents of registry keys</span></span>

<span data-ttu-id="7fffc-151">Registret är indelat i nycklar, under nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="7fffc-151">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="7fffc-152">Mer information om register strukturen finns i [strukturen för registret](/windows/desktop/sysinfo/structure-of-the-registry).</span><span class="sxs-lookup"><span data-stu-id="7fffc-152">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="7fffc-153">I en **register** enhet är varje nyckel en behållare.</span><span class="sxs-lookup"><span data-stu-id="7fffc-153">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="7fffc-154">En nyckel kan innehålla valfritt antal nycklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-154">A key can contain any number of keys.</span></span> <span data-ttu-id="7fffc-155">En register nyckel som har en överordnad nyckel kallas för en under nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-155">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="7fffc-156">Du kan använda `Get-ChildItem` för att Visa register nycklar och `Set-Location` navigera till en nyckel Sök väg.</span><span class="sxs-lookup"><span data-stu-id="7fffc-156">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="7fffc-157">Register värden är attribut för en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-157">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="7fffc-158">I **register** enheten kallas de för **objekt egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="7fffc-158">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="7fffc-159">En register nyckel kan ha både underordnade nycklar och objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="7fffc-159">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="7fffc-160">I det här exemplet visas skillnaden mellan `Get-Item` och `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-160">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="7fffc-161">När du använder `Get-Item` på register nyckeln "Spooler" kan du se dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="7fffc-161">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

```
PS C:\ > Get-Item -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services


Name        Property
----        --------
Spooler     DependOnService    : {RPCSS, http}
            Description        : @%systemroot%\system32\spoolsv.exe,-2
            DisplayName        : @%systemroot%\system32\spoolsv.exe,-1
            ErrorControl       : 1
            FailureActions     : {16, 14, 0, 0...}
            Group              : SpoolerGroup
            ImagePath          : C:\WINDOWS\System32\spoolsv.exe
            ObjectName         : LocalSystem
            RequiredPrivileges : {SeTcbPrivilege, SeImpersonatePrivilege, ...
            ServiceSidType     : 1
            Start              : 2
            Type               : 27
```

<span data-ttu-id="7fffc-162">Varje register nyckel kan också ha under nycklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-162">Each registry key can also have subkeys.</span></span> <span data-ttu-id="7fffc-163">Under `Get-Item` nycklarna visas inte när du använder på en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-163">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="7fffc-164">I `Get-ChildItem` cmdleten visas underordnade objekt i nyckeln "Spooler", inklusive egenskaperna för varje under nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-164">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="7fffc-165">Egenskaperna för överordnade nycklar visas inte när du använder `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-165">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

```
PS C:\> Get-ChildItem -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler


    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services\Spooler


Name             Property
----             --------
Performance      Close           : PerfClose
                 Collect         : PerfCollect
                 Collect Timeout : 2000
                 Library         : C:\Windows\System32\winspool.drv
                 Object List     : 1450
                 Open            : PerfOpen
                 Open Timeout    : 4000
Security         Security : {1, 0, 20, 128...}
```

<span data-ttu-id="7fffc-166">`Get-Item`Cmdleten kan också användas på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="7fffc-166">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="7fffc-167">I följande exempel navigerar du till register nyckeln Spooler (Spooler) och hämtar objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="7fffc-167">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="7fffc-168">Punkten `.` används för att ange den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="7fffc-168">The dot `.` is used to indicate the current location.</span></span>

```
PS C:\> cd HKLM:\System\CurrentControlSet\Services\Spooler
PS HKLM:\SYSTEM\CurrentControlSet\Services\Spooler> Get-Item .

    Hive: HKEY_LOCAL_MACHINE\SYSTEM\CurrentControlSet\Services

Name             Property
----             --------
Spooler          DependOnService    : {RPCSS, http}
                 Description        : @%systemroot%\system32\spoolsv.exe,-2
...
```

<span data-ttu-id="7fffc-169">Mer information om de cmdlets som beskrivs i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-169">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="7fffc-170">-[Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="7fffc-170">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="7fffc-171">Visa register nyckel värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-171">Viewing registry key values</span></span>

<span data-ttu-id="7fffc-172">Register nyckel värden lagras som egenskaper för varje register nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-172">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="7fffc-173">`Get-ItemProperty`Cmdleten visar register nyckel egenskaperna med det namn som du anger.</span><span class="sxs-lookup"><span data-stu-id="7fffc-173">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="7fffc-174">Resultatet är en **PSCustomObject** som innehåller de egenskaper som du anger.</span><span class="sxs-lookup"><span data-stu-id="7fffc-174">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="7fffc-175">I följande exempel används `Get-ItemProperty` cmdleten för att visa alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="7fffc-175">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="7fffc-176">Genom att lagra det resulterande objektet i en variabel kan du komma åt önskat egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="7fffc-176">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="7fffc-177">Om du anger ett värde för `-Name` parametern väljs de egenskaper som du anger och returnerar **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="7fffc-177">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="7fffc-178">I följande exempel visas skillnaden i utdata när du använder- `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="7fffc-178">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

```
PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem

BUILD                      : 17134.1
Installation Directory     : C:\WINDOWS\system32\WBEM
MOF Self-Install Directory : C:\WINDOWS\system32\WBEM\MOF
PSPath                     : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath               : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName                : Wbem
PSDrive                    : HKLM
PSProvider                 : Microsoft.PowerShell.Core\Registry

PS C:\> Get-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD

BUILD        : 17134.1
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Wbem
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft
PSChildName  : Wbem
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
```

<span data-ttu-id="7fffc-179">Från och med PowerShell 5,0 `Get-ItemPropertyValue` returnerar cmdleten bara värdet för den egenskap som du anger.</span><span class="sxs-lookup"><span data-stu-id="7fffc-179">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="7fffc-180">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-180">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="7fffc-181">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-181">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="7fffc-182">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="7fffc-182">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="7fffc-183">Ändra register nyckel värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-183">Changing registry key values</span></span>

<span data-ttu-id="7fffc-184">`Set-ItemProperty`Cmdlet: en kommer att ange attribut för register nycklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-184">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="7fffc-185">I följande exempel används `Set-ItemProperty` för att ändra start typen för Spooler-tjänsten till manuell.</span><span class="sxs-lookup"><span data-stu-id="7fffc-185">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="7fffc-186">Exemplet ändrar **StartType** tillbaka till *automatiskt* med hjälp av `Set-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="7fffc-186">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

```
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler Automatic

PS C:\> $path = "HKLM:\SYSTEM\CurrentControlSet\Services\Spooler\"
PS C:\> Set-ItemProperty -Path $path -Name Start -Value 3
PS C:\> Get-Service spooler | Select-Object Name, StartMode

Name    StartType
----    ---------
spooler    Manual

PS C:\> Set-Service -Name Spooler -StartupType Automatic
```

<span data-ttu-id="7fffc-187">Varje register nyckel har ett *Standardvärde* .</span><span class="sxs-lookup"><span data-stu-id="7fffc-187">Each registry key has a *default* value.</span></span> <span data-ttu-id="7fffc-188">Du kan ändra *standardvärdet* för en register nyckel med antingen `Set-Item` eller `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-188">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="7fffc-189">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-189">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="7fffc-190">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-190">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="7fffc-191">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-191">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="7fffc-192">Skapa register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-192">Creating registry keys and values</span></span>

<span data-ttu-id="7fffc-193">`New-Item`Cmdleten skapar register nycklar med ett namn som du anger.</span><span class="sxs-lookup"><span data-stu-id="7fffc-193">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="7fffc-194">Du kan också använda `mkdir` funktionen som anropar `New-Item` cmdleten internt.</span><span class="sxs-lookup"><span data-stu-id="7fffc-194">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="7fffc-195">Du kan använda `New-ItemProperty` cmdleten för att skapa värden i en register nyckel som du anger.</span><span class="sxs-lookup"><span data-stu-id="7fffc-195">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="7fffc-196">I följande exempel skapas ett nytt DWORD-värde i register nyckeln ContosoCompany.</span><span class="sxs-lookup"><span data-stu-id="7fffc-196">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="7fffc-197">Läs avsnittet dynamiska parametrar i den här artikeln för andra tillåtna typ värden.</span><span class="sxs-lookup"><span data-stu-id="7fffc-197">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="7fffc-198">Detaljerad cmdlet-användning finns i [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span><span class="sxs-lookup"><span data-stu-id="7fffc-198">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="7fffc-199">Kopiera register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-199">Copying registry keys and values</span></span>

<span data-ttu-id="7fffc-200">I **Registry** -providern använder du `Copy-Item` cmdleten för att kopiera register nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="7fffc-200">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="7fffc-201">Använd `Copy-ItemProperty` cmdleten för att endast kopiera register värden.</span><span class="sxs-lookup"><span data-stu-id="7fffc-201">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="7fffc-202">Följande kommando kopierar register nyckeln "contoso" och dess egenskaper till den angivna platsen "HKLM: \ Software\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="7fffc-202">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="7fffc-203">`Copy-Item` skapar mål nyckeln om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="7fffc-203">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="7fffc-204">Om mål nyckeln finns `Copy-Item` skapar en dubblett av käll nyckeln som ett underordnat objekt (under nyckel) för mål nyckeln.</span><span class="sxs-lookup"><span data-stu-id="7fffc-204">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="7fffc-205">Följande kommando använder `Copy-ItemProperty` cmdleten för att kopiera "Server"-värdet från "contoso"-nyckeln till "Fabrikam"-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="7fffc-205">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="7fffc-206">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-206">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="7fffc-207">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-207">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="7fffc-208">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-208">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="7fffc-209">Flytta register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-209">Moving registry keys and values</span></span>

<span data-ttu-id="7fffc-210">`Move-Item` `Move-ItemProperty` Cmdletarna och beter sig som deras "kopiering"-motsvarigheter.</span><span class="sxs-lookup"><span data-stu-id="7fffc-210">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="7fffc-211">Om målet finns `Move-Item` flyttar käll nyckeln under mål nyckeln.</span><span class="sxs-lookup"><span data-stu-id="7fffc-211">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="7fffc-212">Om mål nyckeln inte finns, flyttas käll nyckeln till mål Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="7fffc-212">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="7fffc-213">Följande kommando flyttar "contoso"-nyckeln till sökvägen "HKLM: \ SOFTWARE\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="7fffc-213">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="7fffc-214">Detta kommando flyttar alla egenskaper från "HKLM: \ SOFTWARE\ContosoCompany" till "HKLM: \ SOFTWARE\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="7fffc-214">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="7fffc-215">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-215">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="7fffc-216">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-216">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="7fffc-217">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-217">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="7fffc-218">Byta namn på register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-218">Renaming registry keys and values</span></span>

<span data-ttu-id="7fffc-219">Du kan byta namn på register nycklar och värden precis som du skulle göra med filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-219">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="7fffc-220">`Rename-Item` byter namn på register nycklar och `Rename-ItemProperty` byter namn på register värden.</span><span class="sxs-lookup"><span data-stu-id="7fffc-220">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="7fffc-221">Ändra säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="7fffc-221">Changing security descriptors</span></span>

<span data-ttu-id="7fffc-222">Du kan begränsa åtkomsten till register nycklar med hjälp av `Get-Acl` `Set-Acl` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="7fffc-222">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="7fffc-223">I följande exempel läggs en ny användare till med fullständig behörighet till register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="7fffc-223">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="7fffc-224">Fler exempel och information om cmdlet-användning finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-224">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="7fffc-225">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="7fffc-225">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="7fffc-226">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="7fffc-226">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="7fffc-227">Ta bort och rensa register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="7fffc-227">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="7fffc-228">Du kan ta bort objekt som finns med hjälp av **Remove-item** , men du uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="7fffc-228">You can remove contained items by using **Remove-Item** , but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="7fffc-229">Följande exempel försöker ta bort en nyckel "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="7fffc-229">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

```
PS C:\> dir HKLM:\SOFTWARE\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE\Contoso

Name                           Property
----                           --------
ChildKey

PS C:\> Remove-Item -Path HKLM:\SOFTWARE\Contoso

Confirm
The item at HKLM:\SOFTWARE\Contoso has children and the -Recurse
parameter was not specified. If you continue, all children will be removed
with the item. Are you sure you want to continue?
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):
```

<span data-ttu-id="7fffc-230">Om du vill ta bort de objekt som finns utan att göra det anger du `-Recurse` parametern.</span><span class="sxs-lookup"><span data-stu-id="7fffc-230">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="7fffc-231">Om du vill ta bort alla objekt inom "HKLM: \ SOFTWARE\Contoso" men inte "HKLM: \ SOFTWARE\Contoso", använder du ett avslutande omvänt snedstreck `\` följt av ett jokertecken.</span><span class="sxs-lookup"><span data-stu-id="7fffc-231">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="7fffc-232">Det här kommandot tar bort registervärdet "ContosoTest" från register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="7fffc-232">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="7fffc-233">`Clear-Item` tar bort alla register värden för en nyckel.</span><span class="sxs-lookup"><span data-stu-id="7fffc-233">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="7fffc-234">I följande exempel rensas alla värden från register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="7fffc-234">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="7fffc-235">Om du bara vill rensa en speciell egenskap använder du `Clear-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="7fffc-235">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

```
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name           Property
----           --------
Contoso        Server     : {a, b, c}
               HereString : {This is text which contains
               newlines. It also contains "quoted" strings}
               (default)  : 1

PS HKLM:\SOFTWARE\> Clear-Item .\Contoso\
PS HKLM:\SOFTWARE\> Get-Item .\Contoso\

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
Contoso
```

<span data-ttu-id="7fffc-236">Fler exempel och information om cmdlet-användning finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="7fffc-236">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="7fffc-237">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-237">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="7fffc-238">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-238">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="7fffc-239">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-239">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="7fffc-240">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-240">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="7fffc-241">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="7fffc-241">Dynamic parameters</span></span>

<span data-ttu-id="7fffc-242">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="7fffc-242">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="7fffc-243">Skriv <Microsoft. Win32. RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="7fffc-243">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="7fffc-244">Skapar eller ändrar data typen för ett register värde.</span><span class="sxs-lookup"><span data-stu-id="7fffc-244">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="7fffc-245">Standardvärdet är `String` (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="7fffc-245">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="7fffc-246">Den här parametern fungerar som den är utformad på cmdleten [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) .</span><span class="sxs-lookup"><span data-stu-id="7fffc-246">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="7fffc-247">Den är också tillgänglig på cmdleten [set-item](xref:Microsoft.PowerShell.Management.Set-Item) i register enheterna, men den har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="7fffc-247">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="7fffc-248">Värde</span><span class="sxs-lookup"><span data-stu-id="7fffc-248">Value</span></span> | <span data-ttu-id="7fffc-249">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7fffc-249">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="7fffc-250">Anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="7fffc-250">Specifies a null-terminated string.</span></span> <span data-ttu-id="7fffc-251">Motsvarar REG_SZ.</span><span class="sxs-lookup"><span data-stu-id="7fffc-251">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="7fffc-252">Anger en null-avslutad sträng som innehåller expanderad</span><span class="sxs-lookup"><span data-stu-id="7fffc-252">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="7fffc-253">referenser till miljövariabler som expanderas när</span><span class="sxs-lookup"><span data-stu-id="7fffc-253">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="7fffc-254">Värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="7fffc-254">the value is retrieved.</span></span> <span data-ttu-id="7fffc-255">Motsvarar REG_EXPAND_SZ.</span><span class="sxs-lookup"><span data-stu-id="7fffc-255">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="7fffc-256">Anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="7fffc-256">Specifies binary data in any form.</span></span> <span data-ttu-id="7fffc-257">Motsvarar REG_BINARY.</span><span class="sxs-lookup"><span data-stu-id="7fffc-257">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="7fffc-258">Anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="7fffc-258">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="7fffc-259">Motsvarar REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="7fffc-259">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="7fffc-260">Anger en matris med null-terminerade strängar som avslut ATS av</span><span class="sxs-lookup"><span data-stu-id="7fffc-260">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="7fffc-261">två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="7fffc-261">two null characters.</span></span> <span data-ttu-id="7fffc-262">Motsvarar REG_MULTI_SZ.</span><span class="sxs-lookup"><span data-stu-id="7fffc-262">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="7fffc-263">Anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="7fffc-263">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="7fffc-264">Motsvarar REG_QWORD.</span><span class="sxs-lookup"><span data-stu-id="7fffc-264">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="7fffc-265">Anger en register data typ som inte stöds, till exempel</span><span class="sxs-lookup"><span data-stu-id="7fffc-265">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="7fffc-266">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="7fffc-266">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="7fffc-267">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="7fffc-267">Cmdlets supported</span></span>

- [<span data-ttu-id="7fffc-268">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="7fffc-268">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="7fffc-269">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="7fffc-269">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="7fffc-270">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="7fffc-270">Using the pipeline</span></span>

<span data-ttu-id="7fffc-271">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="7fffc-271">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="7fffc-272">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="7fffc-272">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="7fffc-273">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="7fffc-273">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="7fffc-274">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="7fffc-274">Getting help</span></span>

<span data-ttu-id="7fffc-275">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="7fffc-275">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="7fffc-276">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett `Get-Help` kommando i en fil system enhet eller använder parametern **Path** för att ange en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="7fffc-276">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="7fffc-277">Se även</span><span class="sxs-lookup"><span data-stu-id="7fffc-277">See also</span></span>

 [<span data-ttu-id="7fffc-278">about_Providers</span><span class="sxs-lookup"><span data-stu-id="7fffc-278">about_Providers</span></span>](../About/about_Providers.md)
