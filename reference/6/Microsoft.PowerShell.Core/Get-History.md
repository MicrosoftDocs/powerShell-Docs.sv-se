---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: 773e7e8d61e0f6158b4501b9c0b23826cbb10820
ms.sourcegitcommit: 1695df0d241c0390cac71a7401e61198fc6ff756
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/06/2020
ms.locfileid: "93269648"
---
# <span data-ttu-id="5d417-103">Get-History</span><span class="sxs-lookup"><span data-stu-id="5d417-103">Get-History</span></span>

## <span data-ttu-id="5d417-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5d417-104">SYNOPSIS</span></span>
<span data-ttu-id="5d417-105">Hämtar en lista med kommandon som angavs under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5d417-105">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="5d417-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5d417-106">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="5d417-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5d417-107">DESCRIPTION</span></span>

<span data-ttu-id="5d417-108">`Get-History`Cmdlet: en hämtar tidigare session, det vill säga en lista med kommandon som angavs under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="5d417-108">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="5d417-109">PowerShell upprätthåller automatiskt en historik över varje session.</span><span class="sxs-lookup"><span data-stu-id="5d417-109">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="5d417-110">Antalet poster i sessionens historik bestäms av värdet för `$MaximumHistoryCount` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="5d417-110">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="5d417-111">Från och med Windows PowerShell 3,0 är standardvärdet `4096` .</span><span class="sxs-lookup"><span data-stu-id="5d417-111">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="5d417-112">Som standard sparas historikfilerna i arbets katalogen, men du kan spara filen var som helst.</span><span class="sxs-lookup"><span data-stu-id="5d417-112">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="5d417-113">Mer information om historik funktionerna i PowerShell finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="5d417-113">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="5d417-114">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="5d417-114">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="5d417-115">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="5d417-115">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="5d417-116">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="5d417-116">This cmdlet only works with the session history.</span></span> <span data-ttu-id="5d417-117">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="5d417-117">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="5d417-118">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5d417-118">EXAMPLES</span></span>

### <span data-ttu-id="5d417-119">Exempel 1: Hämta tidigare session</span><span class="sxs-lookup"><span data-stu-id="5d417-119">Example 1: Get the session history</span></span>

<span data-ttu-id="5d417-120">Det här exemplet hämtar posterna i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="5d417-120">This example gets the entries in the session history.</span></span> <span data-ttu-id="5d417-121">Standard visningen visar varje kommando och dess ID, som anger i vilken ordning de kördes.</span><span class="sxs-lookup"><span data-stu-id="5d417-121">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="5d417-122">Exempel 2: hämta poster som innehåller en sträng</span><span class="sxs-lookup"><span data-stu-id="5d417-122">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="5d417-123">I det här exemplet hämtas poster i kommando historiken som innehåller sträng tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5d417-123">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="5d417-124">Det första kommandot hämtar alla poster i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="5d417-124">The first command gets all entries in the session history.</span></span> <span data-ttu-id="5d417-125">Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som endast väljer de kommandon som inkluderar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="5d417-125">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="5d417-126">Exempel 3: exportera historik poster upp till ett angivet ID</span><span class="sxs-lookup"><span data-stu-id="5d417-126">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="5d417-127">Det här exemplet hämtar de fem senaste historik posterna som slutar med Entry 7.</span><span class="sxs-lookup"><span data-stu-id="5d417-127">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="5d417-128">Pipeline-operatorn skickar resultatet till `Export-Csv` cmdleten, som formaterar historiken som kommaavgränsad text och sparar den i History.csv-filen.</span><span class="sxs-lookup"><span data-stu-id="5d417-128">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="5d417-129">Filen innehåller de data som visas när du formaterar historiken som en lista.</span><span class="sxs-lookup"><span data-stu-id="5d417-129">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="5d417-130">Detta inkluderar kommandonas status och start-och slut tid.</span><span class="sxs-lookup"><span data-stu-id="5d417-130">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="5d417-131">Exempel 4: Visa det senaste kommandot</span><span class="sxs-lookup"><span data-stu-id="5d417-131">Example 4: Display the most recent command</span></span>

<span data-ttu-id="5d417-132">Det här exemplet hämtar det sista kommandot i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="5d417-132">This example gets the last command in the command history.</span></span> <span data-ttu-id="5d417-133">Det sista kommandot är det senast angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="5d417-133">The last command is the most recently entered command.</span></span> <span data-ttu-id="5d417-134">Det här kommandot använder **Count** -parametern för att visa bara ett kommando.</span><span class="sxs-lookup"><span data-stu-id="5d417-134">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="5d417-135">Som standard `Get-History` hämtar de senaste kommandona.</span><span class="sxs-lookup"><span data-stu-id="5d417-135">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="5d417-136">Det här kommandot kan förkortas till "h-c 1" och motsvarar att trycka på tangenten UPPIL.</span><span class="sxs-lookup"><span data-stu-id="5d417-136">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="5d417-137">Exempel 5: Visa alla egenskaper för posterna i historiken</span><span class="sxs-lookup"><span data-stu-id="5d417-137">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="5d417-138">I det här exemplet visas alla egenskaper för poster i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="5d417-138">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="5d417-139">Pipeline-operatorn skickar resultatet av ett `Get-History` kommando till `Format-List` cmdleten, som visar alla egenskaper för varje historik post.</span><span class="sxs-lookup"><span data-stu-id="5d417-139">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="5d417-140">Detta omfattar kommandots ID, status, start-och slut tid.</span><span class="sxs-lookup"><span data-stu-id="5d417-140">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="5d417-141">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5d417-141">PARAMETERS</span></span>

### <span data-ttu-id="5d417-142">-Antal</span><span class="sxs-lookup"><span data-stu-id="5d417-142">-Count</span></span>

<span data-ttu-id="5d417-143">Anger antalet senaste historik poster som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="5d417-143">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="5d417-144">Som standard `Get-History` hämtar alla poster i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="5d417-144">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="5d417-145">Om du använder både **Count** -och **ID-** parametrarna i ett kommando avslutas skärmen med kommandot som anges av **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="5d417-145">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="5d417-146">I Windows PowerShell 2,0 hämtar som standard `Get-History` de 32 senaste posterna.</span><span class="sxs-lookup"><span data-stu-id="5d417-146">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="5d417-147">-ID</span><span class="sxs-lookup"><span data-stu-id="5d417-147">-Id</span></span>

<span data-ttu-id="5d417-148">Anger en matris med ID: n för poster i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="5d417-148">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="5d417-149">`Get-History` hämtar endast angivna poster.</span><span class="sxs-lookup"><span data-stu-id="5d417-149">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="5d417-150">Om du använder båda parametrarna **ID** och **Count** i ett kommando `Get-History` hämtar de senaste posterna som slutar med den post som anges av **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="5d417-150">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

```yaml
Type: System.Int64[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### <span data-ttu-id="5d417-151">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5d417-151">CommonParameters</span></span>

<span data-ttu-id="5d417-152">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5d417-152">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5d417-153">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5d417-153">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5d417-154">INDATA</span><span class="sxs-lookup"><span data-stu-id="5d417-154">INPUTS</span></span>

### <span data-ttu-id="5d417-155">System. Int64</span><span class="sxs-lookup"><span data-stu-id="5d417-155">System.Int64</span></span>

<span data-ttu-id="5d417-156">Du kan skicka vidare ett historik-ID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5d417-156">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="5d417-157">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5d417-157">OUTPUTS</span></span>

### <span data-ttu-id="5d417-158">Microsoft. PowerShell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="5d417-158">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="5d417-159">Denna cmdlet returnerar ett historik objekt för varje historik objekt som det får.</span><span class="sxs-lookup"><span data-stu-id="5d417-159">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="5d417-160">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5d417-160">NOTES</span></span>

<span data-ttu-id="5d417-161">Tidigare session är en lista över kommandon som anges under sessionen.</span><span class="sxs-lookup"><span data-stu-id="5d417-161">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="5d417-162">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="5d417-162">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="5d417-163">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="5d417-163">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="5d417-164">Mer information om kommando historiken finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="5d417-164">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="5d417-165">Från och med Windows PowerShell 3,0 är standardvärdet för `$MaximumHistoryCount` Preference-variabeln `4096` .</span><span class="sxs-lookup"><span data-stu-id="5d417-165">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="5d417-166">I Windows PowerShell 2,0 är standardvärdet `64` .</span><span class="sxs-lookup"><span data-stu-id="5d417-166">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="5d417-167">Mer information om `$MaximumHistoryCount` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="5d417-167">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="5d417-168">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5d417-168">RELATED LINKS</span></span>

[<span data-ttu-id="5d417-169">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="5d417-169">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="5d417-170">Rensa – historik</span><span class="sxs-lookup"><span data-stu-id="5d417-170">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="5d417-171">Anropa-historik</span><span class="sxs-lookup"><span data-stu-id="5d417-171">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="5d417-172">about_History</span><span class="sxs-lookup"><span data-stu-id="5d417-172">about_History</span></span>](About/about_History.md)
