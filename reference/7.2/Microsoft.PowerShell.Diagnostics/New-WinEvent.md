---
external help file: Microsoft.PowerShell.Commands.Diagnostics.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Diagnostics
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.diagnostics/new-winevent?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: New-WinEvent
ms.openlocfilehash: 5b4b150a1c02e5d0689b44db9b2a984e297db766
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710872"
---
# New-WinEvent

## SAMMANFATTNING
Skapar en ny Windows-händelse för den angivna händelse leverantören.

## SYNTAX

```
New-WinEvent [-ProviderName] <String> [-Id] <Int32> [-Version <Byte>] [[-Payload] <Object[]>]
 [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **New-WinEvent** skapar en ETW (Event tracing for Windows)-händelse (ETW) för en händelse leverantör.
Du kan använda denna cmdlet för att lägga till händelser till ETW-kanaler från PowerShell.

## EXEMPEL

### Exempel 1

```powershell
PS C:\> New-WinEvent -ProviderName Microsoft-Windows-PowerShell -Id 45090 -Payload @("Workflow", "Running")
```

Det här kommandot använder cmdleten **New-WinEvent** för att skapa händelse 45090 för Microsoft-Windows-PowerShell-providern.

## PARAMETRAR

### -ID

Anger ett händelse-ID som har registrerats via ett Instrumentation-manifest.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Nytto Last

Anger meddelandet för händelsen. När händelsen skrivs till en händelse logg, lagras nytto lasten i händelse objektets **meddelande** egenskap.

När den angivna nytto lasten inte matchar nytto lasten i händelse definitionen genererar PowerShell en varning, men kommandot slutförs fortfarande.

```yaml
Type: System.Object[]
Parameter Sets: (All)
Aliases:

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ProviderName

Anger den Händelseprovidern som skriver händelsen till en händelse logg, till exempel "Microsoft-Windows-PowerShell". En ETW-Händelseprovidern är en logisk entitet som skriver händelser till ETW-sessioner.

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

### -Version

Anger händelsens versions nummer. Skriv händelse numret. PowerShell konverterar talet till den typ av byte som krävs.

Med den här parametern kan du ange en händelse när olika versioner av samma händelse definieras.

```yaml
Type: System.Byte
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inga

Den här cmdleten tar inte emot några ininformation från pipelinen.

## UTDATA

### Inga

Den här cmdleten genererar utdata.

## ANTECKNINGAR

* När providern skriver till en EventLog kan du hämta händelsen från händelse loggen med hjälp av cmdleten Get-WinEvent.

## RELATERADE LÄNKAR

[Get-WinEvent](Get-WinEvent.md)

