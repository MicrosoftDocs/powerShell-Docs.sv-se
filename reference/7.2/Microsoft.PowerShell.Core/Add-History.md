---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/add-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Add-History
ms.openlocfilehash: d2c0abb0e6742de3e316fe964d5945375591ef4d
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708815"
---
# <span data-ttu-id="30da3-102">Add-History</span><span class="sxs-lookup"><span data-stu-id="30da3-102">Add-History</span></span>

## <span data-ttu-id="30da3-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="30da3-103">SYNOPSIS</span></span>
<span data-ttu-id="30da3-104">Lägger till poster i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="30da3-104">Appends entries to the session history.</span></span>

## <span data-ttu-id="30da3-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="30da3-105">SYNTAX</span></span>

```
Add-History [[-InputObject] <PSObject[]>] [-Passthru] [<CommonParameters>]
```

## <span data-ttu-id="30da3-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="30da3-106">DESCRIPTION</span></span>

<span data-ttu-id="30da3-107">`Add-History`Cmdleten lägger till poster i slutet av tidigare sessioner, det vill säga en lista över kommandon som angavs under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-107">The `Add-History` cmdlet adds entries to the end of the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="30da3-108">Tidigare session är en lista över kommandon som anges under sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-108">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="30da3-109">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="30da3-109">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="30da3-110">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="30da3-110">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="30da3-111">Mer information om tidigare sessioner finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="30da3-111">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="30da3-112">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="30da3-112">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="30da3-113">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="30da3-113">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="30da3-114">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="30da3-114">This cmdlet only works with the session history.</span></span> <span data-ttu-id="30da3-115">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="30da3-115">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

<span data-ttu-id="30da3-116">Du kan använda `Get-History` cmdleten för att hämta kommandon och skicka dem till `Add-History` , eller så kan du exportera kommandona till en CSV-eller XML-fil, sedan importera kommandona och skicka den importerade filen till `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="30da3-116">You can use the `Get-History` cmdlet to get the commands and pass them to `Add-History`, or you can export the commands to a CSV or XML file, then import the commands, and pass the imported file to `Add-History`.</span></span> <span data-ttu-id="30da3-117">Du kan använda denna cmdlet för att lägga till vissa kommandon i historiken eller för att skapa en enskild historik fil som innehåller kommandon från fler än en session.</span><span class="sxs-lookup"><span data-stu-id="30da3-117">You can use this cmdlet to add specific commands to the history or to create a single history file that includes commands from more than one session.</span></span>

## <span data-ttu-id="30da3-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="30da3-118">EXAMPLES</span></span>

### <span data-ttu-id="30da3-119">Exempel 1: Lägg till kommandon i historiken för en annan session</span><span class="sxs-lookup"><span data-stu-id="30da3-119">Example 1: Add commands to the history of a different session</span></span>

<span data-ttu-id="30da3-120">I det här exemplet lägger du till kommandona som skrevs i en PowerShell-session i historiken för en annan PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="30da3-120">This example add the commands typed in one PowerShell session to the history of a different PowerShell session.</span></span>

```powershell
Get-History | Export-Csv c:\testing\history.csv -IncludeTypeInformation
Import-Csv c:\testing\history.csv | Add-History
```

<span data-ttu-id="30da3-121">Det första kommandot hämtar objekt som representerar kommandona i historiken och exporterar dem till `History.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="30da3-121">The first command gets objects representing the commands in the history and exports them to the `History.csv` file.</span></span>

<span data-ttu-id="30da3-122">Det andra kommandot anges på kommando raden i en annan session.</span><span class="sxs-lookup"><span data-stu-id="30da3-122">The second command is typed at the command line of a different session.</span></span> <span data-ttu-id="30da3-123">Den använder `Import-Csv` cmdleten för att importera objekten i `History.csv` filen.</span><span class="sxs-lookup"><span data-stu-id="30da3-123">It uses the `Import-Csv` cmdlet to import the objects in the `History.csv` file.</span></span> <span data-ttu-id="30da3-124">Pipeline-operatorn ( `|` ) skickar objekten till `Add-History` cmdleten, som lägger till de objekt som representerar kommandona i `History.csv` filen i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-124">The pipeline operator (`|`) passes the objects to the `Add-History` cmdlet, which adds the objects representing the commands in the `History.csv` file to the current session history.</span></span>

### <span data-ttu-id="30da3-125">Exempel 2: importera och kör kommandon</span><span class="sxs-lookup"><span data-stu-id="30da3-125">Example 2: Import and run commands</span></span>

<span data-ttu-id="30da3-126">Det här exemplet importerar kommandon från `History.xml` filen, lägger till dem i den aktuella tidigare sessionen och kör sedan kommandona i den kombinerade historiken.</span><span class="sxs-lookup"><span data-stu-id="30da3-126">This example imports commands from the `History.xml` file, adds them to the current session history, and then runs the commands in the combined history.</span></span>

```powershell
Import-Clixml c:\temp\history.xml | Add-History -PassThru | ForEach-Object -Process {Invoke-History}
```

<span data-ttu-id="30da3-127">Det första kommandot använder `Import-Clixml` cmdleten för att importera en kommando historik som exporter ATS till `History.xml` filen.</span><span class="sxs-lookup"><span data-stu-id="30da3-127">The first command uses the `Import-Clixml` cmdlet to import a command history that was exported to the `History.xml` file.</span></span> <span data-ttu-id="30da3-128">Pipeline-operatorn skickar kommandon till `Add-History` cmdleten, som lägger till kommandon i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-128">The pipeline operator passes the commands to the `Add-History` cmdlet, which adds the commands to the current session history.</span></span> <span data-ttu-id="30da3-129">Parametern **Passthru** skickar objekten som representerar de tillagda kommandona nedåt i pipelinen.</span><span class="sxs-lookup"><span data-stu-id="30da3-129">The **PassThru** parameter passes the objects representing the added commands down the pipeline.</span></span>

<span data-ttu-id="30da3-130">Kommandot använder sedan `ForEach-Object` cmdleten för att tillämpa `Invoke-History` kommandot på varje kommando i den kombinerade historiken.</span><span class="sxs-lookup"><span data-stu-id="30da3-130">The command then uses the `ForEach-Object` cmdlet to apply the `Invoke-History` command to each of the commands in the combined history.</span></span> <span data-ttu-id="30da3-131">`Invoke-History`Kommandot är formaterat som ett skript block som omges av klammerparenteser ( `{}` ), vilket krävs för cmdlet-parametern **process** `ForEach-Object` .</span><span class="sxs-lookup"><span data-stu-id="30da3-131">The `Invoke-History` command is formatted as a script block, enclosed in braces (`{}`), as required by the **Process** parameter of the `ForEach-Object` cmdlet.</span></span>

### <span data-ttu-id="30da3-132">Exempel 3: Lägg till kommandon i historiken i slutet av historiken</span><span class="sxs-lookup"><span data-stu-id="30da3-132">Example 3: Add commands in the history to the end of the history</span></span>

<span data-ttu-id="30da3-133">Det här exemplet lägger till de första fem kommandona i historiken i slutet av historik listan.</span><span class="sxs-lookup"><span data-stu-id="30da3-133">This example adds the first five commands in the history to the end of the history list.</span></span>

```powershell
Get-History -Id 5 -Count 5 | Add-History
```

<span data-ttu-id="30da3-134">`Get-History`Cmdlet: en hämtar de fem kommandona som slutar på kommando 5.</span><span class="sxs-lookup"><span data-stu-id="30da3-134">The `Get-History` cmdlet gets the five commands ending in command 5.</span></span> <span data-ttu-id="30da3-135">Pipeline-operatorn skickar dem till `Add-History` cmdleten, som lägger till dem i den aktuella historiken.</span><span class="sxs-lookup"><span data-stu-id="30da3-135">The pipeline operator passes them to the `Add-History` cmdlet, which appends them to the current history.</span></span> <span data-ttu-id="30da3-136">`Add-History`Kommandot innehåller inga parametrar, men PowerShell associerar objekten som skickas via pipelinen med **InputObject** -parametern för `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="30da3-136">The `Add-History` command does not include any parameters, but PowerShell associates the objects passed through the pipeline with the **InputObject** parameter of `Add-History`.</span></span>

### <span data-ttu-id="30da3-137">Exempel 4: Lägg till kommandon i en CSV-fil i den aktuella historiken</span><span class="sxs-lookup"><span data-stu-id="30da3-137">Example 4: Add commands in a .csv file to the current history</span></span>

<span data-ttu-id="30da3-138">I det här exemplet lägger du till kommandona i `History.csv` filen i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-138">This example add the commands in the `History.csv` file to the current session history.</span></span>

```powershell
$a = Import-Csv c:\testing\history.csv
Add-History -InputObject $a -PassThru
```

<span data-ttu-id="30da3-139">`Import-Csv`Cmdleten importerar kommandona i `History.csv` filen och lagrar dess innehåll i variabeln `$a` .</span><span class="sxs-lookup"><span data-stu-id="30da3-139">The `Import-Csv` cmdlet imports the commands in the `History.csv` file and store its contents in the variable `$a`.</span></span>

<span data-ttu-id="30da3-140">Det andra kommandot använder `Add-History` cmdleten för att lägga till kommandona från `History.csv` i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-140">The second command uses the `Add-History` cmdlet to add the commands from `History.csv` to the current session history.</span></span> <span data-ttu-id="30da3-141">Parametern **InputObject** används för att ange `$a` variabeln och parametern **Passthru** för att generera ett objekt som ska visas på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="30da3-141">It uses the **InputObject** parameter to specify the `$a` variable and the **PassThru** parameter to generate an object to display at the command line.</span></span> <span data-ttu-id="30da3-142">Utan parametern **Passthru** `Add-History` genererar cmdleten inga utdata.</span><span class="sxs-lookup"><span data-stu-id="30da3-142">Without the **PassThru** parameter, the `Add-History` cmdlet does not generate any output.</span></span>

### <span data-ttu-id="30da3-143">Exempel 5: Lägg till kommandon i en XML-fil i den aktuella historiken</span><span class="sxs-lookup"><span data-stu-id="30da3-143">Example 5: Add commands in an .xml file to the current history</span></span>

<span data-ttu-id="30da3-144">I det här exemplet läggs kommandona i `history.xml` filen till i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-144">This example adds the commands in the `history.xml` file to the current session history.</span></span>

```powershell
Add-History -InputObject (Import-Clixml c:\temp\history.xml)
```

<span data-ttu-id="30da3-145">Parametern **InputObject** skickar kommandots resultat inom parentes till `Add-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="30da3-145">The **InputObject** parameter passes the results of the command in parentheses to the `Add-History` cmdlet.</span></span> <span data-ttu-id="30da3-146">Kommandot inom parenteser, som körs först, importerar `history.xml` filen till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="30da3-146">The command in parentheses, which is executed first, imports the `history.xml` file into PowerShell.</span></span> <span data-ttu-id="30da3-147">`Add-History`Cmdleten lägger sedan till kommandona i filen i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="30da3-147">The `Add-History` cmdlet then adds the commands in the file to the session history.</span></span>

## <span data-ttu-id="30da3-148">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="30da3-148">PARAMETERS</span></span>

### <span data-ttu-id="30da3-149">– InputObject</span><span class="sxs-lookup"><span data-stu-id="30da3-149">-InputObject</span></span>

<span data-ttu-id="30da3-150">Anger en matris med poster som ska läggas till i historiken som **HistoryInfo** -objekt i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="30da3-150">Specifies an array of entries to add to the history as **HistoryInfo** object to the session history.</span></span>
<span data-ttu-id="30da3-151">Du kan använda den här parametern för att skicka ett **HistoryInfo** -objekt, till exempel de som returneras av `Get-History` `Import-Clixml` cmdletarna,, eller `Import-Csv` `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="30da3-151">You can use this parameter to submit a **HistoryInfo** object, such as the ones that are returned by the `Get-History`, `Import-Clixml`, or `Import-Csv` cmdlets, to `Add-History`.</span></span>

```yaml
Type: System.Management.Automation.PSObject[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="30da3-152">– Passthru</span><span class="sxs-lookup"><span data-stu-id="30da3-152">-Passthru</span></span>

<span data-ttu-id="30da3-153">Anger att denna cmdlet returnerar ett **HistoryInfo** -objekt för varje historik post.</span><span class="sxs-lookup"><span data-stu-id="30da3-153">Indicates that this cmdlet returns a **HistoryInfo** object for each history entry.</span></span> <span data-ttu-id="30da3-154">Som standard genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="30da3-154">By default, this cmdlet does not generate any output.</span></span>

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="30da3-155">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="30da3-155">CommonParameters</span></span>

<span data-ttu-id="30da3-156">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="30da3-156">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="30da3-157">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="30da3-157">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="30da3-158">INDATA</span><span class="sxs-lookup"><span data-stu-id="30da3-158">INPUTS</span></span>

### <span data-ttu-id="30da3-159">Microsoft. PowerShell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="30da3-159">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="30da3-160">Du kan skicka ett **HistoryInfo** -objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="30da3-160">You can pipe a **HistoryInfo** object to this cmdlet.</span></span>

## <span data-ttu-id="30da3-161">UTDATA</span><span class="sxs-lookup"><span data-stu-id="30da3-161">OUTPUTS</span></span>

### <span data-ttu-id="30da3-162">Ingen eller Microsoft. PowerShell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="30da3-162">None or Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="30da3-163">Denna cmdlet returnerar ett **HistoryInfo** -objekt om du anger parametern **Passthru** .</span><span class="sxs-lookup"><span data-stu-id="30da3-163">This cmdlet returns a **HistoryInfo** object if you specify the **PassThru** parameter.</span></span> <span data-ttu-id="30da3-164">Annars genererar denna cmdlet inga utdata.</span><span class="sxs-lookup"><span data-stu-id="30da3-164">Otherwise, this cmdlet does not generate any output.</span></span>

## <span data-ttu-id="30da3-165">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="30da3-165">NOTES</span></span>

<span data-ttu-id="30da3-166">Tidigare session är en lista över de kommandon som angavs under sessionen tillsammans med ID: t.</span><span class="sxs-lookup"><span data-stu-id="30da3-166">The session history is a list of the commands entered during the session together with the ID.</span></span> <span data-ttu-id="30da3-167">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="30da3-167">The session history represents the order of execution, the status, and the start and end times of the command.</span></span> <span data-ttu-id="30da3-168">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="30da3-168">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="30da3-169">Mer information om tidigare sessioner finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="30da3-169">For more information about the session history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="30da3-170">Använd parametern **InputObject** för att ange vilka kommandon som ska läggas till i historiken.</span><span class="sxs-lookup"><span data-stu-id="30da3-170">To specify the commands to add to the history, use the **InputObject** parameter.</span></span> <span data-ttu-id="30da3-171">`Add-History`Kommandot accepterar endast **HistoryInfo** -objekt, till exempel de som returneras för varje kommando av `Get-History` cmdleten.</span><span class="sxs-lookup"><span data-stu-id="30da3-171">The `Add-History` command accepts only **HistoryInfo** objects, such as those returned for each command by the `Get-History` cmdlet.</span></span> <span data-ttu-id="30da3-172">Du kan inte skicka en sökväg och ett fil namn eller en lista med kommandon.</span><span class="sxs-lookup"><span data-stu-id="30da3-172">You cannot pass it a path and file name or a list of commands.</span></span>

<span data-ttu-id="30da3-173">Du kan använda parametern **InputObject** för att skicka en fil med **HistoryInfo** -objekt till `Add-History` .</span><span class="sxs-lookup"><span data-stu-id="30da3-173">You can use the **InputObject** parameter to pass a file of **HistoryInfo** objects to `Add-History`.</span></span> <span data-ttu-id="30da3-174">Det gör du genom att exportera resultatet av ett `Get-History` kommando till en fil med hjälp av `Export-Csv` `Export-Clixml` cmdleten eller och sedan importera filen med hjälp av `Import-Csv` `Import-Clixml` cmdletarna eller.</span><span class="sxs-lookup"><span data-stu-id="30da3-174">To do so, export the results of a `Get-History` command to a file by using the `Export-Csv` or `Export-Clixml` cmdlet and then import the file by using the `Import-Csv` or `Import-Clixml` cmdlets.</span></span> <span data-ttu-id="30da3-175">Sedan kan du skicka filen med importerade **HistoryInfo** -objekt till `Add-History` en pipeline eller i en variabel.</span><span class="sxs-lookup"><span data-stu-id="30da3-175">You can then pass the file of imported **HistoryInfo** objects to `Add-History` through a pipeline or in a variable.</span></span> <span data-ttu-id="30da3-176">Mer information finns i exemplen.</span><span class="sxs-lookup"><span data-stu-id="30da3-176">For more information, see the examples.</span></span>

<span data-ttu-id="30da3-177">Filen med **HistoryInfo** -objekt som du skickar till `Add-History` cmdleten måste innehålla typ information, kolumn rubriker och alla egenskaper för **HistoryInfo** -objekten.</span><span class="sxs-lookup"><span data-stu-id="30da3-177">The file of **HistoryInfo** objects that you pass to the `Add-History` cmdlet must include the type information, column headings, and all of the properties of the **HistoryInfo** objects.</span></span> <span data-ttu-id="30da3-178">Om du tänker skicka tillbaka objekten till ska `Add-History` du inte använda **NoTypeInformation** -parametern för `Export-Csv` cmdleten och inte ta bort typ informationen, kolumn rubrikerna eller något fält i filen.</span><span class="sxs-lookup"><span data-stu-id="30da3-178">If you intend to pass the objects back to `Add-History`, do not use the **NoTypeInformation** parameter of the `Export-Csv` cmdlet and do not delete the type information, column headings, or any fields in the file.</span></span>

<span data-ttu-id="30da3-179">Om du vill ändra sessionens historik exporterar du sessionen till en CSV-eller XML-fil, ändrar filen, importerar filen och använder `Add-History` den för att lägga till den i den aktuella tidigare sessionen.</span><span class="sxs-lookup"><span data-stu-id="30da3-179">To modify the session history, export the session to a CSV or XML file, modify the file, import the file, and use `Add-History` to append it to the current session history.</span></span>

## <span data-ttu-id="30da3-180">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="30da3-180">RELATED LINKS</span></span>

[<span data-ttu-id="30da3-181">Rensa – historik</span><span class="sxs-lookup"><span data-stu-id="30da3-181">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="30da3-182">Hämta historik</span><span class="sxs-lookup"><span data-stu-id="30da3-182">Get-History</span></span>](Get-History.md)

[<span data-ttu-id="30da3-183">Anropa-historik</span><span class="sxs-lookup"><span data-stu-id="30da3-183">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="30da3-184">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="30da3-184">about_PSReadLine</span></span>](../PSReadLine/About/about_PSReadLine.md)

[<span data-ttu-id="30da3-185">Get-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="30da3-185">Get-PSReadLineOption</span></span>](/powershell/module/psreadline/get-psreadlineoption)

[<span data-ttu-id="30da3-186">Set-PSReadLineOption</span><span class="sxs-lookup"><span data-stu-id="30da3-186">Set-PSReadLineOption</span></span>](/powershell/module/psreadline/set-psreadlineoption)

