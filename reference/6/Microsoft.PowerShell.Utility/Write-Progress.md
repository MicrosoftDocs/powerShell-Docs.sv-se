---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-progress?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Progress
ms.openlocfilehash: 1e0a52340aedfc606134f42e855b2e1cf49930b5
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272685"
---
# Write-Progress

## SAMMANFATTNING
Visar en förlopps indikator i ett PowerShell-kommando fönster.

## SYNTAX

```
Write-Progress [-Activity] <String> [[-Status] <String>] [[-Id] <Int32>] [-PercentComplete <Int32>]
 [-SecondsRemaining <Int32>] [-CurrentOperation <String>] [-ParentId <Int32>] [-Completed] [-SourceId <Int32>]
 [<CommonParameters>]
```

## BESKRIVNING

`Write-Progress`Cmdleten visar en förlopps indikator i ett PowerShell-kommando fönster som visar statusen för ett kommando eller skript som körs. Du kan välja de indikatorer som stapeln visar och texten som visas ovanför och under förlopps indikatorn.

## EXEMPEL

### Exempel 1: Visa förloppet för en for-loop

```powershell
for ($i = 1; $i -le 100; $i++ )
{
    Write-Progress -Activity "Search in Progress" -Status "$i% Complete:" -PercentComplete $i;
}
```

Det här kommandot visar förloppet för en for-loop som räknas från 1 till 100.

`Write-Progress`Cmdlet: en innehåller en Statusfälts rubrik, `Activity` en status rad och variabeln `$i` (räknaren i for-slingan) som visar den relativa hela uppgiften.

### Exempel 2: Visa förloppet för kapslade slingor

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

I det här exemplet visas förloppet för två kapslade för slingor som representeras av en förlopps indikator.

`Write-Progress`Kommandot för den andra förlopps indikatorn innehåller **ID-** parametern som särskiljer den från den första förlopps indikatorn.

Utan parametern **ID** skulle förlopps staplarna placeras ovanpå varandra i stället för att visas en under den andra.

### Exempel 3: Visa förloppet när du söker efter en sträng

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

Det här kommandot visar förloppet för ett kommando för att hitta strängen "BIOS" i system händelse loggen.

Parametervärdet för **procent färdigt** beräknas genom att antalet händelser som har bearbetats divideras med `$I` det totala antalet händelser som hämtats `$Events.count` och sedan multipliceras resultatet med 100.

### Exempel 4: Visa förloppet för varje nivå i en kapslad process

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

I det här exemplet kan du använda **parametern** libför att Visa indragna utdata för att visa överordnade/underordnade relationer i förloppet för varje steg.

## PARAMETRAR

### -Aktivitet

Anger den första text raden i rubriken ovanför statusfältet.
Den här texten beskriver den aktivitet vars förlopp rapporteras.

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

### -Slutförd

Anger om förlopps indikatorn är synlig.
Om den här parametern utelämnas `Write-Progress` visas information om förloppet.

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

### -CurrentOperation

Anger text raden under förlopps indikatorn.
I den här texten beskrivs den åtgärd som pågår.

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

### -ID

Anger ett ID som särskiljer varje förlopps indikator från de andra. Använd den här parametern när du skapar fler än en förlopps indikator i ett enda kommando. Om förlopps staplarna inte har olika ID: n placeras de ovanpå i stället för att visas i en serie.

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

### -ID

Anger den överordnade aktiviteten för den aktuella aktiviteten.
Använd värdet-1 om den aktuella aktiviteten inte har någon överordnad aktivitet.

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

### -Procent färdigt

Anger procent andelen för den aktivitet som har slutförts.
Använd värdet-1 om procent andelen Slutför är okänd eller inte tillämplig.

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

### -SecondsRemaining

Anger det planerade antalet sekunder kvar tills aktiviteten har slutförts.
Använd värdet-1 om det återstående antalet sekunder är okänt eller inte tillämpligt.

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

### -SourceId

Anger postens källa. Du kan använda detta i stället för **ID** **, men** kan inte användas med andra parametrar som t. ex..

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

### -Status

Anger den andra text raden i rubriken ovanför statusfältet.
Den här texten beskriver aktivitetens aktuella status.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget

`Write-Progress` genererar inga utdata.

## ANTECKNINGAR

Om förlopps indikatorn inte visas kontrollerar du värdet för `$ProgressPreference` variabeln. Om värdet är inställt på SilentlyContinue visas inte förlopps indikatorn. Mer information om PowerShell-inställningar finns [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

Parametrarna för cmdleten motsvarar egenskaperna för klassen **system. Management. Automation. progressRecord** . Mer information finns i [progressRecord-klass](/dotnet/api/system.management.automation.progressrecord).

## RELATERADE LÄNKAR

[Skriv-debug](Write-Debug.md)

[Skriv-fel](Write-Error.md)

[Skriv värd](Write-Host.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)
