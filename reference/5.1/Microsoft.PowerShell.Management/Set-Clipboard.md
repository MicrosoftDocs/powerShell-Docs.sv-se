---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: f3230c247296d5fd907d580e719cbbbc560183a9
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265418"
---
# Set-Clipboard

## SAMMANFATTNING
Anger det aktuella urklipps posten i Windows.

## SYNTAX

### Sträng (standard)

```
Set-Clipboard [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Värde

```
Set-Clipboard [-Value] <String[]> [-Append] [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Sökväg

```
Set-Clipboard [-Append] -Path <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Set-Clipboard [-Append] -LiteralPath <String[]> [-AsHtml] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Clipboard`Cmdleten anger det aktuella urklipps posten i Windows.

## EXEMPEL

### Exempel 1: kopiera text till Urklipp

```powershell
Set-Clipboard -Value "This is a test string"
```

### Exempel 2: kopiera innehållet i en katalog till Urklipp

Det här kommandot kopierar innehållet i den angivna mappen till Urklipp.

```powershell
Set-Clipboard -Path "C:\Staging\"
```

## PARAMETRAR

### -Lägg till

Anger att cmdleten inte rensar Urklipp och lägger till innehåll i den.

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

### -HTML

Anger att cmdleten återger innehållet som HTML i Urklipp.

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

### -LiteralPath

Anger sökvägen till det objekt som kopieras till Urklipp. Till skillnad från **sökväg** används värdet för **LiteralPath** exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken anger att Windows PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till det objekt som kopieras till Urklipp. Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -Värde

Anger, som en sträng mat ris, det innehåll som ska kopieras till Urklipp.

```yaml
Type: System.String[]
Parameter Sets: Value
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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

### System.String[]

## UTDATA

## ANTECKNINGAR

I sällsynta fall när `Set-Clipboard` du använder med ett stort antal värden i snabb följd, som i en slinga, kan du sporadiskt få ett tomt värde från Urklipp. Detta kan åtgärdas med hjälp av `Start-Sleep -Milliseconds 1` i slingan.

## RELATERADE LÄNKAR

[Hämta Urklipp](Get-Clipboard.md)
