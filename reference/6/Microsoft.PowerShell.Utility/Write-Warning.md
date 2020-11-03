---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 10/14/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/write-warning?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Write-Warning
ms.openlocfilehash: 5553f61038c10d0c7c251609f729d157c53b03b9
ms.sourcegitcommit: 16883bb67e34b3915798070f60f974bf85160bd3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/16/2020
ms.locfileid: "93272684"
---
# Write-Warning

## SAMMANFATTNING
Skriver ett varnings meddelande.

## SYNTAX

```
Write-Warning [-Message] <String> [<CommonParameters>]
```

## BESKRIVNING

`Write-Warning`Cmdleten skriver ett varnings meddelande till PowerShell-värden. Svaret på varningen beror på värdet på användarens `$WarningPreference` variabel och användningen av den gemensamma **WarningAction** -parametern.

## EXEMPEL

### Exempel 1: Skriv ett varnings meddelande

Det här kommandot visar meddelandet "Varning: Detta är bara en test varning".

```powershell
Write-Warning "This is only a test warning."
```

### Exempel 2: skicka en sträng till Write-Warning

Det här kommandot visar att du kan använda en pipeline-operator ( `|` ) för att skicka en sträng till `Write-Warning` .
Du kan spara strängen i en variabel, som du ser i det här kommandot eller skicka vidare strängen direkt till `Write-Warning` .

```powershell
$w = "This is only a test warning."
$w | Write-Warning
```

### Exempel 3: Ange variabeln $WarningPreference och skriv en varning

I det här exemplet visas resultatet av `$WarningPreference` variabeln i ett `Write-Warning` kommando.

```powershell
PS> $WarningPreference
Continue
PS> Write-Warning "This is only a test warning."
This is only a test warning.
PS> $WarningPreference = "SilentlyContinue"
PS> Write-Warning "This is only a test warning."
PS> $WarningPreference = "Stop"
PS> Write-Warning "This is only a test warning."
WARNING: This is only a test message.
Write-Warning : Command execution stopped because the shell variable "WarningPreference" is set to Stop.
At line:1 char:14
     + Write-Warning <<<<  "This is only a test message."
```

Det första kommandot visar standardvärdet för `$WarningPreference` variabeln, som är `Continue` . Det innebär att när du skriver en varning visas varnings meddelandet och körningen fortsätter.

När du ändrar värdet för `$WarningPreference` variabeln ändras effekterna av `Write-Warning` kommandot igen. Värdet `SilentlyContinue` förhindrar varningen. Värdet `Stop` visar varningen och sedan stoppas körningen av kommandot.

Mer information om `$WarningPreference` variabeln finns i [about_Preference_Variables](../Microsoft.Powershell.Core/About/about_Preference_Variables.md).

### Exempel 4: ange parametern WarningAction och skriv en varning

Det här exemplet visar effekterna av den gemensamma parametern **WarningAction** i ett `Write-Warning` kommando. Du kan använda den gemensamma parametern **WarningAction** med valfri cmdlet för att avgöra hur PowerShell svarar på varningar som orsakas av kommandot. Parametern **WarningAction** common åsidosätter bara värdet för det `$WarningPreference` specifika kommandot.

```powershell
PS> Write-Warning "This is only a test warning." -WarningAction Inquire
WARNING: This is only a test warning.
Confirm
Continue with this operation?
 [Y] Yes  [A] Yes to All  [H] Halt Command  [S] Suspend  [?] Help (default is "Y"):
```

Detta kommando använder `Write-Warning` cmdleten för att visa en varning. Den gemensamma parametern **WarningAction** med värdet fråga instruerar systemet att fråga användaren när kommandot visar en varning.

Mer information om den gemensamma parametern **WarningAction** finns [about_CommonParameters](../Microsoft.Powershell.Core/About/about_CommonParameters.md).

## PARAMETRAR

### – Meddelande
Anger varnings meddelandet.

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

Du kan skicka vidare en sträng som innehåller varningen till `Write-Warning` .

## UTDATA

### Inget

`Write-Warning` skriver endast till varnings strömmen. Inga andra utdata genereras.

## ANTECKNINGAR

Standardvärdet för `$WarningPreference` variabeln är `Continue` , som visar varningen och fortsätter att köra kommandot. Om du vill fastställa giltiga värden för en inställnings variabel, till exempel `$WarningPreference` , anger du den till en sträng med slumpmässiga tecken, till exempel "ABC". I det resulterande fel meddelandet visas giltiga värden.

## RELATERADE LÄNKAR

[about_Output_Streams](../Microsoft.PowerShell.Core/About/about_Output_Streams.md)

[about_Redirection](../Microsoft.PowerShell.Core/About/about_Redirection.md)

[Skriv-debug](Write-Debug.md)

[Skriv-fel](Write-Error.md)

[Skriv värd](Write-Host.md)

[Skriv information](Write-Information.md)

[Skriva-utdata](Write-Output.md)

[Skriv förlopp](Write-Progress.md)

[Skriv-verbose](Write-Verbose.md)
