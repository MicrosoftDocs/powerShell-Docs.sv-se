---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med registerposter
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: 667d17d0d62745a27ffef5f1912336b72f74c2a9
ms.sourcegitcommit: 806cf87488b80800b9f50a8af286e8379519a034
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2019
ms.locfileid: "59293086"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="3c91f-103">Arbeta med registerposter</span><span class="sxs-lookup"><span data-stu-id="3c91f-103">Working with Registry Entries</span></span>

<span data-ttu-id="3c91f-104">Eftersom registerposter är egenskaper för nycklar och därför kan inte direkt sökas, behöver vi dra ett något annat sätt när du arbetar med dem.</span><span class="sxs-lookup"><span data-stu-id="3c91f-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="3c91f-105">Visa en lista över registerposter</span><span class="sxs-lookup"><span data-stu-id="3c91f-105">Listing Registry Entries</span></span>

<span data-ttu-id="3c91f-106">Det finns många olika sätt att undersöka registerposter.</span><span class="sxs-lookup"><span data-stu-id="3c91f-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="3c91f-107">Det enklaste sättet är att få de kolumner som är associerade med en nyckel.</span><span class="sxs-lookup"><span data-stu-id="3c91f-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="3c91f-108">Till exempel vill visa namnen på de posterna i registernyckeln `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, använda `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="3c91f-109">Registernycklar har en egenskap med samlingsnamnet ”Property” som är en lista över registerposter i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="3c91f-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="3c91f-110">Följande kommando väljer egenskapen egenskapen och utökar objekt så att de visas i en lista:</span><span class="sxs-lookup"><span data-stu-id="3c91f-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

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

<span data-ttu-id="3c91f-111">Du kan visa registerposterna i ett mer lättläst format `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="3c91f-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

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

<span data-ttu-id="3c91f-112">Windows PowerShell-relaterade egenskaperna för nyckeln har alla prefixet ”PS”, till exempel **PSPath**, **PSParentPath**, **PSChildName**, och **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="3c91f-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="3c91f-113">Du kan använda den `*.*` notation för att referera till den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="3c91f-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="3c91f-114">Du kan använda `Set-Location` att ändra till den **CurrentVersion** container registry första:</span><span class="sxs-lookup"><span data-stu-id="3c91f-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3c91f-115">Du kan också använda den inbyggda HKLM PSDrive med `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="3c91f-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3c91f-116">Du kan sedan använda den `*.*` notation för den aktuella platsen om du vill visa egenskaperna utan att ange en fullständig sökväg:</span><span class="sxs-lookup"><span data-stu-id="3c91f-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

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

<span data-ttu-id="3c91f-117">Sökvägen expansion fungerar på samma sätt som i filsystem, så från den här platsen kan du hämta den **itemproperty-egenskap** för `HKLM:\SOFTWARE\Microsoft\Windows\Help` med hjälp av `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="3c91f-118">Hämta en enda registerpost</span><span class="sxs-lookup"><span data-stu-id="3c91f-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="3c91f-119">Om du vill hämta en viss post i en registernyckel, kan du använda någon av flera möjliga metoder.</span><span class="sxs-lookup"><span data-stu-id="3c91f-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3c91f-120">Det här exemplet efter värdet för **DevicePath** i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="3c91f-121">Med hjälp av `Get-ItemProperty`, använda den **sökväg** parametern för att ange namnet på nyckeln, och **namn** parametern för att ange namnet på den **DevicePath** posten.</span><span class="sxs-lookup"><span data-stu-id="3c91f-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="3c91f-122">Det här kommandot returnerar standardegenskaper för Windows PowerShell och **DevicePath** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="3c91f-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="3c91f-123">Även om `Get-ItemProperty` har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="3c91f-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3c91f-124">De här parametrarna avser registernycklar som är objektet sökvägar och inte registerposter.</span><span class="sxs-lookup"><span data-stu-id="3c91f-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="3c91f-125">Registerposter som är egenskaper för konfigurationsobjekt.</span><span class="sxs-lookup"><span data-stu-id="3c91f-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="3c91f-126">Ett annat alternativ är att använda kommandoradsverktyget Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="3c91f-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3c91f-127">Om du vill ha hjälp med reg.exe skriver `reg.exe /?` i Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="3c91f-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="3c91f-128">Använd reg.exe för att hitta posten DevicePath, som visas i följande kommando:</span><span class="sxs-lookup"><span data-stu-id="3c91f-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="3c91f-129">Du kan också använda den **WshShell** COM-objekt samt att hitta vissa registerposter, även om den här metoden inte fungerar med stora binära data eller med namn på registret poster som innehåller tecken, till exempel ”\\”).</span><span class="sxs-lookup"><span data-stu-id="3c91f-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="3c91f-130">Lägg till egenskapsnamnet till objekt-sökväg med en \\ avgränsare:</span><span class="sxs-lookup"><span data-stu-id="3c91f-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="3c91f-131">Ange en enda registerpost</span><span class="sxs-lookup"><span data-stu-id="3c91f-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="3c91f-132">Om du vill ändra en viss post i en registernyckel, kan du använda någon av flera möjliga metoder.</span><span class="sxs-lookup"><span data-stu-id="3c91f-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="3c91f-133">Det här exemplet ändrar den **sökväg** posten under `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="3c91f-134">Den **sökväg** posten anger var du hittar körbara filer.</span><span class="sxs-lookup"><span data-stu-id="3c91f-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="3c91f-135">Hämta det aktuella värdet för den **sökväg** post med hjälp av `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="3c91f-136">Lägg till det nya värdet, att avgränsa dem med en `;`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="3c91f-137">Använd `Set-ItemProperty` med angiven nyckel, postens namn och värde för att ändra registerposten.</span><span class="sxs-lookup"><span data-stu-id="3c91f-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="3c91f-138">Även om `Set-ItemProperty` har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="3c91f-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="3c91f-139">De här parametrarna avser registernycklar, som är objektet sökvägar – och inte registerposter – som är egenskaper för konfigurationsobjekt.</span><span class="sxs-lookup"><span data-stu-id="3c91f-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="3c91f-140">Ett annat alternativ är att använda kommandoradsverktyget Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="3c91f-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="3c91f-141">Om du vill ha hjälp med reg.exe skriver **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="3c91f-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="3c91f-142">i Kommandotolken.</span><span class="sxs-lookup"><span data-stu-id="3c91f-142">at a command prompt.</span></span>

<span data-ttu-id="3c91f-143">Följande exempel ändringar i **sökväg** post genom att ta bort sökvägen som har lagts till i exemplet ovan.</span><span class="sxs-lookup"><span data-stu-id="3c91f-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
`Get-ItemProperty` <span data-ttu-id="3c91f-144">fortfarande används för att hämta det aktuella värdet för att undvika att behöva Parsar då strängen som returnerades från `reg query`.</span><span class="sxs-lookup"><span data-stu-id="3c91f-144">is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="3c91f-145">Den **delsträngen** och **LastIndexOf** metoder används för att hämta den senaste sökvägen som lagts till i den **sökväg** posten.</span><span class="sxs-lookup"><span data-stu-id="3c91f-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="3c91f-146">Skapar nya registerposter</span><span class="sxs-lookup"><span data-stu-id="3c91f-146">Creating New Registry Entries</span></span>

<span data-ttu-id="3c91f-147">Att lägga till en ny post med namnet ”PowerShellPath” i den **CurrentVersion** , nyckelanvändningen `New-ItemProperty` med sökvägen till nyckeln, namnet och värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="3c91f-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="3c91f-148">I det här exemplet tar vi värdet för Windows PowerShell-variabel `$PSHome`, som lagrar sökvägen till installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="3c91f-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="3c91f-149">Du kan lägga till den nya posten till nyckeln med hjälp av följande kommando och kommandot returnerar också information om den nya posten:</span><span class="sxs-lookup"><span data-stu-id="3c91f-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="3c91f-150">Den **%d{PropertyType/** måste vara namnet på en **Microsoft.Win32.RegistryValueKind** uppräkningsmedlem i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="3c91f-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="3c91f-151">%D{PropertyType/ värde</span><span class="sxs-lookup"><span data-stu-id="3c91f-151">PropertyType Value</span></span>|<span data-ttu-id="3c91f-152">Innebörd</span><span class="sxs-lookup"><span data-stu-id="3c91f-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="3c91f-153">Binär</span><span class="sxs-lookup"><span data-stu-id="3c91f-153">Binary</span></span>|<span data-ttu-id="3c91f-154">Binära data</span><span class="sxs-lookup"><span data-stu-id="3c91f-154">Binary data</span></span>|
|<span data-ttu-id="3c91f-155">DWord</span><span class="sxs-lookup"><span data-stu-id="3c91f-155">DWord</span></span>|<span data-ttu-id="3c91f-156">Ett tal som är en giltig UInt32</span><span class="sxs-lookup"><span data-stu-id="3c91f-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="3c91f-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="3c91f-157">ExpandString</span></span>|<span data-ttu-id="3c91f-158">En sträng som kan innehålla miljövariabler som dynamiskt expanderas</span><span class="sxs-lookup"><span data-stu-id="3c91f-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="3c91f-159">MultiString</span><span class="sxs-lookup"><span data-stu-id="3c91f-159">MultiString</span></span>|<span data-ttu-id="3c91f-160">En flerradig sträng</span><span class="sxs-lookup"><span data-stu-id="3c91f-160">A multiline string</span></span>|
|<span data-ttu-id="3c91f-161">Sträng</span><span class="sxs-lookup"><span data-stu-id="3c91f-161">String</span></span>|<span data-ttu-id="3c91f-162">ett värde</span><span class="sxs-lookup"><span data-stu-id="3c91f-162">Any string value</span></span>|
|<span data-ttu-id="3c91f-163">QWord</span><span class="sxs-lookup"><span data-stu-id="3c91f-163">QWord</span></span>|<span data-ttu-id="3c91f-164">8 byte av binära data</span><span class="sxs-lookup"><span data-stu-id="3c91f-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="3c91f-165">Du kan lägga till en registerpost till flera platser genom att ange en matris med värden för den **sökväg** parameter:</span><span class="sxs-lookup"><span data-stu-id="3c91f-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="3c91f-166">Du kan också skriva över en befintlig post registervärdet genom att lägga till den **kraft** parametern till någon `New-ItemProperty` kommando.</span><span class="sxs-lookup"><span data-stu-id="3c91f-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="3c91f-167">Renaming Registry Entries</span><span class="sxs-lookup"><span data-stu-id="3c91f-167">Renaming Registry Entries</span></span>

<span data-ttu-id="3c91f-168">Att byta namn på den **PowerShellPath** posten ”PSHome”, Använd `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="3c91f-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="3c91f-169">Om du vill visa omdöpt värdet, lägger du till den **PassThru** parameter i kommandot.</span><span class="sxs-lookup"><span data-stu-id="3c91f-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="3c91f-170">Tar bort registerposter</span><span class="sxs-lookup"><span data-stu-id="3c91f-170">Deleting Registry Entries</span></span>

<span data-ttu-id="3c91f-171">Ta bort registerposter för både PSHome och PowerShellPath genom att använda `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="3c91f-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
