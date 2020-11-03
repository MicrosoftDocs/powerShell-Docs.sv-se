---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/undo-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Undo-Transaction
ms.openlocfilehash: 1acb06ea7b05a2127b04a22c4c51b92cd68056f2
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265322"
---
# Undo-Transaction

## SAMMANFATTNING
Återställer den aktiva transaktionen.

## SYNTAX

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Undo-Transaction** rullar tillbaka den aktiva transaktionen.
När du återställer en transaktion ignoreras de ändringar som utfördes av kommandona i transaktionen och data återställs till dess ursprungliga form.

Om transaktionen innehåller flera prenumeranter återställs hela transaktionen för alla prenumeranter via kommandot **Ångra transaktion** .

Som standard återställs transaktioner automatiskt om ett kommando i transaktionen genererar ett fel.
Transaktioner kan dock startas med hjälp av en annan återställnings inställning och du kan använda den här cmdleten för att återställa den aktiva transaktionen när som helst.

Cmdleten **Undo-Transaction** är en uppsättning cmdlets som stöder funktionen transaktioner i Windows PowerShell.
Mer information finns i about_Transactions.

## EXEMPEL

### Exempel 1: Återställ den aktuella transaktionen

```
PS C:\> Undo-Transaction
```

Detta kommando återställer den aktuella, aktiva, transaktionen.

### Exempel 2: starta och återställa en transaktion

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

Det här exemplet startar en transaktion och slår sedan tillbaka den igen.
Därför görs inga ändringar i registret.

### Exempel 3: återställa en transaktion för alla prenumeranter

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                1                 Active

PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                2                 Active

PS HKCU:\Software> Undo-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----
Error                0                 RolledBack
```

Det här exemplet visar att hela transaktionen återställs för alla prenumeranter när en prenumerant återställer en transaktion.

Det första kommandot ändrar platsen till register nyckeln HKCU: \ Software.

Det andra kommandot startar en transaktion.

Det tredje kommandot använder cmdleten New-Item för att skapa en ny register nyckel.
Kommandot använder parametern *UseTransaction* för att inkludera ändringen i transaktionen.

Det fjärde kommandot använder cmdleten Get-Transaction för att hämta den aktiva transaktionen.
Observera att statusen är aktiv och antalet prenumeranter är 1.

Det femte kommandot använder kommandot Start-Transaction igen.
Normalt sker start av en transaktion medan en annan transaktion pågår när ett skript som används av huvud transaktionen inkluderar en egen fullständig transaktion.
Det här exemplet utförs interaktivt så att du kan undersöka det i olika steg.
När du kör ett kommando för att **Starta transaktion** medan en annan transaktion pågår, är kommandona kopplade till den befintliga transaktionen som en ny prenumerant och antalet prenumeranter ökar.

Det sjätte kommandot använder cmdleten **Get-Transaction** för att hämta den aktiva transaktionen.
Observera att antalet prenumeranter nu är 2.

Det sjunde kommandot använder **Undo-Transaction** för att återställa transaktionen.
Det här kommandot returnerar inga objekt.

Det sista kommandot är ett **Get-Transaction-** kommando som hämtar det aktiva, eller i det här fallet den senast aktiva transaktionen.
Resultaten visar att transaktionen återställs och att antalet prenumeranter är 0, vilket visar att transaktionen har återställts för alla prenumeranter.

## PARAMETRAR

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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet returnerar inga utdata.

## ANTECKNINGAR

* Det går inte att återställa en transaktion som har genomförts.

  Du kan inte återställa någon annan transaktion än den aktiva transaktionen.
Om du vill återställa en annan, oberoende transaktion måste du först genomföra eller återställa den aktiva transaktionen.

  Att återställa transaktionen avslutar transaktionen.
Om du vill använda en transaktion igen måste du starta en ny transaktion.

## RELATERADE LÄNKAR

[Slutförd transaktion](Complete-Transaction.md)

[Hämta transaktion](Get-Transaction.md)

[Starta transaktion](Start-Transaction.md)

[Använd transaktion](Use-Transaction.md)
