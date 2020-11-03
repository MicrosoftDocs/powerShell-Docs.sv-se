---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-debug?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Debug
ms.openlocfilehash: 3217a3c67c262f8061963fd1302c6782620e270d
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272852"
---
# Write-Debug

## SAMMANFATTNING
Skriver ett fel söknings meddelande till-konsolen.

## SYNTAX

```
Write-Debug [-Message] <String> [<CommonParameters>]
```

## BESKRIVNING

`Write-Debug`Cmdleten skriver fel söknings meddelanden till värden från ett skript eller kommando.

Som standard visas inte fel söknings meddelanden i-konsolen, men du kan visa dem med hjälp av parametern **Debug** eller `$DebugPreference` variabeln.

## EXEMPEL

### Exempel 1: förstå $DebugPreference

Det här exemplet skriver ett fel söknings meddelande.

```powershell
Write-Debug "Cannot open file."
```

Standardvärdet för `$DebugPreference` är **SilentlyContinue**. Meddelandet visas därför inte i-konsolen.

### Exempel 2: ändra värdet för $DebugPreference

I det här exemplet visas effekterna av att ändra värdet för `$DebugPreference` variabeln. Först visar vi det aktuella värdet för `$DebugPreference` och försöker skriva ett fel söknings meddelande. Sedan ändrar vi värdet för `$DebugPreference` att **fortsätta** , vilket gör att fel söknings meddelanden visas.

```
PS> $DebugPreference
SilentlyContinue
PS> Write-Debug "Cannot open file."
PS>
PS> $DebugPreference = "Continue"
PS> Write-Debug "Cannot open file."
DEBUG: Cannot open file.
```

Mer information om `$DebugPreference` finns i [about_Preference_Variables](/powershell/module/Microsoft.PowerShell.Core/About/about_Preference_Variables).

### Exempel 3: Använd fel söknings parametern om du vill åsidosätta $DebugPreference

`Test-Debug`Funktionen skriver värdet för `$DebugPreference` variabeln till PowerShell-värden och fel söknings strömmen. I det här exemplet använder vi parametern **Felsök** för att åsidosätta `$DebugPreference` värdet.

```powershell
function Test-Debug {
    [CmdletBinding()]
    param()
    Write-Debug ('$DebugPreference is ' + $DebugPreference)
    Write-Host ('$DebugPreference is ' + $DebugPreference)
}
```

```
PS> Test-Debug
$DebugPreference is SilentlyContinue

PS> Test-Debug -Debug
DEBUG: $DebugPreference is Continue
$DebugPreference is Continue
PS> $DebugPreference
SilentlyContinue
```

Observera att värdet för `$DebugPreference` ändras när du använder **fel söknings** parametern. Den här ändringen påverkar bara funktionens omfattning. Värdet påverkas inte utanför funktionen.

Mer information om den vanliga **fel söknings** parametern finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## PARAMETRAR

### – Meddelande

Anger fel söknings meddelandet som ska skickas till-konsolen.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: Msg

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller ett fel söknings meddelande till `Write-Debug` .

## UTDATA

### Inget

`Write-Debug` skriver endast till fel söknings data ström. Det skriver inte några objekt till pipelinen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Skriv-fel](Write-Error.md)

[Skriv värd](Write-Host.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)

[Skriv varning](Write-Warning.md)
