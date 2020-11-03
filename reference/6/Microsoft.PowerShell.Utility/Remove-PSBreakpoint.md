---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/remove-psbreakpoint?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Remove-PSBreakpoint
ms.openlocfilehash: 0d50fe8359f54b8aaac9482d162cc0865b1824fe
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93264435"
---
# Remove-PSBreakpoint

## SAMMANFATTNING
Tar bort Bryt punkter från den aktuella konsolen.

## SYNTAX

### Bryt punkt (standard)

```
Remove-PSBreakpoint [-Breakpoint] <Breakpoint[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Id

```
Remove-PSBreakpoint [-Id] <Int32[]> [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdlet: en **Remove-PSBreakpoint** tar bort en Bryt punkt.
Ange ett Bryt punkts objekt eller ett Bryt punkts-ID.

När du tar bort en Bryt punkt är objektet Bryt punkten inte längre tillgängligt eller fungerar inte längre.
Om du har sparat ett Bryt punkts objekt i en variabel, finns referensen fortfarande, men Bryt punkten fungerar inte.

**Remove-PSBreakpoint** är en av flera cmdletar utformade för fel sökning av PowerShell-skript.
Mer information om PowerShell-felsökaren finns i about_Debuggers.

## EXEMPEL

### Exempel 1: ta bort alla Bryt punkter

```
PS C:\> Get-PSBreakpoint | Remove-PSBreakpoint
```

Det här kommandot tar bort alla Bryt punkter i den aktuella konsolen.

### Exempel 2: ta bort en angiven Bryt punkt

```
PS C:\> $B = Set-PSBreakpoint -Script "sample.ps1" -Variable "Name"
PS C:\> $B | Remove-PSBreakpoint
```

Det här kommandot tar bort en Bryt punkt.

Det första kommandot använder cmdleten Set-PSBreakpoint för att skapa en Bryt punkt för variabeln Name i Sample.ps1-skriptet.
Sedan sparas objektet Bryt punkt i variabeln $B.

Det andra kommandot använder cmdleten **Remove-PSBreakpoint** för att ta bort den nya Bryt punkten.
En pipeline-operator (|) används för att skicka Bryt punkts objektet i $B-variabeln till cmdleten **Remove-PSBreakpoint** .

Om du kör skriptet körs det som ett resultat av det här kommandot utan att stoppa.
Dessutom returnerar cmdleten **Get-PSBreakpoint** inte den här Bryt punkten.

### Exempel 3: ta bort en Bryt punkt per ID

```
PS C:\> Remove-PSBreakpoint -Id 2
```

Det här kommandot tar bort Bryt punkten med Bryt punkts-ID 2.

### Exempel 4: Använd en funktion för att ta bort alla Bryt punkter

```
PS C:\> function del-psb { get-psbreakpoint | remove-psbreakpoint }
```

Den här enkla funktionen tar bort alla Bryt punkter i den aktuella konsolen.
Den använder Get-PSBreakpoint-cmdlet för att hämta Bryt punkterna.
Sedan använder den en pipeline-operator (|) för att skicka Bryt punkterna till cmdleten **Remove-PSBreakpoint** , som tar bort dem.

Därför kan du skriva `del-psb` i stället för kommandot längre.

Om du vill spara funktionen lägger du till den i din PowerShell-profil.

## PARAMETRAR

### – Bryt punkt
Anger de Bryt punkter som ska tas bort.
Ange en variabel som innehåller Bryt punkts objekt eller ett kommando som hämtar Bryt punkts objekt, till exempel ett **Get-PSBreakpoint** -kommando.
Du kan också skicka Bryt punkts objekt till **Remove-PSBreakpoint**.

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
Anger Bryt punkts-ID: n för vilka denna cmdlet tar bort Bryt punkter.

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
Du kan skicka Bryt punkts objekt till **Remove-PSBreakpoint**.

## UTDATA

### Inget
Cmdleten genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Disable-PSBreakpoint](Disable-PSBreakpoint.md)

[Aktivera – PSBreakpoint](Enable-PSBreakpoint.md)

[Get-PSBreakpoint](Get-PSBreakpoint.md)

[Get-PSCallStack](Get-PSCallStack.md)

[Set-PSBreakpoint](Set-PSBreakpoint.md)
