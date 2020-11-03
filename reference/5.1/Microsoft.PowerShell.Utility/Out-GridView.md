---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/28/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/out-gridview?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Out-GridView
ms.openlocfilehash: 473571aa73d9b9331545b80cb5949e7a83c26eff
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264909"
---
# <span data-ttu-id="210d0-103">Out-GridView</span><span class="sxs-lookup"><span data-stu-id="210d0-103">Out-GridView</span></span>

## <span data-ttu-id="210d0-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="210d0-104">SYNOPSIS</span></span>
<span data-ttu-id="210d0-105">Skickar utdata till en interaktiv tabell i ett separat fönster.</span><span class="sxs-lookup"><span data-stu-id="210d0-105">Sends output to an interactive table in a separate window.</span></span>

## <span data-ttu-id="210d0-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="210d0-106">SYNTAX</span></span>

### <span data-ttu-id="210d0-107">PassThru (standard)</span><span class="sxs-lookup"><span data-stu-id="210d0-107">PassThru (Default)</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-PassThru] [<CommonParameters>]
```

### <span data-ttu-id="210d0-108">Vänta</span><span class="sxs-lookup"><span data-stu-id="210d0-108">Wait</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-Wait] [<CommonParameters>]
```

### <span data-ttu-id="210d0-109">OutputMode</span><span class="sxs-lookup"><span data-stu-id="210d0-109">OutputMode</span></span>

```
Out-GridView [-InputObject <PSObject>] [-Title <String>] [-OutputMode <OutputModeOption>]
 [<CommonParameters>]
```

## <span data-ttu-id="210d0-110">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="210d0-110">DESCRIPTION</span></span>

<span data-ttu-id="210d0-111">`Out-GridView`Cmdleten skickar utdata från ett kommando till ett fönster för rutnätsvy där utdata visas i en interaktiv tabell.</span><span class="sxs-lookup"><span data-stu-id="210d0-111">The `Out-GridView` cmdlet sends the output from a command to a grid view window where the output is displayed in an interactive table.</span></span>

<span data-ttu-id="210d0-112">Eftersom denna cmdlet kräver ett användar gränssnitt fungerar den inte på Windows Server Core eller Windows Nano Server.</span><span class="sxs-lookup"><span data-stu-id="210d0-112">Because this cmdlet requires a user interface, it does not work on Windows Server Core or Windows Nano Server.</span></span>

<span data-ttu-id="210d0-113">Du kan använda följande funktioner i tabellen för att undersöka dina data:</span><span class="sxs-lookup"><span data-stu-id="210d0-113">You can use the following features of the table to examine your data:</span></span>

- <span data-ttu-id="210d0-114">Dölj, Visa och ordna om kolumner</span><span class="sxs-lookup"><span data-stu-id="210d0-114">Hide, Show, and Reorder Columns</span></span>
- <span data-ttu-id="210d0-115">Sortera rader</span><span class="sxs-lookup"><span data-stu-id="210d0-115">Sort rows</span></span>
- <span data-ttu-id="210d0-116">Snabb filter</span><span class="sxs-lookup"><span data-stu-id="210d0-116">Quick Filter</span></span>
- <span data-ttu-id="210d0-117">Lägg till villkors filter</span><span class="sxs-lookup"><span data-stu-id="210d0-117">Add Criteria Filter</span></span>
- <span data-ttu-id="210d0-118">Kopiera och klistra in</span><span class="sxs-lookup"><span data-stu-id="210d0-118">Copy and paste</span></span>

<span data-ttu-id="210d0-119">Fullständiga instruktioner finns i avsnittet [anteckningar](#notes) i den här artikeln.</span><span class="sxs-lookup"><span data-stu-id="210d0-119">For full instructions, see the [Notes](#notes) section of this article.</span></span>

## <span data-ttu-id="210d0-120">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="210d0-120">EXAMPLES</span></span>

### <span data-ttu-id="210d0-121">Exempel 1: utmatnings processer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-121">Example 1: Output processes to a grid view</span></span>

<span data-ttu-id="210d0-122">Det här exemplet hämtar processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-122">This example gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
Get-Process | Out-GridView
```

### <span data-ttu-id="210d0-123">Exempel 2: använda en variabel för att visa processer i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-123">Example 2: Use a variable to output processes to a grid view</span></span>

<span data-ttu-id="210d0-124">Det här exemplet hämtar också processerna som körs på den lokala datorn och skickar dem till ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-124">This example also gets the processes running on the local computer and sends them to a grid view window.</span></span>

```powershell
$P = Get-Process
$P | Out-GridView
```

<span data-ttu-id="210d0-125">Utdata från `Get-Process` cmdleten sparas i `$P` variabeln.</span><span class="sxs-lookup"><span data-stu-id="210d0-125">The output of the `Get-Process` cmdlet is saved in the `$P` variable.</span></span> <span data-ttu-id="210d0-126">Sedan `$P` är skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-126">Then, `$P` is piped to `Out-GridView`.</span></span>

### <span data-ttu-id="210d0-127">Exempel 3: Visa markerade egenskaper i en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-127">Example 3: Display a selected properties in a grid view</span></span>

<span data-ttu-id="210d0-128">I det här exemplet visas valda egenskaper för de processer som körs i en rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-128">This example displays selected properties of the running processes in a grid view.</span></span>

```powershell
Get-Process | Select-Object -Property Name, WorkingSet, PeakWorkingSet |
  Sort-Object -Property WorkingSet -Descending | Out-GridView
```

<span data-ttu-id="210d0-129">Utdatan från `Get-Process` är skickas `Select-Object` till för att välja egenskaper **WorkingSet** för **namn** , för-och **PeakWorkingSet** .</span><span class="sxs-lookup"><span data-stu-id="210d0-129">The output of `Get-Process` is piped to `Select-Object` to select the **Name** , **WorkingSet** , and **PeakWorkingSet** properties.</span></span> <span data-ttu-id="210d0-130">En annan pipeline-operator skickar filtrerade objekt till `Sort-Object` cmdleten för att sortera dem i fallande ordning efter värdet för den **aktiva** egenskapen.</span><span class="sxs-lookup"><span data-stu-id="210d0-130">Another pipeline operator sends the filtered objects to the `Sort-Object` cmdlet to sort them in descending order by the value of the **WorkingSet** property.</span></span>
<span data-ttu-id="210d0-131">Sedan är de sorterade resultaten skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-131">Then, the sorted results are piped to `Out-GridView`.</span></span> <span data-ttu-id="210d0-132">Nu kan du använda funktionerna i diagramvyn för att söka, sortera och filtrera data.</span><span class="sxs-lookup"><span data-stu-id="210d0-132">You can now use the features of the grid view to search, sort, and filter the data.</span></span>

### <span data-ttu-id="210d0-133">Exempel 4: spara utdata till en variabel och sedan Visa en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-133">Example 4: Save output to a variable, and then output a grid view</span></span>

<span data-ttu-id="210d0-134">Det här exemplet sparar cmdlet-utdata i en variabel och skickar den sedan till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-134">This example saves cmdlet output in a variable then sends it to `Out-GridView`.</span></span>

```powershell
($A = Get-ChildItem -Path $PSHOME -Recurse) | Out-GridView
```

<span data-ttu-id="210d0-135">`Get-ChildItem` hämtar alla filer i installations katalogen för PowerShell och dess under kataloger med hjälp av den `$PSHOME` automatiska variabeln.</span><span class="sxs-lookup"><span data-stu-id="210d0-135">`Get-ChildItem` gets all the files in the PowerShell installation directory and its subdirectories using the the `$PSHOME` automatic variable.</span></span> <span data-ttu-id="210d0-136">Parenteserna i kommandot fastställer ordningen för åtgärder.</span><span class="sxs-lookup"><span data-stu-id="210d0-136">The parentheses in the command establish the order of operations.</span></span> <span data-ttu-id="210d0-137">Därför sparas utdata från `Get-ChildItem` kommandot i `$A` variabeln innan det skickas till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-137">As a result, the output from the `Get-ChildItem` command is saved in the `$A` variable before it is sent to `Out-GridView`.</span></span>

### <span data-ttu-id="210d0-138">Exempel 5: utmatnings processer för en angiven dator till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-138">Example 5: Output processes for a specified computer to a grid view</span></span>

<span data-ttu-id="210d0-139">I det här exemplet visas de processer som körs på Server01-datorn i ett fönster för rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-139">This example displays the processes that are running on the Server01 computer in a grid view window.</span></span>

```powershell
Get-Process -ComputerName "Server01" | ogv -Title "Processes - Server01"
```

<span data-ttu-id="210d0-140">Examle använder `ogv` , vilket är aliaset för `Out-GridView` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="210d0-140">The examle uses `ogv`, which is the alias for the `Out-GridView` cmdlet.</span></span> <span data-ttu-id="210d0-141">Parametern **title** anger fönstrets rubrik.</span><span class="sxs-lookup"><span data-stu-id="210d0-141">The **Title** parameter specifies the window title.</span></span>

### <span data-ttu-id="210d0-142">Exempel 6: Spara data från fjärrdatorer till en rutnätsvy</span><span class="sxs-lookup"><span data-stu-id="210d0-142">Example 6: Output data from remote computers to a grid view</span></span>

<span data-ttu-id="210d0-143">Det här exemplet visar hur du skickar data som samlas in från fjärrdatorer till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-143">This example shows how to send data collected from remote computers to `Out-GridView`.</span></span>

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture} | Out-GridView
```

<span data-ttu-id="210d0-144">`Invoke-Command` körs `Get-Culture` på tre fjärrdatorer.</span><span class="sxs-lookup"><span data-stu-id="210d0-144">`Invoke-Command` runs `Get-Culture` on three remote computers.</span></span> <span data-ttu-id="210d0-145">Resulterande data är skickas `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-145">The resulting data is piped to `Out-GridView`.</span></span> <span data-ttu-id="210d0-146">Observera att skript blocket som körs på fjärrdatorn inte innehåller `Out-GridView` kommandot.</span><span class="sxs-lookup"><span data-stu-id="210d0-146">Notice that the script block that runs on the remote computer does not include the `Out-GridView` command.</span></span> <span data-ttu-id="210d0-147">Om den gjorde det kunde kommandot inte utföras när det försökte öppna ett fönster för rutnätsvy på var och en av de fjärranslutna datorerna.</span><span class="sxs-lookup"><span data-stu-id="210d0-147">If it did, the command would fail when it tried to open a grid view window on each of the remote computers.</span></span>

### <span data-ttu-id="210d0-148">Exempel 7: skicka flera objekt via `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="210d0-148">Example 7: Pass multiple items through `Out-GridView`</span></span>

<span data-ttu-id="210d0-149">I det här exemplet kan du välja flera processer i `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="210d0-149">This example lets you select multiple processes from the `Out-GridView` window.</span></span> <span data-ttu-id="210d0-150">De processer som du väljer skickas till `Export-Csv` kommandot och skrivs till `ProcessLog.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="210d0-150">The processes that you select are passed to the `Export-Csv` command and written to the `ProcessLog.csv` file.</span></span>

```powershell
Get-Process | Out-GridView -PassThru | Export-Csv -Path .\ProcessLog.csv
```

<span data-ttu-id="210d0-151">Med parametern **Passthru** `Out-GridView` kan du skicka flera objekt nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="210d0-151">The **PassThru** parameter of `Out-GridView` lets you send multiple items down the pipeline.</span></span> <span data-ttu-id="210d0-152">Parametern **Passthru** motsvarar användningen av **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="210d0-152">The **PassThru** parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

### <span data-ttu-id="210d0-153">Exempel 8: skapa en Windows-genväg till `Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="210d0-153">Example 8: Create a Windows shortcut to `Out-GridView`</span></span>

<span data-ttu-id="210d0-154">Det här exemplet visar hur du använder **wait** -parametern för `Out-GridView` för att skapa en Windows-genväg till `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="210d0-154">This example shows how to use the **Wait** parameter of `Out-GridView` to create a Windows shortcut to the `Out-GridView` window.</span></span>

```powershell
pwsh -Command "Get-Service | Out-GridView -Wait"
```

<span data-ttu-id="210d0-155">Den här kommando raden kan användas i en Windows-genväg.</span><span class="sxs-lookup"><span data-stu-id="210d0-155">This command line can be used in a Windows shortcut.</span></span> <span data-ttu-id="210d0-156">Utan parametern **wait** avslutas PowerShell så snart `Out-GridView` fönstret har öppnats, vilket skulle stänga `Out-GridView` fönstret nästan omedelbart.</span><span class="sxs-lookup"><span data-stu-id="210d0-156">Without the **Wait** parameter, PowerShell would exit as soon as the `Out-GridView` window opened, which would close the `Out-GridView` window almost immediately.</span></span>

## <span data-ttu-id="210d0-157">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="210d0-157">PARAMETERS</span></span>

### <span data-ttu-id="210d0-158">– InputObject</span><span class="sxs-lookup"><span data-stu-id="210d0-158">-InputObject</span></span>

<span data-ttu-id="210d0-159">Anger objekt som cmdleten accepterar som ininformation för `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-159">Specifies object that the cmdlet accepts as input for `Out-GridView`.</span></span>

<span data-ttu-id="210d0-160">När du använder parametern **InputObject** för att skicka en samling objekt till `Out-GridView` , `Out-GridView` behandlar samlingen som ett samlings objekt och visar en rad som representerar samlingen.</span><span class="sxs-lookup"><span data-stu-id="210d0-160">When you use the **InputObject** parameter to send a collection of objects to `Out-GridView`, `Out-GridView` treats the collection as one collection object, and it displays one row that represents the collection.</span></span> <span data-ttu-id="210d0-161">Om du vill visa varje objekt i samlingen använder du en pipeline-operator (|) för att skicka objekt till `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-161">To display the each object in the collection, use a pipeline operator (|) to send objects to `Out-GridView`.</span></span>

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

### <span data-ttu-id="210d0-162">-OutputMode</span><span class="sxs-lookup"><span data-stu-id="210d0-162">-OutputMode</span></span>

<span data-ttu-id="210d0-163">Anger de objekt som det interaktiva fönstret skickar nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="210d0-163">Specifies the items that the interactive window sends down the pipeline as input to other commands.</span></span>
<span data-ttu-id="210d0-164">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="210d0-164">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="210d0-165">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="210d0-165">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span>

<span data-ttu-id="210d0-166">Värdena för den här parametern avgör hur många objekt du kan skicka pipelinen.</span><span class="sxs-lookup"><span data-stu-id="210d0-166">The values of this parameter determine how many items you can send down the pipeline.</span></span>

- <span data-ttu-id="210d0-167">Inga.</span><span class="sxs-lookup"><span data-stu-id="210d0-167">None.</span></span>  <span data-ttu-id="210d0-168">Inga objekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-168">No items.</span></span> <span data-ttu-id="210d0-169">Detta är standardvärdet.</span><span class="sxs-lookup"><span data-stu-id="210d0-169">This is the default value.</span></span>
- <span data-ttu-id="210d0-170">Samma.</span><span class="sxs-lookup"><span data-stu-id="210d0-170">Single.</span></span> <span data-ttu-id="210d0-171">Noll objekt eller ett objekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-171">Zero items or one item.</span></span> <span data-ttu-id="210d0-172">Använd det här värdet när nästa kommando bara kan ta ett indatamängds objekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-172">Use this value when the next command can take only one input object.</span></span>
- <span data-ttu-id="210d0-173">Flera.</span><span class="sxs-lookup"><span data-stu-id="210d0-173">Multiple.</span></span> <span data-ttu-id="210d0-174">Noll, ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-174">Zero, one, or many items.</span></span> <span data-ttu-id="210d0-175">Använd det här värdet när nästa kommando kan ta flera inobjekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-175">Use this value when the next command can take multiple input objects.</span></span> <span data-ttu-id="210d0-176">Värdet motsvarar parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="210d0-176">This value is equivalent to the **Passthru** parameter.</span></span>

<span data-ttu-id="210d0-177">Den här parametern introducerades i Windows PowerShell 3,0.</span><span class="sxs-lookup"><span data-stu-id="210d0-177">This parameter was introduced in Windows PowerShell 3.0.</span></span>

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

### <span data-ttu-id="210d0-178">– PassThru</span><span class="sxs-lookup"><span data-stu-id="210d0-178">-PassThru</span></span>

<span data-ttu-id="210d0-179">Anger att cmdleten skickar objekt från det interaktiva fönstret nedåt i pipeline som ininformation till andra kommandon.</span><span class="sxs-lookup"><span data-stu-id="210d0-179">Indicates that the cmdlet sends items from the interactive window down the pipeline as input to other commands.</span></span> <span data-ttu-id="210d0-180">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="210d0-180">By default, this cmdlet does not generate any output.</span></span> <span data-ttu-id="210d0-181">Den här parametern motsvarar att använda **Multiple** -värdet för parametern **OutputMode** .</span><span class="sxs-lookup"><span data-stu-id="210d0-181">This parameter is equivalent to using the **Multiple** value of the **OutputMode** parameter.</span></span>

<span data-ttu-id="210d0-182">Om du vill skicka objekt från det interaktiva fönstret nedåt i pipelinen klickar du på objekten och klickar sedan på OK.</span><span class="sxs-lookup"><span data-stu-id="210d0-182">To send items from the interactive window down the pipeline, click to select the items and then click OK.</span></span> <span data-ttu-id="210d0-183">Shift-klicka och Ctrl-klicka stöds.</span><span class="sxs-lookup"><span data-stu-id="210d0-183">Shift-click and Ctrl-click are supported.</span></span>

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

### <span data-ttu-id="210d0-184">– Rubrik</span><span class="sxs-lookup"><span data-stu-id="210d0-184">-Title</span></span>

<span data-ttu-id="210d0-185">Anger den text som visas i namn listen för `Out-GridView` fönstret.</span><span class="sxs-lookup"><span data-stu-id="210d0-185">Specifies the text that appears in the title bar of the `Out-GridView` window.</span></span> <span data-ttu-id="210d0-186">Som standard visar namn listen det kommando som anropar `Out-GridView` .</span><span class="sxs-lookup"><span data-stu-id="210d0-186">By default, the title bar displays the command that invokes `Out-GridView`.</span></span>

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

### <span data-ttu-id="210d0-187">– Vänta</span><span class="sxs-lookup"><span data-stu-id="210d0-187">-Wait</span></span>

<span data-ttu-id="210d0-188">Anger att cmdleten ignorerar kommando tolken och förhindrar att Windows PowerShell stängs tills `Out-GridView` fönstret har stängts.</span><span class="sxs-lookup"><span data-stu-id="210d0-188">Indicates that the cmdlet suppresses the command prompt and prevents Windows PowerShell from closing until the `Out-GridView` window is closed.</span></span> <span data-ttu-id="210d0-189">Som standard returnerar kommando tolken när `Out-GridView` fönstret öppnas.</span><span class="sxs-lookup"><span data-stu-id="210d0-189">By default, the command prompt returns when the `Out-GridView` window opens.</span></span>

<span data-ttu-id="210d0-190">Med den här funktionen kan du använda `Out-GridView` cmdlets i Windows-genvägar.</span><span class="sxs-lookup"><span data-stu-id="210d0-190">This feature lets you use the `Out-GridView` cmdlets in Windows shortcuts.</span></span> <span data-ttu-id="210d0-191">När `Out-GridView` används i en genväg utan parametern **wait** , `Out-GridView` visas fönstret bara tillfälligt innan PowerShell stängs.</span><span class="sxs-lookup"><span data-stu-id="210d0-191">When `Out-GridView` is used in a shortcut without the **Wait** parameter, the `Out-GridView` window appears only momentarily before PowerShell closes.</span></span>

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

### <span data-ttu-id="210d0-192">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="210d0-192">CommonParameters</span></span>

<span data-ttu-id="210d0-193">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="210d0-193">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="210d0-194">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="210d0-194">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="210d0-195">INDATA</span><span class="sxs-lookup"><span data-stu-id="210d0-195">INPUTS</span></span>

### <span data-ttu-id="210d0-196">System. Management. Automation. PSObject</span><span class="sxs-lookup"><span data-stu-id="210d0-196">System.Management.Automation.PSObject</span></span>

<span data-ttu-id="210d0-197">Du kan skicka valfritt objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="210d0-197">You can send any object to this cmdlet.</span></span>

## <span data-ttu-id="210d0-198">UTDATA</span><span class="sxs-lookup"><span data-stu-id="210d0-198">OUTPUTS</span></span>

### <span data-ttu-id="210d0-199">Inget</span><span class="sxs-lookup"><span data-stu-id="210d0-199">None</span></span>

<span data-ttu-id="210d0-200">Normalt `Out-GridView` returnerar inte några objekt.</span><span class="sxs-lookup"><span data-stu-id="210d0-200">Normally, `Out-GridView` does not return any objects.</span></span> <span data-ttu-id="210d0-201">När du använder parametern **Passthru** returneras objekten som representerar de valda raderna till pipelinen.</span><span class="sxs-lookup"><span data-stu-id="210d0-201">When using the **PassThru** parameter, the objects representing the selected rows are returned to the pipeline.</span></span>

## <span data-ttu-id="210d0-202">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="210d0-202">NOTES</span></span>

<span data-ttu-id="210d0-203">Du kan inte använda ett fjärran slutet kommando för att öppna ett fönster för rutnätsvy på en annan dator.</span><span class="sxs-lookup"><span data-stu-id="210d0-203">You cannot use a remote command to open a grid view window on another computer.</span></span>

<span data-ttu-id="210d0-204">Kommandots utdata som du skickar till `Out-GridView` kan inte formateras med `Format` cmdletarna, till exempel `Format-Table` eller- `Format-Wide` cmdletar.</span><span class="sxs-lookup"><span data-stu-id="210d0-204">The command output that you send to `Out-GridView` cannot be formatted using the `Format` cmdlets, such as `Format-Table` or `Format-Wide` cmdlets.</span></span> <span data-ttu-id="210d0-205">Använd cmdleten för att välja egenskaper `Select-Object` .</span><span class="sxs-lookup"><span data-stu-id="210d0-205">To select properties, use the `Select-Object` cmdlet.</span></span>

<span data-ttu-id="210d0-206">Avserialiserade utdata från fjärrkommandon kanske inte är korrekt formaterade i rutnätsvy-fönstret.</span><span class="sxs-lookup"><span data-stu-id="210d0-206">Deserialized output from remote commands might not be formatted correctly in the grid view window.</span></span>

<span data-ttu-id="210d0-207">Kortkommandon **för**`Out-GridView`</span><span class="sxs-lookup"><span data-stu-id="210d0-207">**Keyboard Shortcuts for** `Out-GridView`</span></span>

|              <span data-ttu-id="210d0-208">Använd den här nyckeln:</span><span class="sxs-lookup"><span data-stu-id="210d0-208">Use this key:</span></span>              |                                   <span data-ttu-id="210d0-209">För att utföra den här åtgärden:</span><span class="sxs-lookup"><span data-stu-id="210d0-209">To perform this action:</span></span>                                    |
| --------------------------------------- | -------------------------------------------------------------------------------------------- |
| <span data-ttu-id="210d0-210"><kbd>Tabbtecken</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-210"><kbd>Tab</kbd></span></span>                          | <span data-ttu-id="210d0-211">Flyttar markören från **filter** rutan till menyn **Lägg till villkor** i tabellen och tillbaka.</span><span class="sxs-lookup"><span data-stu-id="210d0-211">Moves the cursor from the **Filter** box to the **Add criteria** menu to the table and back.</span></span> |
| <span data-ttu-id="210d0-212"><kbd>Nedåtpil</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-212"><kbd>UpArrow</kbd></span></span>                      | <span data-ttu-id="210d0-213">Flytta upp en rad.</span><span class="sxs-lookup"><span data-stu-id="210d0-213">Move up one row.</span></span> <span data-ttu-id="210d0-214">Flyttar till kolumn rubriker från första raden med data.</span><span class="sxs-lookup"><span data-stu-id="210d0-214">Moves to column headers from first row of data.</span></span>                             |
| <span data-ttu-id="210d0-215"><kbd>NEDPIL</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-215"><kbd>DownArrow</kbd></span></span>                    | <span data-ttu-id="210d0-216">Flytta ned en rad.</span><span class="sxs-lookup"><span data-stu-id="210d0-216">Move down one row.</span></span>                                                                           |
| <span data-ttu-id="210d0-217"><kbd>LeftArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-217"><kbd>LeftArrow</kbd></span></span>                    | <span data-ttu-id="210d0-218">Flytta en kolumn till vänster i kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="210d0-218">In column header row, move left one column.</span></span>                                                  |
| <span data-ttu-id="210d0-219"><kbd>RightArrow</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-219"><kbd>RightArrow</kbd></span></span>                   | <span data-ttu-id="210d0-220">I kolumn rubrik raden flyttar du en kolumn till höger.</span><span class="sxs-lookup"><span data-stu-id="210d0-220">In column header row, move right one column.</span></span>                                                 |
| <span data-ttu-id="210d0-221"><kbd>ContextMenuKey</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-221"><kbd>ContextMenuKey</kbd></span></span>               | <span data-ttu-id="210d0-222">I kolumn rubrik raden visas alternativet Välj kolumner.</span><span class="sxs-lookup"><span data-stu-id="210d0-222">In column header row, displays the Select Columns option.</span></span>                                    |
| <span data-ttu-id="210d0-223"><kbd>Ange</kbd> eller <kbd>blank steg</kbd></span><span class="sxs-lookup"><span data-stu-id="210d0-223"><kbd>Enter</kbd> or <kbd>Spacebar</kbd></span></span> | <span data-ttu-id="210d0-224">I kolumn rubrik raden sorterar du kolumn data (växla A-Z, Z-A).</span><span class="sxs-lookup"><span data-stu-id="210d0-224">In column header row, sort column data (toggle A-Z, Z-A).</span></span>                                    |

<span data-ttu-id="210d0-225">**Använda funktionerna i rutnätsvy-fönstret**</span><span class="sxs-lookup"><span data-stu-id="210d0-225">**How to Use the Grid View Window Features**</span></span>

<span data-ttu-id="210d0-226">**För att dölja eller Visa en kolumn:**</span><span class="sxs-lookup"><span data-stu-id="210d0-226">**To hide or show a column:**</span></span>

1. <span data-ttu-id="210d0-227">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="210d0-227">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="210d0-228">I dialog rutan **Välj kolumner** använder du piltangenterna för att flytta kolumnerna mellan de markerade kolumnerna i rutorna tillgängliga kolumner.</span><span class="sxs-lookup"><span data-stu-id="210d0-228">In the **Select Columns** dialog box, use the arrow keys to move the columns between the Selected columns to the Available columns boxes.</span></span> <span data-ttu-id="210d0-229">Endast kolumner i rutan **Välj kolumner** visas i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-229">Only columns in the **Select Columns** box appear in the grid view window.</span></span>

<span data-ttu-id="210d0-230">**Så här ordnar du om kolumner:**</span><span class="sxs-lookup"><span data-stu-id="210d0-230">**To reorder columns:**</span></span>

<span data-ttu-id="210d0-231">Du kan dra och släppa kolumner till önskad plats.</span><span class="sxs-lookup"><span data-stu-id="210d0-231">You can drag and drop columns into the desired location.</span></span> <span data-ttu-id="210d0-232">Eller Använd följande steg:</span><span class="sxs-lookup"><span data-stu-id="210d0-232">Or use the following steps:</span></span>

1. <span data-ttu-id="210d0-233">Högerklicka på en kolumn rubrik och klicka på **Välj kolumner**.</span><span class="sxs-lookup"><span data-stu-id="210d0-233">Right-click any column header and click **Select Columns**.</span></span>
2. <span data-ttu-id="210d0-234">I dialog rutan **Välj kolumner** använder du knapparna **Flytta upp** och **Flytta ned** för att ändra ordning på kolumnerna.</span><span class="sxs-lookup"><span data-stu-id="210d0-234">In the **Select Columns** dialog box, use the **Move up** and **Move down** buttons to reorder the columns.</span></span> <span data-ttu-id="210d0-235">Kolumner överst i listan visas till vänster om kolumner längst ned i listan i fönstret rutnätsvy.</span><span class="sxs-lookup"><span data-stu-id="210d0-235">Columns at the top of the list appear to the left of columns at the bottom of the list in the grid view window.</span></span>

<span data-ttu-id="210d0-236">**Sortera tabell data**</span><span class="sxs-lookup"><span data-stu-id="210d0-236">**How to Sort Table Data**</span></span>

- <span data-ttu-id="210d0-237">Om du vill sortera data klickar du på en kolumn rubrik.</span><span class="sxs-lookup"><span data-stu-id="210d0-237">To sort the data, click a column header.</span></span>
- <span data-ttu-id="210d0-238">Klicka på kolumn rubriken igen om du vill ändra sorterings ordningen.</span><span class="sxs-lookup"><span data-stu-id="210d0-238">To change the sort order, click the column header again.</span></span> <span data-ttu-id="210d0-239">Varje gången du klickar på samma rubrik växlar sorterings ordningen mellan stigande till fallande ordning.</span><span class="sxs-lookup"><span data-stu-id="210d0-239">Each time you click the same header, the sort order toggles between ascending to descending order.</span></span> <span data-ttu-id="210d0-240">Den aktuella ordningen anges av en triangel i kolumn rubriken.</span><span class="sxs-lookup"><span data-stu-id="210d0-240">The current order is indicated by a triangle in the column header.</span></span>

<span data-ttu-id="210d0-241">**Så här väljer du tabell data**</span><span class="sxs-lookup"><span data-stu-id="210d0-241">**How to Select Table Data**</span></span>

- <span data-ttu-id="210d0-242">Om du vill markera en rad markerar du raden eller använder upp-eller nedpilen för att navigera till raden.</span><span class="sxs-lookup"><span data-stu-id="210d0-242">To select a row, select the row or use the up or down arrow to navigate to the row.</span></span>
- <span data-ttu-id="210d0-243">Om du vill markera alla rader (förutom rubrik raden) trycker du på <kbd>CTRL</kbd> + <kbd>A</kbd>.</span><span class="sxs-lookup"><span data-stu-id="210d0-243">To select all rows (except for the header row), press <kbd>CTRL</kbd>+<kbd>A</kbd>.</span></span>
- <span data-ttu-id="210d0-244">Om du vill markera efterföljande rader trycker du på och håller <kbd>ned SKIFT</kbd> -tangenten medan du klickar på raderna eller använder piltangenterna.</span><span class="sxs-lookup"><span data-stu-id="210d0-244">To select consecutive rows, press and hold the <kbd>SHIFT</kbd> key while clicking the rows or using the arrow keys.</span></span>
- <span data-ttu-id="210d0-245">Om du vill markera rader som inte är i följd trycker du på <kbd>CTRL</kbd> -tangenten och klickar för att lägga till en rad i markeringen.</span><span class="sxs-lookup"><span data-stu-id="210d0-245">To select nonconsecutive rows, press the <kbd>CTRL</kbd> key and click to add a row to the selection.</span></span>
- <span data-ttu-id="210d0-246">Det går inte att markera kolumner och det går inte att markera hela kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="210d0-246">You cannot select columns, and you cannot select the entire column header row.</span></span>

<span data-ttu-id="210d0-247">**Kopiera rader**</span><span class="sxs-lookup"><span data-stu-id="210d0-247">**How to Copy Rows**</span></span>

- <span data-ttu-id="210d0-248">Om du vill kopiera en eller flera rader från tabellen markerar du raderna och trycker sedan på CTRL + C.</span><span class="sxs-lookup"><span data-stu-id="210d0-248">To copy one or more rows from the table, select the rows and then press CTRL+C.</span></span>

  <span data-ttu-id="210d0-249">Du kan klistra in data i valfritt text-eller kalkyl blads program.</span><span class="sxs-lookup"><span data-stu-id="210d0-249">You can paste the data into any text or spreadsheet program.</span></span> <span data-ttu-id="210d0-250">Du kan inte kopiera kolumner eller delar av rader och du kan inte kopiera kolumn rubrik raden.</span><span class="sxs-lookup"><span data-stu-id="210d0-250">You cannot copy columns or parts of rows and you cannot copy the column header row.</span></span>

<span data-ttu-id="210d0-251">**Söka i tabellen (snabb filter)**</span><span class="sxs-lookup"><span data-stu-id="210d0-251">**How to Search in the Table (Quick Filter)**</span></span>

<span data-ttu-id="210d0-252">Använd filter rutan för att söka efter data i tabellen.</span><span class="sxs-lookup"><span data-stu-id="210d0-252">Use the Filter box to search for data in the table.</span></span> <span data-ttu-id="210d0-253">När du skriver i rutan visas endast objekt som innehåller texten som skrivs in i tabellen.</span><span class="sxs-lookup"><span data-stu-id="210d0-253">When you type in the box, only items that include the typed text appear in the table.</span></span>

- <span data-ttu-id="210d0-254">Sök efter text.</span><span class="sxs-lookup"><span data-stu-id="210d0-254">Search for text.</span></span> <span data-ttu-id="210d0-255">Om du vill söka efter text i tabellen skriver du den text som du vill söka efter i rutan filter.</span><span class="sxs-lookup"><span data-stu-id="210d0-255">To search for text in the table, in the Filter box, type the text to find.</span></span>
- <span data-ttu-id="210d0-256">Sök efter flera ord.</span><span class="sxs-lookup"><span data-stu-id="210d0-256">Search for multiple words.</span></span> <span data-ttu-id="210d0-257">Om du vill söka efter flera ord i tabellen skriver du orden avgränsade med blank steg.</span><span class="sxs-lookup"><span data-stu-id="210d0-257">To search for multiple words in the table, type the words separated by spaces.</span></span> <span data-ttu-id="210d0-258">`Out-GridView` visar rader som innehåller alla ord (logiska och).</span><span class="sxs-lookup"><span data-stu-id="210d0-258">`Out-GridView` displays rows that include all the words (logical AND).</span></span>
- <span data-ttu-id="210d0-259">Sök efter litterala fraser.</span><span class="sxs-lookup"><span data-stu-id="210d0-259">Search for literal phrases.</span></span> <span data-ttu-id="210d0-260">Om du vill söka efter fraser som innehåller blank steg eller specialtecken, omger du frasen med citat tecken.</span><span class="sxs-lookup"><span data-stu-id="210d0-260">To search for phrases that include spaces or special characters, enclose the phrase in quotation marks.</span></span> <span data-ttu-id="210d0-261">`Out-GridView` visar rader som innehåller en exakt matchning för frasen.</span><span class="sxs-lookup"><span data-stu-id="210d0-261">`Out-GridView` displays rows that include an exact match for the phrase.</span></span>
- <span data-ttu-id="210d0-262">Sök i kolumner.</span><span class="sxs-lookup"><span data-stu-id="210d0-262">Search in columns.</span></span> <span data-ttu-id="210d0-263">Om du vill söka efter text i en eller flera kolumner använder du följande format:</span><span class="sxs-lookup"><span data-stu-id="210d0-263">To search for text in one or more columns, use the following format:</span></span>

  `<column>:<text> [<column>:<text>] ...`

  <span data-ttu-id="210d0-264">Om du till exempel vill hitta "net" i kolumnen **DisplayName** i rutan **filter** skriver du:</span><span class="sxs-lookup"><span data-stu-id="210d0-264">For example, to find "Net" in the **DisplayName** column, in the **Filter** box, type:</span></span>

  `displayname:net`

  <span data-ttu-id="210d0-265">Om du vill hitta rader med "net" i kolumnerna **DisplayName** och **namn** , skriver du följande i rutan **filter** :</span><span class="sxs-lookup"><span data-stu-id="210d0-265">To find rows with "Net" in the **DisplayName** and **Name** columns, in the **Filter** box, type:</span></span>

  `displayname:net name:net`

- <span data-ttu-id="210d0-266">Stäng av Sök funktionen.</span><span class="sxs-lookup"><span data-stu-id="210d0-266">Turn off search.</span></span> <span data-ttu-id="210d0-267">Om du vill visa hela tabellen igen klickar du på knappen röd X i det övre högra hörnet av **filter** rutan eller tar bort texten från **filter** rutan.</span><span class="sxs-lookup"><span data-stu-id="210d0-267">To display the entire table again, click the red X button in the top right corner of the **Filter** box or delete the text from the **Filter** box.</span></span>

<span data-ttu-id="210d0-268">**Använd villkor för att filtrera tabellen**</span><span class="sxs-lookup"><span data-stu-id="210d0-268">**Use Criteria to Filter the Table**</span></span>

<span data-ttu-id="210d0-269">Du kan använda regler eller kriterier för att avgöra vilka objekt som visas i tabellen.</span><span class="sxs-lookup"><span data-stu-id="210d0-269">You can use rules or criteria to determine which items are displayed in the table.</span></span> <span data-ttu-id="210d0-270">Objekt visas bara när de uppfyller alla kriterier som du upprättar.</span><span class="sxs-lookup"><span data-stu-id="210d0-270">Items appear only when they satisfy all the criteria that you establish.</span></span> <span data-ttu-id="210d0-271">De tillgängliga kriterierna bestäms av egenskaperna för de objekt som visas i fönstret rutnätsvy och .NET Framework typer av dessa egenskaper.</span><span class="sxs-lookup"><span data-stu-id="210d0-271">The available criteria are determined by the properties of the objects displayed in the grid view window and the .NET Framework types of those properties.</span></span>

<span data-ttu-id="210d0-272">Varje kriterium har följande format:</span><span class="sxs-lookup"><span data-stu-id="210d0-272">Each criterion has the following format:</span></span>

`<column> <operator> <value>`

<span data-ttu-id="210d0-273">Villkor för olika egenskaper är anslutna med **och**.</span><span class="sxs-lookup"><span data-stu-id="210d0-273">Criteria for different properties are connected by **AND**.</span></span> <span data-ttu-id="210d0-274">Villkor för samma egenskap är anslutna med **eller**.</span><span class="sxs-lookup"><span data-stu-id="210d0-274">Criteria for the same property are connected by **OR**.</span></span> <span data-ttu-id="210d0-275">Du kan inte ändra de logiska anslutningarna.</span><span class="sxs-lookup"><span data-stu-id="210d0-275">You cannot change the logical connectors.</span></span>

<span data-ttu-id="210d0-276">Kriterierna påverkar bara visningen.</span><span class="sxs-lookup"><span data-stu-id="210d0-276">The criteria only affects the display.</span></span> <span data-ttu-id="210d0-277">Objekt tas inte bort från tabellen.</span><span class="sxs-lookup"><span data-stu-id="210d0-277">It does not delete items from the table.</span></span>

<span data-ttu-id="210d0-278">**Lägga till villkor**</span><span class="sxs-lookup"><span data-stu-id="210d0-278">**How to Add Criteria**</span></span>

1. <span data-ttu-id="210d0-279">Om du vill visa meny knappen **Lägg till villkor** klickar du på pilen i det övre högra hörnet i fönstret.</span><span class="sxs-lookup"><span data-stu-id="210d0-279">To display the **Add criteria** menu button, in the upper right corner of the window, click the Expand arrow.</span></span>
2. <span data-ttu-id="210d0-280">Klicka på Meny knappen **Lägg till villkor** .</span><span class="sxs-lookup"><span data-stu-id="210d0-280">Click the **Add Criteria** menu button.</span></span>
3. <span data-ttu-id="210d0-281">Klicka för att välja kolumner (egenskaper).</span><span class="sxs-lookup"><span data-stu-id="210d0-281">Click to select columns (properties).</span></span> <span data-ttu-id="210d0-282">Du kan välja en eller flera egenskaper.</span><span class="sxs-lookup"><span data-stu-id="210d0-282">You can select one or many properties.</span></span>
4. <span data-ttu-id="210d0-283">När du är färdig med att välja egenskaper klickar du på knappen **Lägg till** .</span><span class="sxs-lookup"><span data-stu-id="210d0-283">When you are finished selecting properties, click the **Add** button.</span></span>
5. <span data-ttu-id="210d0-284">Klicka på **Avbryt** om du vill avbryta tilläggen.</span><span class="sxs-lookup"><span data-stu-id="210d0-284">To cancel the additions, click **Cancel**.</span></span>
6. <span data-ttu-id="210d0-285">Om du vill lägga till fler villkor klickar du på knappen **Lägg till villkor** igen.</span><span class="sxs-lookup"><span data-stu-id="210d0-285">To add more criteria, click the **Add Criteria** button again.</span></span>

<span data-ttu-id="210d0-286">**Så här redigerar du ett kriterium**</span><span class="sxs-lookup"><span data-stu-id="210d0-286">**How to Edit a Criterion**</span></span>

- <span data-ttu-id="210d0-287">Om du vill ändra en operator klickar du på värdet blå operator och väljer sedan en annan operator i list rutan.</span><span class="sxs-lookup"><span data-stu-id="210d0-287">To change an operator, click the blue operator value, and then select a different operator from the drop-down list.</span></span>
- <span data-ttu-id="210d0-288">Ange ett värde i rutan värde om du vill ange eller ändra ett värde.</span><span class="sxs-lookup"><span data-stu-id="210d0-288">To enter or change a value, type a value in the value box.</span></span> <span data-ttu-id="210d0-289">Om du anger ett värde som inte är giltigt visas en cirkel X-ikon.</span><span class="sxs-lookup"><span data-stu-id="210d0-289">If you enter a value that is not valid, a circular X icon appears.</span></span> <span data-ttu-id="210d0-290">Ändra värdet om du vill ta bort det.</span><span class="sxs-lookup"><span data-stu-id="210d0-290">To remove it, change the value.</span></span>
- <span data-ttu-id="210d0-291">Om du vill skapa en **or** -instruktion lägger du till ett villkor med samma egenskap.</span><span class="sxs-lookup"><span data-stu-id="210d0-291">To create an **OR** statement, add a criteria with the same property.</span></span>

<span data-ttu-id="210d0-292">**Ta bort villkor**</span><span class="sxs-lookup"><span data-stu-id="210d0-292">**How to Delete Criteria**</span></span>

- <span data-ttu-id="210d0-293">Om du vill ta bort de valda villkoren klickar du på det röda krysset bredvid varje kriterium.</span><span class="sxs-lookup"><span data-stu-id="210d0-293">To delete selected criteria, click the red X beside each criterion.</span></span>
- <span data-ttu-id="210d0-294">Om du vill ta bort alla kriterier klickar du på knappen **Rensa alla** .</span><span class="sxs-lookup"><span data-stu-id="210d0-294">To delete all criteria, click the **Clear All** button.</span></span>

## <span data-ttu-id="210d0-295">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="210d0-295">RELATED LINKS</span></span>

[<span data-ttu-id="210d0-296">Ut-fil</span><span class="sxs-lookup"><span data-stu-id="210d0-296">Out-File</span></span>](Out-File.md)

[<span data-ttu-id="210d0-297">Out-Printer</span><span class="sxs-lookup"><span data-stu-id="210d0-297">Out-Printer</span></span>](Out-Printer.md)

[<span data-ttu-id="210d0-298">Out-sträng</span><span class="sxs-lookup"><span data-stu-id="210d0-298">Out-String</span></span>](Out-String.md)
