---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/get-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Get-Transaction
ms.openlocfilehash: bb8e9e1f204c67207f31613181f856d3bcaf8dc3
ms.sourcegitcommit: 2e497178126b2b33a169ff04c31e251e0b59e89b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/02/2020
ms.locfileid: "93261527"
---
# Get-Transaction

## SAMMANFATTNING
Hämtar den aktuella (aktiva) transaktionen.

## SYNTAX

```
Get-Transaction [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Get-Transaction** hämtar ett objekt som representerar den aktuella transaktionen i sessionen.

Denna cmdlet returnerar aldrig fler än ett objekt, eftersom endast en transaktion är aktiv i taget.
Om du startar en eller flera oberoende transaktioner (genom att använda den oberoende parametern för start transaktion) är den senast startade transaktionen aktiv och det är den transaktion som **erhåller transaktions** returer.

När alla aktiva transaktioner antingen har återställts eller bekräftats, visar denna cmdlet den transaktion som senast var aktiv i sessionen.

Denna cmdlet är en uppsättning cmdletar som har stöd för funktionen Transactions i Windows PowerShell.
Mer information finns i about_Transactions.

## EXEMPEL

### Exempel 1: hämta den aktuella transaktionen

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Det här kommandot använder cmdleten Get-Transaction för att hämta den aktuella transaktionen.

### Exempel 2: Visa egenskaper och metoder för Transaction-objektet

```
PS C:\> Get-Transaction | Get-Member

Name               MemberType Definition
----               ---------- ----------
Dispose            Method     System.Void Dispose(), System.Void Dispose(Boolean disposing)
Equals             Method     System.Boolean Equals(Object obj)
GetHashCode        Method     System.Int32 GetHashCode()
GetType            Method     System.Type GetType()
ToString           Method     System.String ToString()
IsCommitted        Property   System.Boolean IsCommitted {get;}
IsRolledBack       Property   System.Boolean IsRolledBack {get;}
RollbackPreference Property   System.Management.Automation.RollbackSeverity RollbackPreference {get;}
SubscriberCount    Property   System.Int32 SubscriberCount {get;set;}
```

Det här kommandot använder Get-Member-cmdleten för att visa egenskaper och metoder för Transaction-objektet.

### Exempel 3: Visa egenskapsvärdena för en återställd back transaktion

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Undo-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ----------
Error                0                 RolledBack
```

Det här kommandot visar egenskaps värden för ett transaktions objekt för en transaktion som har återställts.

### Exempel 4: Visa egenskaps värden för en allokerad transaktion

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

Det här kommandot visar egenskaps värden för ett transaktions objekt för en transaktion som har genomförts.

### Exempel 5: starta en transaktion medan en annan pågår

```
PS C:\> cd hklm:\software
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany -UseTransaction
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> New-Item MyCompany2 -UseTransaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ---------
Error                1                 Committed
```

I det här exemplet visas effekterna av transaktions objekt som startar en transaktion medan en annan transaktion pågår.
Detta inträffar vanligt vis när ett skript som kör en transaktion innehåller en funktion eller anropar ett skript som innehåller en annan fullständig transaktion.

Om inte det andra **Start transaktions** kommandot innehåller den *oberoende* parametern, skapas ingen ny transaktion vid **Start transaktion** .
Istället lägger den till en andra prenumerant till den ursprungliga transaktionen.

Det första **Start transaktions** kommandot startar transaktionen.
Ett New-Item-kommando med parametern *UseTransaction* är en del av transaktionen.

Ett andra **Start transaktions** kommando lägger till en prenumerant i transaktionen.
Nästa New-Item-kommandot ingår också i transaktionen.

Det första kommandot **Get-Transaction** visar multi-Subscriber-transaktionen.
Observera att antalet prenumeranter är 2.

Det första Complete-Transaction kommandot genomför inte transaktionen, men minskar antalet prenumeranter till 1.

Det andra **slutförda transaktions** kommandot genomför transaktionen.

### Exempel 6: starta en oberoende transaktion medan en annan pågår

```
PS C:\>
HKLM:\SOFTWARE> Start-Transaction
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Start-Transaction -Independent
HKLM:\SOFTWARE> Get-Transaction

RollbackPreference   SubscriberCount   IsRolledBack   IsCommitted
------------------   ---------------   ------------   -----------
Error                1                 False          False

HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
HKLM:\SOFTWARE> Complete-Transaction
HKLM:\SOFTWARE> Get-Transaction
```

I det här exemplet visas effekterna av transaktions objekt för att starta en oberoende transaktion medan en annan transaktion pågår.

Det första **Start transaktions** kommandot startar transaktionen.
Ett **nytt-objekt-** kommando med parametern *UseTransaction* är en del av transaktionen.

Ett andra **Start transaktions** kommando lägger till en prenumerant i transaktionen.
Nästa **nya-objekt-** kommandot ingår också i transaktionen.

Det första kommandot **Get-Transaction** visar multi-Subscriber-transaktionen.
Observera att antalet prenumeranter är 2.

Kommandot **fullständig transaktion** minskar antalet prenumeranter till 1, men transaktionen slutförs inte.

Det andra **slutförda transaktions** kommandot genomför transaktionen.

## PARAMETRAR

### CommonParameters
Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable. Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).

## INDATA

### Inget
Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### System. Management. Automation. PSTransaction
Denna cmdlet returnerar ett objekt som representerar den aktuella transaktionen.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Slutförd transaktion](Complete-Transaction.md)

[Starta transaktion](Start-Transaction.md)

[Ångra-transaktion](Undo-Transaction.md)

[Använd transaktion](Use-Transaction.md)

[Nytt objekt](New-Item.md)
