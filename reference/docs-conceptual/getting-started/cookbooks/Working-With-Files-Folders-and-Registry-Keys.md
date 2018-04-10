---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="69091-103">Arbeta med filer, mappar och registernycklar</span><span class="sxs-lookup"><span data-stu-id="69091-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="69091-104">Windows PowerShell använder substantivet **objektet** att referera till objekt som finns på en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="69091-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="69091-105">När du hanterar filsystem för Windows PowerShell-providern en **objektet** kan vara en fil, en mapp eller Windows PowerShell-enheten.</span><span class="sxs-lookup"><span data-stu-id="69091-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="69091-106">Lista och arbeta med dessa objekt är en kritisk standardaktivitet i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.</span><span class="sxs-lookup"><span data-stu-id="69091-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="69091-107">Uppräkning av filer, mappar och registernycklar (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="69091-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="69091-108">Eftersom hämtningen av en samling objekt från en viss plats är sådan vanliga uppgift i **Get-ChildItem** cmdlet är utformad särskilt för att returnera alla poster som hittades i en behållare, till exempel en mapp.</span><span class="sxs-lookup"><span data-stu-id="69091-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="69091-109">Om du vill återställa alla filer och mappar som finns i mappen C: direkt\\Windows, typ:</span><span class="sxs-lookup"><span data-stu-id="69091-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="69091-110">Listan liknar vad som visas när du anger den **dir** i **Cmd.exe**, eller **ls** i UNIX-kommandogränssnittet.</span><span class="sxs-lookup"><span data-stu-id="69091-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="69091-111">Du kan utföra mycket komplex listor med hjälp av parametrarna för den **Get-ChildItem** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="69091-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="69091-112">Vi ska titta på några scenarier nästa.</span><span class="sxs-lookup"><span data-stu-id="69091-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="69091-113">Du kan se syntaxen i **Get-ChildItem** cmdlet genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="69091-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="69091-114">De här parametrarna kan blandas och matchas för att hämta anpassade utdata.</span><span class="sxs-lookup"><span data-stu-id="69091-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="69091-115">Visar en lista över alla artiklar som ingår (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="69091-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="69091-116">Både objekt i en Windows-mappen och alla objekt som ingår i undermapparna, Använd den **Recurse** -parametern för **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="69091-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="69091-117">Listan visar allt i Windows-mappen och objekten i dess undermappar.</span><span class="sxs-lookup"><span data-stu-id="69091-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="69091-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="69091-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="69091-119">Filtrera objekt efter namn (-namn)</span><span class="sxs-lookup"><span data-stu-id="69091-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="69091-120">Använd för att visa endast namnen på objekten i **namn** -parametern för **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="69091-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="69091-121">Framtvingar lista dolda objekt (-Force)</span><span class="sxs-lookup"><span data-stu-id="69091-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="69091-122">Objekt som är normalt osynliga i Utforskaren eller Cmd.exe visas inte i utdata från en **Get-ChildItem** kommando.</span><span class="sxs-lookup"><span data-stu-id="69091-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="69091-123">Använd för att visa dolda objekt i **kraft** -parametern för **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="69091-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="69091-124">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="69091-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="69091-125">Den här parametern heter kraft eftersom du kan framtvinga åsidosätta normalt av den **Get-ChildItem** kommando.</span><span class="sxs-lookup"><span data-stu-id="69091-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="69091-126">Force är en mycket vanlig parameter som tvingar en åtgärd som en cmdlet inte normalt utförs, även om det inte kommer att utföra en åtgärd som äventyrar säkerheten för systemet.</span><span class="sxs-lookup"><span data-stu-id="69091-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="69091-127">Matcha namn med jokertecken</span><span class="sxs-lookup"><span data-stu-id="69091-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="69091-128">**Get-ChildItem** kommandot accepterar jokertecken i sökvägen för objekt i listan.</span><span class="sxs-lookup"><span data-stu-id="69091-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="69091-129">Eftersom matchning med jokertecken hanteras av Windows PowerShell-motorn kan alla cmdletar som accepterar jokertecken använder samma notation och har samma matchande beteende.</span><span class="sxs-lookup"><span data-stu-id="69091-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="69091-130">Windows PowerShell med jokertecken notation innehåller:</span><span class="sxs-lookup"><span data-stu-id="69091-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="69091-131">Asterisk (\*) matchar noll eller flera förekomster av ett tecken.</span><span class="sxs-lookup"><span data-stu-id="69091-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="69091-132">Frågetecken (?) matchar exakt ett tecken.</span><span class="sxs-lookup"><span data-stu-id="69091-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="69091-133">Vänster hakparentes (\[) tecken och höger hakparentes (]) tecken omges av en uppsättning tecken som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="69091-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="69091-134">Här följer några exempel på hur det fungerar med jokertecken-specifikationen.</span><span class="sxs-lookup"><span data-stu-id="69091-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="69091-135">Hitta alla filer i Windows-katalogen med suffixet **.log** och fem tecknen i det grundläggande namnet, anger du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="69091-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="69091-136">Hitta alla filer som börjar med bokstaven **x** i Windows-katalogen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="69091-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="69091-137">Hitta alla filer vars namn börjar med **x** eller **z**, typ:</span><span class="sxs-lookup"><span data-stu-id="69091-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="69091-138">Exkludera objekt (-exkludera)</span><span class="sxs-lookup"><span data-stu-id="69091-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="69091-139">Du kan exkludera specifika objekt med hjälp av den **undanta** parametern för Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="69091-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="69091-140">På så sätt kan du utföra komplicerade filtrering i en enskild instruktion.</span><span class="sxs-lookup"><span data-stu-id="69091-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="69091-141">Anta att du vill hitta Windows tid tjänsten DLL-filen i mappen System32 och alla du kommer ihåg om DLL-namn är att den börjar med ”W” och ”32” det finns i.</span><span class="sxs-lookup"><span data-stu-id="69091-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="69091-142">Ett uttryck som **w\&#42; 32\&#42;. DLL-filen** hittar alla DLL: er som uppfyller villkoren, men den kan också returnera Windows 95 och 16-bitars Windows-kompatibilitet DLL-filer som innehåller ”95” eller ”16” i sina namn.</span><span class="sxs-lookup"><span data-stu-id="69091-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="69091-143">Du kan hoppa över filer med någon av dessa siffror i sina namn med hjälp av den **undanta** parameter med mönstret  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="69091-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

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

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="69091-144">Blanda Get-ChildItem parametrar</span><span class="sxs-lookup"><span data-stu-id="69091-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="69091-145">Du kan använda flera av parametrarna i den **Get-ChildItem** cmdlet i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="69091-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="69091-146">Innan du blanda parametrar måste du kontrollera att du förstår matchning med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="69091-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="69091-147">Till exempel returnerar följande kommando inga resultat:</span><span class="sxs-lookup"><span data-stu-id="69091-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="69091-148">Det finns inga resultat, även om det finns två DLL: er som börjar med bokstaven ”z” i Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="69091-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="69091-149">Inga resultat returnerades eftersom vi har angetts till jokertecken som en del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="69091-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="69091-150">Även om kommandot var rekursiv den **Get-ChildItem** cmdlet begränsad objekten till dem som finns i Windows-mappen med namn som slutar med ”dll”.</span><span class="sxs-lookup"><span data-stu-id="69091-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="69091-151">Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster i **-inkludera** parameter.</span><span class="sxs-lookup"><span data-stu-id="69091-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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