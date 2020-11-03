---
description: Beskriver hur du hanterar överförda åtgärder i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_transactions?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Transactions
ms.openlocfilehash: 522e0f727754b0b0153571039f3bf3966d0abf20
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271383"
---
# <a name="about-transactions"></a>Om transaktioner

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver hur du hanterar överförda åtgärder i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Transaktioner stöds i PowerShell som börjar i PowerShell 2,0. Med den här funktionen kan du starta en transaktion, för att ange vilka kommandon som ingår i transaktionen och för att genomföra eller återställa en transaktion.

## <a name="about-transactions"></a>OM TRANSAKTIONER

I PowerShell är en transaktion en uppsättning av ett eller flera kommandon som hanteras som en logisk enhet. En transaktion kan slutföras ("bekräftad"), vilket ändrar data som påverkas av transaktionen. Eller så kan en transaktion helt ångras ("återställd") så att de berörda data inte ändras av transaktionen.

Eftersom kommandona i en transaktion hanteras som en enhet, utförs antingen alla kommandon eller också återställs alla kommandon.

Transaktioner används ofta i data bearbetning, främst i databas åtgärder och för ekonomiska transaktioner. Transaktioner används oftast när värsta fall scenariot för en uppsättning kommandon inte är att de Miss lyckas, men att vissa kommandon lyckas medan andra Miss lyckas, lämnar systemet i ett skadat, falskt eller avtolknings tillstånd som är svårt att reparera.

## <a name="transaction-cmdlets"></a>TRANSAKTIONS-CMDLETAR

PowerShell innehåller flera cmdletar utformade för att hantera transaktioner.

- Starta transaktion: startar en ny transaktion.
- Använd-Transaction: lägger till ett kommando eller uttryck i transaktionen. Kommandot måste använda transaktions aktiverade objekt.
- Ångra-transaktion: återställer transaktionen så att inga data ändras av transaktionen.
- Slutförd-transaktion: genomför transaktionen. De data som påverkas av transaktionen ändras.
- Get-Transaction: hämtar information om den aktiva transaktionen.

Om du vill visa en lista över transaktions-cmdletar skriver du:

```powershell
get-command *transaction
```

Om du vill ha detaljerad information om cmdletarna skriver du:

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a>TRANSAKTIONS AKTIVERADE ELEMENT

För att delta i en transaktion måste både cmdleten och providern ha stöd för transaktioner. Den här funktionen är inbyggd i de objekt som påverkas av transaktionen.

PowerShell-dataprovidern stöder transaktioner i Windows Vista. TransactedString-objektet (Microsoft. PowerShell. commands. Management. TransactedString) fungerar med alla operativ system som kör PowerShell.

Andra PowerShell-leverantörer kan stödja transaktioner. Om du vill hitta PowerShell-providers i sessionen som stöder transaktioner använder du följande kommando för att hitta värdet "transaktioner" i egenskapen Capabilities för providers:

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

Mer information om en provider finns i hjälpen för providern. Om du vill ha hjälp för leverantören skriver du:

```
get-help <provider-name>
```

Om du till exempel vill få hjälp med register leverantören skriver du:

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a>PARAMETERN USETRANSACTION

-Cmdletar som kan stödja transaktioner har en UseTransaction-parameter. Den här parametern inkluderar kommandot i den aktiva transaktionen. Du kan använda det fullständiga parameter namnet eller dess alias, "usetx".

Parametern kan endast användas när sessionen innehåller en aktiv transaktion. Om du anger ett kommando med parametern UseTransaction när det inte finns någon aktiv transaktion, Miss lyckas kommandot.

Om du vill hitta cmdletar med parametern UseTransaction skriver du:

```powershell
get-help * -parameter UseTransaction
```

I PowerShell Core har alla cmdletar utformats för att fungera med PowerShell-leverantörer som stöder transaktioner. Därför kan du använda Provider-cmdletar för att hantera transaktioner.

Mer information om PowerShell-leverantörer finns [about_Providers](about_Providers.md).

## <a name="the-transaction-object"></a>TRANSAKTIONS OBJEKT

Transaktioner visas i PowerShell av ett transaktions objekt, system. Management. Automation. Transaction.

Objektet har följande egenskaper:

- RollbackPreference: innehåller återställnings inställnings uppsättningen för den aktuella transaktionen. Du kan ställa in återställnings inställningen när du använder Start-Transaction för att starta transaktionen.

  Återställnings inställningen avgör under vilka omständigheter som transaktionen återställs automatiskt. Giltiga värden är error, TerminatingError och Never. Standardvärdet är error.

- Status: innehåller transaktionens aktuella status. Giltiga värden är Active, Committed och återställd.

- SubscriberCount: innehåller antalet prenumeranter för transaktionen. En prenumerant läggs till i en transaktion när du startar en transaktion medan en annan transaktion pågår. Antalet prenumeranter minskas när en prenumerant genomför transaktionen.

## <a name="active-transactions"></a>AKTIVA TRANSAKTIONER

I PowerShell är det bara en transaktion som är aktiv i taget och du kan bara hantera den aktiva transaktionen. Flera transaktioner kan pågå i samma session samtidigt, men det är bara den senast startade transaktionen som är aktiv.

Därför kan du inte ange en viss transaktion när du använder transaktions-cmdletar. Kommandon gäller alltid för den aktiva transaktionen.

Detta är mest uppenbart i beteendet för Get-Transaction-cmdleten. När du anger ett Get-Transaction kommando får Get-Transaction alltid bara ett transaktions objekt. Det här objektet är det objekt som representerar den aktiva transaktionen.

Om du vill hantera en annan transaktion måste du först avsluta den aktiva transaktionen, antingen genom att utföra den eller återställa den. När du gör det aktive ras den tidigare transaktionen automatiskt. Transaktioner aktive ras i omvänd ordning för de startas, så att den senast startade transaktionen alltid är aktiv.

## <a name="subscribers-and-independent-transactions"></a>PRENUMERANTER OCH OBEROENDE TRANSAKTIONER

Om du startar en transaktion medan en annan transaktion pågår, startar inte PowerShell en ny transaktion som standard. Istället lägger den till en "prenumerant" i den aktuella transaktionen.

När en transaktion har flera prenumeranter, återställer ett enda Undo-Transaction-kommando åt hela transaktionen för alla prenumeranter. Men för att genomföra transaktionen måste du ange ett Complete-Transaction-kommando för varje prenumerant.

Om du vill hitta antalet prenumeranter för en transaktion kontrollerar du egenskapen SubscriberCount för objektet. Följande kommando använder exempelvis cmdleten Get-Transaction för att hämta värdet för egenskapen SubscriberCount för den aktiva transaktionen:

```powershell
(Get-Transaction).SubscriberCount
```

Att lägga till en prenumerant är standard beteendet eftersom de flesta transaktioner som startas medan en annan transaktion pågår är relaterade till den ursprungliga transaktionen. I den typiska modellen anropar ett skript som innehåller en transaktion ett hjälp skript som innehåller en egen transaktion. Eftersom transaktionerna är relaterade bör de återställas eller allokeras som en enhet.

Du kan dock starta en transaktion som är oberoende av den aktuella transaktionen genom att använda den oberoende parametern i Start-Transaction-cmdleten.

När du startar en oberoende transaktion skapar Start-Transaction ett nytt transaktions objekt och den nya transaktionen blir den aktiva transaktionen.
Den oberoende transaktionen kan allokeras eller återställas utan att den ursprungliga transaktionen påverkas.

När den oberoende transaktionen är slutförd (allokerad eller återställd) blir den ursprungliga transaktionen den aktiva transaktionen igen.

## <a name="changing-data"></a>ÄNDRA DATA

När du använder transaktioner för att ändra data, ändras inte data som påverkas av transaktionen förrän du genomför transaktionen. Samma data kan dock ändras av kommandon som inte ingår i transaktionen.

Tänk på detta när du använder transaktioner för att hantera delade data.
Normalt har databaser en mekanism som låser data medan du arbetar med den, vilket förhindrar andra användare och andra kommandon, skript och funktioner, från att ändra den.

Låset är dock en funktion i databasen. Den är inte relaterad till transaktioner. Om du arbetar i ett transaktions aktiverat fil system eller ett annat data lager, kan data ändras medan transaktionen pågår.

## <a name="examples"></a>EXEMPEL

I exemplen i det här avsnittet används PowerShell-registernyckeln och vi antar att du är bekant med den. Om du vill ha mer information om register leverantören skriver du "Get-Help Registry".

### <a name="example-1-committing-a-transaction"></a>EXEMPEL 1: GENOMFÖR EN TRANSAKTION

Använd Start-Transaction-cmdleten om du vill skapa en transaktion. Följande kommando startar en transaktion med standardinställningarna.

```powershell
start-transaction
```

Om du vill inkludera kommandon i transaktionen använder du parametern UseTransaction för cmdleten. Som standard ingår inte kommandon i transaktionen.

Följande kommando, som anger den aktuella platsen i program varu nyckeln för HKCU: Drive, ingår inte i transaktionen.

```powershell
cd hkcu:\Software
```

Följande kommando, som skapar nyckeln för företags nyckeln, använder parametern UseTransaction i cmdleten New-Item för att inkludera kommandot i den aktiva transaktionen.

```powershell
new-item MyCompany -UseTransaction
```

Kommandot returnerar ett objekt som representerar den nya nyckeln, men eftersom kommandot är en del av transaktionen har registret inte ändrats än.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

Använd Complete-Transaction-cmdleten för att genomföra transaktionen. Eftersom den alltid påverkar den aktiva transaktionen kan du inte ange transaktionen.

```powershell
complete-transaction
```

Det innebär att nyckeln för företags nyckeln läggs till i registret.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-2-rolling-back-a-transaction"></a>EXEMPEL 2: ÅTERSTÄLLA EN TRANSAKTION

Använd Start-Transaction-cmdleten om du vill skapa en transaktion. Följande kommando startar en transaktion med standardinställningarna.

```powershell
start-transaction
```

Följande kommando, som skapar MyOtherCompany-nyckeln, använder parametern UseTransaction för cmdleten New-Item för att inkludera kommandot i den aktiva transaktionen.

```powershell
new-item MyOtherCompany -UseTransaction
```

Kommandot returnerar ett objekt som representerar den nya nyckeln, men eftersom kommandot är en del av transaktionen har registret inte ändrats än.

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

Använd Undo-Transaction-cmdleten om du vill återställa transaktionen. Eftersom det alltid påverkar den aktiva transaktionen anger du inte transaktionen.

```powershell
Undo-transaction
```

Resultatet är att nyckeln MyOtherCompany inte har lagts till i registret.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

### <a name="example-3-previewing-a-transaction"></a>EXEMPEL 3: FÖR HANDS GRANS KAR EN TRANSAKTION

Normalt används de kommandon som används i en transaktion för att ändra data. De kommandon som hämtar data är dock användbara i en transaktion, även om de hämtar data i transaktionen. Detta ger en förhands granskning av de ändringar som genomför transaktionen.

I följande exempel visas hur du använder kommandot Get-ChildItem (aliaset är "dir") för att förhandsgranska ändringarna i en transaktion.

Följande kommando startar en transaktion.

```powershell
start-transaction
```

Följande kommando använder cmdleten New-ItemProperty för att lägga till register posten MyKey i företags nyckeln. Kommandot använder parametern UseTransaction för att inkludera kommandot i transaktionen.

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

Kommandot returnerar ett objekt som representerar den nya register posten, men register posten har inte ändrats.

```
MyKey
-----
123
```

Om du vill hämta de objekt som för närvarande finns i registret använder du ett Get-ChildItem kommando ("dir") utan parametern UseTransaction. Följande kommando hämtar objekt som börjar med "M".

```powershell
dir m*
```

Resultatet visar att inga poster ännu har lagts till i företags nyckeln.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

Om du vill förhandsgranska resultatet av transaktionen anger du ett Get-ChildItem (dir)-kommando med parametern UseTransaction. Det här kommandot innehåller en vy över data i transaktionen.

```powershell
dir m* -useTransaction
```

Resultatet visar att om transaktionen är genomförd, läggs MyKey-posten till i företags nyckeln.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a>EXEMPEL 4: KOMBINERA ÖVERFÖRDA OCH ICKE-ÖVERFÖRDA KOMMANDON

Du kan ange icke-överförda kommandon under en transaktion. De ej överförda kommandona påverkar data direkt, men de påverkar inte transaktionen.
Följande kommando startar en transaktion i register nyckeln HKCU: \ Software.

```powershell
start-transaction
```

Följande tre kommandon använder cmdleten New-Item för att lägga till nycklar i registret.
De första och tredje kommandona använder parametern UseTransaction för att inkludera kommandona i transaktionen. Det andra kommandot utesluter parametern. Eftersom det andra kommandot inte ingår i transaktionen börjar det gälla omedelbart.

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

Om du vill visa det aktuella status för registret använder du kommandot Get-ChildItem (dir) utan parametern UseTransaction. Det här kommandot hämtar objekt som börjar med "M".

```powershell
dir m*
```

Resultatet visar att nyckeln MyCompany2 har lagts till i registret, men att nycklarna MyCompany1 och MyCompany3, som ingår i transaktionen, inte läggs till.

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

Följande kommando utför transaktionen.

```powershell
complete-transaction
```

Nu visas nycklarna som lades till som en del av transaktionen i registret.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
83   1 Microsoft                      {(default)}
0    0 MyCompany1                     {}
0    0 MyCompany2                     {}
0    0 MyCompany3                     {}
```

### <a name="example-5-using-automatic-rollback"></a>EXEMPEL 5: ANVÄNDA AUTOMATISK ÅTERSTÄLLNING

När ett kommando i en transaktion genererar ett fel av någon typ återställs transaktionen automatiskt.

Det här standard beteendet är utformat för skript som kör transaktioner. Skript är vanligt vis väl testade och innehåller fel hanterings logik, så fel förväntas inte och bör avslutas med transaktionen.

Det första kommandot startar en transaktion i register nyckeln HKCU: \ Software.

```powershell
start-transaction
```

Följande kommando använder cmdleten New-Item för att lägga till företagets nyckel i registret. Kommandot använder parametern UseTransaction (aliaset är "usetx") för att inkludera kommandot i transaktionen.

```powershell
New-Item MyCompany -UseTX
```

Eftersom det redan finns en företags nyckel i registret, Miss lyckas kommandot och transaktionen återställs.

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Ett Get-Transaction-kommando bekräftar att transaktionen har återställts och att SubscriberCount är 0.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a>EXEMPEL 6: ÄNDRA ÅTERSTÄLLNINGS INSTÄLLNINGEN

Om du vill att transaktionen ska vara mer feltolerant kan du använda RollbackPreference-parametern för Start-Transaction för att ändra inställningen.

Följande kommando startar en transaktion med återställnings inställningen "Never".

```powershell
start-transaction -rollbackpreference Never
```

I det här fallet när kommandot Miss lyckas återställs inte transaktionen automatiskt.

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

Eftersom transaktionen fortfarande är aktiv kan du skicka kommandot igen som en del av transaktionen.

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a>EXEMPEL 7: ANVÄNDA CMDLETEN USE-TRANSACTION

Med hjälp av cmdleten Use-Transaction kan du göra direkta skript mot transaktionsskyddade Microsoft .NET Ramverks objekt. Use-Transaction tar ett skript block som bara kan innehålla kommandon och uttryck som använder transaktions aktiverade .NET Framework objekt, till exempel instanser av klassen Microsoft. PowerShell. commands. TransactedString.

Följande kommando startar en transaktion.

```powershell
start-transaction
```

Följande New-Object-kommando skapar en instans av klassen TransactedString och sparar den i variabeln $t.

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

Följande kommando använder metoden append för TransactedString-objektet för att lägga till text i strängen. Eftersom kommandot inte är en del av transaktionen börjar ändringen gälla omedelbart.

```powershell
$t.append("Windows")
```

Följande kommando använder samma append-metod för att lägga till text, men den lägger till texten som en del av transaktionen. Kommandot omges av klammerparenteser och anges som värdet för parametern script block för use-Transaction. UseTransaction-parametern (UseTx) krävs.

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

Om du vill se det aktuella innehållet i den överförda strängen i $t använder du metoden ToString för TransactedString-objektet.

```powershell
$t.tostring()
```

Utdata visar att endast de icke-överförda ändringarna är effektiva.

```output
Windows
```

Om du vill se det aktuella innehållet i den överförda strängen i $t inifrån transaktionen, bäddar du in uttrycket i ett Use-Transaction-kommando.

```powershell
use-transaction {$s.tostring()} -usetx
```

Utdata visar datakällvyn.

```output
PowerShell
```

Följande kommando utför transaktionen.

```powershell
complete-transaction
```

Så här visar du den sista strängen:

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a>EXEMPEL 8: HANTERA MULTI-SUBSCRIBER-TRANSAKTIONER

När du startar en transaktion medan en annan transaktion pågår, skapar inte PowerShell en andra transaktion som standard. Istället lägger den till en prenumerant till den aktuella transaktionen.

Det här exemplet visar hur du visar och hanterar en transaktion med flera prenumerationer.

Börja med att starta en transaktion i program varu nyckeln HKCU: \.

```powershell
start-transaction
```

Följande kommando använder kommandot Get-Transaction för att hämta den aktiva transaktionen.

```powershell
get-transaction
```

Resultatet visar det objekt som representerar den aktiva transaktionen.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Följande kommando lägger till företags nyckeln till registret. Kommandot använder parametern UseTransaction för att inkludera kommandot i transaktionen.

```powershell
new-item MyCompany -UseTransaction
```

Följande kommando använder kommandot Start-Transaction för att starta en transaktion. Även om det här kommandot skrivs i kommando tolken, är det mer sannolikt att det här scenariot inträffar när du kör ett skript som innehåller en transaktion.

```powershell
start-transaction
```

Ett Get-Transaction-kommando visar att antalet prenumeranter för Transaction-objektet ökar. Värdet är nu 2.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

Nästa kommando använder cmdleten New-ItemProperty för att lägga till register posten MyKey i företags nyckeln. Parametern UseTransaction används för att inkludera kommandot i transaktionen.

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

Min företags nyckel finns inte i registret, men det här kommandot lyckas eftersom de två kommandona ingår i samma transaktion.

Följande kommando utför transaktionen. Om transaktionen återställdes återställs transaktionen för alla prenumeranter.

```powershell
complete-transaction
```

Ett Get-Transaction-kommando visar att antalet prenumeranter för transaktionsobjektet är 1, men värdet för status är fortfarande aktivt (inte dedikerat).

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Slutför transaktionen genom att ange ett andra kommando för fullständig transaktion. Om du vill genomföra en transaktion med flera prenumerationer måste du ange ett Complete-Transaction-kommando för varje Start-Transaction-kommando.

```powershell
complete-transaction
```

Ett annat Get-Transaction kommando visar att transaktionen har genomförts.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a>EXEMPEL 9: HANTERA OBEROENDE TRANSAKTIONER

När du startar en transaktion medan en annan transaktion pågår kan du använda den oberoende parametern för Start-Transaction för att skapa den nya transaktionen oberoende av den ursprungliga transaktionen.

När du gör det skapar Start-Transaction ett nytt transaktions objekt och gör den nya transaktionen till aktiv transaktion.

Börja med att starta en transaktion i HKCU: \\ Software-nyckeln.

```powershell
start-transaction
```

Följande kommando använder kommandot Get-Transaction för att hämta den aktiva transaktionen.

```powershell
get-transaction
```

Resultatet visar det objekt som representerar den aktiva transaktionen.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Följande kommando lägger till register nyckeln min företag som en del av transaktionen. Den använder UseTransaction-parametern (UseTx) för att inkludera kommandot i den aktiva transaktionen.

```powershell
new-item MyCompany -use
```

Följande kommando startar en ny transaktion. Kommandot använder den oberoende parametern för att ange att transaktionen inte är en prenumerant på den aktiva transaktionen.

```powershell
start-transaction -independent
```

När du skapar en oberoende transaktion blir den nya transaktionen (senast skapade) den aktiva transaktionen. Du kan använda ett Get-Transaction-kommando för att hämta den aktiva transaktionen.

```powershell
get-transaction
```

Observera att SubscriberCount för transaktionen är 1, vilket indikerar att det inte finns några andra prenumeranter och att transaktionen är ny.

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Den nya transaktionen måste vara slutförd (antingen allokerad eller återställd) innan du kan hantera den ursprungliga transaktionen.

Följande kommando lägger till nyckeln MyOtherCompany i registret. Den använder UseTransaction-parametern (UseTx) för att inkludera kommandot i den aktiva transaktionen.

```powershell
new-item MyOtherCompany -usetx
```

Återställ nu transaktionen. Om det fanns en enda transaktion med två prenumeranter återställs hela transaktionen för alla prenumeranter om du återställer transaktionen.

Men eftersom dessa transaktioner är oberoende, avbryter den senaste transaktionen register ändringarna och gör den ursprungliga transaktionen till en aktiv transaktion.

```powershell
undo-transaction
```

Ett Get-Transaction-kommando bekräftar att den ursprungliga transaktionen fortfarande är aktiv i sessionen.

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

Följande kommando utför den aktiva transaktionen.

```powershell
complete-transaction
```

Ett Get-ChildItem-kommando visar att registret har ändrats.

```powershell
dir m*
```

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

## <a name="see-also"></a>SE ÄVEN

[Starta transaktion](xref:Microsoft.PowerShell.Management.Start-Transaction)

[Hämta transaktion](xref:Microsoft.PowerShell.Management.Get-Transaction)

[Slutförd transaktion](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[Ångra-transaktion](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[Använd transaktion](xref:Microsoft.PowerShell.Management.Use-Transaction)

[Get-PSProvider](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[Get-ChildItem](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[about_Providers](about_Providers.md)
