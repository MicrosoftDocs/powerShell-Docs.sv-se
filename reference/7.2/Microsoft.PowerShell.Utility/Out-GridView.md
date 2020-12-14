---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 19a53b5b14d2dfdb513fbbda4c55ba0df37ab1c0
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709067"
---
# <span data-ttu-id="92f27-102">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="92f27-102">Out-GridView</span></span>

## <span data-ttu-id="92f27-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="92f27-103">SYNOPSIS</span></span>
<span data-ttu-id="92f27-104">Skickar utdata till en interaktiv tabell i ett separat fönster.</span><span class="sxs-lookup"><span data-stu-id="92f27-104">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="92f27-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="92f27-105">SYNTAX</span></span>

### <span data-ttu-id="92f27-106">PassThru (standard)</span><span class="sxs-lookup"><span data-stu-id="92f27-106">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="92f27-107">Vänta</span><span class="sxs-lookup"><span data-stu-id="92f27-107">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="92f27-108">OutputMode</span><span class="sxs-lookup"><span data-stu-id="92f27-108">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="92f27-109">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="92f27-109">DESCRIPTION</span></span>

<span data-ttu-id="92f27-110">`Out-GridView`Cmdleten skickar utdata från ett kommando till ett fönster för rutnätsvy där utdata visas i en interaktiv tabell.</span><span class="sxs-lookup"><span data-stu-id="92f27-110">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="92f27-111">Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="92f27-111">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="92f27-112">Du kan använda följande funktioner i tabellen för att undersöka dina data:</span><span class="sxs-lookup"><span data-stu-id="92f27-112">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="92f27-113">Dölj, Visa och ordna om kolumner</span><span class="sxs-lookup"><span data-stu-id="92f27-113">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="92f27-114">Sortera rader</span><span class="sxs-lookup"><span data-stu-id="92f27-114">Sort rows</span></span>
- <span data-ttu-id="92f27-115">Snabb filter</span><span class="sxs-lookup"><span data-stu-id="92f27-115">Quick Filter</span></span>
- <span data-ttu-id="92f27-116">Lägg till villkors filter</span><span class="sxs-lookup"><span data-stu-id="92f27-116">Add Criteria Filter</span></span>
- <span data-ttu-id="92f27-117">Kopiera och klistra in</span><span class="sxs-lookup"><span data-stu-id="92f27-117">Copy and paste</span></span>

<span data-ttu-id="92f27-118">Fullständiga instruktioner finns i avsnittet [anteckningar](#notes) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="92f27-118">For full instructions, see the [Notes](#notes) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="92f27-119">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="92f27-119">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="92f27-120">Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="92f27-120">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span> <span data-ttu-id="92f27-121">En plattforms oberoende version av denna cmdlet finns i [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) -modulen i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="92f27-121">For a cross-platform version of this cmdlet, see the [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) module in the PowerShell Gallery.</span></span>

## <span data-ttu-id="92f27-122">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="92f27-122">EXAMPLES</span></span>

### <span data-ttu-id="92f27-123">Exempel 1: utmatnings processer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-123">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="92f27-124">Det här exemplet hämtar processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-124">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="92f27-125">Exempel 2: använda en variabel för att visa processer i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-125">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="92f27-126">Det här exemplet hämtar också processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-126">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="92f27-127">Utdata från `Get-Process` cmdleten sparas i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="92f27-127">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="92f27-128">Sedan `$P` är skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-128">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="92f27-129">Exempel 3: Visa markerade egenskaper i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-129">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="92f27-130">I det här exemplet visas valda egenskaper för de processer som körs i en rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-130">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="92f27-131">Utdatan från `Get-Process` är skickas `Select-Object` till för att välja egenskaper för **namn**, för-och **PeakWorkingSet** .</span><span class="sxs-lookup"><span data-stu-id="92f27-131">The output of `Get-Process` is piped to `Select-Object` to select the **Name**, **WorkingSet**, and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="92f27-132">En annan pipeline-operator skickar filtrerade objekt till `Sort-Object` cmdleten för att sortera dem i fallande ordning efter värdet för den **aktiva** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="92f27-132">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="92f27-133">Sedan är de sorterade resultaten skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-133">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="92f27-134">Nu kan du använda funktionerna i diagramvyn för att söka, sortera och filtrera data.</span><span class="sxs-lookup"><span data-stu-id="92f27-134">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="92f27-135">Exempel 4: spara utdata till en variabel och sedan Visa en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-135">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="92f27-136">Det här exemplet sparar cmdlet-utdata i en variabel och skickar den sedan till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-136">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="92f27-137">`Get-ChildItem` hämtar alla filer i installations katalogen för PowerShell och dess under kataloger med hjälp av den `$PSHOME` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="92f27-137">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="92f27-138">Parenteserna i kommandot fastställer ordningen för åtgärder.</span><span class="sxs-lookup"><span data-stu-id="92f27-138">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="92f27-139">Därför sparas utdata från `Get-ChildItem` kommandot i `$A` variabeln innan det skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-139">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="92f27-140">Exempel 5: utmatnings processer för en angiven dator till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-140">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="92f27-141">I det här exemplet visas de processer som körs på Server01-datorn i ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-141">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="92f27-142">Examle använder `ogv` , vilket är aliaset för `Out-GridView` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="92f27-142">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="92f27-143">Parametern **title** anger fönstrets rubrik.</span><span class="sxs-lookup"><span data-stu-id="92f27-143">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="92f27-144">Exempel 6: Spara data från fjärrdatorer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="92f27-144">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="92f27-145">Det här exemplet visar hur du skickar data som samlas in från fjärrdatorer till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-145">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="92f27-146">`Invoke-Command` körs `Get-Culture` på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="92f27-146">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="92f27-147">Resulterande data är skickas `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-147">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="92f27-148">Observera att skript blocket som körs på fjärrdatorn inte innehåller `Out-GridView` kommandot.</span><span class="sxs-lookup"><span data-stu-id="92f27-148">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="92f27-149">Om den gjorde det kunde kommandot inte utföras när det försökte öppna ett fönster för rutnätsvy på var och en av de fjärranslutna datorerna.</span><span class="sxs-lookup"><span data-stu-id="92f27-149">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="92f27-150">Exempel 7: skicka flera objekt via `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="92f27-150">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="92f27-151">I det här exemplet kan du välja flera processer i `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="92f27-151">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="92f27-152">De processer som du väljer skickas till `Export-Csv` kommandot och skrivs till `ProcessLog.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="92f27-152">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="92f27-153">Med parametern **Passthru** `Out-GridView` kan du skicka flera objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="92f27-153">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="92f27-154">Parametern **Passthru** motsvarar användningen av **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="92f27-154">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="92f27-155">Exempel 8: skapa en Windows-genväg till `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="92f27-155">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="92f27-156">Det här exemplet visar hur du använder **wait** -parametern för `Out-GridView` för att skapa en Windows-genväg till `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="92f27-156">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="92f27-157">Den här kommando raden kan användas i en Windows-genväg.</span><span class="sxs-lookup"><span data-stu-id="92f27-157">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="92f27-158">Utan parametern **wait** avslutas PowerShell så snart `Out-GridView` fönstret har öppnats, vilket skulle stänga `Out-GridView` fönstret nästan omedelbart.</span><span class="sxs-lookup"><span data-stu-id="92f27-158">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="92f27-159">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="92f27-159">PARAMETERS</span></span>

### <span data-ttu-id="92f27-160">– InputObject</span><span class="sxs-lookup"><span data-stu-id="92f27-160">-InputObject</span></span>

<span data-ttu-id="92f27-161">Anger objekt som cmdleten accepterar som ininformation för `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-161">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="92f27-162">När du använder parametern **InputObject** för att skicka en samling objekt till `Out-GridView` , `Out-GridView` behandlar samlingen som ett samlings objekt och visar en rad som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="92f27-162">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="92f27-163">Om du vill visa varje objekt i samlingen använder du en pipeline-operator ( `|` ) för att skicka objekt till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-163">To display the each object in the collection, use a pipeline operator (`|`) to send objects to `Out-GridView`.</span></span>

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="92f27-164">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="92f27-164">-OutputMode</span></span>

<span data-ttu-id="92f27-165">Anger de objekt som det interaktiva fönstret skickar nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="92f27-165">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="92f27-166">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="92f27-166">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="92f27-167">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="92f27-167">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="92f27-168">Värdena för den här parametern avgör hur många objekt du kan skicka pipelinen.</span><span class="sxs-lookup"><span data-stu-id="92f27-168">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="92f27-169">Inga.</span><span class="sxs-lookup"><span data-stu-id="92f27-169">None.</span></span>  <span data-ttu-id="92f27-170">Inga objekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-170">No items.</span></span> <span data-ttu-id="92f27-171">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="92f27-171">This is the default value.</span></span>
- <span data-ttu-id="92f27-172">Samma.</span><span class="sxs-lookup"><span data-stu-id="92f27-172">Single.</span></span> <span data-ttu-id="92f27-173">Noll objekt eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-173">Zero items or one item.</span></span> <span data-ttu-id="92f27-174">Använd det här värdet när nästa kommando bara kan ta ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-174">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="92f27-175">Flera.</span><span class="sxs-lookup"><span data-stu-id="92f27-175">Multiple.</span></span> <span data-ttu-id="92f27-176">Noll, ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-176">Zero, one, or many items.</span></span> <span data-ttu-id="92f27-177">Använd det här värdet när nästa kommando kan ta flera inobjekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-177">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="92f27-178">Värdet motsvarar parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="92f27-178">This value is equivalent to the **Passthru** parameter.</span></span>

```yaml
Type: Microsoft.PowerShell.Commands.OutputModeOption
Parameter Sets: OutputMode
Aliases:
Accepted values: None, Single, Multiple

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92f27-179">– PassThru</span><span class="sxs-lookup"><span data-stu-id="92f27-179">-PassThru</span></span>

<span data-ttu-id="92f27-180">Anger att cmdleten skickar objekt från det interaktiva fönstret nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="92f27-180">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="92f27-181">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="92f27-181">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="92f27-182">Den här parametern motsvarar att använda **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="92f27-182">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="92f27-183">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="92f27-183">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="92f27-184">Shift-klicka och Ctrl-klicka stöds.</span><span class="sxs-lookup"><span data-stu-id="92f27-184">Shift-click and Ctrl-click are supported.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: PassThru
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92f27-185">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="92f27-185">-Title</span></span>

<span data-ttu-id="92f27-186">Anger den text som visas i namn listen för `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="92f27-186">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="92f27-187">Som standard visar namn listen det kommando som anropar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="92f27-187">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92f27-188">– Vänta</span><span class="sxs-lookup"><span data-stu-id="92f27-188">-Wait</span></span>

<span data-ttu-id="92f27-189">Anger att cmdleten ignorerar kommando tolken och förhindrar att Windows PowerShell stängs tills `Out-GridView` fönstret har stängts.</span><span class="sxs-lookup"><span data-stu-id="92f27-189">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="92f27-190">Som standard returnerar kommando tolken när `Out-GridView` fönstret öppnas.</span><span class="sxs-lookup"><span data-stu-id="92f27-190">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="92f27-191">Med den här funktionen kan du använda `Out-GridView` cmdlets i Windows-genvägar.</span><span class="sxs-lookup"><span data-stu-id="92f27-191">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="92f27-192">När `Out-GridView` används i en genväg utan parametern **wait** , `Out-GridView` visas fönstret bara tillfälligt innan PowerShell stängs.</span><span class="sxs-lookup"><span data-stu-id="92f27-192">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: Wait
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="92f27-193">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="92f27-193">CommonParameters</span></span>

<span data-ttu-id="92f27-194">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="92f27-194">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="92f27-195">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="92f27-195">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="92f27-196">INDATA</span><span class="sxs-lookup"><span data-stu-id="92f27-196">INPUTS</span></span>

### <span data-ttu-id="92f27-197">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="92f27-197">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="92f27-198">Du kan skicka valfritt objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="92f27-198">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="92f27-199">UTDATA</span><span class="sxs-lookup"><span data-stu-id="92f27-199">OUTPUTS</span></span>

### <span data-ttu-id="92f27-200">Inga</span><span class="sxs-lookup"><span data-stu-id="92f27-200">None</span></span>

<span data-ttu-id="92f27-201">Normalt `Out-GridView` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="92f27-201">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="92f27-202">När du använder parametern **Passthru** returneras objekten som representerar de valda raderna till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="92f27-202">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="92f27-203">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="92f27-203">NOTES</span></span>

<span data-ttu-id="92f27-204">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="92f27-204">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="92f27-205">Du kan inte använda ett fjärran slutet kommando för att öppna ett fönster för rutnätsvy på en annan dator.</span><span class="sxs-lookup"><span data-stu-id="92f27-205">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="92f27-206">Kommandots utdata som du skickar till `Out-GridView` kan inte formateras med `Format` cmdletarna, till exempel `Format-Table` eller- `Format-Wide` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="92f27-206">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="92f27-207">Använd cmdleten för att välja egenskaper `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="92f27-207">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="92f27-208">Avserialiserade utdata från fjärrkommandon kanske inte är korrekt formaterade i rutnätsvy-fönstret.</span><span class="sxs-lookup"><span data-stu-id="92f27-208">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="92f27-209">Kortkommandon **för**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="92f27-209">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="92f27-210">Använd den här nyckeln:</span><span class="sxs-lookup"><span data-stu-id="92f27-210">Use this key:</span></span>              |                                   <span data-ttu-id="92f27-211">För att utföra den här åtgärden:</span><span class="sxs-lookup"><span data-stu-id="92f27-211">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="92f27-212"><kbd>Tabbtecken</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-212"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="92f27-213">Flyttar markören från **filter** rutan till menyn **Lägg till villkor** i tabellen och tillbaka.</span><span class="sxs-lookup"><span data-stu-id="92f27-213">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="92f27-214"><kbd>Nedåtpil</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-214"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="92f27-215">Flytta upp en rad.</span><span class="sxs-lookup"><span data-stu-id="92f27-215">Move up one row.</span></span> <span data-ttu-id="92f27-216">Flyttar till kolumn rubriker från första raden med data.</span><span class="sxs-lookup"><span data-stu-id="92f27-216">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="92f27-217"><kbd>NEDPIL</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-217"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="92f27-218">Flytta ned en rad.</span><span class="sxs-lookup"><span data-stu-id="92f27-218">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="92f27-219"><kbd>LeftArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-219"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="92f27-220">Flytta en kolumn till vänster i kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="92f27-220">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="92f27-221"><kbd>RightArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-221"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="92f27-222">I kolumn rubrik raden flyttar du en kolumn till höger.</span><span class="sxs-lookup"><span data-stu-id="92f27-222">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="92f27-223"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-223"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="92f27-224">I kolumn rubrik raden visas alternativet Välj kolumner.</span><span class="sxs-lookup"><span data-stu-id="92f27-224">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="92f27-225"><kbd>Ange</kbd> eller <kbd>blank steg</kbd></span><span class="sxs-lookup"><span data-stu-id="92f27-225"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="92f27-226">I kolumn rubrik raden sorterar du kolumn data (växla A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="92f27-226">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="92f27-227">**Använda funktionerna i rutnätsvy-fönstret**</span><span class="sxs-lookup"><span data-stu-id="92f27-227">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="92f27-228">**För att dölja eller Visa en kolumn:**</span><span class="sxs-lookup"><span data-stu-id="92f27-228">**To hide or show a column:**</span></span>

1. <span data-ttu-id="92f27-229">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="92f27-229">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="92f27-230">I dialog rutan **Välj kolumner** använder du piltangenterna för att flytta kolumnerna mellan de markerade kolumnerna i rutorna tillgängliga kolumner.</span><span class="sxs-lookup"><span data-stu-id="92f27-230">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="92f27-231">Endast kolumner i rutan **Välj kolumner** visas i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-231">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="92f27-232">**Så här ordnar du om kolumner:**</span><span class="sxs-lookup"><span data-stu-id="92f27-232">**To reorder columns:**</span></span>

<span data-ttu-id="92f27-233">Du kan dra och släppa kolumner till önskad plats.</span><span class="sxs-lookup"><span data-stu-id="92f27-233">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="92f27-234">Eller Använd följande steg:</span><span class="sxs-lookup"><span data-stu-id="92f27-234">Or use the following steps:</span></span>

1. <span data-ttu-id="92f27-235">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="92f27-235">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="92f27-236">I dialog rutan **Välj kolumner** använder du knapparna **Flytta upp** och **Flytta ned** för att ändra ordning på kolumnerna.</span><span class="sxs-lookup"><span data-stu-id="92f27-236">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="92f27-237">Kolumner överst i listan visas till vänster om kolumner längst ned i listan i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="92f27-237">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="92f27-238">**Sortera tabell data**</span><span class="sxs-lookup"><span data-stu-id="92f27-238">**How to Sort Table Data**</span></span>

- <span data-ttu-id="92f27-239">Om du vill sortera data klickar du på en kolumn rubrik.</span><span class="sxs-lookup"><span data-stu-id="92f27-239">To sort the data, click a column header.</span></span>
- <span data-ttu-id="92f27-240">Klicka på kolumn rubriken igen om du vill ändra sorterings ordningen.</span><span class="sxs-lookup"><span data-stu-id="92f27-240">To change the sort order, click the column header again.</span></span> <span data-ttu-id="92f27-241">Varje gången du klickar på samma rubrik växlar sorterings ordningen mellan stigande till fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="92f27-241">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="92f27-242">Den aktuella ordningen anges av en triangel i kolumn rubriken.</span><span class="sxs-lookup"><span data-stu-id="92f27-242">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="92f27-243">**Så här väljer du tabell data**</span><span class="sxs-lookup"><span data-stu-id="92f27-243">**How to Select Table Data**</span></span>

- <span data-ttu-id="92f27-244">Om du vill markera en rad markerar du raden eller använder upp-eller nedpilen för att navigera till raden.</span><span class="sxs-lookup"><span data-stu-id="92f27-244">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="92f27-245">Om du vill markera alla rader (förutom rubrik raden) trycker du på <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="92f27-245">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="92f27-246">Om du vill markera efterföljande rader trycker du på och håller <kbd>ned SKIFT</kbd> -tangenten medan du klickar på raderna eller använder piltangenterna.</span><span class="sxs-lookup"><span data-stu-id="92f27-246">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="92f27-247">Om du vill markera rader som inte är i följd trycker du på <kbd>CTRL</kbd> -tangenten och klickar för att lägga till en rad i markeringen.</span><span class="sxs-lookup"><span data-stu-id="92f27-247">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="92f27-248">Det går inte att markera kolumner och det går inte att markera hela kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="92f27-248">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="92f27-249">**Kopiera rader**</span><span class="sxs-lookup"><span data-stu-id="92f27-249">**How to Copy Rows**</span></span>

- <span data-ttu-id="92f27-250">Om du vill kopiera en eller flera rader från tabellen markerar du raderna och trycker sedan på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="92f27-250">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="92f27-251">Du kan klistra in data i valfritt text-eller kalkyl blads program.</span><span class="sxs-lookup"><span data-stu-id="92f27-251">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="92f27-252">Du kan inte kopiera kolumner eller delar av rader och du kan inte kopiera kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="92f27-252">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="92f27-253">**Söka i tabellen (snabb filter)**</span><span class="sxs-lookup"><span data-stu-id="92f27-253">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="92f27-254">Använd filter rutan för att söka efter data i tabellen.</span><span class="sxs-lookup"><span data-stu-id="92f27-254">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="92f27-255">När du skriver i rutan visas endast objekt som innehåller texten som skrivs in i tabellen.</span><span class="sxs-lookup"><span data-stu-id="92f27-255">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="92f27-256">Sök efter text.</span><span class="sxs-lookup"><span data-stu-id="92f27-256">Search for text.</span></span> <span data-ttu-id="92f27-257">Om du vill söka efter text i tabellen skriver du den text som du vill söka efter i rutan filter.</span><span class="sxs-lookup"><span data-stu-id="92f27-257">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="92f27-258">Sök efter flera ord.</span><span class="sxs-lookup"><span data-stu-id="92f27-258">Search for multiple words.</span></span> <span data-ttu-id="92f27-259">Om du vill söka efter flera ord i tabellen skriver du orden avgränsade med blank steg.</span><span class="sxs-lookup"><span data-stu-id="92f27-259">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="92f27-260">`Out-GridView` visar rader som innehåller alla ord (logiska och).</span><span class="sxs-lookup"><span data-stu-id="92f27-260">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="92f27-261">Sök efter litterala fraser.</span><span class="sxs-lookup"><span data-stu-id="92f27-261">Search for literal phrases.</span></span> <span data-ttu-id="92f27-262">Om du vill söka efter fraser som innehåller blank steg eller specialtecken, omger du frasen med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="92f27-262">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="92f27-263">`Out-GridView` visar rader som innehåller en exakt matchning för frasen.</span><span class="sxs-lookup"><span data-stu-id="92f27-263">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="92f27-264">Sök i kolumner.</span><span class="sxs-lookup"><span data-stu-id="92f27-264">Search in columns.</span></span> <span data-ttu-id="92f27-265">Om du vill söka efter text i en eller flera kolumner använder du följande format:</span><span class="sxs-lookup"><span data-stu-id="92f27-265">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="92f27-266">Om du till exempel vill hitta "net" i kolumnen **DisplayName** i rutan **filter** skriver du:</span><span class="sxs-lookup"><span data-stu-id="92f27-266">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="92f27-267">Om du vill hitta rader med "net" i kolumnerna **DisplayName** och **namn** , skriver du följande i rutan **filter** :</span><span class="sxs-lookup"><span data-stu-id="92f27-267">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="92f27-268">Stäng av Sök funktionen.</span><span class="sxs-lookup"><span data-stu-id="92f27-268">Turn off search.</span></span> <span data-ttu-id="92f27-269">Om du vill visa hela tabellen igen klickar du på knappen röd X i det övre högra hörnet av **filter** rutan eller tar bort texten från **filter** rutan.</span><span class="sxs-lookup"><span data-stu-id="92f27-269">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="92f27-270">**Använd villkor för att filtrera tabellen**</span><span class="sxs-lookup"><span data-stu-id="92f27-270">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="92f27-271">Du kan använda regler eller kriterier för att avgöra vilka objekt som visas i tabellen.</span><span class="sxs-lookup"><span data-stu-id="92f27-271">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="92f27-272">Objekt visas bara när de uppfyller alla kriterier som du upprättar.</span><span class="sxs-lookup"><span data-stu-id="92f27-272">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="92f27-273">De tillgängliga kriterierna bestäms av egenskaperna för de objekt som visas i fönstret rutnätsvy och .NET Framework typer av dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="92f27-273">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="92f27-274">Varje kriterium har följande format:</span><span class="sxs-lookup"><span data-stu-id="92f27-274">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="92f27-275">Villkor för olika egenskaper är anslutna med **och**.</span><span class="sxs-lookup"><span data-stu-id="92f27-275">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="92f27-276">Villkor för samma egenskap är anslutna med **eller**.</span><span class="sxs-lookup"><span data-stu-id="92f27-276">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="92f27-277">Du kan inte ändra de logiska anslutningarna.</span><span class="sxs-lookup"><span data-stu-id="92f27-277">You cannot change the logical connectors.</span></span>

<span data-ttu-id="92f27-278">Kriterierna påverkar bara visningen.</span><span class="sxs-lookup"><span data-stu-id="92f27-278">The criteria only affects the display.</span></span> <span data-ttu-id="92f27-279">Objekt tas inte bort från tabellen.</span><span class="sxs-lookup"><span data-stu-id="92f27-279">It does not delete items from the table.</span></span>

<span data-ttu-id="92f27-280">**Lägga till villkor**</span><span class="sxs-lookup"><span data-stu-id="92f27-280">**How to Add Criteria**</span></span>

1. <span data-ttu-id="92f27-281">Om du vill visa meny knappen **Lägg till villkor** klickar du på pilen i det övre högra hörnet i fönstret.</span><span class="sxs-lookup"><span data-stu-id="92f27-281">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="92f27-282">Klicka på Meny knappen **Lägg till villkor** .</span><span class="sxs-lookup"><span data-stu-id="92f27-282">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="92f27-283">Klicka för att välja kolumner (egenskaper).</span><span class="sxs-lookup"><span data-stu-id="92f27-283">Click to select columns (properties).</span></span> <span data-ttu-id="92f27-284">Du kan välja en eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="92f27-284">You can select one or many properties.</span></span>
4. <span data-ttu-id="92f27-285">När du är färdig med att välja egenskaper klickar du på knappen **Lägg till** .</span><span class="sxs-lookup"><span data-stu-id="92f27-285">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="92f27-286">Klicka på **Avbryt** om du vill avbryta tilläggen.</span><span class="sxs-lookup"><span data-stu-id="92f27-286">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="92f27-287">Om du vill lägga till fler villkor klickar du på knappen **Lägg till villkor** igen.</span><span class="sxs-lookup"><span data-stu-id="92f27-287">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="92f27-288">**Så här redigerar du ett kriterium**</span><span class="sxs-lookup"><span data-stu-id="92f27-288">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="92f27-289">Om du vill ändra en operator klickar du på värdet blå operator och väljer sedan en annan operator i list rutan.</span><span class="sxs-lookup"><span data-stu-id="92f27-289">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="92f27-290">Ange ett värde i rutan värde om du vill ange eller ändra ett värde.</span><span class="sxs-lookup"><span data-stu-id="92f27-290">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="92f27-291">Om du anger ett värde som inte är giltigt visas en cirkel X-ikon.</span><span class="sxs-lookup"><span data-stu-id="92f27-291">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="92f27-292">Ändra värdet om du vill ta bort det.</span><span class="sxs-lookup"><span data-stu-id="92f27-292">To remove it, change the value.</span></span>
- <span data-ttu-id="92f27-293">Om du vill skapa en **or** -instruktion lägger du till ett villkor med samma egenskap.</span><span class="sxs-lookup"><span data-stu-id="92f27-293">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="92f27-294">**Ta bort villkor**</span><span class="sxs-lookup"><span data-stu-id="92f27-294">**How to Delete Criteria**</span></span>

- <span data-ttu-id="92f27-295">Om du vill ta bort de valda villkoren klickar du på det röda krysset bredvid varje kriterium.</span><span class="sxs-lookup"><span data-stu-id="92f27-295">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="92f27-296">Om du vill ta bort alla kriterier klickar du på knappen **Rensa alla** .</span><span class="sxs-lookup"><span data-stu-id="92f27-296">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="92f27-297">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="92f27-297">RELATED LINKS</span></span>

[<span data-ttu-id="92f27-298">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="92f27-298">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="92f27-299">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="92f27-299">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="92f27-300">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="92f27-300">Out-String</span></span>](Out-String.md)

