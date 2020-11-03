---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/import-alias?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Import-Alias
ms.openlocfilehash: 50bc53d284fada31cf01b0504d89128eeb1710e2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264321"
---
# Import-Alias

## SAMMANFATTNING
Importerar en aliasresurspost från en fil.

## SYNTAX

### ByPath (standard)

```
Import-Alias [-Path] <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### ByLiteralPath

```
Import-Alias -LiteralPath <String> [-Scope <String>] [-PassThru] [-Force] [-WhatIf] [-Confirm]
 [<CommonParameters>]
```

## BESKRIVNING

`Import-Alias`Cmdleten importerar en lista med alias från en fil.

Från och med Windows PowerShell 3,0, som en säkerhetsfunktion, `Import-Alias` skriver inte befintliga alias över som standard.
Om du vill skriva över ett befintligt alias, när du har bevarat att innehållet i Ali Aset är säkert, använder du parametern **Force** .

## EXEMPEL

### Exempel 1: importera alias från en fil

```powershell
Import-Alias test.txt
```

Det här kommandot importerar Ali Aset information från en fil med namnet test.txt.

## PARAMETRAR

### -Force

Tillåter att cmdleten importerar ett alias som redan har definierats eller är skrivskyddat.
Du kan använda följande kommando för att visa information om de för närvarande definierade aliasen:

`Get-Alias | Select-Object Name, Options`

Om motsvarande alias är skrivskyddat visas det i värdet för egenskapen **Options** .

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

Anger sökvägen till en fil som innehåller information om exporterat alias.
Till skillnad från parametern **Path** används värdet för parametern **LiteralPath** exakt som det har angetts.
Inga tecken tolkas som jokertecken.
Om sökvägen innehåller escape-tecken omger du den med enkla citat tecken.
Enkla citat tecken säger att PowerShell inte tolkar några tecken som escape-sekvenser.

```yaml
Type: System.String
Parameter Sets: ByLiteralPath
Aliases: PSPath, LP

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

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

Anger sökvägen till en fil som innehåller information om exporterat alias.
Jokertecken tillåts, men de måste matcha ett enda namn.

```yaml
Type: System.String
Parameter Sets: ByPath
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### – Omfattning

Anger omfattningen som aliasen importeras till.
De acceptabla värdena för den här parametern är:

- Global
- Lokal
- Skript
- Ett tal i förhållande till det aktuella omfånget (0 till antalet omfattningar, där 0 är det aktuella omfånget och 1 är överordnat)

Standardvärdet är Local.
Mer information finns i about_Scopes.

```yaml
Type: System.String
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

Visar vad som skulle hända om cmdleten kördes.
Cmdleten körs inte.

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

Du kan skicka vidare en sträng som innehåller en sökväg till `Import-Alias` .

## UTDATA

### Ingen eller system. Management. Automation. AliasInfo

När du använder parametern **Passthru** `Import-Alias` returneras ett objekt av **system. Management. Automation. AliasInfo** som representerar aliaset.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Exportera-alias](Export-Alias.md)

[Get-alias](Get-Alias.md)

[Nytt-alias](New-Alias.md)

[Set-alias](Set-Alias.md)

