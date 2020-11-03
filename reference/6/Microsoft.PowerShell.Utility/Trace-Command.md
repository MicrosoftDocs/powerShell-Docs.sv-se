---
external help file: Microsoft.PowerShell.Commands.Utility.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Utility
ms.date: 04/09/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.utility/trace-command?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Trace-Command
ms.openlocfilehash: 9147be62c881e81a4ff1352a1b9fe7a34d2610cd
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266715"
---
# Trace-Command

## SAMMANFATTNING
Konfigurerar och startar en spårning av det angivna uttrycket eller kommandot.

## SYNTAX

### expressionSet (standard)

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Expression] <ScriptBlock> [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force] [-Debugger]
 [-PSHost] [<CommonParameters>]
```

### commandSet

```
Trace-Command [-InputObject <PSObject>] [-Name] <String[]> [[-Option] <PSTraceSourceOptions>]
 [-Command] <String> [-ArgumentList <Object[]>] [-ListenerOption <TraceOptions>] [-FilePath <String>] [-Force]
 [-Debugger] [-PSHost] [<CommonParameters>]
```

## BESKRIVNING
`Trace-Command`Cmdleten konfigurerar och startar en spårning av det angivna uttrycket eller kommandot.
Den fungerar som set-TraceSource, förutom att den endast gäller för det angivna kommandot.

## EXEMPEL

### Exempel 1: spåra metadata-bearbetning, parameter bindning och ett uttryck

I det här exemplet startas en spårning av metadata-bearbetning, parameter bindning och skapande och destruktion av uttrycket för cmdleten `Get-Process Notepad` .

```powershell
Trace-Command -Name metadata,parameterbinding,cmdlet -Expression {Get-Process Notepad} -PSHost
```

Parametern **Name** används för att ange spårnings källorna, **uttrycks** parametern för att ange kommandot och parametern **PSHost** för att skicka utdata till-konsolen. Eftersom det inte anger några spårnings alternativ eller lyssnar alternativ använder kommandot standardvärdena:

- Alla för spårnings alternativ
- Ingen för alternativen för lyssnare

### Exempel 2: spåra åtgärder för ParameterBinding-åtgärder

Det här exemplet spårar åtgärder för **ParameterBinding** -åtgärder för PowerShell medan den bearbetar ett `Get-Alias` uttryck som tar emot inmatade från pipelinen.

```powershell
$A = "i*"
Trace-Command ParameterBinding {Get-Alias $Input} -PSHost -InputObject $A
```

I `Trace-Command` skickar **InputObject** -parametern ett objekt till det uttryck som bearbetas under spårningen.

Det första kommandot lagrar strängen `i*` i `$A` variabeln. Det andra kommandot använder `Trace-Command` cmdleten med ParameterBinding spårnings källa. Parametern **PSHost** skickar utdata till-konsolen.

Uttrycket som bearbetas är `Get-Alias $Input` , där `$Input` variabeln är associerad med parametern **InputObject** . Parametern **InputObject** skickar variabeln `$A` till uttrycket. I praktiken är kommandot som bearbetas under spårningen `Get-Alias -InputObject $A" or "$A | Get-Alias` .

## PARAMETRAR

### – Argument List

Anger parametrar och parameter värden för det kommando som spåras. Aliaset för **argument List** är **argument**. Den här funktionen är särskilt användbar för fel sökning av dynamiska parametrar.

Mer information om beteendet för **argument List** finns [about_Splatting](../Microsoft.PowerShell.Core/About/about_Splatting.md#splatting-with-arrays).

```yaml
Type: System.Object[]
Parameter Sets: commandSet
Aliases: Args

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Kommando

Anger ett kommando som bearbetas under spårningen.

```yaml
Type: System.String
Parameter Sets: commandSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – Fel sökning

Anger att cmdleten skickar spårningsutdata till fel söknings programmet. Du kan visa utdata i valfri fel sökare för användarläge eller kernelläge eller i Visual Studio. Den här parametern väljer också standard spårnings lyssnaren.

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

### – Uttryck

Anger det uttryck som bearbetas under spårningen. Omge uttrycket med klammerparenteser ( `{}` ).

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: expressionSet
Aliases:

Required: True
Position: 1
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Sökväg

Anger en fil som cmdleten skickar spårningsutdata till. Den här parametern väljer också lyssnaren för fil spårning.

```yaml
Type: System.String
Parameter Sets: (All)
Aliases: PSPath, Path

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Force

Tvingar kommandot att köras utan att fråga användaren om bekräftelse. Används med parametern **sökväg** . Även om du använder **Force** -parametern kan inte cmdlet: en åsidosätta säkerhets begränsningar.

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

### – InputObject

Anger ininformation till det uttryck som bearbetas under spårningen. Du kan ange en variabel som representerar inmatade uttryck eller skicka ett objekt via pipelinen.

```yaml
Type: System.Management.Automation.PSObject
Parameter Sets: (All)
Aliases:

Required: False
Position: Named
Default value: None
Accept pipeline input: True (ByValue)
Accept wildcard characters: False
```

### -ListenerOption

Anger valfria data till prefixet för varje spårnings meddelande i utdata. De acceptabla värdena för den här parametern är:

- Inget
- LogicalOperationStack
- DateTime
- Timestamp
- ProcessId
- ThreadId
- Callstacken

**Inget** är standardvärdet.

Om du vill ange flera alternativ avgränsar du dem med kommatecken, men utan blank steg och omger dem med citat tecken, till exempel "ProcessID, ThreadID".

```yaml
Type: System.Diagnostics.TraceOptions
Parameter Sets: (All)
Aliases:
Accepted values: None, LogicalOperationStack, DateTime, Timestamp, ProcessId, ThreadId, Callstack

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Name

Anger en matris med PowerShell-komponenter som spåras. Ange namnet på spårnings källan för varje komponent. Jokertecken är tillåtna. Om du vill hitta spårnings källorna på datorn skriver du `Get-TraceSource` .

```yaml
Type: System.String[]
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Alternativ

Bestämmer vilken typ av händelser som spåras. De acceptabla värdena för den här parametern är:

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
Parameter Sets: (All)
Aliases:
Accepted values: None, Constructor, Dispose, Finalizer, Method, Property, Delegates, Events, Exception, Lock, Error, Errors, Warning, Verbose, WriteLine, Data, Scope, ExecutionFlow, Assert, All

Required: False
Position: 2
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -PSHost

Anger att cmdleten skickar spårningsutdata till PowerShell-värden. Den här parametern väljer också spårnings lyssnaren PSHost.

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

### CommonParameters

Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### System. Management. Automation. PSObject

Du kan skicka pipe-objekt som representerar inmatade uttryck till `Trace-Command` .

## UTDATA

### System. Management. Automation. PSObject

Returnerar kommando spårningen i fel söknings data strömmen.

## ANTECKNINGAR

- Spårning är en metod som utvecklare använder för att felsöka och förfina program. När du spårar genererar programmet detaljerade meddelanden om varje steg i den interna bearbetningen.

- Cmdletarna för PowerShell-spårning är utformade för att hjälpa PowerShell-utvecklare, men de är tillgängliga för alla användare. De gör det möjligt för dig att övervaka nästan varje aspekt av funktionerna i gränssnittet.

- Om du vill hitta de PowerShell-komponenter som är aktiverade för spårning skriver du `Get-Help Get-TraceSource` .

  En spårnings källa är en del av varje PowerShell-komponent som hanterar spårning och genererar spårnings meddelanden för komponenten. Om du vill spåra en komponent identifierar du dess spårnings källa.

  En spårnings lyssnare tar emot utdata från spårningen och visar den för användaren. Du kan välja att skicka spårnings data till en användar-eller kernelläge, till värden eller konsolen, till en fil eller till en anpassad lyssnare som härletts från klassen **system. Diagnostics. TraceListener** .

- När du använder parameter uppsättningen commandSet, bearbetar PowerShell kommandot precis som det skulle bearbetas i en pipeline. Till exempel upprepas inte kommando identifiering för varje inkommande objekt.

- Namnen på **namn** , **uttryck** , **alternativ** och **kommando** parametrar är valfria. Om du utelämnar parameter namnen måste de parameter värden som inte är namngivna visas i den här ordningen: **namn** , **uttryck** , **alternativ** eller **namn** , **kommando** , **alternativ**. Om du inkluderar parameter namnen kan parametrarna visas i vilken ordning som helst.

## RELATERADE LÄNKAR

[Get-TraceSource](Get-TraceSource.md)

[Measure-Command](Measure-Command.md)

[Set-TraceSource](Set-TraceSource.md)
