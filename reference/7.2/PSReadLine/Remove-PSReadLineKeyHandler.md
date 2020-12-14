---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/remove-psreadlinekeyhandler?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSReadLineKeyHandler
ms.openlocfilehash: d280eba2e717ccfb0b896d62f42079390d1db848
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94709031"
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

### Inga

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inga

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)

[Set-PSReadLineKeyHandler](Set-PSReadLineKeyHandler.md)

