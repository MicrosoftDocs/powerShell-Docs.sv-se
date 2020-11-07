---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 37b5349c8ed39ff70453b59fe6758c57880f0087
ms.sourcegitcommit: 177ae45034b58ead716853096b2e72e4864e6df6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/07/2020
ms.locfileid: "94346946"
---
# <span data-ttu-id="b2c95-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="b2c95-103">Out-GridView</span></span>

## <span data-ttu-id="b2c95-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b2c95-104">SYNOPSIS</span></span>
<span data-ttu-id="b2c95-105">Skickar utdata till en interaktiv tabell i ett separat fönster.</span><span class="sxs-lookup"><span data-stu-id="b2c95-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="b2c95-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b2c95-106">SYNTAX</span></span>

### <span data-ttu-id="b2c95-107">PassThru (standard)</span><span class="sxs-lookup"><span data-stu-id="b2c95-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="b2c95-108">Vänta</span><span class="sxs-lookup"><span data-stu-id="b2c95-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="b2c95-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="b2c95-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="b2c95-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b2c95-110">DESCRIPTION</span></span>

<span data-ttu-id="b2c95-111">`Out-GridView`Cmdleten skickar utdata från ett kommando till ett fönster för rutnätsvy där utdata visas i en interaktiv tabell.</span><span class="sxs-lookup"><span data-stu-id="b2c95-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="b2c95-112">Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="b2c95-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="b2c95-113">Du kan använda följande funktioner i tabellen för att undersöka dina data:</span><span class="sxs-lookup"><span data-stu-id="b2c95-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="b2c95-114">Dölj, Visa och ordna om kolumner</span><span class="sxs-lookup"><span data-stu-id="b2c95-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="b2c95-115">Sortera rader</span><span class="sxs-lookup"><span data-stu-id="b2c95-115">Sort rows</span></span>
- <span data-ttu-id="b2c95-116">Snabb filter</span><span class="sxs-lookup"><span data-stu-id="b2c95-116">Quick Filter</span></span>
- <span data-ttu-id="b2c95-117">Lägg till villkors filter</span><span class="sxs-lookup"><span data-stu-id="b2c95-117">Add Criteria Filter</span></span>
- <span data-ttu-id="b2c95-118">Kopiera och klistra in</span><span class="sxs-lookup"><span data-stu-id="b2c95-118">Copy and paste</span></span>

<span data-ttu-id="b2c95-119">Fullständiga instruktioner finns i avsnittet [anteckningar](#notes) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="b2c95-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

> [!NOTE]
> <span data-ttu-id="b2c95-120">Den här cmdleten introducerades om i PowerShell 7.</span><span class="sxs-lookup"><span data-stu-id="b2c95-120">This cmdlet was reintroduced in PowerShell 7.</span></span> <span data-ttu-id="b2c95-121">Den här cmdleten är endast tillgänglig på Windows-system som stöder Windows-skrivbordet.</span><span class="sxs-lookup"><span data-stu-id="b2c95-121">This cmdlet is only available on Windows systems that support the Windows Desktop.</span></span> <span data-ttu-id="b2c95-122">En plattforms oberoende version av denna cmdlet finns i [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) -modulen i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b2c95-122">For a cross-platform version of this cmdlet, see the [GraphicalTools](https://www.powershellgallery.com/packages/Microsoft.PowerShell.GraphicalTools) module in the PowerShell Gallery.</span></span>

## <span data-ttu-id="b2c95-123">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b2c95-123">EXAMPLES</span></span>

### <span data-ttu-id="b2c95-124">Exempel 1: utmatnings processer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-124">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="b2c95-125">Det här exemplet hämtar processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-125">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="b2c95-126">Exempel 2: använda en variabel för att visa processer i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-126">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="b2c95-127">Det här exemplet hämtar också processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-127">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="b2c95-128">Utdata från `Get-Process` cmdleten sparas i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="b2c95-128">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="b2c95-129">Sedan `$P` är skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-129">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="b2c95-130">Exempel 3: Visa markerade egenskaper i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-130">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="b2c95-131">I det här exemplet visas valda egenskaper för de processer som körs i en rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-131">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="b2c95-132">Utdatan från `Get-Process` är skickas `Select-Object` till för att välja egenskaper **WorkingSet** för **namn** , för-och **PeakWorkingSet** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-132">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="b2c95-133">En annan pipeline-operator skickar filtrerade objekt till `Sort-Object` cmdleten för att sortera dem i fallande ordning efter värdet för den **aktiva** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-133">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="b2c95-134">Sedan är de sorterade resultaten skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-134">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="b2c95-135">Nu kan du använda funktionerna i diagramvyn för att söka, sortera och filtrera data.</span><span class="sxs-lookup"><span data-stu-id="b2c95-135">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="b2c95-136">Exempel 4: spara utdata till en variabel och sedan Visa en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-136">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="b2c95-137">Det här exemplet sparar cmdlet-utdata i en variabel och skickar den sedan till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-137">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="b2c95-138">`Get-ChildItem` hämtar alla filer i installations katalogen för PowerShell och dess under kataloger med hjälp av den `$PSHOME` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="b2c95-138">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="b2c95-139">Parenteserna i kommandot fastställer ordningen för åtgärder.</span><span class="sxs-lookup"><span data-stu-id="b2c95-139">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="b2c95-140">Därför sparas utdata från `Get-ChildItem` kommandot i `$A` variabeln innan det skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-140">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="b2c95-141">Exempel 5: utmatnings processer för en angiven dator till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-141">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="b2c95-142">I det här exemplet visas de processer som körs på Server01-datorn i ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-142">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="b2c95-143">Examle använder `ogv` , vilket är aliaset för `Out-GridView` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b2c95-143">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="b2c95-144">Parametern **title** anger fönstrets rubrik.</span><span class="sxs-lookup"><span data-stu-id="b2c95-144">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="b2c95-145">Exempel 6: Spara data från fjärrdatorer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="b2c95-145">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="b2c95-146">Det här exemplet visar hur du skickar data som samlas in från fjärrdatorer till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-146">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="b2c95-147">`Invoke-Command` körs `Get-Culture` på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="b2c95-147">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="b2c95-148">Resulterande data är skickas `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-148">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="b2c95-149">Observera att skript blocket som körs på fjärrdatorn inte innehåller `Out-GridView` kommandot.</span><span class="sxs-lookup"><span data-stu-id="b2c95-149">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="b2c95-150">Om den gjorde det kunde kommandot inte utföras när det försökte öppna ett fönster för rutnätsvy på var och en av de fjärranslutna datorerna.</span><span class="sxs-lookup"><span data-stu-id="b2c95-150">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="b2c95-151">Exempel 7: skicka flera objekt via `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="b2c95-151">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="b2c95-152">I det här exemplet kan du välja flera processer i `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="b2c95-152">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="b2c95-153">De processer som du väljer skickas till `Export-Csv` kommandot och skrivs till `ProcessLog.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-153">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="b2c95-154">Med parametern **Passthru** `Out-GridView` kan du skicka flera objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-154">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="b2c95-155">Parametern **Passthru** motsvarar användningen av **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-155">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="b2c95-156">Exempel 8: skapa en Windows-genväg till `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="b2c95-156">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="b2c95-157">Det här exemplet visar hur du använder **wait** -parametern för `Out-GridView` för att skapa en Windows-genväg till `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="b2c95-157">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="b2c95-158">Den här kommando raden kan användas i en Windows-genväg.</span><span class="sxs-lookup"><span data-stu-id="b2c95-158">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="b2c95-159">Utan parametern **wait** avslutas PowerShell så snart `Out-GridView` fönstret har öppnats, vilket skulle stänga `Out-GridView` fönstret nästan omedelbart.</span><span class="sxs-lookup"><span data-stu-id="b2c95-159">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="b2c95-160">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b2c95-160">PARAMETERS</span></span>

### <span data-ttu-id="b2c95-161">– InputObject</span><span class="sxs-lookup"><span data-stu-id="b2c95-161">-InputObject</span></span>

<span data-ttu-id="b2c95-162">Anger objekt som cmdleten accepterar som ininformation för `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-162">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="b2c95-163">När du använder parametern **InputObject** för att skicka en samling objekt till `Out-GridView` , `Out-GridView` behandlar samlingen som ett samlings objekt och visar en rad som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-163">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="b2c95-164">Om du vill visa varje objekt i samlingen använder du en pipeline-operator ( `|` ) för att skicka objekt till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-164">To display the each object in the collection, use a pipeline operator (`|`) to send objects to `Out-GridView`.</span></span>

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

### <span data-ttu-id="b2c95-165">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="b2c95-165">-OutputMode</span></span>

<span data-ttu-id="b2c95-166">Anger de objekt som det interaktiva fönstret skickar nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="b2c95-166">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="b2c95-167">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b2c95-167">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="b2c95-168">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="b2c95-168">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="b2c95-169">Värdena för den här parametern avgör hur många objekt du kan skicka pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-169">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="b2c95-170">Inga.</span><span class="sxs-lookup"><span data-stu-id="b2c95-170">None.</span></span>  <span data-ttu-id="b2c95-171">Inga objekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-171">No items.</span></span> <span data-ttu-id="b2c95-172">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="b2c95-172">This is the default value.</span></span>
- <span data-ttu-id="b2c95-173">Samma.</span><span class="sxs-lookup"><span data-stu-id="b2c95-173">Single.</span></span> <span data-ttu-id="b2c95-174">Noll objekt eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-174">Zero items or one item.</span></span> <span data-ttu-id="b2c95-175">Använd det här värdet när nästa kommando bara kan ta ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-175">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="b2c95-176">Flera.</span><span class="sxs-lookup"><span data-stu-id="b2c95-176">Multiple.</span></span> <span data-ttu-id="b2c95-177">Noll, ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-177">Zero, one, or many items.</span></span> <span data-ttu-id="b2c95-178">Använd det här värdet när nästa kommando kan ta flera inobjekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-178">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="b2c95-179">Värdet motsvarar parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-179">This value is equivalent to the **Passthru** parameter.</span></span>

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

### <span data-ttu-id="b2c95-180">– PassThru</span><span class="sxs-lookup"><span data-stu-id="b2c95-180">-PassThru</span></span>

<span data-ttu-id="b2c95-181">Anger att cmdleten skickar objekt från det interaktiva fönstret nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="b2c95-181">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="b2c95-182">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b2c95-182">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="b2c95-183">Den här parametern motsvarar att använda **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-183">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="b2c95-184">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="b2c95-184">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="b2c95-185">Shift-klicka och Ctrl-klicka stöds.</span><span class="sxs-lookup"><span data-stu-id="b2c95-185">Shift-click and Ctrl-click are supported.</span></span>

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

### <span data-ttu-id="b2c95-186">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="b2c95-186">-Title</span></span>

<span data-ttu-id="b2c95-187">Anger den text som visas i namn listen för `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="b2c95-187">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="b2c95-188">Som standard visar namn listen det kommando som anropar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-188">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

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

### <span data-ttu-id="b2c95-189">– Vänta</span><span class="sxs-lookup"><span data-stu-id="b2c95-189">-Wait</span></span>

<span data-ttu-id="b2c95-190">Anger att cmdleten ignorerar kommando tolken och förhindrar att Windows PowerShell stängs tills `Out-GridView` fönstret har stängts.</span><span class="sxs-lookup"><span data-stu-id="b2c95-190">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="b2c95-191">Som standard returnerar kommando tolken när `Out-GridView` fönstret öppnas.</span><span class="sxs-lookup"><span data-stu-id="b2c95-191">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="b2c95-192">Med den här funktionen kan du använda `Out-GridView` cmdlets i Windows-genvägar.</span><span class="sxs-lookup"><span data-stu-id="b2c95-192">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="b2c95-193">När `Out-GridView` används i en genväg utan parametern **wait** , `Out-GridView` visas fönstret bara tillfälligt innan PowerShell stängs.</span><span class="sxs-lookup"><span data-stu-id="b2c95-193">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

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

### <span data-ttu-id="b2c95-194">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b2c95-194">CommonParameters</span></span>

<span data-ttu-id="b2c95-195">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b2c95-195">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b2c95-196">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b2c95-196">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b2c95-197">INDATA</span><span class="sxs-lookup"><span data-stu-id="b2c95-197">INPUTS</span></span>

### <span data-ttu-id="b2c95-198">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="b2c95-198">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="b2c95-199">Du kan skicka valfritt objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b2c95-199">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="b2c95-200">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b2c95-200">OUTPUTS</span></span>

### <span data-ttu-id="b2c95-201">Inget</span><span class="sxs-lookup"><span data-stu-id="b2c95-201">None</span></span>

<span data-ttu-id="b2c95-202">Normalt `Out-GridView` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="b2c95-202">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="b2c95-203">När du använder parametern **Passthru** returneras objekten som representerar de valda raderna till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-203">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="b2c95-204">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b2c95-204">NOTES</span></span>

<span data-ttu-id="b2c95-205">Den här cmdleten är endast tillgänglig på Windows-plattformar.</span><span class="sxs-lookup"><span data-stu-id="b2c95-205">This cmdlet is only available on Windows platforms.</span></span>

<span data-ttu-id="b2c95-206">Du kan inte använda ett fjärran slutet kommando för att öppna ett fönster för rutnätsvy på en annan dator.</span><span class="sxs-lookup"><span data-stu-id="b2c95-206">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="b2c95-207">Kommandots utdata som du skickar till `Out-GridView` kan inte formateras med `Format` cmdletarna, till exempel `Format-Table` eller- `Format-Wide` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="b2c95-207">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="b2c95-208">Använd cmdleten för att välja egenskaper `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="b2c95-208">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="b2c95-209">Avserialiserade utdata från fjärrkommandon kanske inte är korrekt formaterade i rutnätsvy-fönstret.</span><span class="sxs-lookup"><span data-stu-id="b2c95-209">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="b2c95-210">Kortkommandon **för**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="b2c95-210">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="b2c95-211">Använd den här nyckeln:</span><span class="sxs-lookup"><span data-stu-id="b2c95-211">Use this key:</span></span>              |                                   <span data-ttu-id="b2c95-212">För att utföra den här åtgärden:</span><span class="sxs-lookup"><span data-stu-id="b2c95-212">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="b2c95-213"><kbd>Tabbtecken</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-213"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="b2c95-214">Flyttar markören från **filter** rutan till menyn **Lägg till villkor** i tabellen och tillbaka.</span><span class="sxs-lookup"><span data-stu-id="b2c95-214">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="b2c95-215"><kbd>Nedåtpil</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-215"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="b2c95-216">Flytta upp en rad.</span><span class="sxs-lookup"><span data-stu-id="b2c95-216">Move up one row.</span></span> <span data-ttu-id="b2c95-217">Flyttar till kolumn rubriker från första raden med data.</span><span class="sxs-lookup"><span data-stu-id="b2c95-217">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="b2c95-218"><kbd>NEDPIL</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-218"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="b2c95-219">Flytta ned en rad.</span><span class="sxs-lookup"><span data-stu-id="b2c95-219">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="b2c95-220"><kbd>LeftArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-220"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="b2c95-221">Flytta en kolumn till vänster i kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="b2c95-221">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="b2c95-222"><kbd>RightArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-222"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="b2c95-223">I kolumn rubrik raden flyttar du en kolumn till höger.</span><span class="sxs-lookup"><span data-stu-id="b2c95-223">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="b2c95-224"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-224"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="b2c95-225">I kolumn rubrik raden visas alternativet Välj kolumner.</span><span class="sxs-lookup"><span data-stu-id="b2c95-225">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="b2c95-226"><kbd>Ange</kbd> eller <kbd>blank steg</kbd></span><span class="sxs-lookup"><span data-stu-id="b2c95-226"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="b2c95-227">I kolumn rubrik raden sorterar du kolumn data (växla A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="b2c95-227">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="b2c95-228">**Använda funktionerna i rutnätsvy-fönstret**</span><span class="sxs-lookup"><span data-stu-id="b2c95-228">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="b2c95-229">**För att dölja eller Visa en kolumn:**</span><span class="sxs-lookup"><span data-stu-id="b2c95-229">**To hide or show a column:**</span></span>

1. <span data-ttu-id="b2c95-230">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="b2c95-230">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="b2c95-231">I dialog rutan **Välj kolumner** använder du piltangenterna för att flytta kolumnerna mellan de markerade kolumnerna i rutorna tillgängliga kolumner.</span><span class="sxs-lookup"><span data-stu-id="b2c95-231">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="b2c95-232">Endast kolumner i rutan **Välj kolumner** visas i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-232">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="b2c95-233">**Så här ordnar du om kolumner:**</span><span class="sxs-lookup"><span data-stu-id="b2c95-233">**To reorder columns:**</span></span>

<span data-ttu-id="b2c95-234">Du kan dra och släppa kolumner till önskad plats.</span><span class="sxs-lookup"><span data-stu-id="b2c95-234">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="b2c95-235">Eller Använd följande steg:</span><span class="sxs-lookup"><span data-stu-id="b2c95-235">Or use the following steps:</span></span>

1. <span data-ttu-id="b2c95-236">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="b2c95-236">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="b2c95-237">I dialog rutan **Välj kolumner** använder du knapparna **Flytta upp** och **Flytta ned** för att ändra ordning på kolumnerna.</span><span class="sxs-lookup"><span data-stu-id="b2c95-237">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="b2c95-238">Kolumner överst i listan visas till vänster om kolumner längst ned i listan i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="b2c95-238">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="b2c95-239">**Sortera tabell data**</span><span class="sxs-lookup"><span data-stu-id="b2c95-239">**How to Sort Table Data**</span></span>

- <span data-ttu-id="b2c95-240">Om du vill sortera data klickar du på en kolumn rubrik.</span><span class="sxs-lookup"><span data-stu-id="b2c95-240">To sort the data, click a column header.</span></span>
- <span data-ttu-id="b2c95-241">Klicka på kolumn rubriken igen om du vill ändra sorterings ordningen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-241">To change the sort order, click the column header again.</span></span> <span data-ttu-id="b2c95-242">Varje gången du klickar på samma rubrik växlar sorterings ordningen mellan stigande till fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="b2c95-242">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="b2c95-243">Den aktuella ordningen anges av en triangel i kolumn rubriken.</span><span class="sxs-lookup"><span data-stu-id="b2c95-243">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="b2c95-244">**Så här väljer du tabell data**</span><span class="sxs-lookup"><span data-stu-id="b2c95-244">**How to Select Table Data**</span></span>

- <span data-ttu-id="b2c95-245">Om du vill markera en rad markerar du raden eller använder upp-eller nedpilen för att navigera till raden.</span><span class="sxs-lookup"><span data-stu-id="b2c95-245">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="b2c95-246">Om du vill markera alla rader (förutom rubrik raden) trycker du på <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="b2c95-246">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="b2c95-247">Om du vill markera efterföljande rader trycker du på och håller <kbd>ned SKIFT</kbd> -tangenten medan du klickar på raderna eller använder piltangenterna.</span><span class="sxs-lookup"><span data-stu-id="b2c95-247">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="b2c95-248">Om du vill markera rader som inte är i följd trycker du på <kbd>CTRL</kbd> -tangenten och klickar för att lägga till en rad i markeringen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-248">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="b2c95-249">Det går inte att markera kolumner och det går inte att markera hela kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="b2c95-249">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="b2c95-250">**Kopiera rader**</span><span class="sxs-lookup"><span data-stu-id="b2c95-250">**How to Copy Rows**</span></span>

- <span data-ttu-id="b2c95-251">Om du vill kopiera en eller flera rader från tabellen markerar du raderna och trycker sedan på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="b2c95-251">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="b2c95-252">Du kan klistra in data i valfritt text-eller kalkyl blads program.</span><span class="sxs-lookup"><span data-stu-id="b2c95-252">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="b2c95-253">Du kan inte kopiera kolumner eller delar av rader och du kan inte kopiera kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="b2c95-253">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="b2c95-254">**Söka i tabellen (snabb filter)**</span><span class="sxs-lookup"><span data-stu-id="b2c95-254">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="b2c95-255">Använd filter rutan för att söka efter data i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-255">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="b2c95-256">När du skriver i rutan visas endast objekt som innehåller texten som skrivs in i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-256">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="b2c95-257">Sök efter text.</span><span class="sxs-lookup"><span data-stu-id="b2c95-257">Search for text.</span></span> <span data-ttu-id="b2c95-258">Om du vill söka efter text i tabellen skriver du den text som du vill söka efter i rutan filter.</span><span class="sxs-lookup"><span data-stu-id="b2c95-258">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="b2c95-259">Sök efter flera ord.</span><span class="sxs-lookup"><span data-stu-id="b2c95-259">Search for multiple words.</span></span> <span data-ttu-id="b2c95-260">Om du vill söka efter flera ord i tabellen skriver du orden avgränsade med blank steg.</span><span class="sxs-lookup"><span data-stu-id="b2c95-260">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="b2c95-261">`Out-GridView` visar rader som innehåller alla ord (logiska och).</span><span class="sxs-lookup"><span data-stu-id="b2c95-261">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="b2c95-262">Sök efter litterala fraser.</span><span class="sxs-lookup"><span data-stu-id="b2c95-262">Search for literal phrases.</span></span> <span data-ttu-id="b2c95-263">Om du vill söka efter fraser som innehåller blank steg eller specialtecken, omger du frasen med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="b2c95-263">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="b2c95-264">`Out-GridView` visar rader som innehåller en exakt matchning för frasen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-264">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="b2c95-265">Sök i kolumner.</span><span class="sxs-lookup"><span data-stu-id="b2c95-265">Search in columns.</span></span> <span data-ttu-id="b2c95-266">Om du vill söka efter text i en eller flera kolumner använder du följande format:</span><span class="sxs-lookup"><span data-stu-id="b2c95-266">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="b2c95-267">Om du till exempel vill hitta "net" i kolumnen **DisplayName** i rutan **filter** skriver du:</span><span class="sxs-lookup"><span data-stu-id="b2c95-267">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="b2c95-268">Om du vill hitta rader med "net" i kolumnerna **DisplayName** och **namn** , skriver du följande i rutan **filter** :</span><span class="sxs-lookup"><span data-stu-id="b2c95-268">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="b2c95-269">Stäng av Sök funktionen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-269">Turn off search.</span></span> <span data-ttu-id="b2c95-270">Om du vill visa hela tabellen igen klickar du på knappen röd X i det övre högra hörnet av **filter** rutan eller tar bort texten från **filter** rutan.</span><span class="sxs-lookup"><span data-stu-id="b2c95-270">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="b2c95-271">**Använd villkor för att filtrera tabellen**</span><span class="sxs-lookup"><span data-stu-id="b2c95-271">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="b2c95-272">Du kan använda regler eller kriterier för att avgöra vilka objekt som visas i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-272">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="b2c95-273">Objekt visas bara när de uppfyller alla kriterier som du upprättar.</span><span class="sxs-lookup"><span data-stu-id="b2c95-273">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="b2c95-274">De tillgängliga kriterierna bestäms av egenskaperna för de objekt som visas i fönstret rutnätsvy och .NET Framework typer av dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b2c95-274">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="b2c95-275">Varje kriterium har följande format:</span><span class="sxs-lookup"><span data-stu-id="b2c95-275">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="b2c95-276">Villkor för olika egenskaper är anslutna med **och**.</span><span class="sxs-lookup"><span data-stu-id="b2c95-276">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="b2c95-277">Villkor för samma egenskap är anslutna med **eller**.</span><span class="sxs-lookup"><span data-stu-id="b2c95-277">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="b2c95-278">Du kan inte ändra de logiska anslutningarna.</span><span class="sxs-lookup"><span data-stu-id="b2c95-278">You cannot change the logical connectors.</span></span>

<span data-ttu-id="b2c95-279">Kriterierna påverkar bara visningen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-279">The criteria only affects the display.</span></span> <span data-ttu-id="b2c95-280">Objekt tas inte bort från tabellen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-280">It does not delete items from the table.</span></span>

<span data-ttu-id="b2c95-281">**Lägga till villkor**</span><span class="sxs-lookup"><span data-stu-id="b2c95-281">**How to Add Criteria**</span></span>

1. <span data-ttu-id="b2c95-282">Om du vill visa meny knappen **Lägg till villkor** klickar du på pilen i det övre högra hörnet i fönstret.</span><span class="sxs-lookup"><span data-stu-id="b2c95-282">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="b2c95-283">Klicka på Meny knappen **Lägg till villkor** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-283">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="b2c95-284">Klicka för att välja kolumner (egenskaper).</span><span class="sxs-lookup"><span data-stu-id="b2c95-284">Click to select columns (properties).</span></span> <span data-ttu-id="b2c95-285">Du kan välja en eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="b2c95-285">You can select one or many properties.</span></span>
4. <span data-ttu-id="b2c95-286">När du är färdig med att välja egenskaper klickar du på knappen **Lägg till** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-286">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="b2c95-287">Klicka på **Avbryt** om du vill avbryta tilläggen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-287">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="b2c95-288">Om du vill lägga till fler villkor klickar du på knappen **Lägg till villkor** igen.</span><span class="sxs-lookup"><span data-stu-id="b2c95-288">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="b2c95-289">**Så här redigerar du ett kriterium**</span><span class="sxs-lookup"><span data-stu-id="b2c95-289">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="b2c95-290">Om du vill ändra en operator klickar du på värdet blå operator och väljer sedan en annan operator i list rutan.</span><span class="sxs-lookup"><span data-stu-id="b2c95-290">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="b2c95-291">Ange ett värde i rutan värde om du vill ange eller ändra ett värde.</span><span class="sxs-lookup"><span data-stu-id="b2c95-291">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="b2c95-292">Om du anger ett värde som inte är giltigt visas en cirkel X-ikon.</span><span class="sxs-lookup"><span data-stu-id="b2c95-292">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="b2c95-293">Ändra värdet om du vill ta bort det.</span><span class="sxs-lookup"><span data-stu-id="b2c95-293">To remove it, change the value.</span></span>
- <span data-ttu-id="b2c95-294">Om du vill skapa en **or** -instruktion lägger du till ett villkor med samma egenskap.</span><span class="sxs-lookup"><span data-stu-id="b2c95-294">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="b2c95-295">**Ta bort villkor**</span><span class="sxs-lookup"><span data-stu-id="b2c95-295">**How to Delete Criteria**</span></span>

- <span data-ttu-id="b2c95-296">Om du vill ta bort de valda villkoren klickar du på det röda krysset bredvid varje kriterium.</span><span class="sxs-lookup"><span data-stu-id="b2c95-296">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="b2c95-297">Om du vill ta bort alla kriterier klickar du på knappen **Rensa alla** .</span><span class="sxs-lookup"><span data-stu-id="b2c95-297">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="b2c95-298">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b2c95-298">RELATED LINKS</span></span>

[<span data-ttu-id="b2c95-299">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="b2c95-299">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="b2c95-300">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="b2c95-300">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="b2c95-301">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="b2c95-301">Out-String</span></span>](Out-String.md)
