---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 09/21/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-clipboard?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Clipboard
ms.openlocfilehash: 2885b2624f8334e8699e0baea5fc41b3f025fe2a
ms.sourcegitcommit: d757d64ea8c8af4d92596e8fbe15f2f40d48d3ac
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/22/2020
ms.locfileid: "93269559"
---
# Get-Clipboard

## SAMMANFATTNING
Hämtar det aktuella urklipps posten i Windows.

## SYNTAX

```
Get-Clipboard [-Format <ClipboardFormat>] [-TextFormatType <TextDataFormat>] [-Raw] [<CommonParameters>]
```

## BESKRIVNING

`Get-Clipboard`Cmdleten hämtar det aktuella urklipps posten i Windows. Flera rader med text returneras som en sträng mat ris som liknar `Get-Content` .

## EXEMPEL

### Exempel 1: hämta innehållet i Urklipp och visa det på kommando raden

I det här exemplet har vi klickat på en bild i en webbläsare och valde **kopierings** åtgärden. Följande kommando visar länken, som en URL, för den bild som lagras i Urklipp.

```powershell
Get-Clipboard
```

```Output
https://en.wikipedia.org/wiki/PowerShell
```

### Exempel 2: hämta innehållet i Urklipp i ett särskilt format

I det här exemplet kopierade filer till Urklipp i Windows Explorerby och trycker på <kbd>CTRL-C</kbd>. Med hjälp av följande kommando kan du komma åt innehållet i Urklipp som en lista över filer:

```powershell
Get-Clipboard -Format FileDropList
```

```Output
    Directory: C:\Git\PS-Docs\PowerShell-Docs\wmf

Mode                LastWriteTime         Length Name
----                -------------         ------ ----
-a----         5/7/2019   1:11 PM          10010 TOC.yml
-a----       11/18/2016  10:10 AM             53 md.style
-a----         5/6/2019   9:32 AM           4177 overview.md
-a----        6/28/2018   2:28 PM            345 README.md
```

## PARAMETRAR

### – Format

Anger urklippets typ eller format. De acceptabla värdena för den här parametern är:

- Text
- FileDropList
- Bild
- Ljud

```yaml
Type: Microsoft.PowerShell.Commands.ClipboardFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, FileDropList, Image, Audio

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – RAW

Hämtar hela innehållet i Urklipp. Flerradig text returneras som en enskild Multiline-sträng i stället för en sträng mat ris.

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

### -TextFormatType

Anger typ av text data format för Urklipp. De acceptabla värdena för den här parametern är:

- Text
- UnicodeText
- RTF
- Html
- CommaSeparatedValue

```yaml
Type: System.Windows.Forms.TextDataFormat
Parameter Sets: (All)
Aliases:
Accepted values: Text, UnicodeText, Rtf, Html, CommaSeparatedValue

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

## UTDATA

### System. String, system. IO. FileInfo, system. IO. Stream, system. Drawing. image

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Ange Urklipp](Set-Clipboard.md)
