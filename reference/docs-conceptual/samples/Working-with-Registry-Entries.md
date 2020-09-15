---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Arbeta med registerposter
ms.openlocfilehash: 7f8ee87cebb8b220570bcb969445071a72a68526
ms.sourcegitcommit: d3f78120bdc9096c72aa0dfdbdd91efaf254c738
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/04/2020
ms.locfileid: "87758490"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="05cb1-103">Arbeta med registerposter</span><span class="sxs-lookup"><span data-stu-id="05cb1-103">Working with Registry Entries</span></span>

<span data-ttu-id="05cb1-104">Eftersom register poster är egenskaper för nycklar och inte kan bläddras direkt, måste vi ta en något annorlunda metod när du arbetar med dem.</span><span class="sxs-lookup"><span data-stu-id="05cb1-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="05cb1-105">Visar register poster</span><span class="sxs-lookup"><span data-stu-id="05cb1-105">Listing Registry Entries</span></span>

<span data-ttu-id="05cb1-106">Det finns många olika sätt att undersöka register poster.</span><span class="sxs-lookup"><span data-stu-id="05cb1-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="05cb1-107">Det enklaste sättet är att hämta egenskaps namnen som är associerade med en nyckel.</span><span class="sxs-lookup"><span data-stu-id="05cb1-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="05cb1-108">Om du till exempel vill se namnen på posterna i register nyckeln använder du `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion` `Get-Item` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="05cb1-109">Register nycklar har en egenskap med det generiska namnet "Property" som är en lista över register poster i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="05cb1-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="05cb1-110">Följande kommando väljer egenskapen egenskap och utökar objekten så att de visas i en lista:</span><span class="sxs-lookup"><span data-stu-id="05cb1-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```powershell
Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion |
  Select-Object -ExpandProperty Property
```

```Output
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="05cb1-111">Om du vill visa register posterna i en mer läsbar form använder du `Get-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="05cb1-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

```powershell
Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

```Output
PSPath              : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows\CurrentVersion
PSParentPath        : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SO
                      FTWARE\Microsoft\Windows
PSChildName         : CurrentVersion
PSDrive             : HKLM
PSProvider          : Microsoft.PowerShell.Core\Registry
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
CommonFilesDir      : C:\Program Files\Common Files
ProductId           : 76487-338-1167776-22465
WallPaperDir        : C:\WINDOWS\Web\Wallpaper
MediaPath           : C:\WINDOWS\Media
ProgramFilesPath    : C:\Program Files
PF_AccessoriesName  : Accessories
(default)           :
```

<span data-ttu-id="05cb1-112">Windows PowerShell-relaterade egenskaper för nyckeln föregås av "PS", till exempel **PSPath**, **PSParentPath**, **PSChildName**och **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="05cb1-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="05cb1-113">Du kan använda `*.*` notationen för att referera till den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="05cb1-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="05cb1-114">Du kan använda `Set-Location` för att ändra till **CurrentVersion** -registerposten först:</span><span class="sxs-lookup"><span data-stu-id="05cb1-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="05cb1-115">Du kan också använda den inbyggda HKLM-PSDrive med `Set-Location` :</span><span class="sxs-lookup"><span data-stu-id="05cb1-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="05cb1-116">Du kan sedan använda `*.*` notationen för den aktuella platsen för att lista egenskaperna utan att ange en fullständig sökväg:</span><span class="sxs-lookup"><span data-stu-id="05cb1-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

```powershell
Get-ItemProperty -Path .
```

```Output
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="05cb1-117">Ökning av sökvägar fungerar på samma sätt som i fil systemet, så från den här platsen kan du hämta **ItemProperty** -listan för `HKLM:\SOFTWARE\Microsoft\Windows\Help` med hjälp av `Get-ItemProperty -Path ..\Help` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="05cb1-118">Hämta en enskild register post</span><span class="sxs-lookup"><span data-stu-id="05cb1-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="05cb1-119">Om du vill hämta en speciell post i en register nyckel kan du använda en av flera olika metoder.</span><span class="sxs-lookup"><span data-stu-id="05cb1-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="05cb1-120">Det här exemplet hittar värdet för **DevicePath** i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="05cb1-121">Med hjälp av använder `Get-ItemProperty` du parametern **Path** för att ange namnet på nyckeln och parametern **Name** för att ange namnet på **DevicePath** -posten.</span><span class="sxs-lookup"><span data-stu-id="05cb1-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```powershell
Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath
```

```Output
PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="05cb1-122">Det här kommandot returnerar standard egenskaperna för Windows PowerShell och egenskapen **DevicePath** .</span><span class="sxs-lookup"><span data-stu-id="05cb1-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="05cb1-123">Även om `Get-ItemProperty` har parametrarna **filter**, **include**och **exclude** kan de inte användas för att filtrera efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="05cb1-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="05cb1-124">De här parametrarna avser register nycklar, som är objekt Sök vägar och inte register poster, som är objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="05cb1-124">These parameters refer to registry keys, which are item paths and not registry entries, which are item properties.</span></span>

<span data-ttu-id="05cb1-125">Ett annat alternativ är att använda kommando rads verktyget Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="05cb1-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="05cb1-126">Om du behöver hjälp med reg.exe skriver du `reg.exe /?` i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="05cb1-126">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="05cb1-127">Använd reg.exe som du ser i följande kommando för att hitta DevicePath-posten:</span><span class="sxs-lookup"><span data-stu-id="05cb1-127">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="05cb1-128">Du kan också använda **WshShell** com-objektet även för att hitta vissa register poster, även om den här metoden inte fungerar med stora binära data eller med register post namn som innehåller tecken som " \\ ").</span><span class="sxs-lookup"><span data-stu-id="05cb1-128">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="05cb1-129">Lägg till egenskaps namnet i objekt Sök vägen med en \\ avgränsare:</span><span class="sxs-lookup"><span data-stu-id="05cb1-129">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="05cb1-130">Ange en enskild register post</span><span class="sxs-lookup"><span data-stu-id="05cb1-130">Setting a Single Registry Entry</span></span>

<span data-ttu-id="05cb1-131">Om du vill ändra en speciell post i en register nyckel kan du använda en av flera olika metoder.</span><span class="sxs-lookup"><span data-stu-id="05cb1-131">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="05cb1-132">I det här exemplet ändras **Sök vägs** posten under `HKEY_CURRENT_USER\Environment` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-132">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="05cb1-133">I **Sök vägs** posten anges var du hittar körbara filer.</span><span class="sxs-lookup"><span data-stu-id="05cb1-133">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="05cb1-134">Hämta det aktuella värdet för **Sök vägs** posten med hjälp av `Get-ItemProperty` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-134">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="05cb1-135">Lägg till det nya värdet och skilj det till ett `;` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-135">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="05cb1-136">Använd `Set-ItemProperty` med den angivna nyckeln, post namnet och värdet för att ändra register posten.</span><span class="sxs-lookup"><span data-stu-id="05cb1-136">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="05cb1-137">Även om `Set-ItemProperty` har parametrarna **filter**, **include**och **exclude** kan de inte användas för att filtrera efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="05cb1-137">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="05cb1-138">Dessa parametrar avser register nycklar, som är objekt Sök vägar, och inte register poster, som är objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="05cb1-138">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="05cb1-139">Ett annat alternativ är att använda kommando rads verktyget Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="05cb1-139">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="05cb1-140">Om du behöver hjälp med reg.exe skriver du **reg.exe/?**</span><span class="sxs-lookup"><span data-stu-id="05cb1-140">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="05cb1-141">i en kommando tolk.</span><span class="sxs-lookup"><span data-stu-id="05cb1-141">at a command prompt.</span></span>

<span data-ttu-id="05cb1-142">I följande exempel ändras **Sök vägs** posten genom att du tar bort sökvägen som lagts till i exemplet ovan.</span><span class="sxs-lookup"><span data-stu-id="05cb1-142">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="05cb1-143">`Get-ItemProperty` används fortfarande för att hämta det aktuella värdet för att undvika att behöva parsa strängen som returnerades från `reg query` .</span><span class="sxs-lookup"><span data-stu-id="05cb1-143">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="05cb1-144">**Substring** -och **LastIndexOf** -metoderna används för att hämta den senaste sökvägen som lagts till i **Sök vägs** posten.</span><span class="sxs-lookup"><span data-stu-id="05cb1-144">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="05cb1-145">Skapa nya register poster</span><span class="sxs-lookup"><span data-stu-id="05cb1-145">Creating New Registry Entries</span></span>

<span data-ttu-id="05cb1-146">Om du vill lägga till en ny post med namnet "PowerShellPath" i **CurrentVersion** -nyckeln använder du `New-ItemProperty` sökvägen till nyckeln, post namnet och värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="05cb1-146">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="05cb1-147">I det här exemplet tar vi värdet för Windows PowerShell-variabeln `$PSHome` som lagrar sökvägen till installations katalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="05cb1-147">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="05cb1-148">Du kan lägga till den nya posten i nyckeln med hjälp av följande kommando, och kommandot returnerar också information om den nya posten:</span><span class="sxs-lookup"><span data-stu-id="05cb1-148">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

```Output
PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="05cb1-149">**PropertyType** måste vara namnet på en **Microsoft. Win32. RegistryValueKind** -uppräknings medlem från följande tabell:</span><span class="sxs-lookup"><span data-stu-id="05cb1-149">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="05cb1-150">PropertyType-värde</span><span class="sxs-lookup"><span data-stu-id="05cb1-150">PropertyType Value</span></span>|<span data-ttu-id="05cb1-151">Innebörd</span><span class="sxs-lookup"><span data-stu-id="05cb1-151">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="05cb1-152">Binär</span><span class="sxs-lookup"><span data-stu-id="05cb1-152">Binary</span></span>|<span data-ttu-id="05cb1-153">Binära data</span><span class="sxs-lookup"><span data-stu-id="05cb1-153">Binary data</span></span>|
|<span data-ttu-id="05cb1-154">DWord</span><span class="sxs-lookup"><span data-stu-id="05cb1-154">DWord</span></span>|<span data-ttu-id="05cb1-155">Ett tal som är en giltig UInt32</span><span class="sxs-lookup"><span data-stu-id="05cb1-155">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="05cb1-156">ExpandString</span><span class="sxs-lookup"><span data-stu-id="05cb1-156">ExpandString</span></span>|<span data-ttu-id="05cb1-157">En sträng som kan innehålla miljövariabler som expanderas dynamiskt</span><span class="sxs-lookup"><span data-stu-id="05cb1-157">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="05cb1-158">Multisträng</span><span class="sxs-lookup"><span data-stu-id="05cb1-158">MultiString</span></span>|<span data-ttu-id="05cb1-159">En flerradig sträng</span><span class="sxs-lookup"><span data-stu-id="05cb1-159">A multiline string</span></span>|
|<span data-ttu-id="05cb1-160">Sträng</span><span class="sxs-lookup"><span data-stu-id="05cb1-160">String</span></span>|<span data-ttu-id="05cb1-161">Valfritt sträng värde</span><span class="sxs-lookup"><span data-stu-id="05cb1-161">Any string value</span></span>|
|<span data-ttu-id="05cb1-162">QWord</span><span class="sxs-lookup"><span data-stu-id="05cb1-162">QWord</span></span>|<span data-ttu-id="05cb1-163">8 byte binära data</span><span class="sxs-lookup"><span data-stu-id="05cb1-163">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="05cb1-164">Du kan lägga till en register post till flera platser genom att ange en matris med värden för parametern **Path** :</span><span class="sxs-lookup"><span data-stu-id="05cb1-164">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="05cb1-165">Du kan också skriva över ett befintligt register post värde genom att lägga till **Force** -parametern i alla `New-ItemProperty` kommandon.</span><span class="sxs-lookup"><span data-stu-id="05cb1-165">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="05cb1-166">Byta namn på register poster</span><span class="sxs-lookup"><span data-stu-id="05cb1-166">Renaming Registry Entries</span></span>

<span data-ttu-id="05cb1-167">Om du vill byta namn på posten **PowerShellPath** till "PSHome" använder du `Rename-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="05cb1-167">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="05cb1-168">Om du vill visa det omdöpta värdet lägger du till parametern **Passthru** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="05cb1-168">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="05cb1-169">Tar bort register poster</span><span class="sxs-lookup"><span data-stu-id="05cb1-169">Deleting Registry Entries</span></span>

<span data-ttu-id="05cb1-170">Om du vill ta bort register posterna PSHome och PowerShellPath använder du `Remove-ItemProperty` :</span><span class="sxs-lookup"><span data-stu-id="05cb1-170">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
