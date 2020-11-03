---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 098e98dec6733af036795e4decb633f59d40c633
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261539"
---
# Get-UICulture

## SAMMANFATTNING
Hämtar de aktuella inställningarna för användar gränssnitts kulturen i operativ systemet.

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## BESKRIVNING
**Get-värdet** -cmdlet: en hämtar information om de aktuella användar gränssnittets inställningar för användar gränssnitt (UI) för Windows.
ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.

Du kan också använda Get-Culture-cmdleten, som hämtar den aktuella kulturen i systemet.
Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum.

## EXEMPEL

### Exempel 1: Hämta UI-kulturen

```
PS C:\> Get-UICulture
```

Det här kommandot hämtar den aktuella kultur informationen för användar gränssnittet.

### Exempel 2: Hämta UI-kulturen och formatera resultaten

```
PS C:\> Get-UICulture | Format-List *
```

Det här kommandot visar värdena för alla egenskaper för den aktuella UI-kulturen i en lista.

### Exempel 3: Hämta värdet för kalender egenskapen

```
PS C:\> (Get-UICulture).Calendar
```

Det här kommandot visar de aktuella värdena för kalender egenskapen för den aktuella UI-kulturen.
Kalendern är bara en egenskap för användar gränssnitts kulturen.
Om du vill se alla egenskaper skriver du `Get-UICulture | Get-Member` .

### Exempel 4: Hämta kort datum mönster

```
PS C:\> (Get-UICulture).DateTimeFormat.ShortDatePattern
```

Det här kommandot visar kort datum mönstret för den aktuella kulturen i användar gränssnittet.
Om du vill se alla subegenskaper för DateTimeFormat-egenskapen för användar gränssnitts kulturen skriver du `(Get-UICulture).DateTimeFormat | gm` .

## PARAMETRAR

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. globalisering. CultureInfo, Microsoft. PowerShell. VistaCultureInfo
**Get-värdet** returnerar ett objekt som representerar den aktuella kulturen för användar gränssnittet.
I Windows PowerShell 3,0 returnerar den ett **CultureInfo** -objekt.
I Windows PowerShell 2,0 returnerar den ett **VistaCultureInfo** -objekt.

## ANTECKNINGAR

* Du kan också använda variablerna $PsCulture och $PsUICulture. Variabeln $PsCulture lagrar namnet på den aktuella kulturen och variabeln $PsUICulture lagrar namnet på den aktuella kulturen för användar gränssnittet.

*

## RELATERADE LÄNKAR

## RELATERADE LÄNKAR
