---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 12/03/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/set-clipboard?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-Clipboard
ms.openlocfilehash: efb24b14122ad37043636d999afaa4199eb3097b
ms.sourcegitcommit: 7b376314e7640c39a53aac9f0db8bb935514a960
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/03/2020
ms.locfileid: "96564381"
---
# Set-Clipboard

## SAMMANFATTNING
Anger innehållet i Urklipp.

## SYNTAX

```
Set-Clipboard [-Value] <string[]> [-Append] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Set-Clipboard`Cmdleten anger innehållet i Urklipp.

> [!NOTE]
> I Linux kräver denna cmdlet att `xclip` verktyget finns i sökvägen.

## EXEMPEL

### Exempel 1: kopiera text till Urklipp

```powershell
Set-Clipboard -Value "This is a test string"
```

### Exempel 2: kopiera innehållet i en fil till Urklipp

Det här exemplet rör innehållet i en fil till Urklipp. I det här exemplet hämtar vi en offentlig SSH-nyckel så att den kan klistras in i ett annat program, t. ex. GitHub.

```powershell
Get-Content C:\Users\user1\.ssh\id_ed25519.pub | Set-Clipboard
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

### -Värde

De sträng värden som ska läggas till i Urklipp.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
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
