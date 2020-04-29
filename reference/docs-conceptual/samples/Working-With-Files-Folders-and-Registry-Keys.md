---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.openlocfilehash: 0c8716c384827d0816e2847ff81232c14638681b
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "67030754"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="ef1c2-103">Arbeta med filer, mappar och register nycklar</span><span class="sxs-lookup"><span data-stu-id="ef1c2-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="ef1c2-104">Windows PowerShell använder **objektet** Substantiv för att referera till objekt som finns på en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="ef1c2-105">När du hanterar Windows PowerShell-filsystem-providern kan ett **objekt** vara en fil, en mapp eller Windows PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="ef1c2-106">Att lista och arbeta med dessa objekt är en viktig grundläggande uppgift i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

## <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="ef1c2-107">Räkna upp filer, mappar och register nycklar (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="ef1c2-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="ef1c2-108">Eftersom hämtning av en samling av objekt från en viss plats är en sådan vanlig uppgift, är cmdleten **Get-ChildItem** utformad för att returnera alla objekt som finns i en behållare, till exempel en mapp.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="ef1c2-109">Om du vill returnera alla filer och mappar som finns direkt i mappen C:\\Windows skriver du:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="ef1c2-110">Listan ser ut ungefär som du ser när du anger kommandot **dir** i **cmd. exe**eller kommandot **ls** i ett UNIX-kommando gränssnitt.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="ef1c2-111">Du kan utföra mycket komplexa listor genom att använda parametrarna för **Get-ChildItem** -cmdlet: en.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="ef1c2-112">Vi kommer att titta på några scenarier härnäst.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="ef1c2-113">Du kan se syntaxen **Get-ChildItem** -cmdleten genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="ef1c2-114">Dessa parametrar kan kombineras och matchas för att få mycket anpassade utdata.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-114">These parameters can be mixed and matched to get highly customized output.</span></span>

### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="ef1c2-115">Visar alla objekt som finns (-rekursivt)</span><span class="sxs-lookup"><span data-stu-id="ef1c2-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="ef1c2-116">Om du vill se både objekten i en Windows-mapp och alla objekt som ingår i undermapparna använder du parametern **rekursivt** för **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="ef1c2-117">I listan visas allting i Windows-mappen och objekten i dess undermappar.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="ef1c2-118">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

### <a name="filtering-items-by-name--name"></a><span data-ttu-id="ef1c2-119">Filtrera objekt efter namn (-namn)</span><span class="sxs-lookup"><span data-stu-id="ef1c2-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="ef1c2-120">Om du bara vill visa objekt namn använder du **Name** -parametern för **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="ef1c2-121">Tvångs lista över dolda objekt (-Force)</span><span class="sxs-lookup"><span data-stu-id="ef1c2-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="ef1c2-122">Objekt som normalt är osynliga i Utforskaren eller cmd. exe visas inte i utdata från ett **Get-ChildItem** -kommando.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="ef1c2-123">Använd parametern **Force** för **Get-ChildItem**om du vill visa dolda objekt.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="ef1c2-124">Ett exempel:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="ef1c2-125">Den här parametern heter Force eftersom du kan framtvinga åsidosättning av det normala beteendet för kommandot **Get-ChildItem** .</span><span class="sxs-lookup"><span data-stu-id="ef1c2-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="ef1c2-126">Force är en mycket Använd parameter som tvingar fram en åtgärd som en cmdlet normalt inte utför, även om den inte kommer att utföra någon åtgärd som äventyrar säkerheten i systemet.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="ef1c2-127">Matchande objekt namn med jokertecken</span><span class="sxs-lookup"><span data-stu-id="ef1c2-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="ef1c2-128">Kommandot **Get-ChildItem** accepterar jokertecken i sökvägen för objekten som ska listas.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="ef1c2-129">Eftersom matchning av jokertecken hanteras av Windows PowerShell-motorn, använder alla cmdlets som accepterar jokertecken samma notation och har samma matchnings beteende.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="ef1c2-130">Jokertecken i Windows PowerShell innehåller:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="ef1c2-131">Asterisk (\*) matchar noll eller flera förekomster av tecken.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="ef1c2-132">Frågetecken (?) matchar exakt ett tecken.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="ef1c2-133">Tecken för vänster\[hak paren tes tecken och höger hak paren tes (]) omger en uppsättning tecken som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="ef1c2-134">Här följer några exempel på hur wildcard-specifikation fungerar.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="ef1c2-135">Om du vill hitta alla filer i Windows-katalogen med suffixet **. log** och exakt fem tecken i bas namnet anger du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="ef1c2-136">Om du vill hitta alla filer som börjar med bokstaven **x** i Windows-katalogen skriver du:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="ef1c2-137">Om du vill hitta alla filer vars namn börjar med **x** eller **z**skriver du:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

### <a name="excluding-items--exclude"></a><span data-ttu-id="ef1c2-138">Uteslut objekt (-exkludera)</span><span class="sxs-lookup"><span data-stu-id="ef1c2-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="ef1c2-139">Du kan exkludera vissa objekt med hjälp av parametern **exclude** för Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="ef1c2-140">På så sätt kan du utföra komplex filtrering i ett enda uttryck.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="ef1c2-141">Anta till exempel att du försöker hitta Windows Time Service-DLL i mappen System32, och allt du kan komma ihåg om DLL-namnet är att det börjar med "W" och innehåller "32".</span><span class="sxs-lookup"><span data-stu-id="ef1c2-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="ef1c2-142">Ett uttryck som **w\&#42; 32\&#42;. DLL** hittar alla DLL: er som uppfyller villkoren, men kan också returnera windows 95-och 16-bitars Windows-kompatibla dll: er som innehåller "95" eller "16" i namnen.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="ef1c2-143">Du kan utelämna filer som har något av dessa nummer i namnen med hjälp av parametern **exclude** med mönstret \*\* \&#42;\[ 9516]\&#42;\*\*:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS\System32\w*32*.dll -Exclude *[9516]*

Directory: Microsoft.PowerShell.Core\FileSystem::C:\WINDOWS\System32
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM     174592 w32time.dll
-a---        2004-08-04   8:00 AM      22016 w32topl.dll
-a---        2004-08-04   8:00 AM     101888 win32spl.dll
-a---        2004-08-04   8:00 AM     172032 wldap32.dll
-a---        2004-08-04   8:00 AM     264192 wow32.dll
-a---        2004-08-04   8:00 AM      82944 ws2_32.dll
-a---        2004-08-04   8:00 AM      42496 wsnmp32.dll
-a---        2004-08-04   8:00 AM      22528 wsock32.dll
-a---        2004-08-04   8:00 AM      18432 wtsapi32.dll
```

### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="ef1c2-144">Blanda get-ChildItem-parametrar</span><span class="sxs-lookup"><span data-stu-id="ef1c2-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="ef1c2-145">Du kan använda flera av parametrarna för **Get-ChildItem** -cmdlet: en i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="ef1c2-146">Innan du blandar parametrar bör du vara säker på att du förstår matchning med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="ef1c2-147">Följande kommando returnerar till exempel inga resultat:</span><span class="sxs-lookup"><span data-stu-id="ef1c2-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="ef1c2-148">Det finns inga resultat, även om det finns två dll: er som börjar med bokstaven "z" i Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="ef1c2-149">Inga resultat returnerades eftersom vi har angett jokertecknet som en del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="ef1c2-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="ef1c2-150">Även om kommandot var rekursivt, har cmdleten **Get-ChildItem** begränsat objekten till de som finns i Windows-mappen med namn som slutar med ". dll".</span><span class="sxs-lookup"><span data-stu-id="ef1c2-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="ef1c2-151">Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster använder du parametern **-include** .</span><span class="sxs-lookup"><span data-stu-id="ef1c2-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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
