---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Set-MarkdownOption?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-MarkdownOption
ms.openlocfilehash: 1f25d8c63ceacb5edc00fd0c2155799f9a8d844d
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103195544"
---
# Set-MarkdownOption

## SAMMANFATTNING
Anger de färger och format som används för att återge markdown-innehåll i-konsolen.

## SYNTAX

### IndividualSetting (standard)

```
Set-MarkdownOption [-Header1Color <String>] [-Header2Color <String>] [-Header3Color <String>]
 [-Header4Color <String>] [-Header5Color <String>] [-Header6Color <String>] [-Code <String>]
 [-ImageAltTextForegroundColor <String>] [-LinkForegroundColor <String>]
 [-ItalicsForegroundColor <String>] [-BoldForegroundColor <String>] [-PassThru]
 [<CommonParameters>]
```

### Tema

```
Set-MarkdownOption [-PassThru] -Theme <String> [<CommonParameters>]
```

### InputObject

```
Set-MarkdownOption [-PassThru] [-InputObject] <PSObject> [<CommonParameters>]
```

## BESKRIVNING

Anger de färger och format som används för att återge markdown-innehåll i-konsolen. Dessa format definieras med ANSI Escape-koder som ändrar färg och format på den markdown text som återges.

Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.

> [!NOTE]
> Sträng värden som används i inställningarna är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen. Inkludera inte **Escape** -tecken i strängen. Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).

## EXEMPEL

### Exempel 1 – växla till det ljusa temat

I det här exemplet väljer du det **ljusa** temat och visar den nya konfigurationen med hjälp av parametern **Passthru** .

```powershell
Set-MarkdownOption -Theme Light -PassThru
```

```Output
Header1         : [7m
Header2         : [4;33m
Header3         : [4;34m
Header4         : [4;35m
Header5         : [4;36m
Header6         : [4;30m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

### Exempel 2 – anpassa inställningarna för färg och stil

I det här exemplet ändras Escape-koden för markdown-huvudena. Standard konfigurationen för huvuden återges som understruken text i olika färger. Den här ändringen tar bort understryknings formatet.

```powershell
$mdOptions = Get-MarkdownOption
$mdOptions.Header2 = '[93m'
$mdOptions.Header3 = '[94m'
$mdOptions.Header4 = '[95m'
$mdOptions.Header5 = '[96m'
$mdOptions.Header6 = '[97m'
Set-MarkdownOption -InputObject $mdOptions -PassThru
```

```Output
Header1         : [7m
Header2         : [93m
Header3         : [94m
Header4         : [95m
Header5         : [96m
Header6         : [97m
Code            : [48;2;155;155;155;38;2;30;30;31m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

## PARAMETRAR

### -BoldForegroundColor

Anger förgrunds färgen för rendering av fet markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kod

Anger färgen för åter givning av kod block och intervall i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header1Color

Anger färgen för åter givning av Header1-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header2Color

Anger färgen för åter givning av Header2-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header3Color

Anger färgen för åter givning av Header3-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header4Color

Anger färgen för åter givning av Header4-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header5Color

Anger färgen för åter givning av Header5-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Header6Color

Anger färgen för åter givning av Header6-block i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ImageAltTextForegroundColor

Anger förgrunds färgen för åter givning av alternativ text för ett bild element i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – InputObject

Ett **PSMarkdownOptionInfo** -objekt som innehåller den konfiguration som ska ställas in.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ItalicsForegroundColor

Anger förgrunds färgen för att återge kursiv stilarna i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -LinkForegroundColor

Anger förgrunds färgen för åter givning av hyperlänkar i markdown text.

```yaml
Type: System.String
Parameter Sets: IndividualSetting
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – PassThru

Gör att cmdleten genererar ett **PSMarkdownOptionInfo** -objekt som innehåller den nya konfigurationen.

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

### – Tema

Väljer ett tema som innehåller fördefinierade färg inställningar. De möjliga värdena är **mörka** och **ljusa**.

```yaml
Type: System.String
Parameter Sets: Theme
Aliases:
Accepted values: Dark, Light

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

## UTDATA

### Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo

## ANTECKNINGAR

De sträng värden som används för att definiera färgen och formatet måste matcha det reguljära uttrycket `^\[*[0-9;]*?m{1}` .

## RELATERADE LÄNKAR

[Get-MarkdownOption](Get-MarkdownOption.md)

[ConvertFrom – markdown](ConvertFrom-Markdown.md)

[Visa markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)
