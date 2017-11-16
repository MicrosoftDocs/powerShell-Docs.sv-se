---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Med formatet kommandon för att ändra utdata vy"
ms.assetid: 63515a06-a6f7-4175-a45e-a0537f4f6d05
ms.openlocfilehash: 0163fcb21d586fc98902d9bdcfab6fe4eb97c225
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="19a6b-103">Med formatet kommandon för att ändra utdata vy</span><span class="sxs-lookup"><span data-stu-id="19a6b-103">Using Format Commands to Change Output View</span></span>
<span data-ttu-id="19a6b-104">Windows PowerShell har en uppsättning cmdlets som låter dig styra vilka egenskaper som visas för vissa objekt.</span><span class="sxs-lookup"><span data-stu-id="19a6b-104">Windows PowerShell has a set of cmdlets that allow you to control which properties are displayed for particular objects.</span></span> <span data-ttu-id="19a6b-105">Namnen på cmdletarna som börjar med verbet **Format**.</span><span class="sxs-lookup"><span data-stu-id="19a6b-105">The names of all the cmdlets begin with the verb **Format**.</span></span> <span data-ttu-id="19a6b-106">De kan du välja en eller flera egenskaper som ska visas.</span><span class="sxs-lookup"><span data-stu-id="19a6b-106">They let you select one or more properties to show.</span></span>

<span data-ttu-id="19a6b-107">Den **Format** cmdlets är **Format hela**, **Format-List**, **Format-Table**, och **Format-anpassad**.</span><span class="sxs-lookup"><span data-stu-id="19a6b-107">The **Format** cmdlets are **Format-Wide**, **Format-List**, **Format-Table**, and **Format-Custom**.</span></span> <span data-ttu-id="19a6b-108">Vi kommer bara beskriver den **Format hela**, **Format-List**, och **Format-Table** cmdlets i den här handboken.</span><span class="sxs-lookup"><span data-stu-id="19a6b-108">We will only describe the **Format-Wide**, **Format-List**, and **Format-Table** cmdlets in this user's guide.</span></span>

<span data-ttu-id="19a6b-109">Varje format-cmdlet har standardegenskaper som ska användas om du inte anger specifika egenskaper som ska visas.</span><span class="sxs-lookup"><span data-stu-id="19a6b-109">Each format cmdlet has default properties that will be used if you do not specify specific properties to display.</span></span> <span data-ttu-id="19a6b-110">Varje cmdlet använder även samma parameternamn, **egenskapen**, för att ange vilka egenskaper som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="19a6b-110">Each cmdlet also uses the same parameter name, **Property**, to specify which properties you want to display.</span></span> <span data-ttu-id="19a6b-111">Eftersom **Format hela** visar bara en enskild egenskap dess **egenskapen** parametern tar bara ett värde, men egenskapen parametrarna för **Format-List** och **Format-Table** tar emot en lista med egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="19a6b-111">Because **Format-Wide** only shows a single property, its **Property** parameter only takes a single value, but the property parameters of **Format-List** and **Format-Table** will accept a list of property names.</span></span>

<span data-ttu-id="19a6b-112">Om du använder kommandot **Get-Process - namnet powershell** med två instanser av Windows PowerShell kör du hämta utdata som ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="19a6b-112">If you use the command **Get-Process -Name powershell** with two instances of Windows PowerShell running, you get output that looks like this:</span></span>

```
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
    995       9    30308      27996   152     2.73   2760 powershell
    331       9    23284      29084   143     1.06   3448 powershell
```

<span data-ttu-id="19a6b-113">I resten av det här avsnittet förklarar vi hur du använder **Format** -cmdletar för att ändra hur utdata från kommandot visas.</span><span class="sxs-lookup"><span data-stu-id="19a6b-113">In the rest of this section, we will explore how to use **Format** cmdlets to change the way the output of this command is displayed.</span></span>

### <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="19a6b-114">Med formatet hela för Single-utdata</span><span class="sxs-lookup"><span data-stu-id="19a6b-114">Using Format-Wide for Single-Item Output</span></span>
<span data-ttu-id="19a6b-115">Den **Format hela** cmdlet, visas som standard endast standardegenskapen för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="19a6b-115">The **Format-Wide** cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="19a6b-116">Information som associeras med varje objekt visas i en enda kolumn:</span><span class="sxs-lookup"><span data-stu-id="19a6b-116">The information associated with each object is displayed in a single column:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide

powershell                              powershell
```

<span data-ttu-id="19a6b-117">Du kan också ange en standardegenskap:</span><span class="sxs-lookup"><span data-stu-id="19a6b-117">You can also specify a non-default property:</span></span>

```
PS> Get-Process -Name powershell | Format-Wide -Property Id

2760                                    3448
```

#### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="19a6b-118">Kontrollera formatet hela bildskärm med kolumnen</span><span class="sxs-lookup"><span data-stu-id="19a6b-118">Controlling Format-Wide Display with Column</span></span>
<span data-ttu-id="19a6b-119">Med den **Format hela** cmdlet, du kan bara visa en enskild egenskap i taget.</span><span class="sxs-lookup"><span data-stu-id="19a6b-119">With the **Format-Wide** cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="19a6b-120">Detta gör att det är användbart om du vill visa enkla listor som visar endast ett element per rad.</span><span class="sxs-lookup"><span data-stu-id="19a6b-120">This makes it useful for displaying simple lists that show only one element per line.</span></span> <span data-ttu-id="19a6b-121">För att få en enkel lista, ange värdet för den **kolumnen** parameter 1 genom att skriva:</span><span class="sxs-lookup"><span data-stu-id="19a6b-121">To get a simple listing, set the value of the **Column** parameter to 1 by typing:</span></span>

```
Get-Command Format-Wide -Property Name -Column 1
```

### <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="19a6b-122">Använda Format-List för en listvy</span><span class="sxs-lookup"><span data-stu-id="19a6b-122">Using Format-List for a List View</span></span>
<span data-ttu-id="19a6b-123">Den **Format-List** cmdlet visar ett objekt i form av en lista med varje egenskap med namnet och visas på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="19a6b-123">The **Format-List** cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```
PS> Get-Process -Name powershell | Format-List

Id      : 2760
Handles : 1242
CPU     : 3.03125
Name    : powershell

Id      : 3448
Handles : 328
CPU     : 1.0625
Name    : powershell
```

<span data-ttu-id="19a6b-124">Du kan ange alla egenskaper som du vill:</span><span class="sxs-lookup"><span data-stu-id="19a6b-124">You can specify as many properties as you want:</span></span>

```
PS> Get-Process -Name powershell | Format-List -Property ProcessName,FileVersion
,StartTime,Id

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:42:00
Id          : 2760

ProcessName : powershell
FileVersion : 1.0.9567.1
StartTime   : 2006-05-24 13:54:28
Id          : 3448
```

#### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="19a6b-125">Hämta detaljerad Information genom att använda Format-List med jokertecken</span><span class="sxs-lookup"><span data-stu-id="19a6b-125">Getting Detailed Information by Using Format-List with Wildcards</span></span>
<span data-ttu-id="19a6b-126">Den **Format-List** cmdlet kan du använda ett jokertecken som värde för dess **egenskapen** parameter.</span><span class="sxs-lookup"><span data-stu-id="19a6b-126">The **Format-List** cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="19a6b-127">På så sätt kan du visa detaljerad information.</span><span class="sxs-lookup"><span data-stu-id="19a6b-127">This lets you display detailed information.</span></span> <span data-ttu-id="19a6b-128">Ofta objekt kan vara mer än vad du behöver, vilket är anledningen till Windows PowerShell inte visar alla egenskapsvärden som standard.</span><span class="sxs-lookup"><span data-stu-id="19a6b-128">Often, objects include more information than you need, which is why Windows PowerShell does not show all property values by default.</span></span> <span data-ttu-id="19a6b-129">Använd för att visa alla egenskaper för ett objekt i **Format-List-egenskapen \&#42;** kommando.</span><span class="sxs-lookup"><span data-stu-id="19a6b-129">To show all of properties of an object, use the **Format-List -Property \&#42;** command.</span></span> <span data-ttu-id="19a6b-130">Följande kommando skapar över 60 raderna i utdata för en enda process:</span><span class="sxs-lookup"><span data-stu-id="19a6b-130">The following command generates over 60 lines of output for a single process:</span></span>

```
Get-Process -Name powershell | Format-List -Property *
```

<span data-ttu-id="19a6b-131">Även om den **Format-List** kommandot är användbara för att visa information om du vill att en översikt över utdata som innehåller många objekt, en enklare tabellvy är ofta mer användbar.</span><span class="sxs-lookup"><span data-stu-id="19a6b-131">Although the **Format-List** command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

### <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="19a6b-132">Med hjälp av Format-Table för Tabular utdata</span><span class="sxs-lookup"><span data-stu-id="19a6b-132">Using Format-Table for Tabular Output</span></span>
<span data-ttu-id="19a6b-133">Om du använder den **Format-Table** med ingen egenskapsnamn som angetts för att formatera utdata från den **Get-Process** kommandot, du får exakt samma utdata som du gör utan att utföra någon formatering.</span><span class="sxs-lookup"><span data-stu-id="19a6b-133">If you use the **Format-Table** cmdlet with no property names specified to format the output of the **Get-Process** command, you get exactly the same output as you do without performing any formatting.</span></span> <span data-ttu-id="19a6b-134">Anledningen är att processer visas vanligtvis i tabellformat, eftersom de flesta Windows PowerShell-objekt.</span><span class="sxs-lookup"><span data-stu-id="19a6b-134">The reason is that processes are usually displayed in a tabular format, as are most Windows PowerShell objects.</span></span>

```
PS> Get-Process -Name powershell | Format-Table

Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
   1488       9    31568      29460   152     3.53   2760 powershell
    332       9    23140        632   141     1.06   3448 powershell
```

#### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="19a6b-135">Förbättra Format-Table utdata (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="19a6b-135">Improving Format-Table Output (AutoSize)</span></span>
<span data-ttu-id="19a6b-136">Även om en tabellvy är användbart om du vill visa en stor mängd jämförbar information, kan det vara svårt att tolka om visningen är för restriktiva för data.</span><span class="sxs-lookup"><span data-stu-id="19a6b-136">Although a tabular view is useful for displaying a lot of comparable information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="19a6b-137">Till exempel om du försöker visa processen sökväg, ID, namn och företag kan hämta du trunkerat utdata för sökvägen till processen och kolumnen företag:</span><span class="sxs-lookup"><span data-stu-id="19a6b-137">For example, if you try to display process path, ID, name, and company, you get truncated output for the process path and the company column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company

Path                Name                                 Id Company
----                ----                                 -- -------
C:\Program Files... powershell                         2836 Microsoft Corpor...
```

<span data-ttu-id="19a6b-138">Om du anger den **AutoSize** parameter när du kör den **Format-Table** kommandot Windows PowerShell beräknar kolumnbredder baserat på de data du vill visa.</span><span class="sxs-lookup"><span data-stu-id="19a6b-138">If you specify the **AutoSize** parameter when you run the **Format-Table** command, Windows PowerShell will calculate column widths based on the actual data you are going to display.</span></span> <span data-ttu-id="19a6b-139">Detta gör det **sökväg** kolumnen läsbar, men kolumnen företag förblir trunkerat:</span><span class="sxs-lookup"><span data-stu-id="19a6b-139">This makes the **Path** column readable, but the company column remains truncated:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Path,Name,Id,Company -
AutoSize

Path                                                    Name         Id Company
----                                                    ----         -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe powershell 2836 Micr...
```

<span data-ttu-id="19a6b-140">Den **Format-Table** cmdlet kan fortfarande trunkera data, men det kommer bara göra det i slutet av skärmen.</span><span class="sxs-lookup"><span data-stu-id="19a6b-140">The **Format-Table** cmdlet might still truncate data, but it will only do so at the end of the screen.</span></span> <span data-ttu-id="19a6b-141">Andra egenskaper än den sista som visas, ges så mycket storlek som de behöver för sin längsta dataelementet ska visas korrekt.</span><span class="sxs-lookup"><span data-stu-id="19a6b-141">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span> <span data-ttu-id="19a6b-142">Du kan se att företagets namn är synligt men trunkeras sökvägen om du byter platserna för **sökväg** och **företagets** i den **egenskapen** värdelistan:</span><span class="sxs-lookup"><span data-stu-id="19a6b-142">You can see that company name is visible but path is truncated if you swap the locations of **Path** and **Company** in the **Property** value list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Name,Id,Path -
AutoSize

Company               Name         Id Path
-------               ----         -- ----
Microsoft Corporation powershell 2836 C:\Program Files\Windows PowerShell\v1...
```

<span data-ttu-id="19a6b-143">Den **Format-Table** kommandot förutsätter att det kommer allt närmare en egenskap som är i början av egenskapslistan, desto mer viktigt det är.</span><span class="sxs-lookup"><span data-stu-id="19a6b-143">The **Format-Table** command assumes that the nearer a property is to the beginning of the property list, the more important it is.</span></span> <span data-ttu-id="19a6b-144">Så försöker visa egenskaper närmsta början helt.</span><span class="sxs-lookup"><span data-stu-id="19a6b-144">So it attempts to display the properties nearest the beginning completely.</span></span> <span data-ttu-id="19a6b-145">Om den **Format-Table** kommandot kan inte visas alla egenskaper som kan den ta bort vissa kolumner som visas och ange en varning.</span><span class="sxs-lookup"><span data-stu-id="19a6b-145">If the **Format-Table** command cannot display all the properties, it will remove some columns from the display and provide a warning.</span></span> <span data-ttu-id="19a6b-146">Du kan se det här beteendet om du gör **namn** senaste egenskap i listan:</span><span class="sxs-lookup"><span data-stu-id="19a6b-146">You can see this behavior if you make **Name** the last property in the list:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Property Company,Path,Id,Name -
AutoSize

WARNING: column "Name" does not fit into the display and was removed.

Company               Path                                                    I
                                                                              d
-------               ----                                                    -
Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\powershell.exe 6
```

<span data-ttu-id="19a6b-147">ID-kolumnen trunkeras så att den passar in i listan i resultatet ovan och kolumnrubrikerna staplade.</span><span class="sxs-lookup"><span data-stu-id="19a6b-147">In the output above, the ID column is truncated to make it fit into the listing, and the column headings are stacked up.</span></span> <span data-ttu-id="19a6b-148">Ändra storlek på kolumnerna automatiskt utför alltid inte vad du vill.</span><span class="sxs-lookup"><span data-stu-id="19a6b-148">Automatically resizing the columns does not always do what you want.</span></span>

#### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="19a6b-149">Byta Format-Table utdata i kolumner (Radbryt)</span><span class="sxs-lookup"><span data-stu-id="19a6b-149">Wrapping Format-Table Output in Columns (Wrap)</span></span>
<span data-ttu-id="19a6b-150">Du kan tvinga långa **Format-Table** data att omsluta i kolumnen visa med hjälp av den **omsluter** parameter.</span><span class="sxs-lookup"><span data-stu-id="19a6b-150">You can force lengthy **Format-Table** data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="19a6b-151">Med hjälp av den **omsluter** parametern enbart inte nödvändigtvis att utföra vad du förväntar dig, eftersom den använder standardinställningarna om du inte också anger **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="19a6b-151">Using the **Wrap** parameter alone will not necessarily do what you expect, since it uses default settings if you do not also specify **AutoSize**:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -Property Name,Id,Company,
Path

Name                                 Id Company             Path
----                                 -- -------             ----
powershell                         2836 Microsoft Corporati C:\Program Files\Wi
                                        on                  ndows PowerShell\v1
                                                            .0\powershell.exe
```

<span data-ttu-id="19a6b-152">En fördel med den **omsluter** parametern ensamt är att den inte fördröjer bearbetning mycket.</span><span class="sxs-lookup"><span data-stu-id="19a6b-152">An advantage of using the **Wrap** parameter by itself is that it does not slow down processing very much.</span></span> <span data-ttu-id="19a6b-153">Om du gör en lista över rekursiv fil för ett stort directory-system, det kan ta mycket lång tid och använda mycket minne innan de första utdata-objekt om du använder **AutoSize**.</span><span class="sxs-lookup"><span data-stu-id="19a6b-153">If you perform a recursive file listing of a large directory system, it might take a very long time and use a lot of memory before displaying the first output items if you use **AutoSize**.</span></span>

<span data-ttu-id="19a6b-154">Om du inte tänker på systembelastning sedan **AutoSize** fungerar bra med den **omsluter** parameter.</span><span class="sxs-lookup"><span data-stu-id="19a6b-154">If you are not concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span> <span data-ttu-id="19a6b-155">De första kolumnerna är alltid tilldelats så mycket bredd som de behöver för att visa objekt på en rad, precis som när du anger **AutoSize** utan den **omsluter** parameter.</span><span class="sxs-lookup"><span data-stu-id="19a6b-155">The initial columns are always allotted as much width as they need to display items on one line, just as when you specify **AutoSize** without the **Wrap** parameter.</span></span> <span data-ttu-id="19a6b-156">Den enda skillnaden är att den sista kolumnen kommer att omslutas om det behövs:</span><span class="sxs-lookup"><span data-stu-id="19a6b-156">The only difference is that the final column will be wrapped if necessary:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Company,Path

Name         Id Company               Path
----         -- -------               ----
powershell 2836 Microsoft Corporation C:\Program Files\Windows PowerShell\v1.0\
                                      powershell.exe
```

<span data-ttu-id="19a6b-157">Vissa kolumner kanske inte visas om du anger de bredaste kolumnerna först, så det är säkrast att ange de minsta dataelement först.</span><span class="sxs-lookup"><span data-stu-id="19a6b-157">Some columns might not be displayed if you specify the widest columns first, so it is safest to specify the smallest data elements first.</span></span> <span data-ttu-id="19a6b-158">I följande exempel tar vi ange mycket brett sökvägselement först och även med radbrytningar, vi fortfarande förlorar slutliga **namn** kolumn:</span><span class="sxs-lookup"><span data-stu-id="19a6b-158">In the following example, we specify the extremely wide path element first, and even with wrapping, we still lose the final **Name** column:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Path,I
d,Company,Name

WARNING: column "Name" does not fit into the display and was removed.

Path                                                      Id Company
----                                                      -- -------
C:\Program Files\Windows PowerShell\v1.0\powershell.exe 2836 Microsoft Corporat
                                                             ion
```

#### <a name="organizing-table-output--groupby"></a><span data-ttu-id="19a6b-159">Ordna Tabellutdata (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="19a6b-159">Organizing Table Output (-GroupBy)</span></span>
<span data-ttu-id="19a6b-160">En annan användbar parametern för tabular utdata-kontroll är **GroupBy**.</span><span class="sxs-lookup"><span data-stu-id="19a6b-160">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="19a6b-161">Längre tabular listor kan i synnerhet vara svåra att jämföra.</span><span class="sxs-lookup"><span data-stu-id="19a6b-161">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="19a6b-162">Den **GroupBy** parametern grupper utdata baserat på ett värde för egenskapen.</span><span class="sxs-lookup"><span data-stu-id="19a6b-162">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="19a6b-163">Vi kan till exempel gruppera processer av företag för enklare kontroll utelämna företagets värdet från egenskapen lista:</span><span class="sxs-lookup"><span data-stu-id="19a6b-163">For example, we can group processes by company for easier inspection, omitting the company value from the property listing:</span></span>

```
PS> Get-Process -Name powershell | Format-Table -Wrap -AutoSize -Property Name,I
d,Path -GroupBy Company

   Company: Microsoft Corporation

Name         Id Path
----         -- ----
powershell 1956 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
powershell 2656 C:\Program Files\Windows PowerShell\v1.0\powershell.exe
```

