---
external help file: System.Management.Automation.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 10/06/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/get-history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-History
ms.openlocfilehash: be47925211c57760ddbd0bd4c8e985e161d24593
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708803"
---
# <span data-ttu-id="4e77d-102">Get-History</span><span class="sxs-lookup"><span data-stu-id="4e77d-102">Get-History</span></span>

## <span data-ttu-id="4e77d-103">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4e77d-103">SYNOPSIS</span></span>
<span data-ttu-id="4e77d-104">Hämtar en lista med kommandon som angavs under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e77d-104">Gets a list of the commands entered during the current session.</span></span>

## <span data-ttu-id="4e77d-105">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4e77d-105">SYNTAX</span></span>

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## <span data-ttu-id="4e77d-106">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4e77d-106">DESCRIPTION</span></span>

<span data-ttu-id="4e77d-107">`Get-History`Cmdlet: en hämtar tidigare session, det vill säga en lista med kommandon som angavs under den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e77d-107">The `Get-History` cmdlet gets the session history, that is, the list of commands entered during the current session.</span></span>

<span data-ttu-id="4e77d-108">PowerShell upprätthåller automatiskt en historik över varje session.</span><span class="sxs-lookup"><span data-stu-id="4e77d-108">PowerShell automatically maintains a history of each session.</span></span> <span data-ttu-id="4e77d-109">Antalet poster i sessionens historik bestäms av värdet för `$MaximumHistoryCount` variabeln Preference.</span><span class="sxs-lookup"><span data-stu-id="4e77d-109">The number of entries in the session history is determined by the value of the `$MaximumHistoryCount` preference variable.</span></span> <span data-ttu-id="4e77d-110">Från och med Windows PowerShell 3,0 är standardvärdet `4096` .</span><span class="sxs-lookup"><span data-stu-id="4e77d-110">Beginning in Windows PowerShell 3.0, the default value is `4096`.</span></span> <span data-ttu-id="4e77d-111">Som standard sparas historikfilerna i arbets katalogen, men du kan spara filen var som helst.</span><span class="sxs-lookup"><span data-stu-id="4e77d-111">By default, history files are saved in the home directory, but you can save the file in any location.</span></span> <span data-ttu-id="4e77d-112">Mer information om historik funktionerna i PowerShell finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="4e77d-112">For more information about the history features in PowerShell, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="4e77d-113">Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="4e77d-113">The session history is managed separately from the history maintained by the **PSReadLine** module.</span></span>
<span data-ttu-id="4e77d-114">Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in.</span><span class="sxs-lookup"><span data-stu-id="4e77d-114">Both histories are available in sessions where **PSReadLine** is loaded.</span></span> <span data-ttu-id="4e77d-115">Den här cmdleten fungerar bara med tidigare session.</span><span class="sxs-lookup"><span data-stu-id="4e77d-115">This cmdlet only works with the session history.</span></span> <span data-ttu-id="4e77d-116">Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="4e77d-116">For more information see, [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).</span></span>

## <span data-ttu-id="4e77d-117">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4e77d-117">EXAMPLES</span></span>

### <span data-ttu-id="4e77d-118">Exempel 1: Hämta tidigare session</span><span class="sxs-lookup"><span data-stu-id="4e77d-118">Example 1: Get the session history</span></span>

<span data-ttu-id="4e77d-119">Det här exemplet hämtar posterna i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="4e77d-119">This example gets the entries in the session history.</span></span> <span data-ttu-id="4e77d-120">Standard visningen visar varje kommando och dess ID, som anger i vilken ordning de kördes.</span><span class="sxs-lookup"><span data-stu-id="4e77d-120">The default display shows each command and its ID, which indicates the order in which they ran.</span></span>

```powershell
Get-History
```

### <span data-ttu-id="4e77d-121">Exempel 2: hämta poster som innehåller en sträng</span><span class="sxs-lookup"><span data-stu-id="4e77d-121">Example 2: Get entries that include a string</span></span>

<span data-ttu-id="4e77d-122">I det här exemplet hämtas poster i kommando historiken som innehåller sträng tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e77d-122">This example gets entries in the command history that include the string service.</span></span> <span data-ttu-id="4e77d-123">Det första kommandot hämtar alla poster i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="4e77d-123">The first command gets all entries in the session history.</span></span> <span data-ttu-id="4e77d-124">Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som endast väljer de kommandon som inkluderar tjänsten.</span><span class="sxs-lookup"><span data-stu-id="4e77d-124">The pipeline operator (`|`) passes the results to the `Where-Object` cmdlet, which selects only the commands that include service.</span></span>

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### <span data-ttu-id="4e77d-125">Exempel 3: exportera historik poster upp till ett angivet ID</span><span class="sxs-lookup"><span data-stu-id="4e77d-125">Example 3: Export history entries up to a specific ID</span></span>

<span data-ttu-id="4e77d-126">Det här exemplet hämtar de fem senaste historik posterna som slutar med Entry 7.</span><span class="sxs-lookup"><span data-stu-id="4e77d-126">This example gets the five most recent history entries ending with entry 7.</span></span> <span data-ttu-id="4e77d-127">Pipeline-operatorn skickar resultatet till `Export-Csv` cmdleten, som formaterar historiken som kommaavgränsad text och sparar den i History.csv-filen.</span><span class="sxs-lookup"><span data-stu-id="4e77d-127">The pipeline operator passes the result to the `Export-Csv` cmdlet, which formats the history as comma-separated text and saves it in the History.csv file.</span></span> <span data-ttu-id="4e77d-128">Filen innehåller de data som visas när du formaterar historiken som en lista.</span><span class="sxs-lookup"><span data-stu-id="4e77d-128">The file includes the data that is displayed when you format the history as a list.</span></span> <span data-ttu-id="4e77d-129">Detta inkluderar kommandonas status och start-och slut tid.</span><span class="sxs-lookup"><span data-stu-id="4e77d-129">This includes the status and start and end times of the command.</span></span>

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### <span data-ttu-id="4e77d-130">Exempel 4: Visa det senaste kommandot</span><span class="sxs-lookup"><span data-stu-id="4e77d-130">Example 4: Display the most recent command</span></span>

<span data-ttu-id="4e77d-131">Det här exemplet hämtar det sista kommandot i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="4e77d-131">This example gets the last command in the command history.</span></span> <span data-ttu-id="4e77d-132">Det sista kommandot är det senast angivna kommandot.</span><span class="sxs-lookup"><span data-stu-id="4e77d-132">The last command is the most recently entered command.</span></span> <span data-ttu-id="4e77d-133">Det här kommandot använder **Count** -parametern för att visa bara ett kommando.</span><span class="sxs-lookup"><span data-stu-id="4e77d-133">This command uses the **Count** parameter to display just one command.</span></span> <span data-ttu-id="4e77d-134">Som standard `Get-History` hämtar de senaste kommandona.</span><span class="sxs-lookup"><span data-stu-id="4e77d-134">By default, `Get-History` gets the most recent commands.</span></span> <span data-ttu-id="4e77d-135">Det här kommandot kan förkortas till "h-c 1" och motsvarar att trycka på tangenten UPPIL.</span><span class="sxs-lookup"><span data-stu-id="4e77d-135">This command can be abbreviated to "h -c 1" and is equivalent to pressing the up-arrow key.</span></span>

```powershell
Get-History -Count 1
```

### <span data-ttu-id="4e77d-136">Exempel 5: Visa alla egenskaper för posterna i historiken</span><span class="sxs-lookup"><span data-stu-id="4e77d-136">Example 5: Display all the properties of the entries in the history</span></span>

<span data-ttu-id="4e77d-137">I det här exemplet visas alla egenskaper för poster i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="4e77d-137">This example displays all of the properties of entries in the session history.</span></span> <span data-ttu-id="4e77d-138">Pipeline-operatorn skickar resultatet av ett `Get-History` kommando till `Format-List` cmdleten, som visar alla egenskaper för varje historik post.</span><span class="sxs-lookup"><span data-stu-id="4e77d-138">The pipeline operator passes the results of a `Get-History` command to the `Format-List` cmdlet, which displays all of the properties of each history entry.</span></span> <span data-ttu-id="4e77d-139">Detta omfattar kommandots ID, status, start-och slut tid.</span><span class="sxs-lookup"><span data-stu-id="4e77d-139">This includes the ID, status, and start and end times of the command.</span></span>

```powershell
Get-History | Format-List -Property *
```

## <span data-ttu-id="4e77d-140">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4e77d-140">PARAMETERS</span></span>

### <span data-ttu-id="4e77d-141">-Antal</span><span class="sxs-lookup"><span data-stu-id="4e77d-141">-Count</span></span>

<span data-ttu-id="4e77d-142">Anger antalet senaste historik poster som denna cmdlet hämtar.</span><span class="sxs-lookup"><span data-stu-id="4e77d-142">Specifies the number of the most recent history entries that this cmdlet gets.</span></span> <span data-ttu-id="4e77d-143">Som standard `Get-History` hämtar alla poster i tidigare sessioner.</span><span class="sxs-lookup"><span data-stu-id="4e77d-143">By, default, `Get-History` gets all entries in the session history.</span></span> <span data-ttu-id="4e77d-144">Om du använder både **Count** -och **ID-** parametrarna i ett kommando avslutas skärmen med kommandot som anges av **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="4e77d-144">If you use both the **Count** and **Id** parameters in a command, the display ends with the command that is specified by the **Id** parameter.</span></span>

<span data-ttu-id="4e77d-145">I Windows PowerShell 2,0 hämtar som standard `Get-History` de 32 senaste posterna.</span><span class="sxs-lookup"><span data-stu-id="4e77d-145">In Windows PowerShell 2.0, by default, `Get-History` gets the 32 most recent entries.</span></span>

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

### <span data-ttu-id="4e77d-146">-ID</span><span class="sxs-lookup"><span data-stu-id="4e77d-146">-Id</span></span>

<span data-ttu-id="4e77d-147">Anger en matris med ID: n för poster i sessionens historik.</span><span class="sxs-lookup"><span data-stu-id="4e77d-147">Specifies an array of the IDs of entries in the session history.</span></span> <span data-ttu-id="4e77d-148">`Get-History` hämtar endast angivna poster.</span><span class="sxs-lookup"><span data-stu-id="4e77d-148">`Get-History` gets only specified entries.</span></span> <span data-ttu-id="4e77d-149">Om du använder båda parametrarna **ID** och **Count** i ett kommando `Get-History` hämtar de senaste posterna som slutar med den post som anges av **ID-** parametern.</span><span class="sxs-lookup"><span data-stu-id="4e77d-149">If you use both the **Id** and **Count** parameters in a command, `Get-History` gets the most recent entries ending with the entry specified by the **Id** parameter.</span></span>

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

### <span data-ttu-id="4e77d-150">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4e77d-150">CommonParameters</span></span>

<span data-ttu-id="4e77d-151">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4e77d-151">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4e77d-152">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4e77d-152">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4e77d-153">INDATA</span><span class="sxs-lookup"><span data-stu-id="4e77d-153">INPUTS</span></span>

### <span data-ttu-id="4e77d-154">System. Int64</span><span class="sxs-lookup"><span data-stu-id="4e77d-154">System.Int64</span></span>

<span data-ttu-id="4e77d-155">Du kan skicka vidare ett historik-ID till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4e77d-155">You can pipe a history ID to this cmdlet.</span></span>

## <span data-ttu-id="4e77d-156">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4e77d-156">OUTPUTS</span></span>

### <span data-ttu-id="4e77d-157">Microsoft. PowerShell. commands. HistoryInfo</span><span class="sxs-lookup"><span data-stu-id="4e77d-157">Microsoft.PowerShell.Commands.HistoryInfo</span></span>

<span data-ttu-id="4e77d-158">Denna cmdlet returnerar ett historik objekt för varje historik objekt som det får.</span><span class="sxs-lookup"><span data-stu-id="4e77d-158">This cmdlet returns a history object for each history item that it gets.</span></span>

## <span data-ttu-id="4e77d-159">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4e77d-159">NOTES</span></span>

<span data-ttu-id="4e77d-160">Tidigare session är en lista över kommandon som anges under sessionen.</span><span class="sxs-lookup"><span data-stu-id="4e77d-160">The session history is a list of the commands entered during the session.</span></span> <span data-ttu-id="4e77d-161">Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot.</span><span class="sxs-lookup"><span data-stu-id="4e77d-161">The session history represents the run order, the status, and the start and end times of the command.</span></span> <span data-ttu-id="4e77d-162">När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det.</span><span class="sxs-lookup"><span data-stu-id="4e77d-162">As you enter each command, PowerShell adds it to the history so that you can reuse it.</span></span> <span data-ttu-id="4e77d-163">Mer information om kommando historiken finns [about_History](About/about_History.md).</span><span class="sxs-lookup"><span data-stu-id="4e77d-163">For more information about the command history, see [about_History](About/about_History.md).</span></span>

<span data-ttu-id="4e77d-164">Från och med Windows PowerShell 3,0 är standardvärdet för `$MaximumHistoryCount` Preference-variabeln `4096` .</span><span class="sxs-lookup"><span data-stu-id="4e77d-164">Starting in Windows PowerShell 3.0, the default value of the `$MaximumHistoryCount` preference variable is `4096`.</span></span> <span data-ttu-id="4e77d-165">I Windows PowerShell 2,0 är standardvärdet `64` .</span><span class="sxs-lookup"><span data-stu-id="4e77d-165">In Windows PowerShell 2.0, the default value is `64`.</span></span> <span data-ttu-id="4e77d-166">Mer information om `$MaximumHistoryCount` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="4e77d-166">For more information about the `$MaximumHistoryCount` variable, see [about_Preference_Variables](About/about_Preference_Variables.md).</span></span>

## <span data-ttu-id="4e77d-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4e77d-167">RELATED LINKS</span></span>

[<span data-ttu-id="4e77d-168">Lägg till-historik</span><span class="sxs-lookup"><span data-stu-id="4e77d-168">Add-History</span></span>](Add-History.md)

[<span data-ttu-id="4e77d-169">Rensa – historik</span><span class="sxs-lookup"><span data-stu-id="4e77d-169">Clear-History</span></span>](Clear-History.md)

[<span data-ttu-id="4e77d-170">Anropa-historik</span><span class="sxs-lookup"><span data-stu-id="4e77d-170">Invoke-History</span></span>](Invoke-History.md)

[<span data-ttu-id="4e77d-171">about_History</span><span class="sxs-lookup"><span data-stu-id="4e77d-171">about_History</span></span>](About/about_History.md)
