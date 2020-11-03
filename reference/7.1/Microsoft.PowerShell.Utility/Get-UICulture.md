---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-uiculture?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-UICulture
ms.openlocfilehash: 3e1ae99f3e2bd52d26e9c567fcc8184b07c71a4a
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261662"
---
# Get-UICulture

## SAMMANFATTNING
Hämtar de aktuella inställningarna för användar gränssnitts kulturen i operativ systemet.

## SYNTAX

```
Get-UICulture [<CommonParameters>]
```

## BESKRIVNING

`Get-UICulture`Cmdleten hämtar information om de aktuella användar gränssnittets inställningar för användar gränssnitt (UI) för Windows.
ANVÄNDAR gränssnittets kultur avgör vilka text strängar som används för gränssnitts element, till exempel menyer och meddelanden.

Du kan också använda `Get-Culture` cmdleten, som hämtar den aktuella kulturen i systemet.
Kulturen bestämmer visnings formatet för objekt som tal, valuta och datum.

## EXEMPEL

### Exempel 1: Hämta UI-kulturen

```powershell
Get-UICulture
```

Det här kommandot hämtar den aktuella kultur informationen för användar gränssnittet.

### Exempel 2: Hämta UI-kulturen och formatera resultaten

```powershell
Get-UICulture | Format-List *
```

Det här kommandot visar värdena för alla egenskaper för den aktuella UI-kulturen i en lista.

### Exempel 3: Hämta värdet för kalender egenskapen

```powershell
(Get-UICulture).Calendar
```

Det här kommandot visar de aktuella värdena för **kalender** egenskapen för den aktuella UI-kulturen.
Kalendern är bara en egenskap för användar gränssnitts kulturen.
Om du vill se alla egenskaper skriver du `Get-UICulture | Get-Member` .

### Exempel 4: Hämta kort datum mönster

```powershell
(Get-UICulture).DateTimeFormat.ShortDatePattern
```

Det här kommandot visar kort datum mönstret för den aktuella kulturen i användar gränssnittet.
Om du vill se alla subegenskaper för **DateTimeFormat** -egenskapen för användar gränssnitts kulturen skriver du `(Get-UICulture).DateTimeFormat | gm` .

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](../Microsoft.PowerShell.Core/About/about_CommonParameters.md).

## INDATA

### Inget

Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### System. globalisering. CultureInfo, Microsoft. PowerShell. VistaCultureInfo

`Get-UICulture` Returnerar ett objekt som representerar den aktuella kulturen för användar gränssnittet.
I Windows PowerShell 3,0 returnerar den ett **CultureInfo** -objekt.
I Windows PowerShell 2,0 returnerar den ett **VistaCultureInfo** -objekt.

## ANTECKNINGAR

- Du kan också använda `$PsCulture` `$PsUICulture` variablerna och. `$PsCulture`Variabeln lagrar namnet på den aktuella kulturen och `$PsUICulture` variabeln lagrar namnet på den aktuella kulturen för användar gränssnittet.

## RELATERADE LÄNKAR

