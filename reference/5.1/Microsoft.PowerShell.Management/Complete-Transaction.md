---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/complete-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Complete-Transaction
ms.openlocfilehash: 20fbdd86aab07dda065492eff2da4f358fb2ffca
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93266228"
---
# Complete-Transaction

## SAMMANFATTNING
Genomför den aktiva transaktionen.

## SYNTAX

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Complete-Transaction** genomför en aktiv transaktion.
När du genomför en transaktion, slutförs kommandona i transaktionen och de data som påverkas av kommandona ändras.

Om transaktionen innehåller flera prenumeranter måste du ange ett **fullständigt transaktions** kommando för varje Start-Transaction-kommando för att genomföra transaktionen.

Cmdleten **Complete-Transaction** är en uppsättning cmdletar som stöder funktionen transaktioner i Windows PowerShell.
Mer information finns i about_Transactions.

## EXEMPEL

### Exempel 1: genomför en transaktion

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}
```

Det här exemplet visar vad som händer när du använder cmdleten **Complete-Transaction** för att genomföra en transaktion.

Kommandot **Start Transaction** startar transaktionen.
Kommandot New-Item använder parametern *UseTransaction* för att inkludera kommandot i transaktionen.

Det första dir-kommandot (Get-ChildItem) visar att det nya objektet ännu inte har lagts till i registret.

Kommandot **fullständig transaktion** genomför transaktionen, vilket gör att register ändringen träder i kraft.
Därför visar det andra kommandot dir att registret har ändrats.

### Exempel 2: genomför en transaktion som har fler än en prenumerant

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
0   0 MyCompany                      {}

PS HKCU:\software> Start-Transaction
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                2                Active

PS HKCU:\software> New-ItemProperty -Path MyCompany -Name MyKey -Value -UseTransaction

MyKey
-----
123

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Get-Transaction

RollbackPreference   SubscriberCount  Status
------------------   ---------------  ------
Error                1                Active

PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   1 MyCompany                      {MyKey}
```

Det här exemplet visar hur du använder **Slutför transaktion** för att genomföra en transaktion som har fler än en prenumerant.

Om du vill genomföra en transaktion med flera prenumerationer måste du ange ett **fullständigt transaktions** kommando för varje **Start transaktions** kommando.
Data ändras endast när kommandot slutlig **slutförd transaktion** skickas.

I demonstrations syfte visar det här exemplet en serie kommandon som anges på kommando raden.
I praktiken kommer transaktioner förmodligen att köras i skript, med den sekundära transaktionen som körs av en funktion eller ett hjälp skript som anropas av huvud skriptet.

I det här exemplet startar ett kommando för att **Starta** transaktionen.
Ett **nytt-objekt-** kommando med parametern *UseTransaction* lägger till företags nyckeln i program varu nyckeln.
Även om cmdleten **New-item** returnerar ett nyckel objekt, ändras inte data i registret än.

Ett andra **Start transaktions** kommando lägger till en andra prenumerant i den befintliga transaktionen.
Cmdleten **Get-Transaction** bekräftar att antalet prenumeranter är 2.
Ett New-ItemProperty-kommando med parametern *UseTransaction* lägger till en register post i den nya företags nyckeln.
Kommandot returnerar ett värde, men registret ändras inte.

Det första **fullständiga transaktions** kommandot minskar antalet prenumeranter med 1.
Detta bekräftas av ett **Get-Transaction-** kommando.
Men inga data ändras, så som de visas i kommandot dir m * ( **Get-ChildItem** ).

Det andra kommandot **fullständig transaktion** genomför hela transaktionen och ändrar data i registret.
Detta bekräftas av ett andra dir m *-kommando som visar ändringarna.

### Exempel 3: utföra en transaktion som inte ändrar några data

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item MyCompany -UseTransaction
PS HKCU:\software> dir m*
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}

PS HKCU:\software> dir m* -UseTransaction
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
82   1 Microsoft                      {(default)}
0   0 MyCompany                      {}

PS HKCU:\software> Complete-Transaction
```

Det här exemplet visar värdet för att använda get- \* commands och andra kommandon som inte ändrar data i en transaktion.
När ett get- \* kommando används i en transaktion hämtas de objekt som ingår i transaktionen.
På så sätt kan du förhandsgranska ändringarna i transaktionen innan du genomför ändringarna.

I det här exemplet startas en transaktion.
Ett New-Item-kommando med parametern *UseTransaction* lägger till en ny nyckel i registret som en del av transaktionen.

Eftersom den nya register nyckeln inte läggs till i registret förrän kommandot **Slutför transaktion** körs, visar ett enkelt dir-kommando ( **Get-ChildItem** ) registret utan den nya nyckeln.

Men när du lägger till parametern *UseTransaction* till kommandot dir blir kommandot en del av transaktionen och det hämtar objekten i transaktionen även om de inte har lagts till i data.

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
Det går inte att skicka pipe-objekt till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

* Du kan inte återställa en transaktion som har genomförts eller allokera en transaktion som har återställts.

  Du kan inte återställa någon annan transaktion än den aktiva transaktionen.
Om du vill återställa en annan transaktion måste du först genomföra eller återställa den aktiva transaktionen.

  Om någon del av en transaktion inte kan genomföras, till exempel när ett kommando i transaktionen resulterar i ett fel, återställs hela transaktionen.

*

## RELATERADE LÄNKAR

[Hämta transaktion](Get-Transaction.md)

[Starta transaktion](Start-Transaction.md)

[Ångra-transaktion](Undo-Transaction.md)

[Använd transaktion](Use-Transaction.md)

[Get-ChildItem](Get-ChildItem.md)

[Nytt objekt](New-Item.md)

[New-ItemProperty](New-ItemProperty.md)
