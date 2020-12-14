---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 05/15/2019
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/get-psbreakpoint?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-PSBreakpoint
ms.openlocfilehash: 78691b806fe68aaa8d9e502d28e6f3967867f95b
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94708634"
---
# Get-PSBreakpoint

## SAMMANFATTNING
Hämtar de Bryt punkter som har angetts i den aktuella sessionen.

## SYNTAX

### Skript (standard)

```
Get-PSBreakpoint [-Script <String[]>] [<CommonParameters>]
```

### Variabel

```
Get-PSBreakpoint [-Script <String[]>] -Variable <String[]> [<CommonParameters>]
```

### Kommando

```
Get-PSBreakpoint [-Script <String[]>] -Command <String[]> [<CommonParameters>]
```

### Typ

```
Get-PSBreakpoint [-Script <String[]>] [-Type] <BreakpointType[]> [<CommonParameters>]
```

### Id

```
Get-PSBreakpoint [-Id] <Int32[]> [<CommonParameters>]
```

## BESKRIVNING

**Get-PSBreakPoint** -cmdlet: en hämtar de Bryt punkter som angetts i den aktuella sessionen.
Du kan använda cmdlet-parametrarna för att hämta vissa Bryt punkter.

En Bryt punkt är en punkt i ett kommando eller skript där körningen stoppas tillfälligt så att du kan granska instruktionerna.
**Get-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript och-kommandon. Mer information om PowerShell-felsökaren finns i about_Debuggers.

## EXEMPEL

### Exempel 1: Hämta alla Bryt punkter för alla skript och funktioner

```
PS C:\> Get-PSBreakpoint
```

Det här kommandot hämtar alla Bryt punkter som anges för alla skript och funktioner i den aktuella sessionen.

### Exempel 2: Hämta Bryt punkter efter ID

```
PS C:\> Get-PSBreakpoint -Id 2
Function   :
IncrementAction     :
Enabled    :
TrueHitCount   : 0
Id         : 2
Script     : C:\ps-test\sample.ps1
ScriptName : C:\ps-test\sample.ps1
```

Det här kommandot hämtar Bryt punkten med Bryt punkts-ID 2.

### Exempel 3: Skicka ett ID till Get-PSBreakpoint

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Command "Increment"
PS C:\> $B.Id | Get-PSBreakpoint
```

Kommandona visar hur du får en Bryt punkt genom att skicka ett Bryt punkts-ID till **Get-PSBreakpoint**.

Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för funktionen Increment i Sample.ps1 skriptet. Det sparar objektet Bryt punkt i $B variabeln.

Det andra kommandot använder punkt operatorn (.) för att hämta egenskapen ID för objektet Bryt punkt i $B variabeln. Den använder en pipeline-operator (|) för att skicka ID: t till **Get-PSBreakpoint** -cmdlet: en.

Resultatet blir att **Get-PSBreakpoint** hämtar Bryt punkten med angivet ID.

### Exempel 4: Hämta Bryt punkter i angivna skriptfiler

```
PS C:\> Get-PSBreakpoint -Script "Sample.ps1, SupportScript.ps1"
```

Det här kommandot hämtar alla Bryt punkter i Sample.ps1 och SupportScript.ps1 filer.

Detta kommando hämtar inte andra Bryt punkter som kan anges i andra skript eller i-funktioner i sessionen.

### Exempel 5: Hämta Bryt punkter i angivna cmdlets

```
PS C:\> Get-PSBreakpoint -Command "Read-Host, Write-Host" -Script "Sample.ps1"
```

Det här kommandot hämtar alla kommando Bryt punkter som är inställda på Read-Host eller Write-Host kommandon i Sample.ps1-filen.

### Exempel 6: Hämta kommando Bryt punkter i en angiven fil

```
PS C:\> Get-PSBreakpoint -Type Command -Script "Sample.ps1"
```

Det här kommandot hämtar alla kommando Bryt punkter i Sample.ps1s filen.

### Exempel 7: Hämta Bryt punkter per variabel

```
PS C:\> Get-PSBreakpoint -Variable "Index, Swap"
```

Detta kommando hämtar Bryt punkter som har angetts för $Index och $Swap variabler i den aktuella sessionen.

### Exempel 8: Hämta alla rad-och variabel Bryt punkter i en fil

```
PS C:\> Get-PSBreakpoint -Type Line, Variable -Script "Sample.ps1"
```

Det här kommandot hämtar alla rad-och variabel Bryt punkter i Sample.ps1-skriptet.

## PARAMETRAR

### -Kommando

Anger en matris med kommando Bryt punkter som anges för de angivna kommando namnen.
Ange kommando namnen, till exempel namnet på en cmdlet eller funktion.

```yaml
Type: System.String[]
Parameter Sets: Command
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ID

Anger de Bryt punkts-ID: n som denna cmdlet hämtar.
Ange ID i en kommaavgränsad lista.
Du kan också skicka Bryt punkts-ID: n till **Get-PSBreakpoint**.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Skript

Anger en matris med skript som innehåller Bryt punkterna.
Ange sökvägen (valfritt) och namn på en eller flera skriptfiler.
Om du utelämnar sökvägen är standard platsen den aktuella katalogen.

```yaml
Type: System.String[]
Parameter Sets: Script, Variable, Command, Type
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Typ

Anger en matris med Bryt punkts typer som denna cmdlet hämtar.
Ange en eller flera typer.
De acceptabla värdena för den här parametern är:

- Linje
- Kommando
- Variabel

Du kan också komma åt Bryt punkts typer för att **få-PSBreakPoint**.

```yaml
Type: Microsoft.PowerShell.Commands.BreakpointType[]
Parameter Sets: Type
Aliases:
Accepted values: Line, Variable, Command

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### – Variabel

Anger en matris med variabla Bryt punkter som anges för de angivna variabel namnen.
Ange variabel namnen utan dollar tecken.

```yaml
Type: System.String[]
Parameter Sets: Variable
Aliases:

Required: True
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i about_CommonParameters ( https://go.microsoft.com/fwlink/?LinkID=113216) .

## INDATA

### System. Int32, Microsoft. PowerShell. commands. BreakpointType

Du kan skicka Bryt punkts-ID: n och Bryt punkts typer för att **få-PSBreakPoint**

## UTDATA

### System. Management. Automation. Bryt punkt

**Get-PSBreakPoint** returnerar objekt som representerar Bryt punkterna i sessionen.

## ANTECKNINGAR

* Du kan använda **Get-PSBreakpoint** eller dess alias, "GBP".

## RELATERADE LÄNKAR

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Aktivera – PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)

