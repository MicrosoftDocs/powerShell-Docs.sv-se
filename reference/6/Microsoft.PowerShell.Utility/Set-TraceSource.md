---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/set-tracesource?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Set-TraceSource
ms.openlocfilehash: e6acb18799646a2e238237d3879198e3a78e7f9a
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266727"
---
# Set-TraceSource

## SAMMANFATTNING
Konfigurerar, startar och stoppar en spårning av PowerShell-komponenter.

## SYNTAX

### optionsSet (standard)

```
Set-TraceSource [-Name] <String[]> [[-Option] <PSTraceSourceOptions>] [-ListenerOption <TraceOptions>]
 [-FilePath <String>] [-Force] [-Debugger] [-PSHost] [-PassThru] [<CommonParameters>]
```

### removeAllListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveListener <String[]>] [<CommonParameters>]
```

### removeFileListenersSet

```
Set-TraceSource [-Name] <String[]> [-RemoveFileListener <String[]>] [<CommonParameters>]
```

## BESKRIVNING

Cmdleten **set-TraceSource** konfigurerar, startar och stoppar en spårning av en PowerShell-komponent.
Du kan använda den för att ange vilka komponenter som ska spåras och var spårnings resultatet skickas.

## EXEMPEL

### Exempel 1: spåra ParameterBinding-komponenten

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -Option ExecutionFlow -PSHost -ListenerOption "ProcessId,TimeStamp"
```

Det här kommandot startar spårning för ParameterBinding-komponenten i PowerShell.
Parametern *Name* används för att ange spårnings källa, *alternativ* parametern för att välja ExecutionFlow spårnings händelser och parametern *PSHost* för att välja PowerShell-värdens lyssnare, som skickar utdata till-konsolen.
Parametern *ListenerOption* lägger till ProcessID-och timestamp-värden i prefixet spåra meddelande.

### Exempel 2: stoppa en spårning

```
PS C:\> Set-TraceSource -Name "ParameterBinding" -RemoveListener "Host"
```

Det här kommandot stoppar spårningen av ParameterBinding-komponenten i PowerShell.
Parametern *Name* används för att identifiera den komponent som spårades och *RemoveListener* -parametern för att identifiera spårnings lyssnaren.

## PARAMETRAR

### – Fel sökning

Anger att cmdleten skickar spårningsutdata till fel söknings programmet.
Du kan visa utdata i valfri fel sökare för användarläge eller kernelläge eller i Microsoft Visual Studio.
Den här parametern väljer också standard spårnings lyssnaren.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger en fil som denna cmdlet skickar spårningsutdata till.
Den här parametern väljer också lyssnaren för fil spårning.
Om du använder den här parametern för att starta spåret använder du parametern *RemoveFileListener* för att stoppa spårningen.

```yaml
Type: System.String
Parameter Sets: optionsSet
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Anger att cmdleten skriver över en skrivskyddad fil.
Använd med parametern *sökväg* .

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -ListenerOption

Anger valfria data till prefixet för varje spårnings meddelande i utdata.
De acceptabla värdena för den här parametern är:

- Inget
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Callstacken

Inget är standardvärdet.

Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem med citat tecken, till exempel "ProcessID, ThreadID".

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger vilka komponenter som spåras.
Ange namnet på spårnings källan för varje komponent.
Jokertecken är tillåtna.

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: True (ByPropertyName, ByValue)
Accept wildcard characters: True
```

### -Alternativ

Anger vilken typ av händelser som spåras.
De acceptabla värdena för den här parametern är:

- Inget
- Konstruktor
- Ta bort
- Finaliserare
- Metod
- Egenskap
- Delegeringar
- Händelser
- Undantag
- Låsa
- Fel
- Fel
- Varning
- Verbose
- WriteLine
- Data
- Omfång
- ExecutionFlow
- Assert
- Alla

All är standard.

Följande värden är kombinationer av andra värden:

- ExecutionFlow: (konstruktör, dispose, slut för ande, metod, ombud, händelser och omfång)
- Data: (konstruktor, dispose, slutförd, egenskap, utförlig och WriteLine)
- Fel: (fel och undantag).

Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem inom citat tecken, till exempel "konstruktor, dispose".

```yaml
Type: System.Management.Automation.PSTraceSourceOptions
Parameter Sets: optionsSet
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 1
Default value: None
Accept pipeline input: True (ByPropertyName)
Accept wildcard characters: False
```

### – PassThru

Returnerar ett objekt som representerar det objekt som du arbetar med.
Som standard genererar denna cmdlet inga utdata.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

ndicates att den här cmdleten skickar spårningsutdata till PowerShell-värden.
Den här parametern väljer också spårnings lyssnaren PSHost.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: optionsSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveFileListener

Stoppar spårningen genom att ta bort den lyssnare för fil spårning som är associerad med den angivna filen.
Ange sökvägen till och fil namnet på filen med spårnings utdatafilen.

```yaml
Type: System.String[]
Parameter Sets: removeFileListenersSet
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -RemoveListener

Stoppar spårningen genom att ta bort spårnings lyssnaren.

Använd följande värden med *RemoveListener* :

- Om du vill ta bort PSHost (konsol) skriver du `Host` .
- Om du vill ta bort fel sökare skriver du `Debug` .
- Om du vill ta bort alla spårnings lyssnare skriver du `*` .

Om du vill ta bort fil spårnings lyssnaren använder du parametern *RemoveFileListener* .

```yaml
Type: System.String[]
Parameter Sets: removeAllListenersSet
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

### System. String

Du kan skicka en sträng som innehåller ett namn till **set-TraceSource**.

## UTDATA

### Ingen eller system. Management. Automation. PSTraceSource

När du använder parametern *Passthru* genererar **set-TraceSource** ett **system. Management. Automation. PSTraceSource** -objekt som representerar spårningssessionen.
Annars genererar denna cmdlet inga utdata.

## ANTECKNINGAR

* Spårning är en metod som utvecklare använder för att felsöka och förfina program. När du spårar genererar programmet detaljerade meddelanden om varje steg i den interna bearbetningen.

  Cmdletarna för PowerShell-spårning är utformade för att hjälpa PowerShell-utvecklare, men de är tillgängliga för alla användare.
De låter dig övervaka nästan alla aspekter av funktionerna i PowerShell.

  En spårnings källa är en del av varje PowerShell-komponent som hanterar spårning och genererar spårnings meddelanden för komponenten.
Om du vill spåra en komponent identifierar du dess spårnings källa.

  En spårnings lyssnare tar emot utdata från spårningen och visar den för användaren.
Du kan välja att skicka spårnings data till en användar-eller kernelläge, till-konsolen, till en fil eller till en anpassad lyssnare som härletts från klassen **system. Diagnostics. TraceListener** .

* Om du vill starta en spårning använder du parametern *Name* för att ange en spårnings källa och *sökvägen* , *fel sökaren* eller *PSHost* -parametrarna för att ange en lyssnare (ett mål för utdata). Använd *alternativ* parametern för att bestämma vilka typer av händelser som spåras och parametern *ListenerOption* för att konfigurera spårningsutdata.
* Om du vill ändra konfigurationen för en spårning anger du ett **set-TraceSource-** kommando som du skulle starta en spårning. PowerShell känner av att spårnings källan redan spåras. Den stoppar spårningen, lägger till den nya konfigurationen och startar eller startar om spårningen.
* Om du vill stoppa en spårning använder du parametern *RemoveListener* . Om du vill stoppa en spårning som använder fil lyssnaren (en spårning som har startats med hjälp av parametern *sökväg* ) använder du parametern *RemoveFileListener* . När du tar bort lyssnaren stoppas spårningen.
* Använd Get-TraceSource för att avgöra vilka komponenter som kan spåras. Spårnings källorna för varje modul läses in automatiskt när komponenten används och de visas i resultatet av **Get-TraceSource**.

## RELATERADE LÄNKAR

[Get-TraceSource](Get-TraceSource.md)

[Spåra-kommando](Trace-Command.md)
