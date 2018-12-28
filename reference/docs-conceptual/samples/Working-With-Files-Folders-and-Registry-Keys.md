---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Arbeta med filer, mappar och registernycklar
ms.assetid: e6cf87aa-b5f8-48d5-a75a-7cb7ecb482dc
ms.openlocfilehash: a09b127d4ba37d33cb4c0f0ce0819e645fd4b137
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53405495"
---
# <a name="working-with-files-folders-and-registry-keys"></a><span data-ttu-id="20a32-103">Arbeta med filer, mappar och registernycklar</span><span class="sxs-lookup"><span data-stu-id="20a32-103">Working With Files, Folders and Registry Keys</span></span>

<span data-ttu-id="20a32-104">Windows PowerShell använder substantivet **objekt** att referera till objekt som finns på en Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="20a32-104">Windows PowerShell uses the noun **Item** to refer to items found on a Windows PowerShell drive.</span></span> <span data-ttu-id="20a32-105">När du hanterar filsystem för Windows PowerShell-providern, en **objekt** kan vara en fil, en mapp eller Windows PowerShell-enhet.</span><span class="sxs-lookup"><span data-stu-id="20a32-105">When dealing with the Windows PowerShell FileSystem provider, an **Item** might be a file, a folder, or the Windows PowerShell drive.</span></span> <span data-ttu-id="20a32-106">Lista och arbeta med de här objekten är en kritisk standardaktivitet i de flesta administrativa inställningar, så vi vill diskutera dessa uppgifter i detalj.</span><span class="sxs-lookup"><span data-stu-id="20a32-106">Listing and working with these items is a critical basic task in most administrative settings, so we want to discuss these tasks in detail.</span></span>

### <a name="enumerating-files-folders-and-registry-keys-get-childitem"></a><span data-ttu-id="20a32-107">Räkna upp filer, mappar och registernycklar (Get-ChildItem)</span><span class="sxs-lookup"><span data-stu-id="20a32-107">Enumerating Files, Folders, and Registry Keys (Get-ChildItem)</span></span>

<span data-ttu-id="20a32-108">Eftersom hämtar en samling objekt från en viss plats är sådan vanliga uppgift, den **Get-ChildItem** cmdlet har utformats speciellt för att returnera alla objekt som hittas i en behållare, till exempel en mapp.</span><span class="sxs-lookup"><span data-stu-id="20a32-108">Since getting a collection of items from a particular location is such a common task, the **Get-ChildItem** cmdlet is designed specifically to return all items found within a container such as a folder.</span></span>

<span data-ttu-id="20a32-109">Om du vill returnera alla filer och mappar som finns direkt i mappen C:\\Windows, typ:</span><span class="sxs-lookup"><span data-stu-id="20a32-109">If you want to return all files and folders that are contained directly within the folder C:\\Windows, type:</span></span>

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

<span data-ttu-id="20a32-110">Listan liknar vad som skulle visas när du anger den **dir** i **Cmd.exe**, eller **ls** i en UNIX-kommandogränssnittet.</span><span class="sxs-lookup"><span data-stu-id="20a32-110">The listing looks similar to what you would see when you enter the **dir** command in **Cmd.exe**, or the **ls** command in a UNIX command shell.</span></span>

<span data-ttu-id="20a32-111">Du kan utföra mycket komplex listor med hjälp av parametrarna för den **Get-ChildItem** cmdlet.</span><span class="sxs-lookup"><span data-stu-id="20a32-111">You can perform very complex listings by using parameters of the **Get-ChildItem** cmdlet.</span></span> <span data-ttu-id="20a32-112">Vi ska titta på några scenarier bredvid.</span><span class="sxs-lookup"><span data-stu-id="20a32-112">We will look at a few scenarios next.</span></span> <span data-ttu-id="20a32-113">Du kan se syntaxen i **Get-ChildItem** cmdlet genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="20a32-113">You can see the syntax the **Get-ChildItem** cmdlet by typing:</span></span>

```powershell
Get-Command -Name Get-ChildItem -Syntax
```

<span data-ttu-id="20a32-114">Dessa parametrar kan kombineras och matchas i syfte för att få stora anpassningar utdata.</span><span class="sxs-lookup"><span data-stu-id="20a32-114">These parameters can be mixed and matched to get highly customized output.</span></span>

#### <a name="listing-all-contained-items--recurse"></a><span data-ttu-id="20a32-115">Lista alla innehöll objekt (-Recurse)</span><span class="sxs-lookup"><span data-stu-id="20a32-115">Listing all Contained Items (-Recurse)</span></span>

<span data-ttu-id="20a32-116">Om du vill se både objekt i en Windows-mapp och alla objekt som ingår i undermapparna, använda den **Recurse** -parametern för **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="20a32-116">To see both the items inside a Windows folder and any items that are contained within the subfolders, use the **Recurse** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="20a32-117">Listan visar allt inom den Windows-mappen och dess undermappar objekt.</span><span class="sxs-lookup"><span data-stu-id="20a32-117">The listing displays everything within the Windows folder and the items in its subfolders.</span></span> <span data-ttu-id="20a32-118">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="20a32-118">For example:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Recurse

    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS
    Directory: Microsoft.Windows PowerShell.Core\FileSystem::C:\WINDOWS\AppPatch
Mode                LastWriteTime     Length Name
----                -------------     ------ ----
-a---        2004-08-04   8:00 AM    1852416 AcGenral.dll
...
```

#### <a name="filtering-items-by-name--name"></a><span data-ttu-id="20a32-119">Filtrera objekt efter namn (-namn)</span><span class="sxs-lookup"><span data-stu-id="20a32-119">Filtering Items by Name (-Name)</span></span>

<span data-ttu-id="20a32-120">Använd för att visa bara namnen på objekten i **namn** -parametern för **Get-Childitem**:</span><span class="sxs-lookup"><span data-stu-id="20a32-120">To display only the names of items, use the **Name** parameter of **Get-Childitem**:</span></span>

```
PS> Get-ChildItem -Path C:\WINDOWS -Name
addins
AppPatch
assembly
...
```

#### <a name="forcibly-listing-hidden-items--force"></a><span data-ttu-id="20a32-121">Forcerar lista dolda objekt (-Force)</span><span class="sxs-lookup"><span data-stu-id="20a32-121">Forcibly Listing Hidden Items (-Force)</span></span>

<span data-ttu-id="20a32-122">Objekt som är normalt osynliga i Utforskaren eller Cmd.exe inte visas i utdata från en **Get-ChildItem** kommando.</span><span class="sxs-lookup"><span data-stu-id="20a32-122">Items that are normally invisible in File Explorer or Cmd.exe are not displayed in the output of a **Get-ChildItem** command.</span></span> <span data-ttu-id="20a32-123">Använd för att visa dolda objekt, den **kraft** -parametern för **Get-ChildItem**.</span><span class="sxs-lookup"><span data-stu-id="20a32-123">To display hidden items, use the **Force** parameter of **Get-ChildItem**.</span></span> <span data-ttu-id="20a32-124">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="20a32-124">For example:</span></span>

```powershell
Get-ChildItem -Path C:\Windows -Force
```

<span data-ttu-id="20a32-125">Den här parametern heter Force eftersom du kan framtvinga åsidosätta det normala beteendet för den **Get-ChildItem** kommando.</span><span class="sxs-lookup"><span data-stu-id="20a32-125">This parameter is named Force because you can forcibly override the normal behavior of the **Get-ChildItem** command.</span></span> <span data-ttu-id="20a32-126">Force är en term som används parameter som tvingar en åtgärd som inte normalt utför en cmdlet, även om det inte att utföra några åtgärder som äventyrar säkerheten i systemet.</span><span class="sxs-lookup"><span data-stu-id="20a32-126">Force is a widely used parameter that forces an action that a cmdlet would not normally perform, although it will not perform any action that compromises the security of the system.</span></span>

#### <a name="matching-item-names-with-wildcards"></a><span data-ttu-id="20a32-127">Matchande namn med jokertecken</span><span class="sxs-lookup"><span data-stu-id="20a32-127">Matching Item Names with Wildcards</span></span>

<span data-ttu-id="20a32-128">**Get-ChildItem** kommando accepterar jokertecken i sökvägen till de objekt som ska visas.</span><span class="sxs-lookup"><span data-stu-id="20a32-128">**The Get-ChildItem** command accepts wildcards in the path of the items to list.</span></span>

<span data-ttu-id="20a32-129">Eftersom matchning med jokertecken hanteras av Windows PowerShell-motorn, alla cmdletar som accepterar jokertecken använder samma notation och har samma matchande beteende.</span><span class="sxs-lookup"><span data-stu-id="20a32-129">Because wildcard matching is handled by the Windows PowerShell engine, all cmdlets that accepts wildcards use the same notation and have the same matching behavior.</span></span> <span data-ttu-id="20a32-130">Windows PowerShell med jokertecken notation innehåller:</span><span class="sxs-lookup"><span data-stu-id="20a32-130">The Windows PowerShell wildcard notation includes:</span></span>

- <span data-ttu-id="20a32-131">Asterisk (\*) matchar noll eller flera förekomster av valfritt tecken.</span><span class="sxs-lookup"><span data-stu-id="20a32-131">Asterisk (\*)matches zero or more occurrences of any character.</span></span>

- <span data-ttu-id="20a32-132">Frågetecken (?) matchar exakt 1 tecken.</span><span class="sxs-lookup"><span data-stu-id="20a32-132">Question mark (?) matches exactly one character.</span></span>

- <span data-ttu-id="20a32-133">Vänster hakparentes (\[) tecken och tecken som höger hakparentes (]) omger du en uppsättning tecken som ska matchas.</span><span class="sxs-lookup"><span data-stu-id="20a32-133">Left bracket (\[) character and right bracket (]) character surround a set of characters to be matched.</span></span>

<span data-ttu-id="20a32-134">Här följer några exempel på hur det fungerar med jokertecken-specifikationen.</span><span class="sxs-lookup"><span data-stu-id="20a32-134">Here are some examples of how wildcard specification works.</span></span>

<span data-ttu-id="20a32-135">Att hitta alla filer i katalogen Windows med suffixet **.log** och fem tecken i det grundläggande namnet, anger du följande kommando:</span><span class="sxs-lookup"><span data-stu-id="20a32-135">To find all files in the Windows directory with the suffix **.log** and exactly five characters in the base name, enter the following command:</span></span>

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

<span data-ttu-id="20a32-136">Att hitta alla filer som börjar med bokstaven **x** i Windows-katalogen, skriver du:</span><span class="sxs-lookup"><span data-stu-id="20a32-136">To find all files that begin with the letter **x** in the Windows directory, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\x*
```

<span data-ttu-id="20a32-137">Att hitta alla filer vars namn börjar med **x** eller **z**, typ:</span><span class="sxs-lookup"><span data-stu-id="20a32-137">To find all files whose names begin with **x** or **z**, type:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\[xz]*
```

#### <a name="excluding-items--exclude"></a><span data-ttu-id="20a32-138">Undanta objekt (-exkludera)</span><span class="sxs-lookup"><span data-stu-id="20a32-138">Excluding Items (-Exclude)</span></span>

<span data-ttu-id="20a32-139">Du kan utesluta specifika objekt med hjälp av den **undanta** -parametern för Get-ChildItem.</span><span class="sxs-lookup"><span data-stu-id="20a32-139">You can exclude specific items by using the **Exclude** parameter of Get-ChildItem.</span></span> <span data-ttu-id="20a32-140">På så sätt kan du utföra komplex filtrering i en enskild instruktion.</span><span class="sxs-lookup"><span data-stu-id="20a32-140">This lets you perform complex filtering in a single statement.</span></span>

<span data-ttu-id="20a32-141">Anta exempelvis att du försöker att hitta Windows Time Service DLL-filen i mappen System32 och allt du kan komma ihåg om DLL-namn är att den börjar med ”W” och innehåller ”32”.</span><span class="sxs-lookup"><span data-stu-id="20a32-141">For example, suppose you are trying to find the Windows Time Service DLL in the System32 folder, and all you can remember about the DLL name is that it begins with "W" and has "32" in it.</span></span>

<span data-ttu-id="20a32-142">Ett uttryck som **w\&#42; 32\&#42;. DLL-filen** hittar alla DLL: er som uppfyller villkoren, men det kan också returnera Windows 95 och 16-bitars Windows kompatibilitet DLL-filer som innehåller ”95” eller ”16” i sina namn.</span><span class="sxs-lookup"><span data-stu-id="20a32-142">An expression like **w\&#42;32\&#42;.dll** will find all DLLs that satisfy the conditions, but it may also return the Windows 95 and 16-bit Windows compatibility DLLs that include "95" or "16" in their names.</span></span> <span data-ttu-id="20a32-143">Du kan hoppa över filer som har någon av dessa siffror i sina namn med hjälp av den **undanta** parametern med mönstret  **\&#42;\[ 9516]\&#42;**:</span><span class="sxs-lookup"><span data-stu-id="20a32-143">You can omit files that have any of these numbers in their names by using the **Exclude** parameter with the pattern **\&#42;\[9516]\&#42;**:</span></span>

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

#### <a name="mixing-get-childitem-parameters"></a><span data-ttu-id="20a32-144">Blandade Get-ChildItem parametrar</span><span class="sxs-lookup"><span data-stu-id="20a32-144">Mixing Get-ChildItem Parameters</span></span>

<span data-ttu-id="20a32-145">Du kan använda flera av parametrarna i den **Get-ChildItem** cmdlet i samma kommando.</span><span class="sxs-lookup"><span data-stu-id="20a32-145">You can use several of the parameters of the **Get-ChildItem** cmdlet in the same command.</span></span> <span data-ttu-id="20a32-146">Innan du blanda parametrar måste du kontrollera att du förstår matchning med jokertecken.</span><span class="sxs-lookup"><span data-stu-id="20a32-146">Before you mix parameters, be sure that you understand wildcard matching.</span></span> <span data-ttu-id="20a32-147">Till exempel returnerar följande kommando inga resultat:</span><span class="sxs-lookup"><span data-stu-id="20a32-147">For example, the following command returns no results:</span></span>

```powershell
Get-ChildItem -Path C:\Windows\*.dll -Recurse -Exclude [a-y]*.dll
```

<span data-ttu-id="20a32-148">Det finns inga resultat, även om det finns två DLL: er som börjar med bokstaven ”z” i Windows-mappen.</span><span class="sxs-lookup"><span data-stu-id="20a32-148">There are no results, even though there are two DLLs that begin with the letter "z" in the Windows folder.</span></span>

<span data-ttu-id="20a32-149">Inga resultat returnerades eftersom vi angav jokertecknet som en del av sökvägen.</span><span class="sxs-lookup"><span data-stu-id="20a32-149">No results were returned because we specified the wildcard as part of the path.</span></span> <span data-ttu-id="20a32-150">Även om kommandot har rekursiv, den **Get-ChildItem** cmdlet begränsade objekten till dem som ingår i Windows-mappen med namn som slutar med ”dll”.</span><span class="sxs-lookup"><span data-stu-id="20a32-150">Even though the command was recursive, the **Get-ChildItem** cmdlet restricted the items to those that are in the Windows folder with names ending with ".dll".</span></span>

<span data-ttu-id="20a32-151">Om du vill ange en rekursiv sökning efter filer vars namn matchar ett särskilt mönster, använda den **-inkludera** parametern.</span><span class="sxs-lookup"><span data-stu-id="20a32-151">To specify a recursive search for files whose names match a special pattern, use the **-Include** parameter.</span></span>

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