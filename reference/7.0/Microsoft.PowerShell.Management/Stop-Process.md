---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/stop-process?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Stop-Process
ms.openlocfilehash: f5f5b8c912664c96762890633297f6325968f3fa
ms.sourcegitcommit: 11abf355ac545531c2b04217a08ebe6be609c0bb
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/18/2020
ms.locfileid: "93269541"
---
# Stop-Process

## SAMMANFATTNING
Stoppar en eller flera processer som körs.

## SYNTAX

### ID (standard)

```
Stop-Process [-Id] <Int32[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### Name

```
Stop-Process -Name <String[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

### InputObject

```
Stop-Process [-InputObject] <Process[]> [-PassThru] [-Force] [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **Stop process** stoppar en eller flera processer som körs.
Du kan ange en process efter process namn eller process-ID (PID) eller skicka ett process objekt till **stopp processen**.
**Stop-processen** fungerar bara på processer som körs på den lokala datorn.

I Windows Vista och senare versioner av Windows operativ system, för att stoppa en process som inte ägs av den aktuella användaren, måste du starta PowerShell med alternativet Kör som administratör.
Du behöver inte heller bekräfta en bekräftelse om du inte anger parametern *Bekräfta* .

## EXEMPEL

### Exempel 1: stoppa alla instanser av en process

```
PS C:\> Stop-Process -Name "notepad"
```

Det här kommandot stoppar alla instanser av anteckningar-processen på datorn.
Varje instans av anteckningar körs i sin egen process.
Parametern *Name* används för att ange processer som har samma namn.
Om du vill använda *ID-* parametern för att stoppa samma processer måste du ange process-ID: n för varje instans av anteckningar.

### Exempel 2: stoppa en speciell instans av en process

```
PS C:\> Stop-Process -Id 3952 -Confirm -PassThru
Confirm
Are you sure you want to perform this action?
Performing operation "Stop-Process" on Target "notepad (3952)".
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help
(default is "Y"):y
Handles  NPM(K)    PM(K)      WS(K) VM(M)   CPU(s)     Id ProcessName
-------  ------    -----      ----- -----   ------     -- -----------
41       2      996       3212    31            3952 notepad
```

Det här kommandot stoppar en viss instans av anteckningar-processen.
Den använder process-ID: t 3952 för att identifiera processen.
Parametern *Confirm* instruerar PowerShell att fråga dig innan processen stoppas.
Eftersom meddelandet innehåller process namnet förutom ID: t, är det här bästa praxis.
Parametern *Passthru* skickar processobjektet till Formatter för visning.
Utan den här parametern visas ingen visning efter ett kommando för att **stoppa processen** .

### Exempel 3: stoppa en process och identifiera att den har stoppats

```
PS C:\> calc
PS C:\> $p = Get-Process -Name "calc"
PS C:\> Stop-Process -InputObject $p
PS C:\> Get-Process | Where-Object {$_.HasExited}
```

Den här serien med kommandon startar och stoppar Calc-processen och identifierar sedan processer som har stoppats.

Det första kommandot startar en variant av kalkylatorn.

Det andra kommandot använder **Get-process** hämtar ett objekt som representerar Calc-processen och lagrar det sedan i variabeln $p.

Det tredje kommandot stoppar Calc-processen.
Parametern *InputObject* används för att skicka objektet till **Stop-process**.

Det sista kommandot hämtar alla processer på datorn som kördes men som nu har stoppats.
Den använder **Get-process** för att hämta alla processer på datorn.
Pipeline-operatorn (|) skickar resultatet till Where-Object-cmdleten, som väljer de där värdet för egenskapen **HasExited** är $true.
**HasExited** är bara en egenskap för process objekt.
Om du vill söka efter alla egenskaper skriver du `Get-Process | Get-Member` .

### Exempel 4: stoppa en process som inte ägs av den aktuella användaren

```
PS C:\> Get-Process -Name "lsass" | Stop-Process

Stop-Process : Cannot stop process 'lsass (596)' because of the following error: Access is denied
At line:1 char:34
+ Get-Process -Name "lsass" | Stop-Process <<<<

[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process

Warning!
Are you sure you want to perform this action?
Performing operation 'Stop-Process' on Target 'lsass(596)'`
[Y] Yes  [A] Yes to All  [N] No  [L] No to All  [S] Suspend  [?] Help (default is "Y"):
[ADMIN]: PS C:\> Get-Process -Name "lsass" | Stop-Process -Force
[ADMIN]: PS C:\>
```

De här kommandona visar effekterna av att använda *tvång* för att stoppa en process som inte ägs av användaren.

Det första kommandot använder **Get-process** för att hämta lsass-processen.
En pipeline-operator skickar processen till **stopp-processen** för att stoppa den.
Som visas i exemplet på utdata Miss lyckas det första kommandot med ett meddelande om nekad åtkomst, eftersom den här processen endast kan stoppas av en medlem i administratörs gruppen på datorn.

När PowerShell öppnas med alternativet Kör som administratör och kommandot upprepas, uppmanas du i PowerShell att bekräfta.

Det andra kommandot anger *tvinga* att utelämna prompten.
Därför stoppas processen utan bekräftelse.

## PARAMETRAR

### -Force

Stoppar de angivna processerna utan att uppmanas att bekräfta.
Som standard uppmanas du att **Bekräfta genom att** bekräfta innan du stoppar en process som inte ägs av den aktuella användaren.

Om du vill hitta ägaren till en process använder du `Get-CimInstance` cmdleten för att hämta ett **Win32_Process** -objekt som representerar processen och använder sedan **GetOwner** -metoden för objektet.

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

### -ID

Anger process-ID: n för de processer som ska stoppas.
Använd kommatecken för att avgränsa ID: n för att ange flera ID: n.
Om du vill hitta ett process-ID skriver du `Get-Process` .

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

### – InputObject

Anger de process objekt som ska stoppas.
Ange en variabel som innehåller objekten eller Skriv ett kommando eller uttryck som hämtar objekten.

```yaml
Type: System.Diagnostics.Process[]
Parameter Sets: InputObject
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -Name

Anger process namnen för de processer som ska stoppas.
Du kan skriva flera process namn, avgränsade med kommatecken eller använda jokertecken.

```yaml
Type: System.String[]
Parameter Sets: Name
Aliases: ProcessName

Required: True
Position: Named
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: True
```

### – PassThru

Returnerar ett objekt som representerar processen.
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

### System. Diagnostics. process

Du kan skicka vidare ett process objekt till denna cmdlet.

## UTDATA

### Ingen, system. Diagnostics. process

Denna cmdlet returnerar ett **system. Diagnostics. process** -objekt som representerar den stoppade processen, om du anger parametern *Passthru* .
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Du kan också referera till **stopp processen** med hjälp av inbyggda alias, **Kill** och **SPPs**. Mer information finns i about_Aliases.

  Du kan också använda egenskaperna och metoderna för **Win32_Process** -objektet Windows Management Instrumentation (WMI) i Windows PowerShell.
Mer information finns i `Get-CimInstance` och WMI SDK.

* När du stoppar processer kan du tänka på att processen som stoppar processen kan stoppa processer och tjänster som är beroende av processen.
I ett extrema fall kan en process stoppa Windows.

## RELATERADE LÄNKAR

[Fel sökning – process](Debug-Process.md)

[Hämta process](Get-Process.md)

[Start process](Start-Process.md)

[Stoppa – process](Stop-Process.md)

[Vänta-process](Wait-Process.md)
