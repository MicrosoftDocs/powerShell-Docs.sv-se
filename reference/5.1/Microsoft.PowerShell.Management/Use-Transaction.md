---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/use-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Use-Transaction
ms.openlocfilehash: db8423aef6dc4b25c4ddd13f9b29b774463c6a6c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265334"
---
# Use-Transaction

## SAMMANFATTNING
Lägger till skript blocket i den aktiva transaktionen.

## SYNTAX

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **use-Transaction** lägger till ett skript block i en aktiv transaktion.
På så sätt kan du utföra överförda skript med hjälp av transaktions-aktiverade Microsoft .NET Ramverks objekt.
Skript blocket kan bara innehålla transaktions aktiverade .NET Framework objekt, till exempel instanser av klassen Microsoft. PowerShell. commands. Management. TransactedString.

Parametern *UseTransaction* , som är valfri för de flesta cmdletar, krävs när du använder den här cmdleten.

**Use-Transaction** är en uppsättning cmdletar som stöder funktionen transaktioner i Windows PowerShell.
Mer information finns i about_Transactions.

## EXEMPEL

### Exempel 1: skript med hjälp av ett transaktions aktiverat objekt

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> $transactedString.ToString()
Hello
PS C:\> Use-Transaction -TransactedScript { $transactedString.ToString() } -UseTransaction
Hello, World
PS C:\> Complete-Transaction
PS C:\> $transactedString.ToString()
Hello, World
```

Det här exemplet visar hur du använder **use-Transaction** för att skript mot ett transaktions aktiverat .NET Framework-objekt.
I det här fallet är objektet ett **TransactedString** -objekt.

Det första kommandot använder Start-Transaction-cmdlet för att starta en transaktion.

Det andra kommandot använder kommandot New-Object för att skapa ett **TransactedString** -objekt.
Objektet lagras i variabeln $TransactedString.

De tredje och fjärde kommandona använder båda metoden **APPEND** för **TransactedString** -objektet för att lägga till text till värdet för $TransactedString.
Ett kommando är en del av transaktionen.
Det andra kommandot är inte.

Det tredje kommandot använder metoden **APPEND** i den överförda strängen för att lägga till Hej till värdet för $TransactedString.
Eftersom kommandot inte är en del av transaktionen tillämpas ändringen omedelbart.

Det fjärde kommandot använder **use-Transaction** för att lägga till text i strängen i transaktionen.
Kommandot använder metoden **APPEND** för att lägga till ", World" till värdet för $TransactedString.
Kommandot omges av klammerparenteser ( {} ) för att göra det till ett skript block.
Parametern *UseTransaction* krävs i det här kommandot.

De femte och sjätte kommandona använder metoden **toString** för **TransactedString** -objektet för att visa värdet för **TransactedString** som en sträng.
Ett nytt kommando är en del av transaktionen.
Den andra transaktionen är inte.

Det femte kommandot använder metoden **toString** för att visa det aktuella värdet för variabeln $TransactedString.
Eftersom den inte är en del av transaktionen visas bara det aktuella status för strängen.

Det sjätte kommandot använder **use-Transaction** för att köra samma kommando i transaktionen.
Eftersom kommandot är en del av transaktionen, visas det aktuella värdet för strängen i transaktionen, ungefär som en förhands granskning av transaktionens ändringar.

Det sjunde kommandot använder Complete-Transaction-cmdlet för att genomföra transaktionen.

Det sista kommandot använder metoden **toString** för att Visa resultatvärdet för variabeln som en sträng.

### Exempel 2: återställa en transaktion

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

I det här exemplet visas effekterna av att återställa en transaktion som innehåller kommandon för att **använda transaktioner** .
Precis som med alla kommandon i en transaktion ignoreras de överförda ändringarna och data är oförändrade när transaktionen återställs.

Det första kommandot använder **Start transaktion** för att starta en transaktion.

Det andra kommandot använder **New-Object** för att skapa ett **TransactedString** -objekt.
Objektet lagras i variabeln $TransactedString.

Det tredje kommandot, som inte är en del av transaktionen, använder metoden **APPEND** för att lägga till "Hej" till värdet för $TransactedString.

Det fjärde kommandot använder **use-Transaction** för att köra ett annat kommando som använder metoden **APPEND** i transaktionen.
Kommandot använder metoden **APPEND** för att lägga till ", World" till värdet för $TransactedString.

Det femte kommandot använder Undo-Transaction-cmdlet: en för att återställa transaktionen.
Därför återställs alla kommandon som utförs i transaktionen.

Det sista kommandot använder metoden **toString** för att Visa resultatvärdet för $TransactedString som en sträng.
Resultaten visar att endast ändringar som gjorts utanför transaktionen tillämpades på objektet.

## PARAMETRAR

### -TransactedScript
Anger det skript block som körs i transaktionen.
Ange ett giltigt skript block som omges av klammerparenteser ({}).
Den här parametern är obligatorisk.

```yaml
Type: System.Management.Automation.ScriptBlock
Parameter Sets: (All)
Aliases:

Required: True
Position: 0
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### – UseTransaction
Inkluderar kommandot i den aktiva transaktionen.
Den här parametern är bara giltig medan en transaktion pågår.
Mer information finns i about_transactions.

```yaml
Type: System.Management.Automation.SwitchParameter
Parameter Sets: (All)
Aliases: usetx

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

### PSObject
Den här cmdleten returnerar resultatet av transaktionen.

## ANTECKNINGAR

* Parametern *UseTransaction* innehåller kommandot i den aktiva transaktionen. Eftersom cmdleten **use-Transaction** alltid används i transaktioner, krävs den här parametern för att använda kommandot **-Transaction-** kommando gällande.

*

## RELATERADE LÄNKAR

[Slutförd transaktion](Complete-Transaction.md)

[Hämta transaktion](Get-Transaction.md)

[Starta transaktion](Start-Transaction.md)

[Ångra-transaktion](Undo-Transaction.md)
