---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med registerposter
ms.openlocfilehash: c1fd6f57f13240eb2039f2d5756796678800aee0
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "67030730"
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="dc854-103">Arbeta med registerposter</span><span class="sxs-lookup"><span data-stu-id="dc854-103">Working with Registry Entries</span></span>

<span data-ttu-id="dc854-104">Eftersom register poster är egenskaper för nycklar och inte kan bläddras direkt, måste vi ta en något annorlunda metod när du arbetar med dem.</span><span class="sxs-lookup"><span data-stu-id="dc854-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

## <a name="listing-registry-entries"></a><span data-ttu-id="dc854-105">Visar register poster</span><span class="sxs-lookup"><span data-stu-id="dc854-105">Listing Registry Entries</span></span>

<span data-ttu-id="dc854-106">Det finns många olika sätt att undersöka register poster.</span><span class="sxs-lookup"><span data-stu-id="dc854-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="dc854-107">Det enklaste sättet är att hämta egenskaps namnen som är associerade med en nyckel.</span><span class="sxs-lookup"><span data-stu-id="dc854-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="dc854-108">Om du till exempel vill visa namnen på posterna i register nyckeln `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`använder du `Get-Item`.</span><span class="sxs-lookup"><span data-stu-id="dc854-108">For example, to see the names of the entries in the registry key `HKEY_LOCAL_MACHINE\Software\Microsoft\Windows\CurrentVersion`, use `Get-Item`.</span></span> <span data-ttu-id="dc854-109">Register nycklar har en egenskap med det generiska namnet "Property" som är en lista över register poster i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="dc854-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span>
<span data-ttu-id="dc854-110">Följande kommando väljer egenskapen egenskap och utökar objekten så att de visas i en lista:</span><span class="sxs-lookup"><span data-stu-id="dc854-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

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

<span data-ttu-id="dc854-111">Om du vill visa register posterna i en mer läsbar form använder du `Get-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="dc854-111">To view the registry entries in a more readable form, use `Get-ItemProperty`:</span></span>

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

<span data-ttu-id="dc854-112">Windows PowerShell-relaterade egenskaper för nyckeln föregås av "PS", till exempel **PSPath**, **PSParentPath**, **PSChildName**och **PSProvider**.</span><span class="sxs-lookup"><span data-stu-id="dc854-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="dc854-113">Du kan använda `*.*` notation för att referera till den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="dc854-113">You can use the `*.*` notation for referring to the current location.</span></span> <span data-ttu-id="dc854-114">Du kan använda `Set-Location` för att ändra till **CurrentVersion** -registerposten först:</span><span class="sxs-lookup"><span data-stu-id="dc854-114">You can use `Set-Location` to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="dc854-115">Du kan också använda den inbyggda HKLM-PSDrive med `Set-Location`:</span><span class="sxs-lookup"><span data-stu-id="dc854-115">Alternatively, you can use the built-in HKLM PSDrive with `Set-Location`:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="dc854-116">Du kan sedan använda `*.*` notation för den aktuella platsen för att lista egenskaperna utan att ange en fullständig sökväg:</span><span class="sxs-lookup"><span data-stu-id="dc854-116">You can then use the `*.*` notation for the current location to list the properties without specifying a full path:</span></span>

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

<span data-ttu-id="dc854-117">Ökning av sökvägar fungerar på samma sätt som i fil systemet, så från den här platsen kan du hämta **ItemProperty** -listan för `HKLM:\SOFTWARE\Microsoft\Windows\Help` med hjälp av `Get-ItemProperty -Path ..\Help`.</span><span class="sxs-lookup"><span data-stu-id="dc854-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for `HKLM:\SOFTWARE\Microsoft\Windows\Help` by using `Get-ItemProperty -Path ..\Help`.</span></span>

## <a name="getting-a-single-registry-entry"></a><span data-ttu-id="dc854-118">Hämta en enskild register post</span><span class="sxs-lookup"><span data-stu-id="dc854-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="dc854-119">Om du vill hämta en speciell post i en register nyckel kan du använda en av flera olika metoder.</span><span class="sxs-lookup"><span data-stu-id="dc854-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="dc854-120">I det här exemplet hittas värdet för **DevicePath** i `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span><span class="sxs-lookup"><span data-stu-id="dc854-120">This example finds the value of **DevicePath** in `HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion`.</span></span>

<span data-ttu-id="dc854-121">Använd `Get-ItemProperty`med parametern **Path** för att ange namnet på nyckeln och parametern **Name** för att ange namnet på **DevicePath** -posten.</span><span class="sxs-lookup"><span data-stu-id="dc854-121">Using `Get-ItemProperty`, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

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

<span data-ttu-id="dc854-122">Det här kommandot returnerar standard egenskaperna för Windows PowerShell och egenskapen **DevicePath** .</span><span class="sxs-lookup"><span data-stu-id="dc854-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="dc854-123">Även om `Get-ItemProperty` har **filter**-, **include**-och **exkluderings** parametrar, kan de inte användas för att filtrera efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="dc854-123">Although `Get-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="dc854-124">De här parametrarna avser register nycklar, som är objekt Sök vägar och inte register poster.</span><span class="sxs-lookup"><span data-stu-id="dc854-124">These parameters refer to registry keys, which are item paths and not registry entries.</span></span> <span data-ttu-id="dc854-125">Register poster som är objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="dc854-125">Registry entries which are item properties.</span></span>

<span data-ttu-id="dc854-126">Ett annat alternativ är att använda kommando rads verktyget REG. exe.</span><span class="sxs-lookup"><span data-stu-id="dc854-126">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="dc854-127">Om du vill ha hjälp med REG. exe skriver du `reg.exe /?` i kommando tolken.</span><span class="sxs-lookup"><span data-stu-id="dc854-127">For help with reg.exe, type `reg.exe /?` at a command prompt.</span></span> <span data-ttu-id="dc854-128">Du hittar posten DevicePath genom att använda REG. exe, som du ser i följande kommando:</span><span class="sxs-lookup"><span data-stu-id="dc854-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```powershell
reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath
```

```Output
! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="dc854-129">Du kan också använda **WshShell** com-objektet för att hitta vissa register poster, men den här metoden fungerar inte med stora binära data eller med register post namn som innehåller tecken som "\\").</span><span class="sxs-lookup"><span data-stu-id="dc854-129">You can also use the **WshShell** COM object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="dc854-130">Lägg till egenskaps namnet till objekt Sök vägen med en \\ avgränsare:</span><span class="sxs-lookup"><span data-stu-id="dc854-130">Append the property name to the item path with a \\ separator:</span></span>

```powershell
(New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
```

```Output
%SystemRoot%\inf
```

## <a name="setting-a-single-registry-entry"></a><span data-ttu-id="dc854-131">Ange en enskild register post</span><span class="sxs-lookup"><span data-stu-id="dc854-131">Setting a Single Registry Entry</span></span>

<span data-ttu-id="dc854-132">Om du vill ändra en speciell post i en register nyckel kan du använda en av flera olika metoder.</span><span class="sxs-lookup"><span data-stu-id="dc854-132">If you want to change a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="dc854-133">I det här exemplet ändras **Sök vägs** posten under `HKEY_CURRENT_USER\Environment`.</span><span class="sxs-lookup"><span data-stu-id="dc854-133">This example modifies the **Path** entry under `HKEY_CURRENT_USER\Environment`.</span></span> <span data-ttu-id="dc854-134">I **Sök vägs** posten anges var du hittar körbara filer.</span><span class="sxs-lookup"><span data-stu-id="dc854-134">The **Path** entry specifies where to find executable files.</span></span>

1. <span data-ttu-id="dc854-135">Hämta det aktuella värdet för **Sök vägs** posten med `Get-ItemProperty`.</span><span class="sxs-lookup"><span data-stu-id="dc854-135">Retrieve the current value of the **Path** entry using `Get-ItemProperty`.</span></span>
2. <span data-ttu-id="dc854-136">Lägg till det nya värdet och skilj det till ett `;`.</span><span class="sxs-lookup"><span data-stu-id="dc854-136">Add the new value, separating it with a `;`.</span></span>
3. <span data-ttu-id="dc854-137">Använd `Set-ItemProperty` med den angivna nyckeln, post namnet och värdet för att ändra register posten.</span><span class="sxs-lookup"><span data-stu-id="dc854-137">Use `Set-ItemProperty` with the specified key, entry name, and value to modify the registry entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path += ";C:\src\bin\"
Set-ItemProperty -Path HKCU:\Environment -Name Path -Value $newpath
```

> [!NOTE]
> <span data-ttu-id="dc854-138">Även om `Set-ItemProperty` har **filter**-, **include**-och **exkluderings** parametrar, kan de inte användas för att filtrera efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="dc854-138">Although `Set-ItemProperty` has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="dc854-139">Dessa parametrar avser register nycklar, som är objekt Sök vägar, och inte register poster, som är objekt egenskaper.</span><span class="sxs-lookup"><span data-stu-id="dc854-139">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="dc854-140">Ett annat alternativ är att använda kommando rads verktyget REG. exe.</span><span class="sxs-lookup"><span data-stu-id="dc854-140">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="dc854-141">Om du vill ha hjälp med REG. exe skriver du **reg. exe/?**</span><span class="sxs-lookup"><span data-stu-id="dc854-141">For help with reg.exe, type **reg.exe /?**</span></span>
<span data-ttu-id="dc854-142">i en kommando tolk.</span><span class="sxs-lookup"><span data-stu-id="dc854-142">at a command prompt.</span></span>

<span data-ttu-id="dc854-143">I följande exempel ändras **Sök vägs** posten genom att du tar bort sökvägen som lagts till i exemplet ovan.</span><span class="sxs-lookup"><span data-stu-id="dc854-143">The following example changes the **Path** entry by removing the path added in the example above.</span></span>
<span data-ttu-id="dc854-144">`Get-ItemProperty` används fortfarande för att hämta det aktuella värdet för att undvika att behöva parsa strängen som returneras från `reg query`.</span><span class="sxs-lookup"><span data-stu-id="dc854-144">`Get-ItemProperty` is still used to retrieve the current value to avoid having to parse the string returned from `reg query`.</span></span> <span data-ttu-id="dc854-145">**Substring** -och **LastIndexOf** -metoderna används för att hämta den senaste sökvägen som lagts till i **Sök vägs** posten.</span><span class="sxs-lookup"><span data-stu-id="dc854-145">The **SubString** and **LastIndexOf** methods are used to retrieve the last path added to the **Path** entry.</span></span>

```powershell
$value = Get-ItemProperty -Path HKCU:\Environment -Name Path
$newpath = $value.Path.SubString(0, $value.Path.LastIndexOf(';'))
reg add HKCU\Environment /v Path /d $newpath /f
```

```Output
The operation completed successfully.
```

## <a name="creating-new-registry-entries"></a><span data-ttu-id="dc854-146">Skapa nya register poster</span><span class="sxs-lookup"><span data-stu-id="dc854-146">Creating New Registry Entries</span></span>

<span data-ttu-id="dc854-147">Om du vill lägga till en ny post med namnet "PowerShellPath" i **CurrentVersion** -nyckeln använder du `New-ItemProperty` med sökvägen till nyckeln, post namnet och värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="dc854-147">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use `New-ItemProperty` with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="dc854-148">I det här exemplet tar vi värdet för variabeln Windows PowerShell `$PSHome`, som lagrar sökvägen till installations katalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="dc854-148">For this example, we will take the value of the Windows PowerShell variable `$PSHome`, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="dc854-149">Du kan lägga till den nya posten i nyckeln med hjälp av följande kommando, och kommandot returnerar också information om den nya posten:</span><span class="sxs-lookup"><span data-stu-id="dc854-149">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

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

<span data-ttu-id="dc854-150">**PropertyType** måste vara namnet på en **Microsoft. Win32. RegistryValueKind** -uppräknings medlem från följande tabell:</span><span class="sxs-lookup"><span data-stu-id="dc854-150">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="dc854-151">PropertyType-värde</span><span class="sxs-lookup"><span data-stu-id="dc854-151">PropertyType Value</span></span>|<span data-ttu-id="dc854-152">Innebörd</span><span class="sxs-lookup"><span data-stu-id="dc854-152">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="dc854-153">Binär</span><span class="sxs-lookup"><span data-stu-id="dc854-153">Binary</span></span>|<span data-ttu-id="dc854-154">Binära data</span><span class="sxs-lookup"><span data-stu-id="dc854-154">Binary data</span></span>|
|<span data-ttu-id="dc854-155">DWord</span><span class="sxs-lookup"><span data-stu-id="dc854-155">DWord</span></span>|<span data-ttu-id="dc854-156">Ett tal som är en giltig UInt32</span><span class="sxs-lookup"><span data-stu-id="dc854-156">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="dc854-157">ExpandString</span><span class="sxs-lookup"><span data-stu-id="dc854-157">ExpandString</span></span>|<span data-ttu-id="dc854-158">En sträng som kan innehålla miljövariabler som expanderas dynamiskt</span><span class="sxs-lookup"><span data-stu-id="dc854-158">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="dc854-159">Multisträng</span><span class="sxs-lookup"><span data-stu-id="dc854-159">MultiString</span></span>|<span data-ttu-id="dc854-160">En flerradig sträng</span><span class="sxs-lookup"><span data-stu-id="dc854-160">A multiline string</span></span>|
|<span data-ttu-id="dc854-161">Sträng</span><span class="sxs-lookup"><span data-stu-id="dc854-161">String</span></span>|<span data-ttu-id="dc854-162">Valfritt sträng värde</span><span class="sxs-lookup"><span data-stu-id="dc854-162">Any string value</span></span>|
|<span data-ttu-id="dc854-163">QWord</span><span class="sxs-lookup"><span data-stu-id="dc854-163">QWord</span></span>|<span data-ttu-id="dc854-164">8 byte binära data</span><span class="sxs-lookup"><span data-stu-id="dc854-164">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="dc854-165">Du kan lägga till en register post till flera platser genom att ange en matris med värden för parametern **Path** :</span><span class="sxs-lookup"><span data-stu-id="dc854-165">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Name PowerShellPath -PropertyType String -Value $PSHome `
  -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="dc854-166">Du kan också skriva över ett befintligt register post värde genom att lägga till parametern **Force** till alla `New-ItemProperty`-kommandon.</span><span class="sxs-lookup"><span data-stu-id="dc854-166">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any `New-ItemProperty` command.</span></span>

## <a name="renaming-registry-entries"></a><span data-ttu-id="dc854-167">Byta namn på register poster</span><span class="sxs-lookup"><span data-stu-id="dc854-167">Renaming Registry Entries</span></span>

<span data-ttu-id="dc854-168">Om du vill byta namn på posten **PowerShellPath** till "PSHome" använder `Rename-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="dc854-168">To rename the **PowerShellPath** entry to "PSHome," use `Rename-ItemProperty`:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="dc854-169">Om du vill visa det omdöpta värdet lägger du till parametern **Passthru** i kommandot.</span><span class="sxs-lookup"><span data-stu-id="dc854-169">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

## <a name="deleting-registry-entries"></a><span data-ttu-id="dc854-170">Tar bort register poster</span><span class="sxs-lookup"><span data-stu-id="dc854-170">Deleting Registry Entries</span></span>

<span data-ttu-id="dc854-171">Om du vill ta bort register posterna PSHome och PowerShellPath använder du `Remove-ItemProperty`:</span><span class="sxs-lookup"><span data-stu-id="dc854-171">To delete both the PSHome and PowerShellPath registry entries, use `Remove-ItemProperty`:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```
