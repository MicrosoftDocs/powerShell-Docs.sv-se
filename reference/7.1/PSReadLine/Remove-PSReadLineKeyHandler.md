---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: a13677035581a081df51917bc6b82efec0ff2156
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273291"
---
# Remove-PSReadLineKeyHandler

## SAMMANFATTNING
Tar bort en nyckel bindning.

## SYNTAX

```
Remove-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

## BESKRIVNING

`Remove-PSReadLineKeyHandler`Cmdleten tar bort en angiven nyckel bindning.

## EXEMPEL

### Exempel 1: ta bort en bindning

```powershell
Remove-PSReadLineKeyHandler -Chord Ctrl+B
```

Det här kommandot tar bort bindningen från nyckel kombinationen eller ackord `Ctrl+B` . `Ctrl+B`Ackord skapas i `Set-PSReadLineKeyHandler` artikeln.

## PARAMETRAR

### – Ackord

Anger en matris med nycklar eller sekvenser med nycklar som ska tas bort. En enda bindning anges genom att använda en enda sträng. Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:

`Ctrl+x,Ctrl+l`

Den här parametern accepterar en sträng mat ris. Varje sträng är en separat bindning, inte en sekvens med nycklar för en enskild bindning.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases: Key

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Ange vilket läge som bindningen gäller för. Möjliga värden är: INSERT, kommando.

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:
Accepted values: Insert, Command

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](http://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)

