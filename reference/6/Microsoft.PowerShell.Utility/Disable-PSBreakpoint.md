---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/disable-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Disable-PSBreakpoint
ms.openlocfilehash: 66ef0cec2bfdb1aa70b97001830811f68c68b911
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93267122"
---
# Disable-PSBreakpoint

## SAMMANFATTNING
Inaktiverar Bryt punkterna i den aktuella konsolen.

## SYNTAX

### Bryt punkt (standard)

```
Disable-PSBreakpoint [-PassThru] [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Disable-PSBreakpoint [-PassThru] [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdlet: en **disable-PSBreakpoint** inaktiverar Bryt punkter, vilket säkerställer att de inte är identiska när skriptet körs.
Du kan använda den för att inaktivera alla Bryt punkter, eller så kan du ange Bryt punkter genom att skicka Bryt punkts objekt eller Bryt punkts-ID: n.

Den här cmdleten ändrar tekniskt värdet för egenskapen Enabled för ett Bryt punkts objekt till falskt.
Använd Enable-PSBreakpoint-cmdleten om du vill återaktivera en Bryt punkt.
Bryt punkter aktive ras som standard när du skapar dem med hjälp av Set-PSBreakpoint-cmdleten.

En Bryt punkt är en punkt i ett skript där körningen stoppas tillfälligt så att du kan granska instruktionerna i skriptet.
**Disable-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript.
Mer information om PowerShell-felsökaren finns i about_Debuggers.

## EXEMPEL

### Exempel 1: Ange en Bryt punkt och inaktivera den

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "name"
PS C:\> $B | Disable-PSBreakpoint
```

Dessa kommandon inaktiverar en nyligen skapad Bryt punkt.

Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för variabeln *Name* i Sample.ps1-skriptet.
Sedan sparas objektet Bryt punkt i variabeln $B.

Det andra kommandot använder cmdleten **disable-PSBreakpoint** för att inaktivera den nya Bryt punkten.
En pipeline-operator (|) används för att skicka Bryt punkts objektet i $B till cmdleten **disable-PSBreakpoint** .

Resultatet av det här kommandot är att värdet för egenskapen Enabled för objektet Bryt punkt i $B är falskt.

### Exempel 2: inaktivera en Bryt punkt

```
PS C:\> Disable-PSBreakpoint -Id 0
```

Detta kommando inaktiverar Bryt punkten med Bryt punkts-ID 0.

### Exempel 3: skapa en inaktive rad Bryt punkt

```
PS C:\> Disable-PSBreakpoint -Breakpoint ($B = Set-PSBreakpoint -Script "sample.ps1" -Line 5)
PS C:\> $B
```

Det här kommandot skapar en ny Bryt punkt som är inaktive rad tills du aktiverar den.

Den använder cmdleten **disable-PSBreakpoint** för att inaktivera Bryt punkten.
Värdet för parametern *Bryt punkt* är ett Set-PSBreakpoint-kommando som anger en ny Bryt punkt, genererar ett Bryt punkts objekt och sparar objektet i $B-variabeln.

Cmdlet-parametrar som tar objekt som värden kan acceptera en variabel som innehåller objektet eller ett kommando som hämtar eller genererar objektet.
I det här fallet, eftersom **set-PSBreakpoint** genererar ett Bryt punkts objekt, kan det användas som värde för *Bryt punkts* parametern.

Det andra kommandot visar objektet Bryt punkt i värdet för variabeln $B.

### Exempel 4: inaktivera alla Bryt punkter i den aktuella konsolen

```
PS C:\> Get-PSBreakpoint | Disable-PSBreakpoint
```

Detta kommando inaktiverar alla Bryt punkter i den aktuella konsolen.
Du kan förkorta det här kommandot som: "GBP | dbp".

## PARAMETRAR

### – Bryt punkt

Anger Bryt punkterna som ska inaktive ras.
Ange en variabel som innehåller Bryt punkts objekt eller ett kommando som hämtar Bryt punkts objekt, till exempel ett Get-PSBreakpoint-kommando.
Du kan också skicka Bryt punkts objekt till cmdlet: en **disable-PSBreakpoint** .

```yaml
Type: System.Management.Automation.Breakpoint[]
Parameter Sets: Breakpoint
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ID

Inaktiverar Bryt punkterna med de angivna Bryt punkts-ID: na.
Ange de ID: n eller en variabel som innehåller ID: n.
Du kan inte skicka pipe-ID: n för att **inaktivera-PSBreakpoint**.

```yaml
Type: System.Int32[]
Parameter Sets: Id
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar de aktiverade Bryt punkterna.
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

### System. Management. Automation. Bryt punkt

Du kan skicka ett Bryt punkts objekt till **disable-PSBreakpoint**.

## UTDATA

### Ingen eller system. Management. Automation. Bryt punkt

När du använder parametern *Passthru* returnerar **disable-PSBreakpoint** ett objekt som representerar den inaktiverade Bryt punkten.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Aktivera – PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Remove-PSBreakpoint](Remove-PSBreakpoint.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
