---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 35b417b35d67e5cbe0df8719ba790135645d64e1
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272834"
---
# <span data-ttu-id="40ecd-103">Write-Progress</span><span class="sxs-lookup"><span data-stu-id="40ecd-103">Write-Progress</span></span>

## <span data-ttu-id="40ecd-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="40ecd-104">SYNOPSIS</span></span>
<span data-ttu-id="40ecd-105">Visar en förlopps indikator i ett PowerShell-kommando fönster.</span><span class="sxs-lookup"><span data-stu-id="40ecd-105">Displays a progress bar within a PowerShell command window.</span></span>

## <span data-ttu-id="40ecd-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="40ecd-106">SYNTAX</span></span>

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## <span data-ttu-id="40ecd-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="40ecd-107">DESCRIPTION</span></span>

<span data-ttu-id="40ecd-108">`Write-Progress`Cmdleten visar en förlopps indikator i ett PowerShell-kommando fönster som visar statusen för ett kommando eller skript som körs.</span><span class="sxs-lookup"><span data-stu-id="40ecd-108">The `Write-Progress` cmdlet displays a progress bar in a PowerShell command window that depicts the status of a running command or script.</span></span> <span data-ttu-id="40ecd-109">Du kan välja de indikatorer som stapeln visar och texten som visas ovanför och under förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="40ecd-109">You can select the indicators that the bar reflects and the text that appears above and below the progress bar.</span></span>

## <span data-ttu-id="40ecd-110">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="40ecd-110">EXAMPLES</span></span>

### <span data-ttu-id="40ecd-111">Exempel 1: Visa förloppet för en for-loop</span><span class="sxs-lookup"><span data-stu-id="40ecd-111">Example 1: Display the progress of a For loop</span></span>

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

<span data-ttu-id="40ecd-112">Det här kommandot visar förloppet för en for-loop som räknas från 1 till 100.</span><span class="sxs-lookup"><span data-stu-id="40ecd-112">This command displays the progress of a For loop that counts from 1 to 100.</span></span>

<span data-ttu-id="40ecd-113">`Write-Progress`Cmdlet: en innehåller en Statusfälts rubrik, `Activity` en status rad och variabeln `$i` (räknaren i for-slingan) som visar den relativa hela uppgiften.</span><span class="sxs-lookup"><span data-stu-id="40ecd-113">The `Write-Progress` cmdlet includes a status bar heading `Activity`, a status line, and the variable `$i` (the counter in the For loop), which indicates the relative completeness of the task.</span></span>

### <span data-ttu-id="40ecd-114">Exempel 2: Visa förloppet för kapslade slingor</span><span class="sxs-lookup"><span data-stu-id="40ecd-114">Example 2: Display the progress of nested For loops</span></span>

```powershell
for($I = 1; $I -lt 101; $I++ )
{
    Write-Progress -Activity Updating -Status 'Progress->' -PercentComplete $I -CurrentOperation OuterLoop
    for($j = 1; $j -lt 101; $j++ )
    {
        Write-Progress -Id 1 -Activity Updating -Status 'Progress' -PercentComplete $j -CurrentOperation InnerLoop
    }
}
```

```Output
Updating
Progress ->
 [ooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooooo]
OuterLoop
Updating
Progress
 [oooooooooooooooooo                                                   ]
InnerLoop
```

<span data-ttu-id="40ecd-115">I det här exemplet visas förloppet för två kapslade för slingor som representeras av en förlopps indikator.</span><span class="sxs-lookup"><span data-stu-id="40ecd-115">This example displays the progress of two nested For loops, each of which is represented by a progress bar.</span></span>

<span data-ttu-id="40ecd-116">`Write-Progress`Kommandot för den andra förlopps indikatorn innehåller **ID-** parametern som särskiljer den från den första förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="40ecd-116">The `Write-Progress` command for the second progress bar includes the **Id** parameter that distinguishes it from the first progress bar.</span></span>

<span data-ttu-id="40ecd-117">Utan parametern **ID** skulle förlopps staplarna placeras ovanpå varandra i stället för att visas en under den andra.</span><span class="sxs-lookup"><span data-stu-id="40ecd-117">Without the **Id** parameter, the progress bars would be superimposed on each other instead of being displayed one below the other.</span></span>

### <span data-ttu-id="40ecd-118">Exempel 3: Visa förloppet när du söker efter en sträng</span><span class="sxs-lookup"><span data-stu-id="40ecd-118">Example 3: Display the progress while searching for a string</span></span>

```powershell
# Use Get-EventLog to get the events in the System log and store them in the $Events variable.
$Events = Get-EventLog -LogName system
# Pipe the events to the ForEach-Object cmdlet.
$Events | ForEach-Object -Begin {
    # In the Begin block, use Clear-Host to clear the screen.
    Clear-Host
    # Set the $i counter variable to zero.
    $i = 0
    # Set the $out variable to a empty string.
    $out = ""
} -Process {
    # In the Process script block search the message property of each incoming object for "bios".
    if($_.message -like "*bios*")
    {
        # Append the matching message to the out variable.
        $out=$out + $_.Message
    }
    # Increment the $i counter variable which is used to create the progress bar.
    $i = $i+1
    # Use Write-Progress to output a progress bar.
    # The Activity and Status parameters create the first and second lines of the progress bar heading, respectively.
    Write-Progress -Activity "Searching Events" -Status "Progress:" -PercentComplete ($i/$Events.count*100)
} -End {
    # Display the matching messages using the out variable.
    $out
}
```

<span data-ttu-id="40ecd-119">Det här kommandot visar förloppet för ett kommando för att hitta strängen "BIOS" i system händelse loggen.</span><span class="sxs-lookup"><span data-stu-id="40ecd-119">This command displays the progress of a command to find the string "bios" in the System event log.</span></span>

<span data-ttu-id="40ecd-120">Parametervärdet för **procent färdigt** beräknas genom att antalet händelser som har bearbetats divideras med `$I` det totala antalet händelser som hämtats `$Events.count` och sedan multipliceras resultatet med 100.</span><span class="sxs-lookup"><span data-stu-id="40ecd-120">The **PercentComplete** parameter value is calculated by dividing the number of events that have been processed `$I` by the total number of events retrieved `$Events.count` and then multiplying that result by 100.</span></span>

### <span data-ttu-id="40ecd-121">Exempel 4: Visa förloppet för varje nivå i en kapslad process</span><span class="sxs-lookup"><span data-stu-id="40ecd-121">Example 4: Display progress for each level of a nested process</span></span>

```powershell
foreach ( $i in 1..10 ) {
  Write-Progress -Id 0 "Step $i"
  foreach ( $j in 1..10 ) {
    Write-Progress -Id 1 -ParentId 0 "Step $i - Substep $j"
    foreach ( $k in 1..10 ) {
      Write-Progress -Id 2  -ParentId 1 "Step $i - Substep $j - iteration $k"; start-sleep -m 150
    }
  }
}
```

```Output
Step 1
     Processing
    Step 1 - Substep 2
         Processing
        Step 1 - Substep 2 - Iteration 3
             Processing
```

<span data-ttu-id="40ecd-122">I det här exemplet kan du använda **parametern** libför att Visa indragna utdata för att visa överordnade/underordnade relationer i förloppet för varje steg.</span><span class="sxs-lookup"><span data-stu-id="40ecd-122">In this example you can use the **ParentId** parameter to have indented output to show parent/child relationships in the progress of each step.</span></span>

## <span data-ttu-id="40ecd-123">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="40ecd-123">PARAMETERS</span></span>

### <span data-ttu-id="40ecd-124">-Aktivitet</span><span class="sxs-lookup"><span data-stu-id="40ecd-124">-Activity</span></span>

<span data-ttu-id="40ecd-125">Anger den första text raden i rubriken ovanför statusfältet.</span><span class="sxs-lookup"><span data-stu-id="40ecd-125">Specifies the first line of text in the heading above the status bar.</span></span>
<span data-ttu-id="40ecd-126">Den här texten beskriver den aktivitet vars förlopp rapporteras.</span><span class="sxs-lookup"><span data-stu-id="40ecd-126">This text describes the activity whose progress is being reported.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-127">-Slutförd</span><span class="sxs-lookup"><span data-stu-id="40ecd-127">-Completed</span></span>

<span data-ttu-id="40ecd-128">Anger om förlopps indikatorn är synlig.</span><span class="sxs-lookup"><span data-stu-id="40ecd-128">Indicates whether the progress bar is visible.</span></span>
<span data-ttu-id="40ecd-129">Om den här parametern utelämnas `Write-Progress` visas information om förloppet.</span><span class="sxs-lookup"><span data-stu-id="40ecd-129">If this parameter is omitted, `Write-Progress` displays progress information.</span></span>

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

### <span data-ttu-id="40ecd-130">-CurrentOperation</span><span class="sxs-lookup"><span data-stu-id="40ecd-130">-CurrentOperation</span></span>

<span data-ttu-id="40ecd-131">Anger text raden under förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="40ecd-131">Specifies the line of text below the progress bar.</span></span>
<span data-ttu-id="40ecd-132">I den här texten beskrivs den åtgärd som pågår.</span><span class="sxs-lookup"><span data-stu-id="40ecd-132">This text describes the operation that is currently taking place.</span></span>

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

### <span data-ttu-id="40ecd-133">-ID</span><span class="sxs-lookup"><span data-stu-id="40ecd-133">-Id</span></span>

<span data-ttu-id="40ecd-134">Anger ett ID som särskiljer varje förlopps indikator från de andra.</span><span class="sxs-lookup"><span data-stu-id="40ecd-134">Specifies an ID that distinguishes each progress bar from the others.</span></span> <span data-ttu-id="40ecd-135">Använd den här parametern när du skapar fler än en förlopps indikator i ett enda kommando.</span><span class="sxs-lookup"><span data-stu-id="40ecd-135">Use this parameter when you are creating more than one progress bar in a single command.</span></span> <span data-ttu-id="40ecd-136">Om förlopps staplarna inte har olika ID: n placeras de ovanpå i stället för att visas i en serie.</span><span class="sxs-lookup"><span data-stu-id="40ecd-136">If the progress bars do not have different IDs, they are superimposed instead of being displayed in a series.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-137">-ID</span><span class="sxs-lookup"><span data-stu-id="40ecd-137">-ParentId</span></span>

<span data-ttu-id="40ecd-138">Anger den överordnade aktiviteten för den aktuella aktiviteten.</span><span class="sxs-lookup"><span data-stu-id="40ecd-138">Specifies the parent activity of the current activity.</span></span>
<span data-ttu-id="40ecd-139">Använd värdet-1 om den aktuella aktiviteten inte har någon överordnad aktivitet.</span><span class="sxs-lookup"><span data-stu-id="40ecd-139">Use the value -1 if the current activity has no parent activity.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-140">-Procent färdigt</span><span class="sxs-lookup"><span data-stu-id="40ecd-140">-PercentComplete</span></span>

<span data-ttu-id="40ecd-141">Anger procent andelen för den aktivitet som har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40ecd-141">Specifies the percentage of the activity that is completed.</span></span>
<span data-ttu-id="40ecd-142">Använd värdet-1 om procent andelen Slutför är okänd eller inte tillämplig.</span><span class="sxs-lookup"><span data-stu-id="40ecd-142">Use the value -1 if the percentage complete is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-143">-SecondsRemaining</span><span class="sxs-lookup"><span data-stu-id="40ecd-143">-SecondsRemaining</span></span>

<span data-ttu-id="40ecd-144">Anger det planerade antalet sekunder kvar tills aktiviteten har slutförts.</span><span class="sxs-lookup"><span data-stu-id="40ecd-144">Specifies the projected number of seconds remaining until the activity is completed.</span></span>
<span data-ttu-id="40ecd-145">Använd värdet-1 om det återstående antalet sekunder är okänt eller inte tillämpligt.</span><span class="sxs-lookup"><span data-stu-id="40ecd-145">Use the value -1 if the number of seconds remaining is unknown or not applicable.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-146">-SourceId</span><span class="sxs-lookup"><span data-stu-id="40ecd-146">-SourceId</span></span>

<span data-ttu-id="40ecd-147">Anger postens källa.</span><span class="sxs-lookup"><span data-stu-id="40ecd-147">Specifies the source of the record.</span></span> <span data-ttu-id="40ecd-148">Du kan använda detta i stället för **ID** **, men** kan inte användas med andra parametrar som t. ex..</span><span class="sxs-lookup"><span data-stu-id="40ecd-148">You can use this in place of **Id** but cannot be used with other parameters like **ParentId**.</span></span>

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-149">-Status</span><span class="sxs-lookup"><span data-stu-id="40ecd-149">-Status</span></span>

<span data-ttu-id="40ecd-150">Anger den andra text raden i rubriken ovanför statusfältet.</span><span class="sxs-lookup"><span data-stu-id="40ecd-150">Specifies the second line of text in the heading above the status bar.</span></span>
<span data-ttu-id="40ecd-151">Den här texten beskriver aktivitetens aktuella status.</span><span class="sxs-lookup"><span data-stu-id="40ecd-151">This text describes current state of the activity.</span></span>

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### <span data-ttu-id="40ecd-152">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="40ecd-152">CommonParameters</span></span>

<span data-ttu-id="40ecd-153">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="40ecd-153">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="40ecd-154">Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span><span class="sxs-lookup"><span data-stu-id="40ecd-154">For more information, see [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).</span></span>

## <span data-ttu-id="40ecd-155">INDATA</span><span class="sxs-lookup"><span data-stu-id="40ecd-155">INPUTS</span></span>

### <span data-ttu-id="40ecd-156">Inget</span><span class="sxs-lookup"><span data-stu-id="40ecd-156">None</span></span>

<span data-ttu-id="40ecd-157">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="40ecd-157">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="40ecd-158">UTDATA</span><span class="sxs-lookup"><span data-stu-id="40ecd-158">OUTPUTS</span></span>

### <span data-ttu-id="40ecd-159">Inget</span><span class="sxs-lookup"><span data-stu-id="40ecd-159">None</span></span>

<span data-ttu-id="40ecd-160">`Write-Progress` genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="40ecd-160">`Write-Progress` does not generate any output.</span></span>

## <span data-ttu-id="40ecd-161">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="40ecd-161">NOTES</span></span>

<span data-ttu-id="40ecd-162">Om förlopps indikatorn inte visas kontrollerar du värdet för `$ProgressPreference` variabeln.</span><span class="sxs-lookup"><span data-stu-id="40ecd-162">If the progress bar does not appear, check the value of the `$ProgressPreference` variable.</span></span> <span data-ttu-id="40ecd-163">Om värdet är inställt på SilentlyContinue visas inte förlopps indikatorn.</span><span class="sxs-lookup"><span data-stu-id="40ecd-163">If the value is set to SilentlyContinue, the progress bar is not displayed.</span></span> <span data-ttu-id="40ecd-164">Mer information om PowerShell-inställningar finns [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="40ecd-164">For more information about PowerShell preferences, see [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).</span></span>

<span data-ttu-id="40ecd-165">Parametrarna för cmdleten motsvarar egenskaperna för klassen **system. Management. Automation. progressRecord** .</span><span class="sxs-lookup"><span data-stu-id="40ecd-165">The parameters of the cmdlet correspond to the properties of the **System.Management.Automation.ProgressRecord** class.</span></span> <span data-ttu-id="40ecd-166">Mer information finns i [progressRecord-klass](/dotnet/api/system.management.automation.progressrecord).</span><span class="sxs-lookup"><span data-stu-id="40ecd-166">For more information, see [ProgressRecord Class](/dotnet/api/system.management.automation.progressrecord).</span></span>

## <span data-ttu-id="40ecd-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="40ecd-167">RELATED LINKS</span></span>

[<span data-ttu-id="40ecd-168">Skriv-debug</span><span class="sxs-lookup"><span data-stu-id="40ecd-168">Write-Debug</span></span>](Write-Debug.md)

[<span data-ttu-id="40ecd-169">Skriv-fel</span><span class="sxs-lookup"><span data-stu-id="40ecd-169">Write-Error</span></span>](Write-Error.md)

[<span data-ttu-id="40ecd-170">Skriv värd</span><span class="sxs-lookup"><span data-stu-id="40ecd-170">Write-Host</span></span>](Write-Host.md)

[<span data-ttu-id="40ecd-171">Skriva-utdata</span><span class="sxs-lookup"><span data-stu-id="40ecd-171">Write-Output</span></span>](Write-Output.md)

[<span data-ttu-id="40ecd-172">Skriv förlopp</span><span class="sxs-lookup"><span data-stu-id="40ecd-172">Write-Progress</span></span>](Write-Progress.md)

[<span data-ttu-id="40ecd-173">Skriv-verbose</span><span class="sxs-lookup"><span data-stu-id="40ecd-173">Write-Verbose</span></span>](Write-Verbose.md)

[<span data-ttu-id="40ecd-174">Skriv varning</span><span class="sxs-lookup"><span data-stu-id="40ecd-174">Write-Warning</span></span>](Write-Warning.md)
