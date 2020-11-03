---
external help file: Microsoft.PowerShell.Commands.Management.dll-Help.xml
keywords: powershell,cmdlet
Locale: en-US
Module Name: Microsoft.PowerShell.Management
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.management/start-transaction?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Start-Transaction
ms.openlocfilehash: 53be131f45f15e5d2053b183040dc7b3dca4a14c
ms.sourcegitcommit: 9b28fb9a3d72655bb63f62af18b3a5af6a05cd3f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/07/2020
ms.locfileid: "93265359"
---
# Start-Transaction

## SAMMANFATTNING
Startar en transaktion.

## SYNTAX

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## BESKRIVNING
Cmdleten **Start-Transaction** startar en transaktion, som är en serie kommandon som hanteras som en enhet.
En transaktion kan slutföras eller bekräftas.
Du kan också helt ångra eller återställa, så att alla data som ändras av transaktionen återställs till dess ursprungliga tillstånd.
Eftersom kommandona i en transaktion hanteras som en enhet, utförs antingen alla kommandon eller också återställs alla kommandon.

Som standard återställs transaktioner automatiskt om ett kommando i transaktionen genererar ett fel.
Du kan ändra det här beteendet med hjälp av parametern *RollbackPreference* .

De cmdletar som används i en transaktion måste utformas för att stödja transaktioner.
Cmdletar som stöder transaktioner har en *UseTransaction* -parameter.
Providern måste ha stöd för transaktioner för att utföra transaktioner i en provider.
Windows PowerShell-registernyckeln i Windows Vista och senare versioner av operativ systemet Windows stöder transaktioner.
Du kan också använda klassen **Microsoft. PowerShell. commands. Management. TransactedString** för att inkludera uttryck i transaktioner på alla versioner av Windows-systemet som stöder Windows PowerShell.
Andra Windows PowerShell-leverantörer kan också stödja transaktioner.

Endast en transaktion kan vara aktiv i taget.
Om du startar en ny, oberoende transaktion medan en transaktion pågår, blir den nya transaktionen den aktiva transaktionen och du måste utföra eller återställa den nya transaktionen innan du gör några ändringar i den ursprungliga transaktionen.

Cmdleten **Start-Transaction** är en uppsättning cmdlets som stöder funktionen transaktioner i Windows PowerShell.
Mer information finns i about_Transactions.

## EXEMPEL

### Exempel 1: starta och återställa en transaktion

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

Kommandona startar och återställer sedan en transaktion.
Eftersom transaktionen återställs görs inga ändringar i registret.

### Exempel 2: starta och slutför en transaktion

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

Kommandona startar och slutför en transaktion.
Inga ändringar görs i registret förrän kommandot **Slutför transaktion** används.

### Exempel 3: Använd olika återställnings inställningar

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

# Start-Transaction (-rollbackpreference error)

PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction
New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name ContosoCompany -UseTransaction

PS HKCU:\software> New-Item -Path . -Name "Contoso" -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  -Path . -Name ContosoCompany -UseTransaction

# Start-Transaction (-rollbackpreference never)

PS HKCU:\software> Start-Transaction -RollbackPreference never
PS HKCU:\software> New-Item -Path "NoPath" -Name "ContosoCompany" -UseTransaction

New-Item : The registry key at the specified path does not exist.
At line:1 char:9
+ new-item <<<<  -Path NoPath -Name "ContosoCompany" -UseTransaction
PS HKCU:\software> New-Item -Path . -Name "ContosoCompany" -UseTransaction

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany                 {}
PS HKCU:\Software> Complete-Transaction

# Succeeds
```

Det här exemplet visar effekterna av att ändra värdet för parametern *RollbackPreference* .

I den första uppsättningen kommandon använder inte **Start transaktion** *RollbackPreference*.
Därför används standardvärdet (Error).
När ett fel uppstår i ett transaktions kommando, det vill säga att den angivna sökvägen inte finns, återställs transaktionen automatiskt.

I den andra uppsättningen kommandon använder **Start-Transaction** *RollbackPreference* med värdet Never.
Det innebär att när ett fel uppstår i ett transaktions kommando är transaktionen fortfarande aktiv och kan slutföras.

Eftersom de flesta transaktionerna måste utföras utan fel, är standardvärdet *RollbackPreference* vanligt vis standard.

### Exempel 4: Använd denna cmdlet när en transaktion pågår

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction
PS HKCU:\software> Get-Transaction
PS HKCU:\software> New-Item "ContosoCompany2" -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\Software> Get-Transaction
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

I det här exemplet visas effekterna av att använda **Start transaktion** medan en transaktion pågår.
Resultatet är ungefär som att delta i pågående transaktioner.

Även om detta är ett förenklat kommando inträffar det här scenariot ofta när transaktionen inbegriper att köra ett skript som innehåller en fullständig transaktion.

Det första **Start transaktions** kommandot startar transaktionen.
Det första kommandot **New-item** är en del av transaktionen.

Det andra **Start transaktions** kommandot lägger till en ny prenumerant i transaktionen.
Kommandot **Get-Transaction** returnerar nu en transaktion med antalet prenumeranter 2.
Det andra kommandot **New-item** är en del av samma transaktion.

Inga ändringar görs i registret förrän hela transaktionen har slutförts.
För att slutföra transaktionen måste du ange två kommandon för **fullständig transaktion** , en för varje prenumerant.
Om du skulle återställa transaktionen när som helst skulle all-transaktionen återställas för båda prenumeranterna.

### Exempel 5: starta en oberoende transaktion medan en pågår

```
PS C:\> cd HKCU:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> Start-Transaction -Independent
PS HKCU:\software> Get-Transaction
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
PS HKCU:\software> Undo-Transaction
PS HKCU:\software> New-ItemProperty -Path "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
MyKey
-----
123
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   1 MyCompany                      {MyKey}
```

Det här exemplet visar effekterna av att använda den *oberoende* parametern för **Start transaktion** för att starta en transaktion medan en annan transaktion pågår.
I det här fallet återställs den nya transaktionen utan att den ursprungliga transaktionen påverkas.

Även om transaktionerna är logiskt oberoende, eftersom endast en transaktion kan vara aktiv i taget, måste du återställa eller bekräfta den senaste transaktionen innan du återupptar arbetet med den ursprungliga transaktionen.

Den första uppsättningen kommandon startar en transaktion.
Kommandot **New-item** är en del av den första transaktionen.

I den andra uppsättningen kommandon använder kommandot **Start Transaction** den *oberoende* parametern.
Kommandot **Get-Transaction** som följer visar transaktions objekt för den aktiva transaktionen, vilket är det nyaste.
Antalet prenumeranter är lika med 1 som visar att transaktionerna är orelaterade.

När den aktiva transaktionen återställs med hjälp av kommandot **Ångra-transaktion** , aktive ras den ursprungliga transaktionen igen.

Kommandot **New-ItemProperty** , som är en del av den ursprungliga transaktionen, slutförs utan fel och den ursprungliga transaktionen kan slutföras med kommandot **Slutför transaktion** .
Det innebär att registret ändras.

### Exempel 6: kör kommandon som inte ingår i en transaktion

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany1" -UseTransaction
PS HKCU:\software> New-Item "ContosoCompany2"
PS HKCU:\software> New-Item "ContosoCompany3" -UseTransaction
PS HKCU:\software> dir contoso*
PS HKCU:\software> Complete-Transaction
PS HKCU:\software> dir contoso*
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany2                {}

PS HKCU:\Software> Complete-Transaction
PS HKCU:\Software> dir contoso*

Hive: HKEY_CURRENT_USER\Software
SKC  VC Name                           Property
---  -- ----                           --------
0   0 ContosoCompany1                     {}
0   0 ContosoCompany2                     {}
0   0 ContosoCompany3                     {}
```

Det här exemplet visar att kommandon som skickas när en transaktion pågår kan tas med i transaktionen eller ingår inte.
Endast kommandon som använder parametern *UseTransaction* är en del av transaktionen.

Det första och tredje kommandot **New-item** använder parametern *UseTransaction* .
Dessa kommandon ingår i transaktionen.
Eftersom det andra kommandot **New-item** inte använder *UseTransaction* -parametern, är den inte en del av transaktionen.

Det första dir-kommandot visar resultatet.
Det andra kommandot **New-item** slutförs omedelbart, men de första och tredje kommandona för **nya objekt** gäller inte förrän transaktionen har genomförts.

Kommandot **fullständig transaktion** genomför transaktionen.
Därför visar det andra kommandot dir att alla nya objekt läggs till i registret.

### Exempel 7: återställa en transaktion som inte slutförs inom en angiven tid

```
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> Get-Transaction
PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction
PS C:\> Start-Transaction -Timeout 2

# Wait two minutes...

PS C:\> > Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   -----------
Error                1                 RolledBack

PS C:\> New-Item HKCU:\Software\ContosoCompany -UseTransaction

New-Item : Cannot use transaction. The transaction has been rolled back or has timed out.
At line:1 char:9
+ new-item <<<<  MyCompany -UseTransaction
```

Det här kommandot använder *timeout* -parametern för **Start-Transaction** för att starta en transaktion som måste slutföras inom två minuter.
Om transaktionen inte är avslutad när tids gränsen går ut, återställs den automatiskt.

När tids gränsen går ut får du inget meddelande, men egenskapen **status** för Transaction-objektet är inställd på återställd och kommandon som använder parametern *UseTransaction* kan inte köras.

## PARAMETRAR

### – Oberoende
Anger att den här cmdleten startar en transaktion som är oberoende av pågående transaktioner.
Om du använder **Start transaktion** medan en annan transaktion pågår läggs en ny prenumerant som standard till i den pågående transaktionen.
Den här parametern har endast en funktion när en transaktion redan pågår i sessionen.

Om du använder **Start transaktion** medan en transaktion pågår, används det befintliga transaktionsobjektet som standard och antalet prenumeranter ökar.
Resultatet är ungefär som att koppla den ursprungliga transaktionen.
Kommandot Undo-Transaction återställer hela transaktionen.
För att slutföra transaktionen måste du ange ett Complete-Transaction-kommando för varje prenumerant.
Eftersom de flesta pågående transaktioner samtidigt är relaterade är standardvärdet tillräckligt för de flesta användnings områden.

Om du anger den *oberoende* parametern skapar denna cmdlet en ny transaktion som kan slutföras eller tas bort utan att den ursprungliga transaktionen påverkas.
Men eftersom bara en transaktion kan vara aktiv i taget, måste du slutföra eller återställa den nya transaktionen innan du återupptar arbetet med den ursprungliga transaktionen.

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

### -RollbackPreference
Anger de villkor under vilka en transaktion återställs automatiskt.
De acceptabla värdena för den här parametern är:

- Fel.
Transaktionen återställs automatiskt om det inträffar ett fel som avslutas eller inte avslutas.
- TerminatingError.
Transaktionen återställs automatiskt om ett avslutande fel inträffar.
- Helt.
Transaktionen återställs aldrig automatiskt.

Standardvärdet är error.

```yaml
Type: System.Management.Automation.RollbackSeverity
Parameter Sets: (All)
Aliases:
Accepted values: Error, TerminatingError, Never

Required: False
Position: Named
Default value: None
Accept pipeline input: False
Accept wildcard characters: False
```

### -Timeout
Anger den maximala tiden, i minuter, som transaktionen är aktiv.
När tids gränsen går ut återställs transaktionen automatiskt.

Som standard finns det ingen tids gräns för transaktioner som startas på kommando raden.
När transaktioner startas av ett skript är standard tids gränsen 30 minuter.

```yaml
Type: System.Int32
Parameter Sets: (All)
Aliases: TimeoutMins

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

### Inget
Du kan inte skicka pipe-ininformation till denna cmdlet.

## UTDATA

### Inget
Denna cmdlet genererar inga utdata.

## ANTECKNINGAR

## RELATERADE LÄNKAR

[Slutförd transaktion](Complete-Transaction.md)

[Hämta transaktion](Get-Transaction.md)

[Ångra-transaktion](Undo-Transaction.md)

[Använd transaktion](Use-Transaction.md)
