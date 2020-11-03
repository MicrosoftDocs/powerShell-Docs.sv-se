---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-verbose?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Verbose
ms.openlocfilehash: 07289eb2f43a0527ab523a10319777d3ef0e8ddf
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272691"
---
# Write-Verbose

## SAMMANFATTNING
Skriver text till data strömmen för utförliga meddelanden.

## SYNTAX

```
Write-Verbose [-Message] <String> [<CommonParameters>]
```

## BESKRIVNING

`Write-Verbose`Cmdleten skriver text till data strömmen för utförliga meddelanden i PowerShell. Den utförliga meddelande strömmen används vanligt vis för att leverera mer ingående information om kommando bearbetning.

Den utförliga meddelande strömmen visas som standard inte, men du kan visa den genom att ändra värdet för `$VerbosePreference` variabeln eller använda den **utförliga** gemensamma parametern i alla kommandon.

## EXEMPEL

### Exempel 1: Skriv ett status meddelande

```powershell
Write-Verbose -Message "Searching the Application Event Log."
Write-Verbose -Message "Searching the Application Event Log." -Verbose
```

Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande. Som standard visas inte meddelandet.

Det andra kommandot använder den **utförliga** gemensamma parametern, som visar alla utförliga meddelanden, oavsett värdet för `$VerbosePreference` variabeln.

### Exempel 2: Ange $VerbosePreference och skriv ett status meddelande

```powershell
$VerbosePreference = "Continue"
Write-Verbose "Copying file $filename"
```

Dessa kommandon använder `Write-Verbose` cmdleten för att visa ett status meddelande. Som standard visas inte meddelandet.

Det första kommandot tilldelar värdet Fortsätt till `$VerbosePreference` Preference-variabeln. Standardvärdet, `SilentlyContinue` , förhindrar utförliga meddelanden. Det andra kommandot skriver ett utförligt meddelande.

## PARAMETRAR

### – Meddelande

Anger meddelandet som ska visas. Den här parametern är obligatorisk. Du kan också skicka en meddelande sträng till `Write-Verbose` .

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

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### System. String

Du kan skicka vidare en sträng som innehåller meddelandet till `Write-Verbose` .

## UTDATA

### Inget

`Write-Verbose` skriver enbart till den utförliga meddelande strömmen.

## ANTECKNINGAR

- Utförliga meddelanden returneras bara när kommandot använder den **utförliga** gemensamma parametern. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).
- I Windows PowerShell bakgrunds jobb och fjärrkommandon `$VerbosePreference` avgör variabeln i jobbschemaläggaren och fjärrsession om utförligt meddelande visas som standard.
  Mer information om `$VerbosePreference` variabeln finns i [about_Preference_Variables](../Microsoft.PowerShell.Core/About/about_Preference_Variables.md).

## RELATERADE LÄNKAR

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Skriv-debug](Write-Debug.md)

[Skriv-fel](Write-Error.md)

[Skriv värd](Write-Host.md)

[Skriv information](Write-Information.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv varning](Write-Warning.md)
