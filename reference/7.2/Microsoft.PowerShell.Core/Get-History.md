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
# Get-History

## SAMMANFATTNING
Hämtar en lista med kommandon som angavs under den aktuella sessionen.

## SYNTAX

```
Get-History [[-Id] <Int64[]>] [[-Count] <Int32>] [<CommonParameters>]
```

## BESKRIVNING

`Get-History`Cmdlet: en hämtar tidigare session, det vill säga en lista med kommandon som angavs under den aktuella sessionen.

PowerShell upprätthåller automatiskt en historik över varje session. Antalet poster i sessionens historik bestäms av värdet för `$MaximumHistoryCount` variabeln Preference. Från och med Windows PowerShell 3,0 är standardvärdet `4096` . Som standard sparas historikfilerna i arbets katalogen, men du kan spara filen var som helst. Mer information om historik funktionerna i PowerShell finns [about_History](About/about_History.md).

Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.
Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in. Den här cmdleten fungerar bara med tidigare session. Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPEL

### Exempel 1: Hämta tidigare session

Det här exemplet hämtar posterna i tidigare sessioner. Standard visningen visar varje kommando och dess ID, som anger i vilken ordning de kördes.

```powershell
Get-History
```

### Exempel 2: hämta poster som innehåller en sträng

I det här exemplet hämtas poster i kommando historiken som innehåller sträng tjänsten. Det första kommandot hämtar alla poster i tidigare sessioner. Pipeline-operatorn ( `|` ) skickar resultatet till `Where-Object` cmdleten, som endast väljer de kommandon som inkluderar tjänsten.

```powershell
Get-History | Where-Object {$_.CommandLine -like "*Service*"}
```

### Exempel 3: exportera historik poster upp till ett angivet ID

Det här exemplet hämtar de fem senaste historik posterna som slutar med Entry 7. Pipeline-operatorn skickar resultatet till `Export-Csv` cmdleten, som formaterar historiken som kommaavgränsad text och sparar den i History.csv-filen. Filen innehåller de data som visas när du formaterar historiken som en lista. Detta inkluderar kommandonas status och start-och slut tid.

```powershell
Get-History -ID 7 -Count 5 | Export-Csv History.csv
```

### Exempel 4: Visa det senaste kommandot

Det här exemplet hämtar det sista kommandot i kommando historiken. Det sista kommandot är det senast angivna kommandot. Det här kommandot använder **Count** -parametern för att visa bara ett kommando. Som standard `Get-History` hämtar de senaste kommandona. Det här kommandot kan förkortas till "h-c 1" och motsvarar att trycka på tangenten UPPIL.

```powershell
Get-History -Count 1
```

### Exempel 5: Visa alla egenskaper för posterna i historiken

I det här exemplet visas alla egenskaper för poster i sessionens historik. Pipeline-operatorn skickar resultatet av ett `Get-History` kommando till `Format-List` cmdleten, som visar alla egenskaper för varje historik post. Detta omfattar kommandots ID, status, start-och slut tid.

```powershell
Get-History | Format-List -Property *
```

## PARAMETRAR

### -Antal

Anger antalet senaste historik poster som denna cmdlet hämtar. Som standard `Get-History` hämtar alla poster i tidigare sessioner. Om du använder både **Count** -och **ID-** parametrarna i ett kommando avslutas skärmen med kommandot som anges av **ID-** parametern.

I Windows PowerShell 2,0 hämtar som standard `Get-History` de 32 senaste posterna.

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

### -ID

Anger en matris med ID: n för poster i sessionens historik. `Get-History` hämtar endast angivna poster. Om du använder båda parametrarna **ID** och **Count** i ett kommando `Get-History` hämtar de senaste posterna som slutar med den post som anges av **ID-** parametern.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Int64

Du kan skicka vidare ett historik-ID till denna cmdlet.

## UTDATA

### Microsoft. PowerShell. commands. HistoryInfo

Denna cmdlet returnerar ett historik objekt för varje historik objekt som det får.

## ANTECKNINGAR

Tidigare session är en lista över kommandon som anges under sessionen. Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot. När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det. Mer information om kommando historiken finns [about_History](About/about_History.md).

Från och med Windows PowerShell 3,0 är standardvärdet för `$MaximumHistoryCount` Preference-variabeln `4096` . I Windows PowerShell 2,0 är standardvärdet `64` . Mer information om `$MaximumHistoryCount` variabeln finns i [about_Preference_Variables](About/about_Preference_Variables.md).

## RELATERADE LÄNKAR

[Lägg till-historik](Add-History.md)

[Rensa – historik](Clear-History.md)

[Anropa-historik](Invoke-History.md)

[about_History](About/about_History.md)
