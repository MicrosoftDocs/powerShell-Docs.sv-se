---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 08/23/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/show-markdown?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Show-Markdown
ms.openlocfilehash: d14e6332a2da5c86c4f8ada0d110c64e080437e7
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709744"
---
# Show-Markdown

## SAMMANFATTNING
Visar en MARKDOWN-fil eller-sträng i-konsolen på ett användarvänligt sätt med VT100 escape-sekvenser eller i en webbläsare med HTML.

## SYNTAX

### Sökväg (standard)

```
Show-Markdown [-Path] <String[]> [-UseBrowser] [<CommonParameters>]
```

### InputObject

```
Show-Markdown -InputObject <PSObject> [-UseBrowser] [<CommonParameters>]
```

### LiteralPath

```
Show-Markdown -LiteralPath <String[]> [-UseBrowser] [<CommonParameters>]
```

## BESKRIVNING

`Show-Markdown`Cmdleten används för att rendera markdown i ett läsligt format, antingen i en terminal eller i en webbläsare.

`Show-Markdown` kan returnera en sträng som innehåller de VT100 escape-sekvenser som terminalen återger (om det stöder VT100 escape-sekvenser). Detta används främst för att Visa markdown-filer i en Terminal. Du kan också hämta den här strängen via `ConvertFrom-Markdown` genom att ange parametern **AsVT100EncodedString** .

`Show-Markdown` har också möjlighet att öppna en webbläsare och visa en renderad version av markdown. Den återger markdown genom att omvandla den till HTML och öppna HTML-filen i din standard webbläsare.

Du kan ändra hur `Show-Markdown` renderar markdown i en Terminal med hjälp av `Set-MarkdownOption` .

Denna cmdlet introducerades i PowerShell 6,1.

## EXEMPEL

### Exempel 1: enkelt exempel som anger en sökväg

```powershell
Show-Markdown -Path ./README.md
```

### Exempel 2: enkelt exempel som anger en sträng

```powershell
@"
# Show-Markdown

## Markdown

You can now interact with Markdown via PowerShell!

*stars*
__underlines__
"@ | Show-Markdown
```

### Exempel 2: öppna markdown i en webbläsare

```powershell
Show-Markdown -Path ./README.md -UseBrowser
```

## PARAMETRAR

### – InputObject

En markdown-sträng som ska visas i terminalen. Om du inte skickar i ett format som stöds `Show-Markdown` genererar ett fel.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: InputObject
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -LiteralPath

Anger sökvägen till en MARKDOWN-fil. Till skillnad från parametern Path används värdet för LiteralPath exakt som det har angetts. Inga tecken tolkas som jokertecken. Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken. Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String[]
Parameter Sets: LiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### -Path

Anger sökvägen till en MARKDOWN-fil som ska renderas.

```yaml
Type: System.String[]
Parameter Sets: Path
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### -UseBrowser

Kompilerar markdown-ingången som HTML och öppnar den i din standard webbläsare.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: False
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

### System.String[]

## UTDATA

### System. String

## ANTECKNINGAR

## RELATERADE LÄNKAR

[ConvertFrom – markdown](ConvertFrom-Markdown.md)

