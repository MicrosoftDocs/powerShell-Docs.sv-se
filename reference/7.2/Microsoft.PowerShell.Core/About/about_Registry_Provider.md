---
description: Register
Locale: en-US
ms.date: 10/18/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_registry_provider?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Register leverantör
ms.openlocfilehash: 2d57afc164885b4d207108a360215e63a5431632
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708446"
---
# <a name="registry-provider"></a><span data-ttu-id="c6575-103">Register leverantör</span><span class="sxs-lookup"><span data-stu-id="c6575-103">Registry provider</span></span>

## <a name="provider-name"></a><span data-ttu-id="c6575-104">Providernamn</span><span class="sxs-lookup"><span data-stu-id="c6575-104">Provider name</span></span>

<span data-ttu-id="c6575-105">Register</span><span class="sxs-lookup"><span data-stu-id="c6575-105">Registry</span></span>

## <a name="drives"></a><span data-ttu-id="c6575-106">Enheter</span><span class="sxs-lookup"><span data-stu-id="c6575-106">Drives</span></span>

<span data-ttu-id="c6575-107">`HKLM:`, `HKCU:`</span><span class="sxs-lookup"><span data-stu-id="c6575-107">`HKLM:`, `HKCU:`</span></span>

## <a name="capabilities"></a><span data-ttu-id="c6575-108">Funktioner</span><span class="sxs-lookup"><span data-stu-id="c6575-108">Capabilities</span></span>

<span data-ttu-id="c6575-109">**ShouldProcess**, **UseTransactions**</span><span class="sxs-lookup"><span data-stu-id="c6575-109">**ShouldProcess**, **UseTransactions**</span></span>

## <a name="short-description"></a><span data-ttu-id="c6575-110">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="c6575-110">Short description</span></span>

<span data-ttu-id="c6575-111">Ger åtkomst till register nycklar, poster och värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6575-111">Provides access to the registry keys, entries, and values in PowerShell.</span></span>

## <a name="detailed-description"></a><span data-ttu-id="c6575-112">Detaljerad beskrivning</span><span class="sxs-lookup"><span data-stu-id="c6575-112">Detailed description</span></span>

<span data-ttu-id="c6575-113">Med PowerShell- **registerposten** kan du hämta, lägga till, ändra, rensa och ta bort register nycklar, poster och värden i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c6575-113">The PowerShell **Registry** provider lets you get, add, change, clear, and delete registry keys, entries, and values in PowerShell.</span></span>

<span data-ttu-id="c6575-114">**Register** enheterna är ett hierarkiskt namn område som innehåller register nycklar och under nycklar på din dator.</span><span class="sxs-lookup"><span data-stu-id="c6575-114">The **Registry** drives are a hierarchical namespace containing the registry keys and subkeys on your computer.</span></span> <span data-ttu-id="c6575-115">Register poster och värden är inte komponenter i den hierarkin.</span><span class="sxs-lookup"><span data-stu-id="c6575-115">Registry entries and values are not components of that hierarchy.</span></span> <span data-ttu-id="c6575-116">De är i stället egenskaper för var och en av nycklarna.</span><span class="sxs-lookup"><span data-stu-id="c6575-116">Instead, they are properties of each of the keys.</span></span>

<span data-ttu-id="c6575-117">**Registry** -providern stöder följande cmdlets, som beskrivs i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="c6575-117">The **Registry** provider supports the following cmdlets, which are covered in this article.</span></span>

- [<span data-ttu-id="c6575-118">Get-location</span><span class="sxs-lookup"><span data-stu-id="c6575-118">Get-Location</span></span>](xref:Microsoft.PowerShell.Management.Get-Location)
- [<span data-ttu-id="c6575-119">Ange plats</span><span class="sxs-lookup"><span data-stu-id="c6575-119">Set-Location</span></span>](xref:Microsoft.PowerShell.Management.Set-Location)
- [<span data-ttu-id="c6575-120">Hämta objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-120">Get-Item</span></span>](xref:Microsoft.PowerShell.Management.Get-Item)
- [<span data-ttu-id="c6575-121">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="c6575-121">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)
- [<span data-ttu-id="c6575-122">Anropa-objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-122">Invoke-Item</span></span>](xref:Microsoft.PowerShell.Management.Invoke-Item)
- [<span data-ttu-id="c6575-123">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-123">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c6575-124">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-124">New-Item</span></span>](xref:Microsoft.PowerShell.Management.New-Item)
- [<span data-ttu-id="c6575-125">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-125">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c6575-126">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-126">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c6575-127">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-127">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)
- [<span data-ttu-id="c6575-128">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-128">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)
- [<span data-ttu-id="c6575-129">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-129">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c6575-130">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c6575-130">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c6575-131">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="c6575-131">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="types-exposed-by-this-provider"></a><span data-ttu-id="c6575-132">Typer som exponeras av denna provider</span><span class="sxs-lookup"><span data-stu-id="c6575-132">Types exposed by this provider</span></span>

<span data-ttu-id="c6575-133">Register nycklar representeras som instanser av klassen [Microsoft. Win32. RegistryKey](/dotnet/api/microsoft.win32.registrykey) .</span><span class="sxs-lookup"><span data-stu-id="c6575-133">Registry keys are represented as instances of the [Microsoft.Win32.RegistryKey](/dotnet/api/microsoft.win32.registrykey) class.</span></span> <span data-ttu-id="c6575-134">Register poster representeras som instanser av klassen [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) .</span><span class="sxs-lookup"><span data-stu-id="c6575-134">Registry entries are represented as instances of the [PSCustomObject](/dotnet/api/system.management.automation.pscustomobject) class.</span></span>

## <a name="navigating-the-registry-drives"></a><span data-ttu-id="c6575-135">Navigera i register enheterna</span><span class="sxs-lookup"><span data-stu-id="c6575-135">Navigating the Registry drives</span></span>

<span data-ttu-id="c6575-136">**Register** leverantören exponerar data lagret som två standard enheter.</span><span class="sxs-lookup"><span data-stu-id="c6575-136">The **Registry** provider exposes its data store as two default drives.</span></span> <span data-ttu-id="c6575-137">Register platsen HKEY_LOCAL_MACHINE mappas till `HKLM:` enheten och HKEY_CURRENT_USER mappas till `HKCU:` enheten.</span><span class="sxs-lookup"><span data-stu-id="c6575-137">The registry location HKEY_LOCAL_MACHINE is mapped to the `HKLM:` drive and HKEY_CURRENT_USER is mapped to the `HKCU:` drive.</span></span> <span data-ttu-id="c6575-138">Om du vill arbeta med registret kan du ändra platsen till `HKLM:` enheten med hjälp av följande kommando.</span><span class="sxs-lookup"><span data-stu-id="c6575-138">To work with the registry, you can change your location to the `HKLM:` drive using the following command.</span></span>

```powershell
Set-Location HKLM:
```

<span data-ttu-id="c6575-139">Om du vill återgå till en fil systemen het skriver du enhetens namn.</span><span class="sxs-lookup"><span data-stu-id="c6575-139">To return to a file system drive, type the drive name.</span></span> <span data-ttu-id="c6575-140">Skriv till exempel:</span><span class="sxs-lookup"><span data-stu-id="c6575-140">For example, type:</span></span>

```powershell
Set-Location C:
```

<span data-ttu-id="c6575-141">Du kan också arbeta med **registrerings** leverantören från andra PowerShell-enheter.</span><span class="sxs-lookup"><span data-stu-id="c6575-141">You can also work with the **Registry** provider from any other PowerShell drive.</span></span> <span data-ttu-id="c6575-142">Om du vill referera till en register nyckel från en annan plats använder du enhets namnet ( `HKLM:` , `HKCU:` ) i sökvägen.</span><span class="sxs-lookup"><span data-stu-id="c6575-142">To reference a registry key from another location, use the drive name (`HKLM:`, `HKCU:`) in the path.</span></span> <span data-ttu-id="c6575-143">Använd ett omvänt snedstreck ( \\ ) eller ett snedstreck (/) för att ange en nivå för **register** enheten.</span><span class="sxs-lookup"><span data-stu-id="c6575-143">Use a backslash (\\) or a forward slash (/) to indicate a level of the **Registry** drive.</span></span>

```powershell
PS C:\> cd HKLM:\Software
```

> [!NOTE]
> <span data-ttu-id="c6575-144">PowerShell använder alias för att ge dig ett välbekant sätt att arbeta med providerns sökvägar.</span><span class="sxs-lookup"><span data-stu-id="c6575-144">PowerShell uses aliases to allow you a familiar way to work with provider paths.</span></span> <span data-ttu-id="c6575-145">Kommandon som `dir` och är `ls` nu alias för [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` är ett alias för [set-location](xref:Microsoft.PowerShell.Management.Set-Location)och `pwd` är ett alias för [Get-location](xref:Microsoft.PowerShell.Management.Get-Location).</span><span class="sxs-lookup"><span data-stu-id="c6575-145">Commands such as `dir` and `ls` are now aliases for [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem), `cd` is an alias for [Set-Location](xref:Microsoft.PowerShell.Management.Set-Location), and `pwd` is an alias for [Get-Location](xref:Microsoft.PowerShell.Management.Get-Location).</span></span>

<span data-ttu-id="c6575-146">I det sista exemplet visas en annan sökväg för sökvägen som du kan använda för att navigera i **register** leverantören.</span><span class="sxs-lookup"><span data-stu-id="c6575-146">This last example shows another path syntax you can use to navigate the **Registry** provider.</span></span> <span data-ttu-id="c6575-147">Den här syntaxen använder Providerns namn, följt av två kolon `::` .</span><span class="sxs-lookup"><span data-stu-id="c6575-147">This syntax uses the provider name, followed by two colons `::`.</span></span> <span data-ttu-id="c6575-148">Med den här syntaxen kan du använda det fullständiga HIVE-namnet i stället för namnet på den mappade enheten `HKLM` .</span><span class="sxs-lookup"><span data-stu-id="c6575-148">This syntax allows you to use the full HIVE name, instead of the mapped drive name `HKLM`.</span></span>

```powershell
cd "Registry::HKEY_LOCAL_MACHINE\Software"
```

## <a name="displaying-the-contents-of-registry-keys"></a><span data-ttu-id="c6575-149">Visar innehållet i register nycklar</span><span class="sxs-lookup"><span data-stu-id="c6575-149">Displaying the contents of registry keys</span></span>

<span data-ttu-id="c6575-150">Registret är indelat i nycklar, under nycklar och poster.</span><span class="sxs-lookup"><span data-stu-id="c6575-150">The registry is divided into keys, subkeys, and entries.</span></span> <span data-ttu-id="c6575-151">Mer information om register strukturen finns i [strukturen för registret](/windows/desktop/sysinfo/structure-of-the-registry).</span><span class="sxs-lookup"><span data-stu-id="c6575-151">For more information about registry structure, see [Structure of the Registry](/windows/desktop/sysinfo/structure-of-the-registry).</span></span>

<span data-ttu-id="c6575-152">I en **register** enhet är varje nyckel en behållare.</span><span class="sxs-lookup"><span data-stu-id="c6575-152">In a **Registry** drive, each key is a container.</span></span> <span data-ttu-id="c6575-153">En nyckel kan innehålla valfritt antal nycklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-153">A key can contain any number of keys.</span></span> <span data-ttu-id="c6575-154">En register nyckel som har en överordnad nyckel kallas för en under nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-154">A registry key that has a parent key is called a subkey.</span></span> <span data-ttu-id="c6575-155">Du kan använda `Get-ChildItem` för att Visa register nycklar och `Set-Location` navigera till en nyckel Sök väg.</span><span class="sxs-lookup"><span data-stu-id="c6575-155">You can use `Get-ChildItem` to view registry keys and `Set-Location` to navigate to a key path.</span></span>

<span data-ttu-id="c6575-156">Register värden är attribut för en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-156">Registry values are attributes of a registry key.</span></span> <span data-ttu-id="c6575-157">I **register** enheten kallas de för **objekt egenskaper**.</span><span class="sxs-lookup"><span data-stu-id="c6575-157">In the **Registry** drive, they are called **Item Properties**.</span></span> <span data-ttu-id="c6575-158">En register nyckel kan ha både underordnade nycklar och objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c6575-158">A registry key can have both children keys and item properties.</span></span>

<span data-ttu-id="c6575-159">I det här exemplet visas skillnaden mellan `Get-Item` och `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c6575-159">In this example, the difference between `Get-Item` and `Get-ChildItem` is shown.</span></span> <span data-ttu-id="c6575-160">När du använder `Get-Item` på register nyckeln "Spooler" kan du se dess egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c6575-160">When you use `Get-Item` on the "Spooler" registry key, you can view its properties.</span></span>

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

<span data-ttu-id="c6575-161">Varje register nyckel kan också ha under nycklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-161">Each registry key can also have subkeys.</span></span> <span data-ttu-id="c6575-162">Under `Get-Item` nycklarna visas inte när du använder på en register nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-162">When you use `Get-Item` on a registry key, the subkeys are not displayed.</span></span> <span data-ttu-id="c6575-163">I `Get-ChildItem` cmdleten visas underordnade objekt i nyckeln "Spooler", inklusive egenskaperna för varje under nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-163">The `Get-ChildItem` cmdlet will show you children items of the "Spooler" key, including each subkey's properties.</span></span> <span data-ttu-id="c6575-164">Egenskaperna för överordnade nycklar visas inte när du använder `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="c6575-164">The parent keys properties are not shown when using `Get-ChildItem`.</span></span>

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

<span data-ttu-id="c6575-165">`Get-Item`Cmdleten kan också användas på den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="c6575-165">The `Get-Item` cmdlet can also be used on the current location.</span></span> <span data-ttu-id="c6575-166">I följande exempel navigerar du till register nyckeln Spooler (Spooler) och hämtar objekt egenskaperna.</span><span class="sxs-lookup"><span data-stu-id="c6575-166">The following example navigates to the "Spooler" registry key and gets the item properties.</span></span>
<span data-ttu-id="c6575-167">Punkten `.` används för att ange den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="c6575-167">The dot `.` is used to indicate the current location.</span></span>

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

<span data-ttu-id="c6575-168">Mer information om de cmdlets som beskrivs i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-168">For more information on the cmdlets covered in this section, see the following articles.</span></span>

<span data-ttu-id="c6575-169">-[Hämta objekt](xref:Microsoft.PowerShell.Management.Get-Item) 
- [Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="c6575-169">-[Get-Item](xref:Microsoft.PowerShell.Management.Get-Item)
-[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)</span></span>

## <a name="viewing-registry-key-values"></a><span data-ttu-id="c6575-170">Visa register nyckel värden</span><span class="sxs-lookup"><span data-stu-id="c6575-170">Viewing registry key values</span></span>

<span data-ttu-id="c6575-171">Register nyckel värden lagras som egenskaper för varje register nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-171">Registry key values are stored as properties of each registry key.</span></span> <span data-ttu-id="c6575-172">`Get-ItemProperty`Cmdleten visar register nyckel egenskaperna med det namn som du anger.</span><span class="sxs-lookup"><span data-stu-id="c6575-172">The `Get-ItemProperty` cmdlet views registry key properties using the name you specify.</span></span> <span data-ttu-id="c6575-173">Resultatet är en **PSCustomObject** som innehåller de egenskaper som du anger.</span><span class="sxs-lookup"><span data-stu-id="c6575-173">The result is a **PSCustomObject** containing the properties you specify.</span></span>

<span data-ttu-id="c6575-174">I följande exempel används `Get-ItemProperty` cmdleten för att visa alla egenskaper.</span><span class="sxs-lookup"><span data-stu-id="c6575-174">The Following example uses the `Get-ItemProperty` cmdlet to view all properties.</span></span> <span data-ttu-id="c6575-175">Genom att lagra det resulterande objektet i en variabel kan du komma åt önskat egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="c6575-175">Storing the resulting object in a variable allows you to access the desired property value.</span></span>

```powershell
$p = Get-ItemProperty -Path HKLM:\SYSTEM\CurrentControlSet\Services\Spooler
$p.DependOnService
```

```output
RPCSS
http
```

<span data-ttu-id="c6575-176">Om du anger ett värde för `-Name` parametern väljs de egenskaper som du anger och returnerar **PSCustomObject**.</span><span class="sxs-lookup"><span data-stu-id="c6575-176">Specifying a value for the `-Name` parameter selects the properties you specify and returns the **PSCustomObject**.</span></span>  <span data-ttu-id="c6575-177">I följande exempel visas skillnaden i utdata när du använder- `-Name` parametern.</span><span class="sxs-lookup"><span data-stu-id="c6575-177">The following example shows the difference in output when you use the `-Name` parameter.</span></span>

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

<span data-ttu-id="c6575-178">Från och med PowerShell 5,0 `Get-ItemPropertyValue` returnerar cmdleten bara värdet för den egenskap som du anger.</span><span class="sxs-lookup"><span data-stu-id="c6575-178">Beginning in PowerShell 5.0, the `Get-ItemPropertyValue` cmdlet returns only the value of the property you specify.</span></span>

```powershell
Get-ItemPropertyValue -Path HKLM:\SOFTWARE\Microsoft\Wbem -Name BUILD
```

```output
17134.1
```

<span data-ttu-id="c6575-179">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-179">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c6575-180">Get-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-180">Get-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)
- [<span data-ttu-id="c6575-181">Get-ItemPropertyValue</span><span class="sxs-lookup"><span data-stu-id="c6575-181">Get-ItemPropertyValue</span></span>](xref:Microsoft.PowerShell.Management.Get-ItemProperty)

## <a name="changing-registry-key-values"></a><span data-ttu-id="c6575-182">Ändra register nyckel värden</span><span class="sxs-lookup"><span data-stu-id="c6575-182">Changing registry key values</span></span>

<span data-ttu-id="c6575-183">`Set-ItemProperty`Cmdlet: en kommer att ange attribut för register nycklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-183">The `Set-ItemProperty` cmdlet will set attributes for registry keys.</span></span> <span data-ttu-id="c6575-184">I följande exempel används `Set-ItemProperty` för att ändra start typen för Spooler-tjänsten till manuell.</span><span class="sxs-lookup"><span data-stu-id="c6575-184">The following example uses `Set-ItemProperty` to change the spooler service start type to manual.</span></span> <span data-ttu-id="c6575-185">Exemplet ändrar **StartType** tillbaka till *automatiskt* med hjälp av `Set-Service` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c6575-185">The example changes the **StartType** back to *Automatic* using the `Set-Service` cmdlet.</span></span>

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

<span data-ttu-id="c6575-186">Varje register nyckel har ett *Standardvärde* .</span><span class="sxs-lookup"><span data-stu-id="c6575-186">Each registry key has a *default* value.</span></span> <span data-ttu-id="c6575-187">Du kan ändra *standardvärdet* för en register nyckel med antingen `Set-Item` eller `Set-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c6575-187">You can change the *default* value for a registry key with either `Set-Item` or `Set-ItemProperty`.</span></span>

```powershell
Set-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name "(default)" -Value "one"
Set-Item -Path HKLM:\SOFTWARE\Contoso -Value "two"
```

<span data-ttu-id="c6575-188">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-188">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c6575-189">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-189">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c6575-190">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-190">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="creating-registry-keys-and-values"></a><span data-ttu-id="c6575-191">Skapa register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c6575-191">Creating registry keys and values</span></span>

<span data-ttu-id="c6575-192">`New-Item`Cmdleten skapar register nycklar med ett namn som du anger.</span><span class="sxs-lookup"><span data-stu-id="c6575-192">The `New-Item` cmdlet will create registry keys with a name that you provide.</span></span>
<span data-ttu-id="c6575-193">Du kan också använda `mkdir` funktionen som anropar `New-Item` cmdleten internt.</span><span class="sxs-lookup"><span data-stu-id="c6575-193">You can also use the `mkdir` function, which calls the `New-Item` cmdlet internally.</span></span>

```
PS HKLM:\SOFTWARE\> mkdir ContosoCompany

    Hive: HKEY_LOCAL_MACHINE\SOFTWARE

Name                           Property
----                           --------
ContosoCompany
```

<span data-ttu-id="c6575-194">Du kan använda `New-ItemProperty` cmdleten för att skapa värden i en register nyckel som du anger.</span><span class="sxs-lookup"><span data-stu-id="c6575-194">You can use the `New-ItemProperty` cmdlet to create values in a registry key that you specify.</span></span> <span data-ttu-id="c6575-195">I följande exempel skapas ett nytt DWORD-värde i register nyckeln ContosoCompany.</span><span class="sxs-lookup"><span data-stu-id="c6575-195">The following example creates a new DWORD value on the ContosoCompany registry key.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\ContosoCompany"
New-ItemProperty -Path  -Name Test -Type DWORD -Value 1
```

> [!NOTE]
> <span data-ttu-id="c6575-196">Läs avsnittet dynamiska parametrar i den här artikeln för andra tillåtna typ värden.</span><span class="sxs-lookup"><span data-stu-id="c6575-196">Review the dynamic parameters section in this article for other allowed type values.</span></span>

<span data-ttu-id="c6575-197">Detaljerad cmdlet-användning finns i [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span><span class="sxs-lookup"><span data-stu-id="c6575-197">For detailed cmdlet usage, see [New-ItemProperty](xref:Microsoft.PowerShell.Management.New-ItemProperty).</span></span>

## <a name="copying-registry-keys-and-values"></a><span data-ttu-id="c6575-198">Kopiera register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c6575-198">Copying registry keys and values</span></span>

<span data-ttu-id="c6575-199">I **Registry** -providern använder du `Copy-Item` cmdleten för att kopiera register nycklar och värden.</span><span class="sxs-lookup"><span data-stu-id="c6575-199">In the **Registry** provider, use the `Copy-Item` cmdlet copies registry keys and values.</span></span> <span data-ttu-id="c6575-200">Använd `Copy-ItemProperty` cmdleten för att endast kopiera register värden.</span><span class="sxs-lookup"><span data-stu-id="c6575-200">Use the `Copy-ItemProperty` cmdlet to copy registry values only.</span></span>
<span data-ttu-id="c6575-201">Följande kommando kopierar register nyckeln "contoso" och dess egenskaper till den angivna platsen "HKLM: \ Software\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="c6575-201">The following command copies the "Contoso" registry key, and its properties to the specified location "HKLM:\Software\Fabrikam".</span></span>

<span data-ttu-id="c6575-202">`Copy-Item` skapar mål nyckeln om den inte finns.</span><span class="sxs-lookup"><span data-stu-id="c6575-202">`Copy-Item` creates the destination key if it does not exist.</span></span> <span data-ttu-id="c6575-203">Om mål nyckeln finns `Copy-Item` skapar en dubblett av käll nyckeln som ett underordnat objekt (under nyckel) för mål nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c6575-203">If the destination key exists, `Copy-Item` creates a duplicate of the source key as a child item (subkey) of the destination key.</span></span>

```powershell
Copy-Item -Path  HKLM:\Software\Contoso -Destination HKLM:\Software\Fabrikam
```

<span data-ttu-id="c6575-204">Följande kommando använder `Copy-ItemProperty` cmdleten för att kopiera "Server"-värdet från "contoso"-nyckeln till "Fabrikam"-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c6575-204">The following command uses the `Copy-ItemProperty` cmdlet to copy the "Server" value from the "Contoso" key to the "Fabrikam" key.</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Copy-ItemProperty -Path $source -Destination $dest -Name Server
```

<span data-ttu-id="c6575-205">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-205">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c6575-206">Kopiera objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-206">Copy-Item</span></span>](xref:Microsoft.PowerShell.Management.Copy-Item)
- [<span data-ttu-id="c6575-207">Kopiera – ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-207">Copy-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Copy-ItemProperty)

## <a name="moving-registry-keys-and-values"></a><span data-ttu-id="c6575-208">Flytta register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c6575-208">Moving registry keys and values</span></span>

<span data-ttu-id="c6575-209">`Move-Item` `Move-ItemProperty` Cmdletarna och beter sig som deras "kopiering"-motsvarigheter.</span><span class="sxs-lookup"><span data-stu-id="c6575-209">The `Move-Item` and `Move-ItemProperty` cmdlets behave like their "Copy" counterparts.</span></span> <span data-ttu-id="c6575-210">Om målet finns `Move-Item` flyttar käll nyckeln under mål nyckeln.</span><span class="sxs-lookup"><span data-stu-id="c6575-210">If the destination exists, `Move-Item` moves the source key underneath the destination key.</span></span> <span data-ttu-id="c6575-211">Om mål nyckeln inte finns, flyttas käll nyckeln till mål Sök vägen.</span><span class="sxs-lookup"><span data-stu-id="c6575-211">If the destination key does not exist, the source key is moved to the destination path.</span></span>

<span data-ttu-id="c6575-212">Följande kommando flyttar "contoso"-nyckeln till sökvägen "HKLM: \ SOFTWARE\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="c6575-212">The following command moves the "Contoso" key to the path "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
Move-Item -Path HKLM:\SOFTWARE\Contoso -Destination HKLM:\SOFTWARE\Fabrikam
```

<span data-ttu-id="c6575-213">Detta kommando flyttar alla egenskaper från "HKLM: \ SOFTWARE\ContosoCompany" till "HKLM: \ SOFTWARE\Fabrikam".</span><span class="sxs-lookup"><span data-stu-id="c6575-213">This command moves all of the properties from "HKLM:\SOFTWARE\ContosoCompany" to "HKLM:\SOFTWARE\Fabrikam".</span></span>

```powershell
$source = "HKLM:\SOFTWARE\Contoso"
$dest = "HKLM:\SOFTWARE\Fabrikam"
Move-ItemProperty -Path $source -Destination $dest -Name *
```

<span data-ttu-id="c6575-214">Mer information om de cmdlets som används i det här avsnittet finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-214">For more information on the cmdlets used in this section, see the following articles.</span></span>

- [<span data-ttu-id="c6575-215">Flytta objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-215">Move-Item</span></span>](xref:Microsoft.PowerShell.Management.Move-Item)
- [<span data-ttu-id="c6575-216">Move-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-216">Move-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Move-ItemProperty)

## <a name="renaming-registry-keys-and-values"></a><span data-ttu-id="c6575-217">Byta namn på register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c6575-217">Renaming registry keys and values</span></span>

<span data-ttu-id="c6575-218">Du kan byta namn på register nycklar och värden precis som du skulle göra med filer och mappar.</span><span class="sxs-lookup"><span data-stu-id="c6575-218">You can rename registry keys and values just like you would files and folders.</span></span>
<span data-ttu-id="c6575-219">`Rename-Item` byter namn på register nycklar och `Rename-ItemProperty` byter namn på register värden.</span><span class="sxs-lookup"><span data-stu-id="c6575-219">`Rename-Item` renames registry keys, while `Rename-ItemProperty` renames registry values.</span></span>

```powershell
$path = "HKLM:\SOFTWARE\Contoso"
Rename-ItemProperty -Path $path -Name ContosoTest -NewName FabrikamTest
Rename-Item -Path $path -NewName Fabrikam
```

## <a name="changing-security-descriptors"></a><span data-ttu-id="c6575-220">Ändra säkerhets beskrivningar</span><span class="sxs-lookup"><span data-stu-id="c6575-220">Changing security descriptors</span></span>

<span data-ttu-id="c6575-221">Du kan begränsa åtkomsten till register nycklar med hjälp av `Get-Acl` `Set-Acl` cmdletarna och.</span><span class="sxs-lookup"><span data-stu-id="c6575-221">You can restrict access to registry keys using the `Get-Acl` and `Set-Acl` cmdlets.</span></span> <span data-ttu-id="c6575-222">I följande exempel läggs en ny användare till med fullständig behörighet till register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="c6575-222">The following example adds a new user with full control to the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
$acl = Get-Acl -Path HKLM:\SOFTWARE\Contoso
$rule = New-Object System.Security.AccessControl.RegistryAccessRule `
("CONTOSO\jsmith", "FullControl", "Allow")
$acl.SetAccessRule($rule)
$acl | Set-Acl -Path HKLM:\SOFTWARE\Contoso
```

<span data-ttu-id="c6575-223">Fler exempel och information om cmdlet-användning finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-223">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c6575-224">Get-ACL</span><span class="sxs-lookup"><span data-stu-id="c6575-224">Get-Acl</span></span>](xref:Microsoft.PowerShell.Security.Get-Acl)
- [<span data-ttu-id="c6575-225">Ange ACL</span><span class="sxs-lookup"><span data-stu-id="c6575-225">Set-Acl</span></span>](xref:Microsoft.PowerShell.Security.Set-Acl)

## <a name="removing-and-clearing-registry-keys-and-values"></a><span data-ttu-id="c6575-226">Ta bort och rensa register nycklar och värden</span><span class="sxs-lookup"><span data-stu-id="c6575-226">Removing and clearing registry keys and values</span></span>

<span data-ttu-id="c6575-227">Du kan ta bort objekt som finns med hjälp av **Remove-item**, men du uppmanas att bekräfta borttagningen om objektet innehåller något annat.</span><span class="sxs-lookup"><span data-stu-id="c6575-227">You can remove contained items by using **Remove-Item**, but you will be prompted to confirm the removal if the item contains anything else.</span></span> <span data-ttu-id="c6575-228">Följande exempel försöker ta bort en nyckel "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="c6575-228">The following example attempts to delete a key "HKLM:\SOFTWARE\Contoso".</span></span>

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

<span data-ttu-id="c6575-229">Om du vill ta bort de objekt som finns utan att göra det anger du `-Recurse` parametern.</span><span class="sxs-lookup"><span data-stu-id="c6575-229">To delete contained items without prompting, specify the `-Recurse` parameter.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso -Recurse
```

<span data-ttu-id="c6575-230">Om du vill ta bort alla objekt inom "HKLM: \ SOFTWARE\Contoso" men inte "HKLM: \ SOFTWARE\Contoso", använder du ett avslutande omvänt snedstreck `\` följt av ett jokertecken.</span><span class="sxs-lookup"><span data-stu-id="c6575-230">If you wanted to remove all items within "HKLM:\SOFTWARE\Contoso" but not "HKLM:\SOFTWARE\Contoso" itself, use a trailing backslash `\` followed by a wildcard.</span></span>

```powershell
Remove-Item -Path HKLM:\SOFTWARE\Contoso\* -Recurse
```

<span data-ttu-id="c6575-231">Det här kommandot tar bort registervärdet "ContosoTest" från register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="c6575-231">This command deletes the "ContosoTest" registry value from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Contoso -Name ContosoTest
```

<span data-ttu-id="c6575-232">`Clear-Item` tar bort alla register värden för en nyckel.</span><span class="sxs-lookup"><span data-stu-id="c6575-232">`Clear-Item` clears all registry values for a key.</span></span> <span data-ttu-id="c6575-233">I följande exempel rensas alla värden från register nyckeln "HKLM: \ SOFTWARE\Contoso".</span><span class="sxs-lookup"><span data-stu-id="c6575-233">The following example clears all values from the "HKLM:\SOFTWARE\Contoso" registry key.</span></span> <span data-ttu-id="c6575-234">Om du bara vill rensa en speciell egenskap använder du `Clear-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="c6575-234">To clear only a specific property, use `Clear-ItemProperty`.</span></span>

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

<span data-ttu-id="c6575-235">Fler exempel och information om cmdlet-användning finns i följande artiklar.</span><span class="sxs-lookup"><span data-stu-id="c6575-235">For more examples and cmdlet usage details see the following articles.</span></span>

- [<span data-ttu-id="c6575-236">Rensa objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-236">Clear-Item</span></span>](xref:Microsoft.PowerShell.Management.Clear-Item)
- [<span data-ttu-id="c6575-237">Clear-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-237">Clear-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Clear-ItemProperty)
- [<span data-ttu-id="c6575-238">Ta bort objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-238">Remove-Item</span></span>](xref:Microsoft.PowerShell.Management.Remove-Item)
- [<span data-ttu-id="c6575-239">Remove-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-239">Remove-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Remove-ItemProperty)

## <a name="dynamic-parameters"></a><span data-ttu-id="c6575-240">Dynamiska parametrar</span><span class="sxs-lookup"><span data-stu-id="c6575-240">Dynamic parameters</span></span>

<span data-ttu-id="c6575-241">Dynamiska parametrar är cmdlet-parametrar som läggs till av en PowerShell-Provider och är bara tillgängliga när cmdleten används i den provider-aktiverade enheten.</span><span class="sxs-lookup"><span data-stu-id="c6575-241">Dynamic parameters are cmdlet parameters that are added by a PowerShell provider and are available only when the cmdlet is being used in the provider-enabled drive.</span></span>

### <a name="type-microsoftwin32registryvaluekind"></a><span data-ttu-id="c6575-242">Skriv <Microsoft. Win32. RegistryValueKind></span><span class="sxs-lookup"><span data-stu-id="c6575-242">Type <Microsoft.Win32.RegistryValueKind></span></span>

<span data-ttu-id="c6575-243">Skapar eller ändrar data typen för ett register värde.</span><span class="sxs-lookup"><span data-stu-id="c6575-243">Establishes or changes the data type of a registry value.</span></span> <span data-ttu-id="c6575-244">Standardvärdet är `String` (REG_SZ).</span><span class="sxs-lookup"><span data-stu-id="c6575-244">The default is `String` (REG_SZ).</span></span>

<span data-ttu-id="c6575-245">Den här parametern fungerar som den är utformad på cmdleten [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) .</span><span class="sxs-lookup"><span data-stu-id="c6575-245">This parameter works as designed on the [Set-ItemProperty](xref:Microsoft.PowerShell.Management.Set-ItemProperty) cmdlet.</span></span> <span data-ttu-id="c6575-246">Den är också tillgänglig på cmdleten [set-item](xref:Microsoft.PowerShell.Management.Set-Item) i register enheterna, men den har ingen påverkan.</span><span class="sxs-lookup"><span data-stu-id="c6575-246">It is also available on the [Set-Item](xref:Microsoft.PowerShell.Management.Set-Item) cmdlet in the registry drives, but it has no effect.</span></span>

|<span data-ttu-id="c6575-247">Värde</span><span class="sxs-lookup"><span data-stu-id="c6575-247">Value</span></span> | <span data-ttu-id="c6575-248">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c6575-248">Description</span></span> |
| ---- | ----------- |
| `String` | <span data-ttu-id="c6575-249">Anger en null-avslutad sträng.</span><span class="sxs-lookup"><span data-stu-id="c6575-249">Specifies a null-terminated string.</span></span> <span data-ttu-id="c6575-250">Motsvarar REG_SZ.</span><span class="sxs-lookup"><span data-stu-id="c6575-250">Equivalent to REG_SZ.</span></span> |
| `ExpandString` | <span data-ttu-id="c6575-251">Anger en null-avslutad sträng som innehåller expanderad</span><span class="sxs-lookup"><span data-stu-id="c6575-251">Specifies a null-terminated string that contains unexpanded</span></span> |
|                | <span data-ttu-id="c6575-252">referenser till miljövariabler som expanderas när</span><span class="sxs-lookup"><span data-stu-id="c6575-252">references to environment variables that are expanded when</span></span> |
|                | <span data-ttu-id="c6575-253">Värdet hämtas.</span><span class="sxs-lookup"><span data-stu-id="c6575-253">the value is retrieved.</span></span> <span data-ttu-id="c6575-254">Motsvarar REG_EXPAND_SZ.</span><span class="sxs-lookup"><span data-stu-id="c6575-254">Equivalent to REG_EXPAND_SZ.</span></span> |
| `Binary` | <span data-ttu-id="c6575-255">Anger binära data i alla former.</span><span class="sxs-lookup"><span data-stu-id="c6575-255">Specifies binary data in any form.</span></span> <span data-ttu-id="c6575-256">Motsvarar REG_BINARY.</span><span class="sxs-lookup"><span data-stu-id="c6575-256">Equivalent to REG_BINARY.</span></span> |
| `DWord` | <span data-ttu-id="c6575-257">Anger ett 32-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="c6575-257">Specifies a 32-bit binary number.</span></span> <span data-ttu-id="c6575-258">Motsvarar REG_DWORD.</span><span class="sxs-lookup"><span data-stu-id="c6575-258">Equivalent to REG_DWORD.</span></span> |
| `MultiString` | <span data-ttu-id="c6575-259">Anger en matris med null-terminerade strängar som avslut ATS av</span><span class="sxs-lookup"><span data-stu-id="c6575-259">Specifies an array of null-terminated strings terminated by</span></span> |
|               | <span data-ttu-id="c6575-260">två NULL-tecken.</span><span class="sxs-lookup"><span data-stu-id="c6575-260">two null characters.</span></span> <span data-ttu-id="c6575-261">Motsvarar REG_MULTI_SZ.</span><span class="sxs-lookup"><span data-stu-id="c6575-261">Equivalent to REG_MULTI_SZ.</span></span> |
| `QWord` | <span data-ttu-id="c6575-262">Anger ett 64-bitars binärt tal.</span><span class="sxs-lookup"><span data-stu-id="c6575-262">Specifies a 64-bit binary number.</span></span> <span data-ttu-id="c6575-263">Motsvarar REG_QWORD.</span><span class="sxs-lookup"><span data-stu-id="c6575-263">Equivalent to REG_QWORD.</span></span> |
| `Unknown` | <span data-ttu-id="c6575-264">Anger en register data typ som inte stöds, till exempel</span><span class="sxs-lookup"><span data-stu-id="c6575-264">Indicates an unsupported registry data type, such as</span></span> |
|           | <span data-ttu-id="c6575-265">REG_RESOURCE_LIST.</span><span class="sxs-lookup"><span data-stu-id="c6575-265">REG_RESOURCE_LIST.</span></span> |

#### <a name="cmdlets-supported"></a><span data-ttu-id="c6575-266">Cmdlets som stöds</span><span class="sxs-lookup"><span data-stu-id="c6575-266">Cmdlets supported</span></span>

- [<span data-ttu-id="c6575-267">Ange objekt</span><span class="sxs-lookup"><span data-stu-id="c6575-267">Set-Item</span></span>](xref:Microsoft.PowerShell.Management.Set-Item)
- [<span data-ttu-id="c6575-268">Set-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="c6575-268">Set-ItemProperty</span></span>](xref:Microsoft.PowerShell.Management.Set-ItemProperty)

## <a name="using-the-pipeline"></a><span data-ttu-id="c6575-269">Använda pipelinen</span><span class="sxs-lookup"><span data-stu-id="c6575-269">Using the pipeline</span></span>

<span data-ttu-id="c6575-270">Provider-cmdletar accepterar pipeline-ininformation.</span><span class="sxs-lookup"><span data-stu-id="c6575-270">Provider cmdlets accept pipeline input.</span></span> <span data-ttu-id="c6575-271">Du kan använda pipelinen för att förenkla uppgiften genom att skicka leverantörs data från en cmdlet till en annan provider-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c6575-271">You can use the pipeline to simplify task by sending provider data from one cmdlet to another provider cmdlet.</span></span> <span data-ttu-id="c6575-272">Mer information om hur du använder pipelinen med Provider-cmdletar finns i cmdlet-referenser som finns i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="c6575-272">To read more about how to use the pipeline with provider cmdlets, see the cmdlet references provided throughout this article.</span></span>

## <a name="getting-help"></a><span data-ttu-id="c6575-273">Få hjälp</span><span class="sxs-lookup"><span data-stu-id="c6575-273">Getting help</span></span>

<span data-ttu-id="c6575-274">Från och med Windows PowerShell 3,0 kan du hämta anpassade hjälp avsnitt för provider-cmdletar som förklarar hur dessa cmdletar fungerar i en fil systemen het.</span><span class="sxs-lookup"><span data-stu-id="c6575-274">Beginning in Windows PowerShell 3.0, you can get customized help topics for provider cmdlets that explain how those cmdlets behave in a file system drive.</span></span>

<span data-ttu-id="c6575-275">Om du vill få hjälp avsnitten som är anpassade för fil system enheten kör du ett `Get-Help` kommando i en fil system enhet eller använder parametern **Path** för att ange en fil system enhet.</span><span class="sxs-lookup"><span data-stu-id="c6575-275">To get the help topics that are customized for the file system drive, run a `Get-Help` command in a file system drive or use the **Path** parameter to specify a file system drive.</span></span>

```powershell
Get-Help Get-ChildItem
```

```powershell
Get-Help Get-ChildItem -Path HKLM:
```

## <a name="see-also"></a><span data-ttu-id="c6575-276">Se även</span><span class="sxs-lookup"><span data-stu-id="c6575-276">See also</span></span>

 [<span data-ttu-id="c6575-277">about_Providers</span><span class="sxs-lookup"><span data-stu-id="c6575-277">about_Providers</span></span>](../About/about_Providers.md)

