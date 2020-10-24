---
ms.date: 11/22/2019
keywords: powershell,cmdlet
title: Använd formatkommandon för att ändra utdatavyn
description: PowerShell har ett utöknings Bart format system som gör att du kan presentera utdata i listor, tabeller eller anpassade layouter.
ms.openlocfilehash: ebb285a19c7fe1bc80608385f9e2842469e95817
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500954"
---
# <a name="using-format-commands-to-change-output-view"></a><span data-ttu-id="70814-104">Använd formatkommandon för att ändra utdatavyn</span><span class="sxs-lookup"><span data-stu-id="70814-104">Using Format Commands to Change Output View</span></span>

<span data-ttu-id="70814-105">PowerShell har en uppsättning cmdletar som gör att du kan styra hur egenskaper visas för specifika objekt.</span><span class="sxs-lookup"><span data-stu-id="70814-105">PowerShell has a set of cmdlets that allow you to control how properties are displayed for particular objects.</span></span> <span data-ttu-id="70814-106">Namnen på alla cmdletar börjar med verbet `Format` .</span><span class="sxs-lookup"><span data-stu-id="70814-106">The names of all the cmdlets begin with the verb `Format`.</span></span> <span data-ttu-id="70814-107">De låter dig välja vilka egenskaper du vill visa.</span><span class="sxs-lookup"><span data-stu-id="70814-107">They let you select which properties you want to show.</span></span>

```powershell
Get-Command -Verb Format -Module Microsoft.PowerShell.Utility
```

```Output
CommandType     Name               Version    Source
-----------     ----               -------    ------
Cmdlet          Format-Custom      6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Hex         6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-List        6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Table       6.1.0.0    Microsoft.PowerShell.Utility
Cmdlet          Format-Wide        6.1.0.0    Microsoft.PowerShell.Utility
```

<span data-ttu-id="70814-108">I den här artikeln `Format-Wide` beskrivs `Format-List` cmdletarna,, och `Format-Table` .</span><span class="sxs-lookup"><span data-stu-id="70814-108">This article describes the `Format-Wide`, `Format-List`, and `Format-Table` cmdlets.</span></span>

<span data-ttu-id="70814-109">Varje objekt typ i PowerShell har standard egenskaper som används när du inte anger vilka egenskaper som ska visas.</span><span class="sxs-lookup"><span data-stu-id="70814-109">Each object type in PowerShell has default properties that are used when you don't specify which properties to display.</span></span> <span data-ttu-id="70814-110">Varje cmdlet använder också samma **egenskaps** parameter för att ange vilka egenskaper som du vill visa.</span><span class="sxs-lookup"><span data-stu-id="70814-110">Each cmdlet also uses the same **Property** parameter to specify which properties you want to display.</span></span> <span data-ttu-id="70814-111">Eftersom `Format-Wide` bara visar en enskild egenskap, tar **egenskaps** parametern bara till ett enda värde, men egenskaps parametrarna för `Format-List` och `Format-Table` accepterar en lista med egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="70814-111">Because `Format-Wide` only shows a single property, its **Property** parameter only takes a single value, but the property parameters of `Format-List` and `Format-Table` accept a list of property names.</span></span>

<span data-ttu-id="70814-112">I det här exemplet visar standardutdata för `Get-Process` cmdleten att vi har två instanser av Internet Explorer igång.</span><span class="sxs-lookup"><span data-stu-id="70814-112">In this example, the default output of `Get-Process` cmdlet shows that we have two instances of Internet Explorer running.</span></span>

```powershell
Get-Process -Name iexplore
```

<span data-ttu-id="70814-113">Standardformat för **process** objekt visar de egenskaper som visas här:</span><span class="sxs-lookup"><span data-stu-id="70814-113">The default format for **Process** objects displays the properties shown here:</span></span>

```Output
 NPM(K)    PM(M)      WS(M)     CPU(s)      Id  SI ProcessName
 ------    -----      -----     ------      --  -- -----------
     32    25.52      10.25      13.11   12808   1 iexplore
     52    11.46      26.46       3.55   21748   1 iexplore
```

## <a name="using-format-wide-for-single-item-output"></a><span data-ttu-id="70814-114">Använda Format-Wide för Single-Item utdata</span><span class="sxs-lookup"><span data-stu-id="70814-114">Using Format-Wide for Single-Item Output</span></span>

<span data-ttu-id="70814-115">`Format-Wide`-Cmdleten visar som standard endast standard egenskapen för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="70814-115">The `Format-Wide` cmdlet, by default, displays only the default property of an object.</span></span> <span data-ttu-id="70814-116">Informationen som är kopplad till varje objekt visas i en enda kolumn:</span><span class="sxs-lookup"><span data-stu-id="70814-116">The information associated with each object is displayed in a single column:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide
```

```Output
Format-Custom          Format-Hex
Format-List            Format-Table
Format-Wide
```

<span data-ttu-id="70814-117">Du kan också ange en egenskap som inte är standard:</span><span class="sxs-lookup"><span data-stu-id="70814-117">You can also specify a non-default property:</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun
```

```Output
Custom                 Hex
List                   Table
Wide
```

### <a name="controlling-format-wide-display-with-column"></a><span data-ttu-id="70814-118">Styra Format-Wide Visa med kolumn</span><span class="sxs-lookup"><span data-stu-id="70814-118">Controlling Format-Wide Display with Column</span></span>

<span data-ttu-id="70814-119">Med `Format-Wide` cmdleten kan du bara visa en enskild egenskap i taget.</span><span class="sxs-lookup"><span data-stu-id="70814-119">With the `Format-Wide` cmdlet, you can only display a single property at a time.</span></span> <span data-ttu-id="70814-120">Detta gör det användbart för att visa stora listor i flera kolumner.</span><span class="sxs-lookup"><span data-stu-id="70814-120">This makes it useful for displaying large lists in multiple columns.</span></span>

```powershell
Get-Command -Verb Format | Format-Wide -Property Noun -Column 3
```

```Output
Custom                 Hex                  List
Table                  Wide

```

## <a name="using-format-list-for-a-list-view"></a><span data-ttu-id="70814-121">Använda Format-List för att visa en listvy</span><span class="sxs-lookup"><span data-stu-id="70814-121">Using Format-List for a List View</span></span>

<span data-ttu-id="70814-122">`Format-List`Cmdleten visar ett objekt i form av en lista, där varje egenskap har etiketten och visas på en separat rad:</span><span class="sxs-lookup"><span data-stu-id="70814-122">The `Format-List` cmdlet displays an object in the form of a listing, with each property labeled and displayed on a separate line:</span></span>

```powershell
Get-Process -Name iexplore | Format-List
```

```Output
Id      : 12808
Handles : 578
CPU     : 13.140625
SI      : 1
Name    : iexplore

Id      : 21748
Handles : 641
CPU     : 3.59375
SI      : 1
Name    : iexplore
```

<span data-ttu-id="70814-123">Du kan ange så många egenskaper du vill:</span><span class="sxs-lookup"><span data-stu-id="70814-123">You can specify as many properties as you want:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property ProcessName,FileVersion,StartTime,Id
```

```Output
ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:58 AM
Id          : 12808

ProcessName : iexplore
FileVersion : 11.00.18362.1 (WinBuild.160101.0800)
StartTime   : 10/22/2019 11:23:57 AM
Id          : 21748
```

### <a name="getting-detailed-information-by-using-format-list-with-wildcards"></a><span data-ttu-id="70814-124">Få detaljerad information med hjälp av Format-List med jokertecken</span><span class="sxs-lookup"><span data-stu-id="70814-124">Getting Detailed Information by Using Format-List with Wildcards</span></span>

<span data-ttu-id="70814-125">Med `Format-List` cmdleten kan du använda jokertecken som värde för **egenskaps** parametern.</span><span class="sxs-lookup"><span data-stu-id="70814-125">The `Format-List` cmdlet lets you use a wildcard as the value of its **Property** parameter.</span></span> <span data-ttu-id="70814-126">På så sätt kan du Visa detaljerad information.</span><span class="sxs-lookup"><span data-stu-id="70814-126">This lets you display detailed information.</span></span> <span data-ttu-id="70814-127">Objekt innehåller ofta mer information än vad du behöver, vilket är anledningen till att PowerShell inte visar alla egenskaps värden som standard.</span><span class="sxs-lookup"><span data-stu-id="70814-127">Often, objects include more information than you need, which is why PowerShell doesn't show all property values by default.</span></span> <span data-ttu-id="70814-128">Om du vill visa alla egenskaper för ett objekt använder du `Format-List -Property *` kommandot.</span><span class="sxs-lookup"><span data-stu-id="70814-128">To show all of properties of an object, use the `Format-List -Property *` command.</span></span> <span data-ttu-id="70814-129">Följande kommando genererar över 60 rader utdata för en enda process:</span><span class="sxs-lookup"><span data-stu-id="70814-129">The following command generates over 60 lines of output for a single process:</span></span>

```powershell
Get-Process -Name iexplore | Format-List -Property *
```

<span data-ttu-id="70814-130">Även `Format-List` om kommandot är användbart för att visa information, är en enklare tabellvy ofta mer användbar om du vill ha en översikt över utdata som innehåller många objekt.</span><span class="sxs-lookup"><span data-stu-id="70814-130">Although the `Format-List` command is useful for showing detail, if you want an overview of output that includes many items, a simpler tabular view is often more useful.</span></span>

## <a name="using-format-table-for-tabular-output"></a><span data-ttu-id="70814-131">Använda Format-Table för tabell data</span><span class="sxs-lookup"><span data-stu-id="70814-131">Using Format-Table for Tabular Output</span></span>

<span data-ttu-id="70814-132">Om du använder `Format-Table` cmdleten utan några egenskaps namn för att formatera `Get-Process` kommandots utdata får du exakt samma utdata som du gör utan en `Format` cmdlet.</span><span class="sxs-lookup"><span data-stu-id="70814-132">If you use the `Format-Table` cmdlet with no property names specified to format the output of the `Get-Process` command, you get exactly the same output as you do without a `Format` cmdlet.</span></span> <span data-ttu-id="70814-133">Som standard visar PowerShell **process** objekt i tabell format.</span><span class="sxs-lookup"><span data-stu-id="70814-133">By default, PowerShell displays **Process** objects in a tabular format.</span></span>

```powershell
Get-Service -Name win* | Format-Table
```

```Output
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  WinHttpAutoProx... WinHTTP Web Proxy Auto-Discovery Se...
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Manag...
```

### <a name="improving-format-table-output-autosize"></a><span data-ttu-id="70814-134">Förbättra Format-Table-utdata (AutoSize)</span><span class="sxs-lookup"><span data-stu-id="70814-134">Improving Format-Table Output (AutoSize)</span></span>

<span data-ttu-id="70814-135">Även om en tabellvy är användbar för att visa massor av information kan det vara svårt att tolka om visningen är för smal för data.</span><span class="sxs-lookup"><span data-stu-id="70814-135">Although a tabular view is useful for displaying lots of information, it may be difficult to interpret if the display is too narrow for the data.</span></span> <span data-ttu-id="70814-136">I föregående exempel trunkeras utdata.</span><span class="sxs-lookup"><span data-stu-id="70814-136">In the previous example, the output is truncated.</span></span> <span data-ttu-id="70814-137">Om du anger parametern **AutoSize** när du kör `Format-Table` kommandot beräknar PowerShell kolumn bredden baserat på de faktiska data som visas.</span><span class="sxs-lookup"><span data-stu-id="70814-137">If you specify the **AutoSize** parameter when you run the `Format-Table` command, PowerShell calculates column widths based on the actual data displayed.</span></span> <span data-ttu-id="70814-138">Det gör kolumnerna läsbara.</span><span class="sxs-lookup"><span data-stu-id="70814-138">This makes the columns readable.</span></span>

```powershell
Get-Service -Name win* | Format-Table -AutoSize
```

```Output
Status  Name                DisplayName
------  ----                -----------
Running WinDefend           Windows Defender Antivirus Service
Running WinHttpAutoProxySvc WinHTTP Web Proxy Auto-Discovery Service
Running Winmgmt             Windows Management Instrumentation
Running WinRM               Windows Remote Management (WS-Management)
```

<span data-ttu-id="70814-139">`Format-Table`Cmdleten kan fortfarande trunkera data, men den trunkeras bara i slutet av skärmen.</span><span class="sxs-lookup"><span data-stu-id="70814-139">The `Format-Table` cmdlet might still truncate data, but it only truncates at the end of the screen.</span></span> <span data-ttu-id="70814-140">Andra egenskaper än den sista som visas, har samma storlek som de behöver för att det ska visas på rätt data element.</span><span class="sxs-lookup"><span data-stu-id="70814-140">Properties, other than the last one displayed, are given as much size as they need for their longest data element to display correctly.</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -AutoSize
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc, iphl…
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms, TPHKLO…
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="70814-141">`Format-Table`Kommandot förutsätter att egenskaper anges i prioritetsordning.</span><span class="sxs-lookup"><span data-stu-id="70814-141">The `Format-Table` command assumes that properties are listed in order of importance.</span></span> <span data-ttu-id="70814-142">Det försöker då att helt Visa egenskaperna närmast början.</span><span class="sxs-lookup"><span data-stu-id="70814-142">So it attempts to fully display the properties nearest the beginning.</span></span> <span data-ttu-id="70814-143">Om `Format-Table` kommandot inte kan visa alla egenskaper tas vissa kolumner bort från visningen.</span><span class="sxs-lookup"><span data-stu-id="70814-143">If the `Format-Table` command can't display all the properties, it removes some columns from the display.</span></span> <span data-ttu-id="70814-144">Du kan se det här beteendet i **DependentServices** -egenskapen i föregående exempel.</span><span class="sxs-lookup"><span data-stu-id="70814-144">You can see this behavior in the **DependentServices** property previous example.</span></span>

### <a name="wrapping-format-table-output-in-columns-wrap"></a><span data-ttu-id="70814-145">Radbryt Format-Table utdata i kolumner (radbyte)</span><span class="sxs-lookup"><span data-stu-id="70814-145">Wrapping Format-Table Output in Columns (Wrap)</span></span>

<span data-ttu-id="70814-146">Du kan tvinga långa `Format-Table` data att radbrytas i sin visnings kolumn med hjälp av parametern **wrap** .</span><span class="sxs-lookup"><span data-stu-id="70814-146">You can force lengthy `Format-Table` data to wrap within its display column by using the **Wrap** parameter.</span></span> <span data-ttu-id="70814-147">**Det går** inte att använda den omslutna parametern, eftersom den använder standardinställningar om du inte också anger **AutoSize**:</span><span class="sxs-lookup"><span data-stu-id="70814-147">Using the **Wrap** parameter may not do what you expect, since it uses default settings if you don't also specify **AutoSize**:</span></span>

```powershell
Get-Service -Name win* | Format-Table -Property Name,Status,StartType,DisplayName,DependentServices -Wrap
```

```Output
Name                 Status StartType DisplayName                               DependentServi
                                                                                ces
----                 ------ --------- -----------                               --------------
WinDefend           Running Automatic Windows Defender Antivirus Service        {}
WinHttpAutoProxySvc Running    Manual WinHTTP Web Proxy Auto-Discovery Service  {NcaSvc,
                                                                                iphlpsvc}
Winmgmt             Running Automatic Windows Management Instrumentation        {vmms,
                                                                                TPHKLOAD,
                                                                                SUService,
                                                                                smstsmgr…}
WinRM               Running Automatic Windows Remote Management (WS-Management) {}
```

<span data-ttu-id="70814-148">Att använda **wrap** -parametern i sig saktar inte ned bearbetningen väldigt mycket.</span><span class="sxs-lookup"><span data-stu-id="70814-148">Using the **Wrap** parameter by itself doesn't slow down processing very much.</span></span> <span data-ttu-id="70814-149">Att använda **AutoSize** för att formatera en rekursiv fil listning av en stor katalog struktur kan dock ta lång tid och använda mycket minne innan de första utmatnings objekten visas.</span><span class="sxs-lookup"><span data-stu-id="70814-149">However, using **AutoSize** to format a recursive file listing of a large directory structure can take a long time and use lots of memory before displaying the first output items.</span></span>

<span data-ttu-id="70814-150">Om du inte bekymrar dig om system belastningen **fungerar** autopassering bra med **wrap** -parametern.</span><span class="sxs-lookup"><span data-stu-id="70814-150">If you aren't concerned about system load, then **AutoSize** works well with the **Wrap** parameter.</span></span>
<span data-ttu-id="70814-151">De ursprungliga kolumnerna använder fortfarande så mycket bredd som det behövs för att visa objekt på en rad, men den sista kolumnen är omsluten, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="70814-151">The initial columns still use as much width as needed to display items on one line, but the final column is wrapped, if necessary.</span></span>

> [!NOTE]
> <span data-ttu-id="70814-152">Vissa kolumner kanske inte visas när du anger de bredaste kolumnerna först.</span><span class="sxs-lookup"><span data-stu-id="70814-152">Some columns may not be displayed when you specify the widest columns first.</span></span> <span data-ttu-id="70814-153">För bästa resultat anger du de minsta data elementen först.</span><span class="sxs-lookup"><span data-stu-id="70814-153">For best results, specify the smallest data elements first.</span></span>

<span data-ttu-id="70814-154">I följande exempel anger vi de bredaste egenskaperna först.</span><span class="sxs-lookup"><span data-stu-id="70814-154">In the following example, we specify the widest properties first.</span></span>

```powershell
Get-Process -Name iexplore | Format-Table -Wrap -AutoSize -Property FileVersion,Path,Name,Id
```

<span data-ttu-id="70814-155">Med rad brytning utelämnas kolumnen slutligt **ID** :</span><span class="sxs-lookup"><span data-stu-id="70814-155">Even with wrapping, the final **Id** column is omitted:</span></span>

```Output
FileVersion                          Path                                                  Nam
                                                                                           e
-----------                          ----                                                  ---
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files (x86)\Internet Explorer\IEXPLORE.EXE iex
                                                                                           plo
                                                                                           re
11.00.18362.1 (WinBuild.160101.0800) C:\Program Files\Internet Explorer\iexplore.exe       iex
                                                                                           plo
                                                                                           re
```

### <a name="organizing-table-output--groupby"></a><span data-ttu-id="70814-156">Organisera tabellens utdata (-GroupBy)</span><span class="sxs-lookup"><span data-stu-id="70814-156">Organizing Table Output (-GroupBy)</span></span>

<span data-ttu-id="70814-157">En annan användbar parameter för kontroll av tabellens utdata är **groupby**.</span><span class="sxs-lookup"><span data-stu-id="70814-157">Another useful parameter for tabular output control is **GroupBy**.</span></span> <span data-ttu-id="70814-158">Längre tabell listor kan vara svåra att jämföra.</span><span class="sxs-lookup"><span data-stu-id="70814-158">Longer tabular listings in particular may be hard to compare.</span></span> <span data-ttu-id="70814-159">Parametern **groupby** grupperar utdata baserat på ett egenskaps värde.</span><span class="sxs-lookup"><span data-stu-id="70814-159">The **GroupBy** parameter groups output based on a property value.</span></span> <span data-ttu-id="70814-160">Vi kan till exempel gruppera tjänster efter **StartType** för enklare granskning och utelämna **StartType** -värdet från egenskaps listan:</span><span class="sxs-lookup"><span data-stu-id="70814-160">For example, we can group services by **StartType** for easier inspection, omitting the **StartType** value from the property listing:</span></span>

```powershell
Get-Service -Name win* | Sort-Object StartType | Format-Table -GroupBy StartType
```

```Output
   StartType: Automatic
Status   Name               DisplayName
------   ----               -----------
Running  WinDefend          Windows Defender Antivirus Service
Running  Winmgmt            Windows Management Instrumentation
Running  WinRM              Windows Remote Management (WS-Managem…

   StartType: Manual
Status   Name               DisplayName
------   ----               -----------
Running  WinHttpAutoProxyS… WinHTTP Web Proxy Auto-Discovery Serv…
```
