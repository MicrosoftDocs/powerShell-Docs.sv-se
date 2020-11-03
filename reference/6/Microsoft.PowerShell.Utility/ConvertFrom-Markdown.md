---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: PowerShell, cmdlet, markdown
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 11/02/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/convertfrom-markdown?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: ConvertFrom-Markdown
ms.openlocfilehash: efa5e65566e3b80f12f3de5ebd1277bf68c03ff0
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267170"
---
# ConvertFrom-Markdown

## SAMMANFATTNING
Konvertera innehållet i en sträng eller en fil till ett **MarkdownInfo** -objekt.

## SYNTAX

### PathParamSet (standard)

```
ConvertFrom-Markdown [-Path] <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### LiteralParamSet

```
ConvertFrom-Markdown -LiteralPath <String[]> [-AsVT100EncodedString] [<CommonParameters>]
```

### InputObjParamSet

```
ConvertFrom-Markdown -InputObject <PSObject> [-AsVT100EncodedString] [<CommonParameters>]
```

## BESKRIVNING

Denna cmdlet konverterar det angivna innehållet till en **MarkdownInfo**. När en fil Sök väg anges för parametern **Path** konverteras innehållet i filen. Objektet utdata har tre egenskaper:

- Egenskapen **token** har det abstrakta syntaxs trädet (AST) för det konverterade objektet
- **HTML-** egenskapen har HTML-konverteringen för angivna inaktuella indatamängdar
- Egenskapen **VT100EncodedString** har den konverterade STRÄNGEN med ANSI (VT100) escape-sekvenser om parametern **AsVT100EncodedString** har angetts

Denna cmdlet introducerades i PowerShell 6,1.

## EXEMPEL

### Exempel 1: konvertera en fil som innehåller markdown-innehåll till HTML

```powershell
ConvertFrom-Markdown -Path .\README.md
```

**MarkdownInfo** -objektet returneras. Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen. **HTML** -egenskapen har HTML-konverterat innehåll i `README.md` filen.

### Exempel 2: konvertera en fil som innehåller markdown-innehåll till en VT100-kodad sträng

```powershell
ConvertFrom-Markdown -Path .\README.md -AsVT100EncodedString
```

**MarkdownInfo** -objektet returneras. Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen. Egenskapen **VT100EncodedString** har den VT100-kodade sträng konverterade `README.md` filens innehåll.

### Exempel 3: konvertera indatamängds objekt som innehåller markdown-innehåll till en VT100-kodad sträng

```powershell
Get-Item .\README.md | ConvertFrom-Markdown -AsVT100EncodedString
```

**MarkdownInfo** -objektet returneras. **Fileinfo** -objektet från `Get-Item` konverteras till en VT100-kodad sträng. Egenskapen **tokens** har AST-värdet för det konverterade innehållet i `README.md` filen. Egenskapen **VT100EncodedString** har den VT100-kodade sträng konverterade `README.md` filens innehåll.

### Exempel 4: konvertera en sträng som innehåller markdown-innehåll till en VT100-kodad sträng

```powershell
"**Bold text**" | ConvertFrom-Markdown -AsVT100EncodedString
```

**MarkdownInfo** -objektet returneras. Den angivna strängen `**Bold text**` konverteras till en VT100-kodad sträng och är tillgänglig i egenskapen **VT100EncodedString** .

## PARAMETRAR

### -AsVT100EncodedString

Anger om utdata ska kodas som en sträng med VT100 Escape-koder.

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

### – InputObject

Anger det objekt som ska konverteras. När ett objekt av typen **system. String** anges konverteras strängen. När ett objekt av typen **system. io. fileinfo** anges konverteras innehållet i den fil som anges av objektet. Objekt av någon annan typ resulterar i ett fel.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObjParamSet
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger en sökväg till filen som ska konverteras.

```yaml
Type: System.String[]
Parameter Sets: LiteralParamSet
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Path

Anger en sökväg till filen som ska konverteras.

```yaml
Type: System.String[]
Parameter Sets: PathParamSet
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: True
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

## UTDATA

### Microsoft. PowerShell. MarkdownRender. MarkdownInfo

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Markdown-tolkare](https://github.com/lunet-io/markdig)

[ANSI Escape-kod](https://wikipedia.org/wiki/ANSI_escape_code)
