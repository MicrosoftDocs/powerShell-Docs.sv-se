---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med registerposter
ms.assetid: fd254570-27ac-4cc9-81d4-011afd29b7dc
ms.openlocfilehash: bffdf80931fc4dc570b584623487077dc5d449dc
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-registry-entries"></a><span data-ttu-id="da6db-103">Arbeta med registerposter</span><span class="sxs-lookup"><span data-stu-id="da6db-103">Working with Registry Entries</span></span>

<span data-ttu-id="da6db-104">Eftersom registerposter är egenskaper för nycklar och därför går inte att direkt Bläddra, behöver vi ta ett något annorlunda sätt när du arbetar med dem.</span><span class="sxs-lookup"><span data-stu-id="da6db-104">Because registry entries are properties of keys and, as such, cannot be directly browsed, we need to take a slightly different approach when working with them.</span></span>

### <a name="listing-registry-entries"></a><span data-ttu-id="da6db-105">Visar en lista över registervärden</span><span class="sxs-lookup"><span data-stu-id="da6db-105">Listing Registry Entries</span></span>

<span data-ttu-id="da6db-106">Det finns många olika sätt att granska registerposter.</span><span class="sxs-lookup"><span data-stu-id="da6db-106">There are many different ways to examine registry entries.</span></span> <span data-ttu-id="da6db-107">Det enklaste sättet är att hämta egenskapsnamn som associeras med en nyckel.</span><span class="sxs-lookup"><span data-stu-id="da6db-107">The simplest way is to get the property names associated with a key.</span></span> <span data-ttu-id="da6db-108">Till exempel för att se namnen på poster i registernyckeln **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**, Använd **Get-objekt** .</span><span class="sxs-lookup"><span data-stu-id="da6db-108">For example, to see the names of the entries in the registry key **HKEY_LOCAL_MACHINE\\Software\\Microsoft\\Windows\\CurrentVersion**, use **Get-Item**.</span></span> <span data-ttu-id="da6db-109">Registernycklar har en egenskap med det allmänna namnet för ”egenskapen” som är en lista över registerposter i nyckeln.</span><span class="sxs-lookup"><span data-stu-id="da6db-109">Registry keys have a property with the generic name of "Property" that is a list of registry entries in the key.</span></span> <span data-ttu-id="da6db-110">Följande kommando väljer egenskapen egenskapen och utökar objekt så att de visas i en lista:</span><span class="sxs-lookup"><span data-stu-id="da6db-110">The following command selects the Property property and expands the items so that they are displayed in a list:</span></span>

```
PS> Get-Item -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion | Select-Object -ExpandProperty Property
DevicePath
MediaPathUnexpanded
ProgramFilesDir
CommonFilesDir
ProductId
```

<span data-ttu-id="da6db-111">Du kan visa registerposterna i ett mer lättläst format **Get-ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="da6db-111">To view the registry entries in a more readable form, use **Get-ItemProperty**:</span></span>

```
PS> Get-ItemProperty -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion

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

<span data-ttu-id="da6db-112">Windows PowerShell-relaterade egenskaper för nyckeln är alla med prefixet ”PS”, som **PSPath**, **PSParentPath**, **PSChildName**, och **PSProvider** .</span><span class="sxs-lookup"><span data-stu-id="da6db-112">The Windows PowerShell-related properties for the key are all prefixed with "PS", such as **PSPath**, **PSParentPath**, **PSChildName**, and **PSProvider**.</span></span>

<span data-ttu-id="da6db-113">Du kan använda den ”**.**” notation för att referera till den aktuella platsen.</span><span class="sxs-lookup"><span data-stu-id="da6db-113">You can use the "**.**" notation for referring to the current location.</span></span> <span data-ttu-id="da6db-114">Du kan använda **Set-Location** ändra till den **CurrentVersion** registret behållaren första:</span><span class="sxs-lookup"><span data-stu-id="da6db-114">You can use **Set-Location** to change to the **CurrentVersion** registry container first:</span></span>

```powershell
Set-Location -Path Registry::HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="da6db-115">Du kan också använda den inbyggda HKLM PSDrive med **Set-Location**:</span><span class="sxs-lookup"><span data-stu-id="da6db-115">Alternatively, you can use the built-in HKLM PSDrive with **Set-Location**:</span></span>

```powershell
Set-Location -Path hklm:\SOFTWARE\Microsoft\Windows\CurrentVersion
```

<span data-ttu-id="da6db-116">Du kan sedan använda den ”**.**” notation för den aktuella platsen om du vill visa egenskaperna utan att ange en fullständig sökväg:</span><span class="sxs-lookup"><span data-stu-id="da6db-116">You can then use the "**.**" notation for the current location to list the properties without specifying a full path:</span></span>

```
PS> Get-ItemProperty -Path .
...
DevicePath          : C:\WINDOWS\inf
MediaPathUnexpanded : C:\WINDOWS\Media
ProgramFilesDir     : C:\Program Files
...
```

<span data-ttu-id="da6db-117">Sökvägen expansion fungerar på samma sätt som i filsystemet, så du kan hämta från den här platsen i **ItemProperty** lista för **HKLM:\\programvara\\Microsoft\\Windows \\Hjälp** med hjälp av **ItemProperty Get-sökvägen... \\Hjälp**.</span><span class="sxs-lookup"><span data-stu-id="da6db-117">Path expansion works the same as it does within the file system, so from this location you can get the **ItemProperty** listing for **HKLM:\\SOFTWARE\\Microsoft\\Windows\\Help** by using **Get-ItemProperty -Path ..\\Help**.</span></span>

### <a name="getting-a-single-registry-entry"></a><span data-ttu-id="da6db-118">Hämta en enda registerpost</span><span class="sxs-lookup"><span data-stu-id="da6db-118">Getting a Single Registry Entry</span></span>

<span data-ttu-id="da6db-119">Om du vill hämta en post i en registernyckel, kan du använda en av flera möjliga metoder.</span><span class="sxs-lookup"><span data-stu-id="da6db-119">If you want to retrieve a specific entry in a registry key, you can use one of several possible approaches.</span></span> <span data-ttu-id="da6db-120">Det här exemplet returnerar värdet för **DevicePath** i **HKEY_LOCAL_MACHINE\\programvara\\Microsoft\\Windows\\CurrentVersion**.</span><span class="sxs-lookup"><span data-stu-id="da6db-120">This example finds the value of **DevicePath** in **HKEY_LOCAL_MACHINE\\SOFTWARE\\Microsoft\\Windows\\CurrentVersion**.</span></span>

<span data-ttu-id="da6db-121">Med hjälp av **Get-ItemProperty**, använda den **sökväg** parametern för att ange namnet på nyckeln och **namn** parametern för att ange namnet på den **DevicePath** transaktionen.</span><span class="sxs-lookup"><span data-stu-id="da6db-121">Using **Get-ItemProperty**, use the **Path** parameter to specify the name of the key, and the **Name** parameter to specify the name of the **DevicePath** entry.</span></span>

```
PS> Get-ItemProperty -Path HKLM:\Software\Microsoft\Windows\CurrentVersion -Name DevicePath

PSPath       : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows\CurrentVersion
PSParentPath : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\Software\
               Microsoft\Windows
PSChildName  : CurrentVersion
PSDrive      : HKLM
PSProvider   : Microsoft.PowerShell.Core\Registry
DevicePath   : C:\WINDOWS\inf
```

<span data-ttu-id="da6db-122">Det här kommandot returnerar standardegenskaper för Windows PowerShell samt de **DevicePath** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="da6db-122">This command returns the standard Windows PowerShell properties as well as the **DevicePath** property.</span></span>

> [!NOTE]
> <span data-ttu-id="da6db-123">Även om **Get-ItemProperty** har **Filter**, **inkludera**, och **undanta** parametrar, de kan inte användas för att filtrera efter namn.</span><span class="sxs-lookup"><span data-stu-id="da6db-123">Although **Get-ItemProperty** has **Filter**, **Include**, and **Exclude** parameters, they cannot be used to filter by property name.</span></span> <span data-ttu-id="da6db-124">Parametrarna avser registernycklar, som är objektet sökvägar, och inte registerposter – som är egenskaper.</span><span class="sxs-lookup"><span data-stu-id="da6db-124">These parameters refer to registry keys—which are item paths—and not registry entries—which are item properties.</span></span>

<span data-ttu-id="da6db-125">Ett annat alternativ är att använda kommandoradsverktyget Reg.exe.</span><span class="sxs-lookup"><span data-stu-id="da6db-125">Another option is to use the Reg.exe command line tool.</span></span> <span data-ttu-id="da6db-126">Hjälp med reg.exe skriver **reg.exe /?**</span><span class="sxs-lookup"><span data-stu-id="da6db-126">For help with reg.exe, type **reg.exe /?**</span></span> <span data-ttu-id="da6db-127">vid en kommandotolk.</span><span class="sxs-lookup"><span data-stu-id="da6db-127">at a command prompt.</span></span> <span data-ttu-id="da6db-128">Använd reg.exe för att hitta posten DevicePath som visas i följande kommando:</span><span class="sxs-lookup"><span data-stu-id="da6db-128">To find the DevicePath entry, use reg.exe as shown in the following command:</span></span>

```
PS> reg query HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion /v DevicePath

! REG.EXE VERSION 3.0

HKEY_LOCAL_MACHINE\SOFTWARE\Microsoft\Windows\CurrentVersion
    DevicePath  REG_EXPAND_SZ   %SystemRoot%\inf
```

<span data-ttu-id="da6db-129">Du kan också använda den **WshShell COM** objekt samt för att hitta vissa registerposter, även om den här metoden inte fungerar med stora binära data eller registret postnamnen som innehåller tecken, till exempel ”\\”).</span><span class="sxs-lookup"><span data-stu-id="da6db-129">You can also use the **WshShell COM** object as well to find some registry entries, although this method does not work with large binary data or with registry entry names that include characters such as "\\").</span></span> <span data-ttu-id="da6db-130">Lägg till egenskapsnamnet objektsökväg med en \\ avgränsare:</span><span class="sxs-lookup"><span data-stu-id="da6db-130">Append the property name to the item path with a \\ separator:</span></span>

```
PS> (New-Object -ComObject WScript.Shell).RegRead("HKLM\SOFTWARE\Microsoft\Windows\CurrentVersion\DevicePath")
%SystemRoot%\inf
```

### <a name="creating-new-registry-entries"></a><span data-ttu-id="da6db-131">Skapa nya registerposter</span><span class="sxs-lookup"><span data-stu-id="da6db-131">Creating New Registry Entries</span></span>

<span data-ttu-id="da6db-132">Att lägga till en ny post med namnet ”PowerShellPath” i den **CurrentVersion** , nyckelanvändning **ny ItemProperty** med sökvägen till nyckeln, namnet och värdet för posten.</span><span class="sxs-lookup"><span data-stu-id="da6db-132">To add a new entry named "PowerShellPath" to the **CurrentVersion** key, use **New-ItemProperty** with the path to the key, the entry name, and the value of the entry.</span></span> <span data-ttu-id="da6db-133">I det här exemplet vi tar värdet för Windows PowerShell-variabel **$PSHome**, som lagrar sökvägen till installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="da6db-133">For this example, we will take the value of the Windows PowerShell variable **$PSHome**, which stores the path to the installation directory for Windows PowerShell.</span></span>

<span data-ttu-id="da6db-134">Du kan lägga till den nya posten i nyckeln med hjälp av kommandot och kommandot returnerar även information om den nya posten:</span><span class="sxs-lookup"><span data-stu-id="da6db-134">You can add the new entry to the key by using the following command, and the command also returns information about the new entry:</span></span>

```
PS> New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome

PSPath         : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows\CurrentVersion
PSParentPath   : Microsoft.PowerShell.Core\Registry::HKEY_LOCAL_MACHINE\SOFTWAR
                 E\Microsoft\Windows
PSChildName    : CurrentVersion
PSDrive        : HKLM
PSProvider     : Microsoft.PowerShell.Core\Registry
PowerShellPath : C:\Program Files\Windows PowerShell\v1.0
```

<span data-ttu-id="da6db-135">Den **PropertyType** måste vara namnet på en **Microsoft.Win32.RegistryValueKind** uppräkningsmedlem i följande tabell:</span><span class="sxs-lookup"><span data-stu-id="da6db-135">The **PropertyType** must be the name of a **Microsoft.Win32.RegistryValueKind** enumeration member from the following table:</span></span>

|<span data-ttu-id="da6db-136">PropertyType värde</span><span class="sxs-lookup"><span data-stu-id="da6db-136">PropertyType Value</span></span>|<span data-ttu-id="da6db-137">Innebörd</span><span class="sxs-lookup"><span data-stu-id="da6db-137">Meaning</span></span>|
|----------------------|-----------|
|<span data-ttu-id="da6db-138">Binär</span><span class="sxs-lookup"><span data-stu-id="da6db-138">Binary</span></span>|<span data-ttu-id="da6db-139">Binära data</span><span class="sxs-lookup"><span data-stu-id="da6db-139">Binary data</span></span>|
|<span data-ttu-id="da6db-140">DWord</span><span class="sxs-lookup"><span data-stu-id="da6db-140">DWord</span></span>|<span data-ttu-id="da6db-141">Ett tal som är en giltig UInt32</span><span class="sxs-lookup"><span data-stu-id="da6db-141">A number that is a valid UInt32</span></span>|
|<span data-ttu-id="da6db-142">ExpandString</span><span class="sxs-lookup"><span data-stu-id="da6db-142">ExpandString</span></span>|<span data-ttu-id="da6db-143">En sträng som kan innehålla miljövariabler som dynamiskt expanderas</span><span class="sxs-lookup"><span data-stu-id="da6db-143">A string that can contain environment variables that are dynamically expanded</span></span>|
|<span data-ttu-id="da6db-144">Längd</span><span class="sxs-lookup"><span data-stu-id="da6db-144">MultiString</span></span>|<span data-ttu-id="da6db-145">En flerradig sträng</span><span class="sxs-lookup"><span data-stu-id="da6db-145">A multiline string</span></span>|
|<span data-ttu-id="da6db-146">Sträng</span><span class="sxs-lookup"><span data-stu-id="da6db-146">String</span></span>|<span data-ttu-id="da6db-147">Ett värde</span><span class="sxs-lookup"><span data-stu-id="da6db-147">Any string value</span></span>|
|<span data-ttu-id="da6db-148">QWord</span><span class="sxs-lookup"><span data-stu-id="da6db-148">QWord</span></span>|<span data-ttu-id="da6db-149">8 byte binära data</span><span class="sxs-lookup"><span data-stu-id="da6db-149">8 bytes of binary data</span></span>|

> [!NOTE]
> <span data-ttu-id="da6db-150">Du kan lägga till en registerpost till flera platser genom att ange en matris med-värden för den **sökväg** parameter:</span><span class="sxs-lookup"><span data-stu-id="da6db-150">You can add a registry entry to multiple locations by specifying an array of values for the **Path** parameter:</span></span>

```powershell
New-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion, HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -PropertyType String -Value $PSHome
```

<span data-ttu-id="da6db-151">Du kan också skriva över en befintlig post registervärdet genom att lägga till den **kraft** parameter till någon **ny ItemProperty** kommando.</span><span class="sxs-lookup"><span data-stu-id="da6db-151">You can also overwrite a pre-existing registry entry value by adding the **Force** parameter to any **New-ItemProperty** command.</span></span>

### <a name="renaming-registry-entries"></a><span data-ttu-id="da6db-152">Byta namn på registerposter</span><span class="sxs-lookup"><span data-stu-id="da6db-152">Renaming Registry Entries</span></span>

<span data-ttu-id="da6db-153">Att byta namn på den **PowerShellPath** post som ”PSHome”, Använd **byta ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="da6db-153">To rename the **PowerShellPath** entry to "PSHome," use **Rename-ItemProperty**:</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome
```

<span data-ttu-id="da6db-154">Om du vill visa värdet har bytt namn till, lägger du till den **PassThru** parametern för kommandot.</span><span class="sxs-lookup"><span data-stu-id="da6db-154">To display the renamed value, add the **PassThru** parameter to the command.</span></span>

```powershell
Rename-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath -NewName PSHome -passthru
```

### <a name="deleting-registry-entries"></a><span data-ttu-id="da6db-155">Om du tar bort registerposter</span><span class="sxs-lookup"><span data-stu-id="da6db-155">Deleting Registry Entries</span></span>

<span data-ttu-id="da6db-156">Om du vill ta bort registerposter för både PSHome och PowerShellPath använder **ta bort ItemProperty**:</span><span class="sxs-lookup"><span data-stu-id="da6db-156">To delete both the PSHome and PowerShellPath registry entries, use **Remove-ItemProperty**:</span></span>

```powershell
Remove-ItemProperty -Path HKLM:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PSHome
Remove-ItemProperty -Path HKCU:\SOFTWARE\Microsoft\Windows\CurrentVersion -Name PowerShellPath
```