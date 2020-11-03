---
external help file: Microsoft.PowerShell.PSReadLine2.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: PSReadLine
ms.date: 12/07/2018
online version: https://docs.microsoft.com/powershell/module/psreadline/set-psreadlinekeyhandler?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-PSReadLineKeyHandler
ms.openlocfilehash: 7794fc8814364d3ee62b0dece787aa0213dc4ff3
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265748"
---
# Set-PSReadLineKeyHandler

## SAMMANFATTNING
Binder nycklar till användardefinierade eller PSReadLine funktioner för nyckel hanterare.

## SYNTAX

### Script block

```
Set-PSReadLineKeyHandler [-ScriptBlock] <ScriptBlock> [-BriefDescription <String>]
 [-Description <String>] [-Chord] <String[]> [-ViMode <ViMode>] [<CommonParameters>]
```

### Funktion

```
Set-PSReadLineKeyHandler [-Chord] <String[]> [-ViMode <ViMode>] [-Function] <String>
 [<CommonParameters>]
```

## BESKRIVNING

`Set-PSReadLineKeyHandler`Cmdleten anpassar resultatet när en nyckel eller en sekvens av nycklar trycks ned. Med användardefinierade nyckel bindningar kan du göra nästan vad som möjligt i ett PowerShell-skript.

## EXEMPEL

### Exempel 1: bind piltangenten till en funktion

Det här kommandot binder upp piltangenten till funktionen **HistorySearchBackward** . Den här funktionen söker igenom kommando historiken för kommando rader som börjar med det aktuella innehållet på kommando raden.

```powershell
Set-PSReadLineKeyHandler -Chord UpArrow -Function HistorySearchBackward
```

### Exempel 2: bind en nyckel till ett skript block

Det här exemplet visar hur du kan använda en enskild nyckel för att köra ett kommando. Kommandot binder nyckeln `Ctrl+B` till ett skript block som rensar raden, infogar ordet "Build" och accepterar sedan raden.

```powershell
Set-PSReadLineKeyHandler -Chord Ctrl+B -ScriptBlock {
    [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
    [Microsoft.PowerShell.PSConsoleReadLine]::Insert('build')
    [Microsoft.PowerShell.PSConsoleReadLine]::AcceptLine()
}
```

## PARAMETRAR

### -BriefDescription

En kort beskrivning av nyckel bindningen. Den här beskrivningen visas av `Get-PSReadLineKeyHandler` cmdleten.

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Ackord

Nyckeln eller sekvensen av nycklar som ska bindas till en funktion eller ett skript block. Använd en enkel sträng för att ange en enskild bindning. Om bindningen är en följd av nycklar separerar du nycklarna med kommatecken, som i följande exempel:

`Ctrl+X,Ctrl+L`

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

### -Beskrivning

Anger en mer detaljerad beskrivning av den nyckel bindning som visas i utdata från `Get-PSReadLineKeyHandler` cmdleten.

```yaml
Type: System.String
Parameter Sets: ScriptBlock
Aliases: LongDescription

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Funktion

Anger namnet på en befintlig nyckel hanterare från PSReadLine. Med den här parametern kan du binda om befintliga nyckel bindningar eller binda en hanterare som för närvarande är obunden.

```yaml
Type: System.String
Parameter Sets: Function
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Script block

Anger ett skript Blocks värde som ska köras när ackord anges. PSReadLine skickar en eller två parametrar till det här skript blocket. Den första parametern är ett **ConsoleKeyInfo** -objekt som representerar tangenten nedtryckt. Det andra argumentet kan vara vilket objekt som helst, beroende på kontexten.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: ScriptBlock
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ViMode

Ange vilket läge som bindningen gäller för.

Giltiga värden är:

- Infogning
- Kommando

```yaml
Type: Microsoft.PowerShell.ViMode
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget

Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget

Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Get-PSReadLineKeyHandler](Get-PSReadLineKeyHandler.md)

[Remove-PSReadLineKeyHandler](Remove-PSReadLineKeyHandler.md)

[Get-PSReadLineOption](Get-PSReadLineOption.md)

[Set-PSReadLineOption](Set-PSReadLineOption.md)
