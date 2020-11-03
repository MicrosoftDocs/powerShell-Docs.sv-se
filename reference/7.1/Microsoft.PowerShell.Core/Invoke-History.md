---
external help file: System.Management.Automation.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Core
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/invoke-history?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Invoke-History
ms.openlocfilehash: 89d1f319bdedc45646fca1cb7ca7e0f78ed88bbf
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267651"
---
# Invoke-History

## SAMMANFATTNING
Kör kommandon från tidigare sessioner.

## SYNTAX

```
Invoke-History [[-Id] <String>] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Invoke-History`Cmdleten kör kommandon från tidigare sessioner. Du kan skicka objekt som representerar kommandona från Get-History till `Invoke-History` , eller så kan du identifiera kommandon i den aktuella historiken med hjälp av deras **ID-** nummer. Använd cmdleten för att hitta identifikations numret för ett kommando `Get-History` .

Historiken för sessionen hanteras separat från historiken som underhålls av **PSReadLine** -modulen.
Båda historiken är tillgängliga i sessioner där **PSReadLine** har lästs in. Den här cmdleten fungerar bara med tidigare session. Mer information finns i [about_PSReadLine](../PSReadLine/About/about_PSReadLine.md).

## EXEMPEL

### Exempel 1: kör det senaste kommandot i historiken

I det här exemplet körs det senaste eller senaste kommandot i tidigare session. Du kan förkorta det här kommandot som `r` alias för `Invoke-History` .

```powershell
Invoke-History
```

### Exempel 2: kör kommandot som har ett angivet ID

I det här exemplet körs kommandot i sessionen med **Id** 132. Eftersom namnet på **ID-** parametern är valfri kan du förkorta det här kommandot med följande: `Invoke-History 132` , `ihy 132` eller `r 132` .

```powershell
Invoke-History -Id 132
```

### Exempel 3: kör det senaste kommandot med hjälp av kommando texten

I det här exemplet körs det senaste `Get-Process` kommandot i tidigare sessioner. När du skriver tecken för **ID-** parametern `Invoke-History` Kör det första kommandot som den hittar som matchar mönstret, med början av de senaste kommandona.

```powershell
Invoke-History -Id get-pr
```

> [!NOTE]
> Mönster matchning är Skift läges känsligt, men mönstret matchar början av linjen.

### Exempel 4: kör en sekvens med kommandon från historiken

I det här exemplet körs kommandon 16 till och med 24. Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en tid för varje **ID-** värde.

```powershell
16..24 | ForEach {Invoke-History -Id $_ }
```

### Exempel 5

I det här exemplet körs sju kommandon i den historik som slutar med kommandot 255 (249 till 255). Den använder `Get-History` cmdleten för att hämta kommandon. Eftersom du bara kan lista ett **ID-** värde använder kommandot `ForEach-Object` cmdleten för att köra `Invoke-History` kommandot en gång för varje **ID-** värde.

```powershell
Get-History -Id 255 -Count 7 | ForEach {Invoke-History -Id $_.Id}
```

## PARAMETRAR

### -ID

Anger **ID** för ett kommando i historiken. Du kan ange **ID-** numret för kommandot eller de första tecknen i kommandot.

Om du skriver tecken `Invoke-History` matchar de senaste kommandona först. Om du utelämnar den här parametern `Invoke-History` körs det senaste eller senaste kommandot. Använd cmdleten för att hitta **ID-** numret för ett kommando `Get-History` .

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Confirm

Uppmanar dig att bekräfta innan du kör cmdleten.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: cf

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### -WhatIf

Visar vad som skulle hända om cmdleten kördes. Cmdleten körs inte.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: wi

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. String

Du kan skicka vidare ett historik **-ID** till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata, men utdata kan genereras av de kommandon som `Invoke-History` körs.

## ANTECKNINGAR

Tidigare session är en lista över kommandon som anges under sessionen. Tidigare sessioner representerar körnings ordning, status och start-och slut tid för kommandot. När du anger varje kommando lägger PowerShell till det i historiken så att du kan återanvända det. Mer information om tidigare sessioner finns [about_History](About/about_History.md).

Du kan också referera till `Invoke-History` med inbyggda alias `r` och `ihy` . Mer information finns i [about_Aliases](About/about_Aliases.md).

## RELATERADE LÄNKAR

[Lägg till-historik](Add-History.md)

[Rensa – historik](Clear-History.md)

[Hämta historik](Get-History.md)

