---
ms.date: 07/28/2020
keywords: powershell,cmdlet
title: Arbeta med filer, mappar och registernycklar
description: Den här artikeln beskriver hur du hanterar aktiviteter för register nyckel hantering med hjälp av PowerShell.
ms.openlocfilehash: 6f653c1fb409a238aa05658e89261a12e96f6fe1
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92499985"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="4b652-104">Arbeta med filer, mappar och register nycklar</span><span class="sxs-lookup"><span data-stu-id="4b652-104">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="4b652-105">Windows PowerShell använder **objektet** Substantiv för att referera till objekt som finns på en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="4b652-105">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span>
<span data-ttu-id="4b652-106">När du hanterar Windows PowerShell-filsystem-providern kan ett **objekt** vara en fil, en mapp eller Windows PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="4b652-106">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="4b652-107">Att lista och arbeta med dessa objekt är en viktig grundläggande uppgift i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.</span><span class="sxs-lookup"><span data-stu-id="4b652-107">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="4b652-108">Räkna upp filer, mappar och register nycklar (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="4b652-108">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="4b652-109">Eftersom hämtning av en samling av objekt från en viss plats är en sådan vanlig uppgift, `Get-ChildItem` är cmdleten utformad för att returnera alla objekt som finns i en behållare, till exempel en mapp.</span><span class="sxs-lookup"><span data-stu-id="4b652-109">Since getting a collection of items from a particular location is such a common task, the `Get-ChildItem` cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="4b652-110">Om du vill returnera alla filer och mappar som finns direkt i mappen C: \\ Windows skriver du:</span><span class="sxs-lookup"><span data-stu-id="4b652-110">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

```
PS> Get-ChildItem -Path C:\Windows
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2006-05-16   8:10 AM          0 0.log
-a---        2005-11-29   3:16 PM         97 acc1.txt
-a---        2005-10-23  11:21 PM       3848 actsetup.log
...
```

<span data-ttu-id="4b652-111">Listan ser ut ungefär som du ser när du anger `dir` kommandot i **Cmd.exe**eller `ls` kommandot i ett UNIX-kommando gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="4b652-111">The listing looks similar to what you would see when you enter the `dir` command in **Cmd.exe**, or the `ls` command in a UNIX command shell.</span></span>

<span data-ttu-id="4b652-112">Du kan utföra mycket komplexa listor genom att använda parametrarna i `Get-ChildItem` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4b652-112">You can perform very complex listings by using parameters of the `Get-ChildItem` cmdlet.</span></span> <span data-ttu-id="4b652-113">Vi kommer att titta på några scenarier härnäst.</span><span class="sxs-lookup"><span data-stu-id="4b652-113">We will look at a few scenarios next.</span></span> <span data-ttu-id="4b652-114">Du kan se syntaxen för `Get-ChildItem` cmdleten genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="4b652-114">You can see the syntax the `Get-ChildItem` cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="4b652-115">Dessa parametrar kan kombineras och matchas för att få mycket anpassade utdata.</span><span class="sxs-lookup"><span data-stu-id="4b652-115">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="4b652-116">Visar alla objekt som finns (-rekursivt)</span><span class="sxs-lookup"><span data-stu-id="4b652-116">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="4b652-117">Om du vill se både objekten i en Windows-mapp och alla objekt som ingår i undermapparna använder du parametern **rekursivt** i `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4b652-117">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of `Get-ChildItem`.</span></span> <span data-ttu-id="4b652-118">I listan visas allting i Windows-mappen och objekten i dess undermappar.</span><span class="sxs-lookup"><span data-stu-id="4b652-118">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="4b652-119">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4b652-119">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="4b652-120">Filtrera objekt efter namn (-namn)</span><span class="sxs-lookup"><span data-stu-id="4b652-120">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="4b652-121">Om du bara vill visa objekt namn använder du parametern **Name** för `Get-Childitem` :</span><span class="sxs-lookup"><span data-stu-id="4b652-121">To display only the names of items, use the **Name** parameter of `Get-Childitem`:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="4b652-122">Tvångs lista över dolda objekt (-Force)</span><span class="sxs-lookup"><span data-stu-id="4b652-122">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="4b652-123">Objekt som normalt är osynliga i Utforskaren eller Cmd.exe visas inte i utdata från ett `Get-ChildItem` kommando.</span><span class="sxs-lookup"><span data-stu-id="4b652-123">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a `Get-ChildItem` command.</span></span> <span data-ttu-id="4b652-124">Om du vill visa dolda objekt använder du **Force** -parametern i `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4b652-124">To display hidden items, use the **Force** parameter of `Get-ChildItem`.</span></span>
<span data-ttu-id="4b652-125">Exempel:</span><span class="sxs-lookup"><span data-stu-id="4b652-125">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="4b652-126">Den här parametern heter Force eftersom du kan framtvinga åsidosättning av `Get-ChildItem` kommandots normala beteende.</span><span class="sxs-lookup"><span data-stu-id="4b652-126">This parameter is named Force because you can forcibly override the normal behavior of the `Get-ChildItem` command.</span></span> <span data-ttu-id="4b652-127">Force är en mycket Använd parameter som tvingar fram en åtgärd som en cmdlet normalt inte utför, även om den inte kommer att utföra någon åtgärd som äventyrar säkerheten i systemet.</span><span class="sxs-lookup"><span data-stu-id="4b652-127">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="4b652-128">Matchande objekt namn med jokertecken</span><span class="sxs-lookup"><span data-stu-id="4b652-128">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="4b652-129">`Get-ChildItem`Kommandot accepterar jokertecken i sökvägen för objekten som ska listas.</span><span class="sxs-lookup"><span data-stu-id="4b652-129">The `Get-ChildItem` command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="4b652-130">Eftersom matchning av jokertecken hanteras av Windows PowerShell-motorn, använder alla cmdlets som accepterar jokertecken samma notation och har samma matchnings beteende.</span><span class="sxs-lookup"><span data-stu-id="4b652-130">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="4b652-131">Jokertecken i Windows PowerShell innehåller:</span><span class="sxs-lookup"><span data-stu-id="4b652-131">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="4b652-132">Asterisk ( `*` ) matchar noll eller flera förekomster av tecken.</span><span class="sxs-lookup"><span data-stu-id="4b652-132">Asterisk (`*`) matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="4b652-133">Frågetecken ( `?` ) matchar exakt ett tecken.</span><span class="sxs-lookup"><span data-stu-id="4b652-133">Question mark (`?`) matches exactly one character.</span></span>

- <span data-ttu-id="4b652-134">Vänster hak paren tes tecken `[` och höger hak paren tes tecken ( `]` ) omger en uppsättning tecken som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="4b652-134">Left bracket (`[`) character and right bracket (`]`) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="4b652-135">Här följer några exempel på hur wildcard-specifikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="4b652-135">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="4b652-136">Om du vill hitta alla filer i Windows-katalogen med suffixet `.log` och exakt fem tecken i bas namnet, anger du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="4b652-136">To find all files in the Windows directory with the suffix `.log` and exactly five characters in the base name, enter the following command:</span></span>

```
PS> Get-ChildItem -Path C:\Windows\?????.log

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
...
-a---        2006-05-11   6:31 PM     204276 ocgen.log
-a---        2006-05-11   6:31 PM      22365 ocmsn.log
...
-a---        2005-11-11   4:55 AM         64 setup.log
-a---        2005-12-15   2:24 PM      17719 VxSDM.log
...
```

<span data-ttu-id="4b652-137">Om du vill hitta alla filer som börjar med bokstaven `x` i Windows-katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="4b652-137">To find all files that begin with the letter `x` in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="4b652-138">Om du vill hitta alla filer vars namn börjar med "x" eller "z", skriver du:</span><span class="sxs-lookup"><span data-stu-id="4b652-138">To find all files whose names begin with "x" or "z", type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

<span data-ttu-id="4b652-139">Mer information om jokertecken finns [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards).</span><span class="sxs-lookup"><span data-stu-id="4b652-139">For more information about wildcards, see [about_Wildcards](/powershell/module/microsoft.powershell.core/about/about_wildcards).</span></span>

### <a name="excluding-items--exclude"></a><span data-ttu-id="4b652-140">Uteslut objekt (-exkludera)</span><span class="sxs-lookup"><span data-stu-id="4b652-140">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="4b652-141">Du kan undanta vissa objekt med hjälp av parametern **exclude** i `Get-ChildItem` .</span><span class="sxs-lookup"><span data-stu-id="4b652-141">You can exclude specific items by using the **Exclude** parameter of `Get-ChildItem`.</span></span> <span data-ttu-id="4b652-142">På så sätt kan du utföra komplex filtrering i ett enda uttryck.</span><span class="sxs-lookup"><span data-stu-id="4b652-142">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="4b652-143">Anta till exempel att du försöker hitta Windows Time Service-DLL i mappen **system32** , och allt du kan komma ihåg om dll-namnet är att det börjar med "W" och innehåller "32".</span><span class="sxs-lookup"><span data-stu-id="4b652-143">For example, suppose you are trying to find the Windows Time Service DLL in the **System32** folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="4b652-144">Ett uttryck som visar `w*32*.dll` alla DLL: er som uppfyller villkoren, men du kanske vill filtrera bort filerna ytterligare och utelämna eventuella Win32-filer.</span><span class="sxs-lookup"><span data-stu-id="4b652-144">An expression like `w*32*.dll` will find all DLLs that satisfy the conditions, but you may want to further filter out the files and omit any win32 files.</span></span> <span data-ttu-id="4b652-145">Du kan utelämna dessa filer med hjälp av parametern **exclude** med mönstret `win*` :</span><span class="sxs-lookup"><span data-stu-id="4b652-145">You can omit these files by using the **Exclude** parameter with the pattern `win*`:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude win*

    Directory: C:\WINDOWS\System32

Mode                 LastWriteTime         Length Name
----                 -------------         ------ ----
-a---           3/18/2019  9:43 PM         495616 w32time.dll
-a---           3/18/2019  9:44 PM          35328 w32topl.dll
-a---           1/24/2020  5:44 PM         401920 Wldap32.dll
-a---          10/10/2019  5:40 PM         442704 ws2_32.dll
-a---           3/18/2019  9:44 PM          66048 wsnmp32.dll
-a---           3/18/2019  9:44 PM          18944 wsock32.dll
-a---           3/18/2019  9:44 PM          64792 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="4b652-146">Blanda Get-ChildItem parametrar</span><span class="sxs-lookup"><span data-stu-id="4b652-146">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="4b652-147">Du kan använda flera av parametrarna i `Get-ChildItem` cmdleten i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="4b652-147">You can use several of the parameters of the `Get-ChildItem` cmdlet in the same command.</span></span> <span data-ttu-id="4b652-148">Innan du blandar parametrar bör du vara säker på att du förstår matchning med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="4b652-148">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="4b652-149">Följande kommando returnerar till exempel inga resultat:</span><span class="sxs-lookup"><span data-stu-id="4b652-149">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="4b652-150">Det finns inga resultat, även om det finns två dll: er som börjar med bokstaven "z" i Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="4b652-150">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="4b652-151">Inga resultat returnerades eftersom vi har angett jokertecknet som en del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="4b652-151">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="4b652-152">Även om kommandot var rekursivt, var cmdlet: en begränsad till de `Get-ChildItem` objekt som finns i Windows-mappen med namn som slutar med `.dll` .</span><span class="sxs-lookup"><span data-stu-id="4b652-152">Even though the command was recursive, the `Get-ChildItem` cmdlet restricted the items to those that are in the Windows folder with names ending with `.dll`.</span></span>

<span data-ttu-id="4b652-153">Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster använder du parametern **include** .</span><span class="sxs-lookup"><span data-stu-id="4b652-153">To specify a recursive search for files whose names match a special pattern, use the **Include** parameter.</span></span>

```
PS> Get-ChildItem -Path C:\Windows -Include *.dll -Recurse -Exclude [a-y]*.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32\Setup

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM       8261 zoneoc.dll

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\Windows\System32

Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     337920 zipfldr.dll
```
