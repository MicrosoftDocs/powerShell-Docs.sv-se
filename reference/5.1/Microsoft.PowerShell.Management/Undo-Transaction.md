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
# <span data-ttu-id="609a8-103">Undo-Transaction</span><span class="sxs-lookup"><span data-stu-id="609a8-103">Undo-Transaction</span></span>

## <span data-ttu-id="609a8-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="609a8-104">SYNOPSIS</span></span>
<span data-ttu-id="609a8-105">Återställer den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-105">Rolls back the active transaction.</span></span>

## <span data-ttu-id="609a8-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="609a8-106">SYNTAX</span></span>

```
Undo-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="609a8-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="609a8-107">DESCRIPTION</span></span>
<span data-ttu-id="609a8-108">Cmdleten **Undo-Transaction** rullar tillbaka den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-108">The **Undo-Transaction** cmdlet rolls back the active transaction.</span></span>
<span data-ttu-id="609a8-109">När du återställer en transaktion ignoreras de ändringar som utfördes av kommandona i transaktionen och data återställs till dess ursprungliga form.</span><span class="sxs-lookup"><span data-stu-id="609a8-109">When you roll back a transaction, the changes that were made by the commands in the transaction are discarded and the data is restored to its original form.</span></span>

<span data-ttu-id="609a8-110">Om transaktionen innehåller flera prenumeranter återställs hela transaktionen för alla prenumeranter via kommandot **Ångra transaktion** .</span><span class="sxs-lookup"><span data-stu-id="609a8-110">If the transaction includes multiple subscribers, an **Undo-Transaction** command rolls back the whole transaction for all subscribers.</span></span>

<span data-ttu-id="609a8-111">Som standard återställs transaktioner automatiskt om ett kommando i transaktionen genererar ett fel.</span><span class="sxs-lookup"><span data-stu-id="609a8-111">By default, transactions are rolled back automatically if any command in the transaction generates an error.</span></span>
<span data-ttu-id="609a8-112">Transaktioner kan dock startas med hjälp av en annan återställnings inställning och du kan använda den här cmdleten för att återställa den aktiva transaktionen när som helst.</span><span class="sxs-lookup"><span data-stu-id="609a8-112">However, transactions can be started by using a different rollback preference and you can use this cmdlet to roll back the active transaction at any time.</span></span>

<span data-ttu-id="609a8-113">Cmdleten **Undo-Transaction** är en uppsättning cmdlets som stöder funktionen transaktioner i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="609a8-113">The **Undo-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="609a8-114">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="609a8-114">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="609a8-115">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="609a8-115">EXAMPLES</span></span>

### <span data-ttu-id="609a8-116">Exempel 1: Återställ den aktuella transaktionen</span><span class="sxs-lookup"><span data-stu-id="609a8-116">Example 1: Roll back the current transaction</span></span>

```
PS C:\> Undo-Transaction
```

<span data-ttu-id="609a8-117">Detta kommando återställer den aktuella, aktiva, transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-117">This command rolls back the current, active, transaction.</span></span>

### <span data-ttu-id="609a8-118">Exempel 2: starta och återställa en transaktion</span><span class="sxs-lookup"><span data-stu-id="609a8-118">Example 2: Start and roll back a transaction</span></span>

```
PS C:\> cd hkcu:\software
PS HKCU:\Software> Start-Transaction
PS HKCU:\Software> New-Item -Path "ContosoCompany" -UseTransaction
PS HKCU:\Software> Undo-Transaction
```

<span data-ttu-id="609a8-119">Det här exemplet startar en transaktion och slår sedan tillbaka den igen.</span><span class="sxs-lookup"><span data-stu-id="609a8-119">This example starts a transaction and then rolls it back.</span></span>
<span data-ttu-id="609a8-120">Därför görs inga ändringar i registret.</span><span class="sxs-lookup"><span data-stu-id="609a8-120">As a result, no changes are made to the registry.</span></span>

### <span data-ttu-id="609a8-121">Exempel 3: återställa en transaktion för alla prenumeranter</span><span class="sxs-lookup"><span data-stu-id="609a8-121">Example 3: Roll back a transaction for all subscribers</span></span>

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

<span data-ttu-id="609a8-122">Det här exemplet visar att hela transaktionen återställs för alla prenumeranter när en prenumerant återställer en transaktion.</span><span class="sxs-lookup"><span data-stu-id="609a8-122">This example demonstrates that when any subscriber rolls back a transaction, the whole transaction is rolled back for all subscribers.</span></span>

<span data-ttu-id="609a8-123">Det första kommandot ändrar platsen till register nyckeln HKCU: \ Software.</span><span class="sxs-lookup"><span data-stu-id="609a8-123">The first command changes the location to the HKCU:\Software registry key.</span></span>

<span data-ttu-id="609a8-124">Det andra kommandot startar en transaktion.</span><span class="sxs-lookup"><span data-stu-id="609a8-124">The second command starts a transaction.</span></span>

<span data-ttu-id="609a8-125">Det tredje kommandot använder cmdleten New-Item för att skapa en ny register nyckel.</span><span class="sxs-lookup"><span data-stu-id="609a8-125">The third command uses the New-Item cmdlet to create a new registry key.</span></span>
<span data-ttu-id="609a8-126">Kommandot använder parametern *UseTransaction* för att inkludera ändringen i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-126">The command uses the *UseTransaction* parameter to include the change in the transaction.</span></span>

<span data-ttu-id="609a8-127">Det fjärde kommandot använder cmdleten Get-Transaction för att hämta den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-127">The fourth command uses the Get-Transaction cmdlet to get the active transaction.</span></span>
<span data-ttu-id="609a8-128">Observera att statusen är aktiv och antalet prenumeranter är 1.</span><span class="sxs-lookup"><span data-stu-id="609a8-128">Notice that the status is Active and the subscriber count is 1.</span></span>

<span data-ttu-id="609a8-129">Det femte kommandot använder kommandot Start-Transaction igen.</span><span class="sxs-lookup"><span data-stu-id="609a8-129">The fifth command uses the Start-Transaction command again.</span></span>
<span data-ttu-id="609a8-130">Normalt sker start av en transaktion medan en annan transaktion pågår när ett skript som används av huvud transaktionen inkluderar en egen fullständig transaktion.</span><span class="sxs-lookup"><span data-stu-id="609a8-130">Typically, starting a transaction while another transaction is in progress occurs when a script that is used by the main transaction includes its own complete transaction.</span></span>
<span data-ttu-id="609a8-131">Det här exemplet utförs interaktivt så att du kan undersöka det i olika steg.</span><span class="sxs-lookup"><span data-stu-id="609a8-131">This example is performed interactively so that you can examine it in stages.</span></span>
<span data-ttu-id="609a8-132">När du kör ett kommando för att **Starta transaktion** medan en annan transaktion pågår, är kommandona kopplade till den befintliga transaktionen som en ny prenumerant och antalet prenumeranter ökar.</span><span class="sxs-lookup"><span data-stu-id="609a8-132">When you run a **Start-Transaction** command while another transaction is in progress, the commands join the existing transaction as a new subscriber and the subscriber count is incremented.</span></span>

<span data-ttu-id="609a8-133">Det sjätte kommandot använder cmdleten **Get-Transaction** för att hämta den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-133">The sixth command uses the **Get-Transaction** cmdlet to get the active transaction.</span></span>
<span data-ttu-id="609a8-134">Observera att antalet prenumeranter nu är 2.</span><span class="sxs-lookup"><span data-stu-id="609a8-134">Notice that the subscriber count is now 2.</span></span>

<span data-ttu-id="609a8-135">Det sjunde kommandot använder **Undo-Transaction** för att återställa transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-135">The seventh command uses **Undo-Transaction** to roll back the transaction.</span></span>
<span data-ttu-id="609a8-136">Det här kommandot returnerar inga objekt.</span><span class="sxs-lookup"><span data-stu-id="609a8-136">This command does not return any objects.</span></span>

<span data-ttu-id="609a8-137">Det sista kommandot är ett **Get-Transaction-** kommando som hämtar det aktiva, eller i det här fallet den senast aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-137">The final command is a **Get-Transaction** command that gets the active, or in this case, the most recently active, transaction.</span></span>
<span data-ttu-id="609a8-138">Resultaten visar att transaktionen återställs och att antalet prenumeranter är 0, vilket visar att transaktionen har återställts för alla prenumeranter.</span><span class="sxs-lookup"><span data-stu-id="609a8-138">The results show that the transaction is rolled back, and that the subscriber count is 0, showing that the transaction was rolled back for all subscribers.</span></span>

## <span data-ttu-id="609a8-139">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="609a8-139">PARAMETERS</span></span>

### <span data-ttu-id="609a8-140">-Confirm</span><span class="sxs-lookup"><span data-stu-id="609a8-140">-Confirm</span></span>
<span data-ttu-id="609a8-141">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="609a8-141">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="609a8-142">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="609a8-142">-WhatIf</span></span>
<span data-ttu-id="609a8-143">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="609a8-143">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="609a8-144">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="609a8-144">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="609a8-145">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="609a8-145">CommonParameters</span></span>
<span data-ttu-id="609a8-146">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="609a8-146">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="609a8-147">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="609a8-147">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="609a8-148">INDATA</span><span class="sxs-lookup"><span data-stu-id="609a8-148">INPUTS</span></span>

### <span data-ttu-id="609a8-149">Inget</span><span class="sxs-lookup"><span data-stu-id="609a8-149">None</span></span>
<span data-ttu-id="609a8-150">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="609a8-150">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="609a8-151">UTDATA</span><span class="sxs-lookup"><span data-stu-id="609a8-151">OUTPUTS</span></span>

### <span data-ttu-id="609a8-152">Inget</span><span class="sxs-lookup"><span data-stu-id="609a8-152">None</span></span>
<span data-ttu-id="609a8-153">Denna cmdlet returnerar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="609a8-153">This cmdlet does not return any output.</span></span>

## <span data-ttu-id="609a8-154">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="609a8-154">NOTES</span></span>

* <span data-ttu-id="609a8-155">Det går inte att återställa en transaktion som har genomförts.</span><span class="sxs-lookup"><span data-stu-id="609a8-155">You cannot roll back a transaction that has been committed.</span></span>

  <span data-ttu-id="609a8-156">Du kan inte återställa någon annan transaktion än den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-156">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="609a8-157">Om du vill återställa en annan, oberoende transaktion måste du först genomföra eller återställa den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-157">To roll back a different, independent transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="609a8-158">Att återställa transaktionen avslutar transaktionen.</span><span class="sxs-lookup"><span data-stu-id="609a8-158">Rolling back the transaction ends the transaction.</span></span>
<span data-ttu-id="609a8-159">Om du vill använda en transaktion igen måste du starta en ny transaktion.</span><span class="sxs-lookup"><span data-stu-id="609a8-159">To use a transaction again, you must start a new transaction.</span></span>

## <span data-ttu-id="609a8-160">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="609a8-160">RELATED LINKS</span></span>

[<span data-ttu-id="609a8-161">Slutförd transaktion</span><span class="sxs-lookup"><span data-stu-id="609a8-161">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="609a8-162">Hämta transaktion</span><span class="sxs-lookup"><span data-stu-id="609a8-162">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="609a8-163">Starta transaktion</span><span class="sxs-lookup"><span data-stu-id="609a8-163">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="609a8-164">Använd transaktion</span><span class="sxs-lookup"><span data-stu-id="609a8-164">Use-Transaction</span></span>](Use-Transaction.md)
