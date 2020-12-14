---
external help file: Microsoft.PowerShell.Archive-help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Archive
ms.date: 07/17/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.archive/expand-archive?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Expand-Archive
ms.openlocfilehash: a4cf8970156f524578f7c9747aef1ffbf9f3eb58
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710260"
---
# Expand-Archive

## SAMMANFATTNING
Extraherar filer från en angiven arkivfil (zippad) fil.

## SYNTAX

### Sökväg (standard)

```
Expand-Archive [-Path] <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

### LiteralPath

```
Expand-Archive -LiteralPath <String> [[-DestinationPath] <String>] [-Force] [-PassThru] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

`Expand-Archive`Cmdleten extraherar filer från en angiven zippad arkivfil till en angiven målmapp. En arkivfil gör att flera filer kan paketeras och eventuellt komprimeras till en enda zippad fil för enklare distribution och lagring.

## EXEMPEL

### Exempel 1: extrahera innehållet i ett arkiv

I det här exemplet extraheras innehållet i en befintlig arkivfil till den mapp som anges av parametern **DestinationPath** .

```powershell
Expand-Archive -LiteralPath 'C:\Archives\Draft[v1].Zip' -DestinationPath C:\Reference
```

I det här exemplet används parametern **LiteralPath** eftersom fil namnet innehåller tecken som kan tolkas som jokertecken.

### Exempel 2: extrahera innehållet i ett arkiv i den aktuella mappen

I det här exemplet extraheras innehållet i en befintlig arkivfil i den aktuella mappen till den mapp som anges av parametern **DestinationPath** .

```powershell
Expand-Archive -Path Draftv2.Zip -DestinationPath C:\Reference
```

## PARAMETRAR

### – DestinationPath

Som standard `Expand-Archive` skapar en mapp på den aktuella platsen som är samma namn som zip-filen. Parametern låter dig ange sökvägen till en annan mapp. Målmappen skapas om den inte finns.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases:

Required: False
Position: 1
Default value: A folder in the current location
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse.

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

Anger sökvägen till en Arkiv fil. Till skillnad från parametern **Path** används värdet för **LiteralPath** exakt som det har angetts. Jokertecken stöds inte. Om sökvägen innehåller escape-tecken, omger du varje escape-tecken inom enkla citat tecken för att instruera PowerShell att inte tolka några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: LiteralPath
Aliases: PSPath

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Gör att cmdleten skickar en lista med filerna expanderade från arkivet.

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

### -Path

Anger sökvägen till Arkiv filen.

```yaml
Type: System.String
Parameter Sets: Path
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

### System. String

Du kan skicka vidare en sträng som innehåller en sökväg till en befintlig arkivfil.

## UTDATA

### System. IO. FileSystemInfo

När `-PassThru` parametern används, matar cmdleten ut en lista över filer som har expanderats från arkivet.

## ANTECKNINGAR

[Zip-filspecifikationen](https://pkware.cachefly.net/webdocs/casestudies/APPNOTE.TXT) anger inte ett standardiserat sätt för kodnings fil namn som innehåller icke-ASCII-tecken. Cmdlet: en `Compress-Archive` använder UTF-8-kodning. Andra ZIP-arkiv verktyg kan använda ett annat kodnings schema. När filer extraheras med fil namn som inte lagras med UTF-8-kodning, `Expand-Archive` används det råa värde som finns i arkivet. Detta kan resultera i ett fil namn som skiljer sig från käll fil namnet som lagras i arkivet.

## RELATERADE LÄNKAR

[Komprimera – arkivera](compress-archive.md)
