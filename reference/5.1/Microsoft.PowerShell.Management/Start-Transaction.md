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
# <span data-ttu-id="4c01a-103">Start-Transaction</span><span class="sxs-lookup"><span data-stu-id="4c01a-103">Start-Transaction</span></span>

## <span data-ttu-id="4c01a-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="4c01a-104">SYNOPSIS</span></span>
<span data-ttu-id="4c01a-105">Startar en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-105">Starts a transaction.</span></span>

## <span data-ttu-id="4c01a-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="4c01a-106">SYNTAX</span></span>

```
Start-Transaction [-Timeout <Int32>] [-Independent] [-RollbackPreference <RollbackSeverity>] [-WhatIf]
 [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="4c01a-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4c01a-107">DESCRIPTION</span></span>
<span data-ttu-id="4c01a-108">Cmdleten **Start-Transaction** startar en transaktion, som är en serie kommandon som hanteras som en enhet.</span><span class="sxs-lookup"><span data-stu-id="4c01a-108">The **Start-Transaction** cmdlet starts a transaction, which is a series of commands that are managed as a unit.</span></span>
<span data-ttu-id="4c01a-109">En transaktion kan slutföras eller bekräftas.</span><span class="sxs-lookup"><span data-stu-id="4c01a-109">A transaction can be completed, or committed.</span></span>
<span data-ttu-id="4c01a-110">Du kan också helt ångra eller återställa, så att alla data som ändras av transaktionen återställs till dess ursprungliga tillstånd.</span><span class="sxs-lookup"><span data-stu-id="4c01a-110">Alternatively, it can be completely undone, or rolled back, so that any data changed by the transaction is restored to its original state.</span></span>
<span data-ttu-id="4c01a-111">Eftersom kommandona i en transaktion hanteras som en enhet, utförs antingen alla kommandon eller också återställs alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="4c01a-111">Because the commands in a transaction are managed as a unit, either all commands are committed or all commands are rolled back.</span></span>

<span data-ttu-id="4c01a-112">Som standard återställs transaktioner automatiskt om ett kommando i transaktionen genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="4c01a-112">By default, if any command in the transaction generates an error, transactions are rolled back automatically.</span></span>
<span data-ttu-id="4c01a-113">Du kan ändra det här beteendet med hjälp av parametern *RollbackPreference* .</span><span class="sxs-lookup"><span data-stu-id="4c01a-113">You can use the *RollbackPreference* parameter to change this behavior.</span></span>

<span data-ttu-id="4c01a-114">De cmdletar som används i en transaktion måste utformas för att stödja transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4c01a-114">The cmdlets used in a transaction must be designed to support transactions.</span></span>
<span data-ttu-id="4c01a-115">Cmdletar som stöder transaktioner har en *UseTransaction* -parameter.</span><span class="sxs-lookup"><span data-stu-id="4c01a-115">Cmdlets that support transactions have a *UseTransaction* parameter.</span></span>
<span data-ttu-id="4c01a-116">Providern måste ha stöd för transaktioner för att utföra transaktioner i en provider.</span><span class="sxs-lookup"><span data-stu-id="4c01a-116">To perform transactions in a provider, the provider must support transactions.</span></span>
<span data-ttu-id="4c01a-117">Windows PowerShell-registernyckeln i Windows Vista och senare versioner av operativ systemet Windows stöder transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4c01a-117">The Windows PowerShell Registry provider in Windows Vista and later versions of the Windows operating system supports transactions.</span></span>
<span data-ttu-id="4c01a-118">Du kan också använda klassen **Microsoft. PowerShell. commands. Management. TransactedString** för att inkludera uttryck i transaktioner på alla versioner av Windows-systemet som stöder Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c01a-118">You can also use the **Microsoft.PowerShell.Commands.Management.TransactedString** class to include expressions in transactions on any version of the Windows system that supports Windows PowerShell.</span></span>
<span data-ttu-id="4c01a-119">Andra Windows PowerShell-leverantörer kan också stödja transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4c01a-119">Other Windows PowerShell providers can also support transactions.</span></span>

<span data-ttu-id="4c01a-120">Endast en transaktion kan vara aktiv i taget.</span><span class="sxs-lookup"><span data-stu-id="4c01a-120">Only one transaction can be active at a time.</span></span>
<span data-ttu-id="4c01a-121">Om du startar en ny, oberoende transaktion medan en transaktion pågår, blir den nya transaktionen den aktiva transaktionen och du måste utföra eller återställa den nya transaktionen innan du gör några ändringar i den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-121">If you start a new, independent transaction while a transaction is in progress, the new transaction becomes the active transaction, and you must commit or roll back the new transaction before you make any changes to the original transaction.</span></span>

<span data-ttu-id="4c01a-122">Cmdleten **Start-Transaction** är en uppsättning cmdlets som stöder funktionen transaktioner i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4c01a-122">**Start-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="4c01a-123">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="4c01a-123">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="4c01a-124">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4c01a-124">EXAMPLES</span></span>

### <span data-ttu-id="4c01a-125">Exempel 1: starta och återställa en transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-125">Example 1: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Undo-Transaction
```

<span data-ttu-id="4c01a-126">Kommandona startar och återställer sedan en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-126">These commands start and then roll back a transaction.</span></span>
<span data-ttu-id="4c01a-127">Eftersom transaktionen återställs görs inga ändringar i registret.</span><span class="sxs-lookup"><span data-stu-id="4c01a-127">Because the transaction is rolled back, no changes are made to the registry.</span></span>

### <span data-ttu-id="4c01a-128">Exempel 2: starta och slutför en transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-128">Example 2: Start and complete a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\software> Start-Transaction
PS HKCU:\software> New-Item "ContosoCompany" -UseTransaction
PS HKCU:\software> New-ItemProperty "ContosoCompany" -Name "MyKey" -Value 123 -UseTransaction
PS HKCU:\software> Complete-Transaction
```

<span data-ttu-id="4c01a-129">Kommandona startar och slutför en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-129">These commands start and then complete a transaction.</span></span>
<span data-ttu-id="4c01a-130">Inga ändringar görs i registret förrän kommandot **Slutför transaktion** används.</span><span class="sxs-lookup"><span data-stu-id="4c01a-130">No changes are made to the registry until the **Complete-Transaction** command is used.</span></span>

### <span data-ttu-id="4c01a-131">Exempel 3: Använd olika återställnings inställningar</span><span class="sxs-lookup"><span data-stu-id="4c01a-131">Example 3: Use different rollback preferences</span></span>

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

<span data-ttu-id="4c01a-132">Det här exemplet visar effekterna av att ändra värdet för parametern *RollbackPreference* .</span><span class="sxs-lookup"><span data-stu-id="4c01a-132">This example demonstrates the effect of changing the *RollbackPreference* parameter value.</span></span>

<span data-ttu-id="4c01a-133">I den första uppsättningen kommandon använder inte **Start transaktion** *RollbackPreference*.</span><span class="sxs-lookup"><span data-stu-id="4c01a-133">In the first set of commands, **Start-Transaction** does not use *RollbackPreference*.</span></span>
<span data-ttu-id="4c01a-134">Därför används standardvärdet (Error).</span><span class="sxs-lookup"><span data-stu-id="4c01a-134">As a result, the default value (Error) is used.</span></span>
<span data-ttu-id="4c01a-135">När ett fel uppstår i ett transaktions kommando, det vill säga att den angivna sökvägen inte finns, återställs transaktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-135">When an error occurs in a transaction command, that is, the specified path does not exist, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="4c01a-136">I den andra uppsättningen kommandon använder **Start-Transaction** *RollbackPreference* med värdet Never.</span><span class="sxs-lookup"><span data-stu-id="4c01a-136">In the second set of commands, **Start-Transaction** uses *RollbackPreference* with a value of Never.</span></span>
<span data-ttu-id="4c01a-137">Det innebär att när ett fel uppstår i ett transaktions kommando är transaktionen fortfarande aktiv och kan slutföras.</span><span class="sxs-lookup"><span data-stu-id="4c01a-137">As a result, when an error occurs in a transaction command, the transaction is still active and can be completed successfully.</span></span>

<span data-ttu-id="4c01a-138">Eftersom de flesta transaktionerna måste utföras utan fel, är standardvärdet *RollbackPreference* vanligt vis standard.</span><span class="sxs-lookup"><span data-stu-id="4c01a-138">Because most transactions must be performed without error, the default value of *RollbackPreference* is typically preferred.</span></span>

### <span data-ttu-id="4c01a-139">Exempel 4: Använd denna cmdlet när en transaktion pågår</span><span class="sxs-lookup"><span data-stu-id="4c01a-139">Example 4: Use this cmdlet while a transaction is in progress</span></span>

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

<span data-ttu-id="4c01a-140">I det här exemplet visas effekterna av att använda **Start transaktion** medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="4c01a-140">This example shows the effect of using **Start-Transaction** while a transaction is in progress.</span></span>
<span data-ttu-id="4c01a-141">Resultatet är ungefär som att delta i pågående transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4c01a-141">The effect is much like joining the transaction in progress.</span></span>

<span data-ttu-id="4c01a-142">Även om detta är ett förenklat kommando inträffar det här scenariot ofta när transaktionen inbegriper att köra ett skript som innehåller en fullständig transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-142">Although this is a simplified command, this scenario frequently occurs when the transaction involves running a script that includes a complete transaction.</span></span>

<span data-ttu-id="4c01a-143">Det första **Start transaktions** kommandot startar transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-143">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="4c01a-144">Det första kommandot **New-item** är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-144">The first **New-Item** command is part of the transaction.</span></span>

<span data-ttu-id="4c01a-145">Det andra **Start transaktions** kommandot lägger till en ny prenumerant i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-145">The second **Start-Transaction** command adds a new subscriber to the transaction.</span></span>
<span data-ttu-id="4c01a-146">Kommandot **Get-Transaction** returnerar nu en transaktion med antalet prenumeranter 2.</span><span class="sxs-lookup"><span data-stu-id="4c01a-146">The **Get-Transaction** command now returns a transaction with a subscriber count of 2.</span></span>
<span data-ttu-id="4c01a-147">Det andra kommandot **New-item** är en del av samma transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-147">The second **New-Item** command is part of the same transaction.</span></span>

<span data-ttu-id="4c01a-148">Inga ändringar görs i registret förrän hela transaktionen har slutförts.</span><span class="sxs-lookup"><span data-stu-id="4c01a-148">No changes are made to the registry until the whole transaction is completed.</span></span>
<span data-ttu-id="4c01a-149">För att slutföra transaktionen måste du ange två kommandon för **fullständig transaktion** , en för varje prenumerant.</span><span class="sxs-lookup"><span data-stu-id="4c01a-149">To complete the transaction, you must enter two **Complete-Transaction** commands, one for each subscriber.</span></span>
<span data-ttu-id="4c01a-150">Om du skulle återställa transaktionen när som helst skulle all-transaktionen återställas för båda prenumeranterna.</span><span class="sxs-lookup"><span data-stu-id="4c01a-150">If you were to roll back the transaction at any point, all the transaction would be rolled back for both subscribers.</span></span>

### <span data-ttu-id="4c01a-151">Exempel 5: starta en oberoende transaktion medan en pågår</span><span class="sxs-lookup"><span data-stu-id="4c01a-151">Example 5: Start an independent transaction while one is in progress</span></span>

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

<span data-ttu-id="4c01a-152">Det här exemplet visar effekterna av att använda den *oberoende* parametern för **Start transaktion** för att starta en transaktion medan en annan transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="4c01a-152">This example shows the effect of using the *Independent* parameter of **Start-Transaction** to start a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="4c01a-153">I det här fallet återställs den nya transaktionen utan att den ursprungliga transaktionen påverkas.</span><span class="sxs-lookup"><span data-stu-id="4c01a-153">In this case, the new transaction is rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="4c01a-154">Även om transaktionerna är logiskt oberoende, eftersom endast en transaktion kan vara aktiv i taget, måste du återställa eller bekräfta den senaste transaktionen innan du återupptar arbetet med den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-154">Although the transactions are logically independent, because only one transaction can be active at a time, you must roll back or commit the newest transaction before resuming work on the original transaction.</span></span>

<span data-ttu-id="4c01a-155">Den första uppsättningen kommandon startar en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4c01a-155">The first set of commands starts a transaction.</span></span>
<span data-ttu-id="4c01a-156">Kommandot **New-item** är en del av den första transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-156">The **New-Item** command is part of the first transaction.</span></span>

<span data-ttu-id="4c01a-157">I den andra uppsättningen kommandon använder kommandot **Start Transaction** den *oberoende* parametern.</span><span class="sxs-lookup"><span data-stu-id="4c01a-157">In the second set of commands, the **Start-Transaction** command uses the *Independent* parameter.</span></span>
<span data-ttu-id="4c01a-158">Kommandot **Get-Transaction** som följer visar transaktions objekt för den aktiva transaktionen, vilket är det nyaste.</span><span class="sxs-lookup"><span data-stu-id="4c01a-158">The **Get-Transaction** command that follows shows the transaction object for the active transaction, which is the newest one.</span></span>
<span data-ttu-id="4c01a-159">Antalet prenumeranter är lika med 1 som visar att transaktionerna är orelaterade.</span><span class="sxs-lookup"><span data-stu-id="4c01a-159">The subscriber count is equal to 1, that shows that the transactions are unrelated.</span></span>

<span data-ttu-id="4c01a-160">När den aktiva transaktionen återställs med hjälp av kommandot **Ångra-transaktion** , aktive ras den ursprungliga transaktionen igen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-160">When the active transaction is rolled back by using an **Undo-Transaction** command, the original transaction becomes active again.</span></span>

<span data-ttu-id="4c01a-161">Kommandot **New-ItemProperty** , som är en del av den ursprungliga transaktionen, slutförs utan fel och den ursprungliga transaktionen kan slutföras med kommandot **Slutför transaktion** .</span><span class="sxs-lookup"><span data-stu-id="4c01a-161">The **New-ItemProperty** command, which is part of the original transaction, finishes without error, and the original transaction can be completed by using the **Complete-Transaction** command.</span></span>
<span data-ttu-id="4c01a-162">Det innebär att registret ändras.</span><span class="sxs-lookup"><span data-stu-id="4c01a-162">As a result, the registry is changed.</span></span>

### <span data-ttu-id="4c01a-163">Exempel 6: kör kommandon som inte ingår i en transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-163">Example 6: Run commands that are not part of a transaction</span></span>

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

<span data-ttu-id="4c01a-164">Det här exemplet visar att kommandon som skickas när en transaktion pågår kan tas med i transaktionen eller ingår inte.</span><span class="sxs-lookup"><span data-stu-id="4c01a-164">This example demonstrates that commands that are submitted while a transaction is in progress can be included in the transaction or not included.</span></span>
<span data-ttu-id="4c01a-165">Endast kommandon som använder parametern *UseTransaction* är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-165">Only commands that use the *UseTransaction* parameter are part of the transaction.</span></span>

<span data-ttu-id="4c01a-166">Det första och tredje kommandot **New-item** använder parametern *UseTransaction* .</span><span class="sxs-lookup"><span data-stu-id="4c01a-166">The first and third **New-Item** commands use the *UseTransaction* parameter.</span></span>
<span data-ttu-id="4c01a-167">Dessa kommandon ingår i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-167">These commands are part of the transaction.</span></span>
<span data-ttu-id="4c01a-168">Eftersom det andra kommandot **New-item** inte använder *UseTransaction* -parametern, är den inte en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-168">Because the second **New-Item** command does not use the *UseTransaction* parameter, it is not part of the transaction.</span></span>

<span data-ttu-id="4c01a-169">Det första dir-kommandot visar resultatet.</span><span class="sxs-lookup"><span data-stu-id="4c01a-169">The first dir command shows the effect.</span></span>
<span data-ttu-id="4c01a-170">Det andra kommandot **New-item** slutförs omedelbart, men de första och tredje kommandona för **nya objekt** gäller inte förrän transaktionen har genomförts.</span><span class="sxs-lookup"><span data-stu-id="4c01a-170">The second **New-Item** command is completed immediately, but the first and third **New-Item** commands are not effective until the transaction is committed.</span></span>

<span data-ttu-id="4c01a-171">Kommandot **fullständig transaktion** genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-171">The **Complete-Transaction** command commits the transaction.</span></span>
<span data-ttu-id="4c01a-172">Därför visar det andra kommandot dir att alla nya objekt läggs till i registret.</span><span class="sxs-lookup"><span data-stu-id="4c01a-172">As a result, the second dir command shows that all of the new items are added to the registry.</span></span>

### <span data-ttu-id="4c01a-173">Exempel 7: återställa en transaktion som inte slutförs inom en angiven tid</span><span class="sxs-lookup"><span data-stu-id="4c01a-173">Example 7: Roll back a transaction that does not finish in a specified time</span></span>

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

<span data-ttu-id="4c01a-174">Det här kommandot använder *timeout* -parametern för **Start-Transaction** för att starta en transaktion som måste slutföras inom två minuter.</span><span class="sxs-lookup"><span data-stu-id="4c01a-174">This command uses the *Timeout* parameter of **Start-Transaction** to start a transaction that must be completed within two minutes.</span></span>
<span data-ttu-id="4c01a-175">Om transaktionen inte är avslutad när tids gränsen går ut, återställs den automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-175">If the transaction is not finished when the time-out expires, it is rolled back automatically.</span></span>

<span data-ttu-id="4c01a-176">När tids gränsen går ut får du inget meddelande, men egenskapen **status** för Transaction-objektet är inställd på återställd och kommandon som använder parametern *UseTransaction* kan inte köras.</span><span class="sxs-lookup"><span data-stu-id="4c01a-176">When the time-out expires, you are not notified, but the **Status** property of the transaction object is set to RolledBack and commands that use the *UseTransaction* parameter fail.</span></span>

## <span data-ttu-id="4c01a-177">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="4c01a-177">PARAMETERS</span></span>

### <span data-ttu-id="4c01a-178">– Oberoende</span><span class="sxs-lookup"><span data-stu-id="4c01a-178">-Independent</span></span>
<span data-ttu-id="4c01a-179">Anger att den här cmdleten startar en transaktion som är oberoende av pågående transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4c01a-179">Indicates that this cmdlet starts a transaction that is independent of any transactions in progress.</span></span>
<span data-ttu-id="4c01a-180">Om du använder **Start transaktion** medan en annan transaktion pågår läggs en ny prenumerant som standard till i den pågående transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-180">By default, if you use **Start-Transaction** while another transaction is in progress, a new subscriber is added to the transaction in progress.</span></span>
<span data-ttu-id="4c01a-181">Den här parametern har endast en funktion när en transaktion redan pågår i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-181">This parameter has an effect only when a transaction is already in progress in the session.</span></span>

<span data-ttu-id="4c01a-182">Om du använder **Start transaktion** medan en transaktion pågår, används det befintliga transaktionsobjektet som standard och antalet prenumeranter ökar.</span><span class="sxs-lookup"><span data-stu-id="4c01a-182">By default, if you use **Start-Transaction** while a transaction is in progress, the existing transaction object is reused and the subscriber count is incremented.</span></span>
<span data-ttu-id="4c01a-183">Resultatet är ungefär som att koppla den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-183">The effect is much like joining the original transaction.</span></span>
<span data-ttu-id="4c01a-184">Kommandot Undo-Transaction återställer hela transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-184">An Undo-Transaction command rolls back the whole the transaction.</span></span>
<span data-ttu-id="4c01a-185">För att slutföra transaktionen måste du ange ett Complete-Transaction-kommando för varje prenumerant.</span><span class="sxs-lookup"><span data-stu-id="4c01a-185">To complete the transaction, you must enter a Complete-Transaction command for each subscriber.</span></span>
<span data-ttu-id="4c01a-186">Eftersom de flesta pågående transaktioner samtidigt är relaterade är standardvärdet tillräckligt för de flesta användnings områden.</span><span class="sxs-lookup"><span data-stu-id="4c01a-186">Because most transactions that are in progress at the same time are related, the default is sufficient for most uses.</span></span>

<span data-ttu-id="4c01a-187">Om du anger den *oberoende* parametern skapar denna cmdlet en ny transaktion som kan slutföras eller tas bort utan att den ursprungliga transaktionen påverkas.</span><span class="sxs-lookup"><span data-stu-id="4c01a-187">If you specify the *Independent* parameter, this cmdlet creates a new transaction that can be completed or undone without affecting the original transaction.</span></span>
<span data-ttu-id="4c01a-188">Men eftersom bara en transaktion kan vara aktiv i taget, måste du slutföra eller återställa den nya transaktionen innan du återupptar arbetet med den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4c01a-188">However, because only one transaction can be active at a time, you must complete or roll back the new transaction before resuming work on the original transaction.</span></span>

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

### <span data-ttu-id="4c01a-189">-RollbackPreference</span><span class="sxs-lookup"><span data-stu-id="4c01a-189">-RollbackPreference</span></span>
<span data-ttu-id="4c01a-190">Anger de villkor under vilka en transaktion återställs automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-190">Specifies the conditions under which a transaction is automatically rolled back.</span></span>
<span data-ttu-id="4c01a-191">De acceptabla värdena för den här parametern är:</span><span class="sxs-lookup"><span data-stu-id="4c01a-191">The acceptable values for this parameter are:</span></span>

- <span data-ttu-id="4c01a-192">Fel.</span><span class="sxs-lookup"><span data-stu-id="4c01a-192">Error.</span></span>
<span data-ttu-id="4c01a-193">Transaktionen återställs automatiskt om det inträffar ett fel som avslutas eller inte avslutas.</span><span class="sxs-lookup"><span data-stu-id="4c01a-193">The transaction is rolled back automatically if a terminating or non-terminating error occurs.</span></span>
- <span data-ttu-id="4c01a-194">TerminatingError.</span><span class="sxs-lookup"><span data-stu-id="4c01a-194">TerminatingError.</span></span>
<span data-ttu-id="4c01a-195">Transaktionen återställs automatiskt om ett avslutande fel inträffar.</span><span class="sxs-lookup"><span data-stu-id="4c01a-195">The transaction is rolled back automatically if a terminating error occurs.</span></span>
- <span data-ttu-id="4c01a-196">Helt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-196">Never.</span></span>
<span data-ttu-id="4c01a-197">Transaktionen återställs aldrig automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-197">The transaction is never rolled back automatically.</span></span>

<span data-ttu-id="4c01a-198">Standardvärdet är error.</span><span class="sxs-lookup"><span data-stu-id="4c01a-198">The default value is Error.</span></span>

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

### <span data-ttu-id="4c01a-199">-Timeout</span><span class="sxs-lookup"><span data-stu-id="4c01a-199">-Timeout</span></span>
<span data-ttu-id="4c01a-200">Anger den maximala tiden, i minuter, som transaktionen är aktiv.</span><span class="sxs-lookup"><span data-stu-id="4c01a-200">Specifies the maximum time, in minutes, that the transaction is active.</span></span>
<span data-ttu-id="4c01a-201">När tids gränsen går ut återställs transaktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4c01a-201">When the time-out expires, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="4c01a-202">Som standard finns det ingen tids gräns för transaktioner som startas på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="4c01a-202">By default, there is no time-out for transactions that are started at the command line.</span></span>
<span data-ttu-id="4c01a-203">När transaktioner startas av ett skript är standard tids gränsen 30 minuter.</span><span class="sxs-lookup"><span data-stu-id="4c01a-203">When transactions are started by a script, the default time-out is 30 minutes.</span></span>

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

### <span data-ttu-id="4c01a-204">-Confirm</span><span class="sxs-lookup"><span data-stu-id="4c01a-204">-Confirm</span></span>
<span data-ttu-id="4c01a-205">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4c01a-205">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="4c01a-206">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="4c01a-206">-WhatIf</span></span>
<span data-ttu-id="4c01a-207">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="4c01a-207">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="4c01a-208">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="4c01a-208">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="4c01a-209">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="4c01a-209">CommonParameters</span></span>
<span data-ttu-id="4c01a-210">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="4c01a-210">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="4c01a-211">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="4c01a-211">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="4c01a-212">INDATA</span><span class="sxs-lookup"><span data-stu-id="4c01a-212">INPUTS</span></span>

### <span data-ttu-id="4c01a-213">Inget</span><span class="sxs-lookup"><span data-stu-id="4c01a-213">None</span></span>
<span data-ttu-id="4c01a-214">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="4c01a-214">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="4c01a-215">UTDATA</span><span class="sxs-lookup"><span data-stu-id="4c01a-215">OUTPUTS</span></span>

### <span data-ttu-id="4c01a-216">Inget</span><span class="sxs-lookup"><span data-stu-id="4c01a-216">None</span></span>
<span data-ttu-id="4c01a-217">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="4c01a-217">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="4c01a-218">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="4c01a-218">NOTES</span></span>

## <span data-ttu-id="4c01a-219">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="4c01a-219">RELATED LINKS</span></span>

[<span data-ttu-id="4c01a-220">Slutförd transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-220">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="4c01a-221">Hämta transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-221">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="4c01a-222">Ångra-transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-222">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="4c01a-223">Använd transaktion</span><span class="sxs-lookup"><span data-stu-id="4c01a-223">Use-Transaction</span></span>](Use-Transaction.md)
