---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 01/30/2020
online version: https://docs.microsoft.com/powershell/module/Microsoft.PowerShell.Utility/Get-MarkdownOption?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-MarkdownOption
ms.openlocfilehash: 4fac43c411fd91575c7169baca3e2ea86bb64e18
ms.sourcegitcommit: 71173a89c4f05b5283ccd1e885a780773c13fa47
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/12/2021
ms.locfileid: "103196310"
---
# Get-MarkdownOption

## SAMMANFATTNING
Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen.

## SYNTAX

```
Get-MarkdownOption [<CommonParameters>]
```

## BESKRIVNING

Returnerar de aktuella färgerna och formaten som används för att återge markdown-innehåll i-konsolen. Strängarna som visas i utdata från den här cmdleten innehåller ANSI-Escape-koderna som används för att ändra färg och format på den markdown text som återges.

Mer information om markdown finns på [CommonMark](https://commonmark.org/) -webbplatsen.

## EXEMPEL

### Exempel 1 – Hämta aktuella färger och format

```powershell
Get-MarkdownOption
```

```Output
Header1         : [7m
Header2         : [4;93m
Header3         : [4;94m
Header4         : [4;95m
Header5         : [4;96m
Header6         : [4;97m
Code            : [48;2;155;155;155;38;2;30;30;30m
Link            : [4;38;5;117m
Image           : [33m
EmphasisBold    : [1m
EmphasisItalics : [36m
```

> [!NOTE]
> Sträng värdena som visas i utdata är de tecken som följer **Escape** -tecknet ( `[char]0x1B` ) för ANSI Escape-sekvensen. Mer information om hur ANSI Escape-koder fungerar finns i [ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code).

## PARAMETRAR

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

## UTDATA

### Microsoft. PowerShell. MarkdownRender. PSMarkdownOptionInfo

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Set-MarkdownOption](Set-MarkdownOption.md)

[ConvertFrom – markdown](ConvertFrom-Markdown.md)

[Visa markdown](Show-Markdown.md)

[ANSI_escape_code](https://en.wikipedia.org/wiki/ANSI_escape_code)

[CommonMark](https://commonmark.org/)

