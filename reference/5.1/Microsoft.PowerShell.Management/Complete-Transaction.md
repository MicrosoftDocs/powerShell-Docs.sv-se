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
# <span data-ttu-id="b04f3-103">Complete-Transaction</span><span class="sxs-lookup"><span data-stu-id="b04f3-103">Complete-Transaction</span></span>

## <span data-ttu-id="b04f3-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="b04f3-104">SYNOPSIS</span></span>
<span data-ttu-id="b04f3-105">Genomför den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-105">Commits the active transaction.</span></span>

## <span data-ttu-id="b04f3-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="b04f3-106">SYNTAX</span></span>

```
Complete-Transaction [-WhatIf] [-Confirm] [<CommonParameters>]
```

## <span data-ttu-id="b04f3-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="b04f3-107">DESCRIPTION</span></span>
<span data-ttu-id="b04f3-108">Cmdleten **Complete-Transaction** genomför en aktiv transaktion.</span><span class="sxs-lookup"><span data-stu-id="b04f3-108">The **Complete-Transaction** cmdlet commits an active transaction.</span></span>
<span data-ttu-id="b04f3-109">När du genomför en transaktion, slutförs kommandona i transaktionen och de data som påverkas av kommandona ändras.</span><span class="sxs-lookup"><span data-stu-id="b04f3-109">When you commit a transaction, the commands in the transaction are finalized and the data affected by the commands is changed.</span></span>

<span data-ttu-id="b04f3-110">Om transaktionen innehåller flera prenumeranter måste du ange ett **fullständigt transaktions** kommando för varje Start-Transaction-kommando för att genomföra transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-110">If the transaction includes multiple subscribers, to commit the transaction, you must enter one **Complete-Transaction** command for every Start-Transaction command.</span></span>

<span data-ttu-id="b04f3-111">Cmdleten **Complete-Transaction** är en uppsättning cmdletar som stöder funktionen transaktioner i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b04f3-111">The **Complete-Transaction** cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="b04f3-112">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="b04f3-112">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="b04f3-113">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="b04f3-113">EXAMPLES</span></span>

### <span data-ttu-id="b04f3-114">Exempel 1: genomför en transaktion</span><span class="sxs-lookup"><span data-stu-id="b04f3-114">Example 1: Commit a transaction</span></span>

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

<span data-ttu-id="b04f3-115">Det här exemplet visar vad som händer när du använder cmdleten **Complete-Transaction** för att genomföra en transaktion.</span><span class="sxs-lookup"><span data-stu-id="b04f3-115">This example shows what happens when you use the **Complete-Transaction** cmdlet to commit a transaction.</span></span>

<span data-ttu-id="b04f3-116">Kommandot **Start Transaction** startar transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-116">The **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="b04f3-117">Kommandot New-Item använder parametern *UseTransaction* för att inkludera kommandot i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-117">The New-Item command uses the *UseTransaction* parameter to include the command in the transaction.</span></span>

<span data-ttu-id="b04f3-118">Det första dir-kommandot (Get-ChildItem) visar att det nya objektet ännu inte har lagts till i registret.</span><span class="sxs-lookup"><span data-stu-id="b04f3-118">The first dir (Get-ChildItem) command shows that the new item has not yet been added to the registry.</span></span>

<span data-ttu-id="b04f3-119">Kommandot **fullständig transaktion** genomför transaktionen, vilket gör att register ändringen träder i kraft.</span><span class="sxs-lookup"><span data-stu-id="b04f3-119">The **Complete-Transaction** command commits the transaction, which makes the registry change effective.</span></span>
<span data-ttu-id="b04f3-120">Därför visar det andra kommandot dir att registret har ändrats.</span><span class="sxs-lookup"><span data-stu-id="b04f3-120">As a result, the second dir command shows that the registry is changed.</span></span>

### <span data-ttu-id="b04f3-121">Exempel 2: genomför en transaktion som har fler än en prenumerant</span><span class="sxs-lookup"><span data-stu-id="b04f3-121">Example 2: Commit a transaction that has more than one subscriber</span></span>

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

<span data-ttu-id="b04f3-122">Det här exemplet visar hur du använder **Slutför transaktion** för att genomföra en transaktion som har fler än en prenumerant.</span><span class="sxs-lookup"><span data-stu-id="b04f3-122">This example shows how to use **Complete-Transaction** to commit a transaction that has more than one subscriber.</span></span>

<span data-ttu-id="b04f3-123">Om du vill genomföra en transaktion med flera prenumerationer måste du ange ett **fullständigt transaktions** kommando för varje **Start transaktions** kommando.</span><span class="sxs-lookup"><span data-stu-id="b04f3-123">To commit a multi-subscriber transaction, you must enter one **Complete-Transaction** command for every **Start-Transaction** command.</span></span>
<span data-ttu-id="b04f3-124">Data ändras endast när kommandot slutlig **slutförd transaktion** skickas.</span><span class="sxs-lookup"><span data-stu-id="b04f3-124">The data is changed only when the final **Complete-Transaction** command is submitted.</span></span>

<span data-ttu-id="b04f3-125">I demonstrations syfte visar det här exemplet en serie kommandon som anges på kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b04f3-125">For demonstration purposes, this example shows a series of commands entered at the command line.</span></span>
<span data-ttu-id="b04f3-126">I praktiken kommer transaktioner förmodligen att köras i skript, med den sekundära transaktionen som körs av en funktion eller ett hjälp skript som anropas av huvud skriptet.</span><span class="sxs-lookup"><span data-stu-id="b04f3-126">In practice, transactions are likely to be run in scripts, with the secondary transaction being run by a function or helper script that is called by the main script.</span></span>

<span data-ttu-id="b04f3-127">I det här exemplet startar ett kommando för att **Starta** transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-127">In this example, a **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="b04f3-128">Ett **nytt-objekt-** kommando med parametern *UseTransaction* lägger till företags nyckeln i program varu nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b04f3-128">A **New-Item** command with the *UseTransaction* parameter adds the MyCompany key to the Software key.</span></span>
<span data-ttu-id="b04f3-129">Även om cmdleten **New-item** returnerar ett nyckel objekt, ändras inte data i registret än.</span><span class="sxs-lookup"><span data-stu-id="b04f3-129">Although the **New-Item** cmdlet returns a key object, the data in the registry is not yet changed.</span></span>

<span data-ttu-id="b04f3-130">Ett andra **Start transaktions** kommando lägger till en andra prenumerant i den befintliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-130">A second **Start-Transaction** command adds a second subscriber to the existing transaction.</span></span>
<span data-ttu-id="b04f3-131">Cmdleten **Get-Transaction** bekräftar att antalet prenumeranter är 2.</span><span class="sxs-lookup"><span data-stu-id="b04f3-131">The **Get-Transaction** cmdlet confirms that the subscriber count is 2.</span></span>
<span data-ttu-id="b04f3-132">Ett New-ItemProperty-kommando med parametern *UseTransaction* lägger till en register post i den nya företags nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b04f3-132">A New-ItemProperty command with the *UseTransaction* parameter adds a registry entry to the new MyCompany key.</span></span>
<span data-ttu-id="b04f3-133">Kommandot returnerar ett värde, men registret ändras inte.</span><span class="sxs-lookup"><span data-stu-id="b04f3-133">Again, the command returns a value, but the registry is not changed.</span></span>

<span data-ttu-id="b04f3-134">Det första **fullständiga transaktions** kommandot minskar antalet prenumeranter med 1.</span><span class="sxs-lookup"><span data-stu-id="b04f3-134">The first **Complete-Transaction** command reduces the subscriber count by 1.</span></span>
<span data-ttu-id="b04f3-135">Detta bekräftas av ett **Get-Transaction-** kommando.</span><span class="sxs-lookup"><span data-stu-id="b04f3-135">This is confirmed by a **Get-Transaction** command.</span></span>
<span data-ttu-id="b04f3-136">Men inga data ändras, så som de visas i kommandot dir m \* ( **Get-ChildItem** ).</span><span class="sxs-lookup"><span data-stu-id="b04f3-136">However, no data is changed, as evidenced by a dir m\* ( **Get-ChildItem** ) command.</span></span>

<span data-ttu-id="b04f3-137">Det andra kommandot **fullständig transaktion** genomför hela transaktionen och ändrar data i registret.</span><span class="sxs-lookup"><span data-stu-id="b04f3-137">The second **Complete-Transaction** command commits the entire transaction and changes the data in the registry.</span></span>
<span data-ttu-id="b04f3-138">Detta bekräftas av ett andra dir m \*-kommando som visar ändringarna.</span><span class="sxs-lookup"><span data-stu-id="b04f3-138">This is confirmed by a second dir m\* command, which shows the changes.</span></span>

### <span data-ttu-id="b04f3-139">Exempel 3: utföra en transaktion som inte ändrar några data</span><span class="sxs-lookup"><span data-stu-id="b04f3-139">Example 3: Perform a transaction that does not change any data</span></span>

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

<span data-ttu-id="b04f3-140">Det här exemplet visar värdet för att använda get- \* commands och andra kommandon som inte ändrar data i en transaktion.</span><span class="sxs-lookup"><span data-stu-id="b04f3-140">This example shows the value of using Get-\* commands, and other commands that do not change data, in a transaction.</span></span>
<span data-ttu-id="b04f3-141">När ett get- \* kommando används i en transaktion hämtas de objekt som ingår i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-141">When a Get-\* command is used in a transaction, it gets the objects that are part of the transaction.</span></span>
<span data-ttu-id="b04f3-142">På så sätt kan du förhandsgranska ändringarna i transaktionen innan du genomför ändringarna.</span><span class="sxs-lookup"><span data-stu-id="b04f3-142">This allows you to preview the changes in the transaction before the changes are committed.</span></span>

<span data-ttu-id="b04f3-143">I det här exemplet startas en transaktion.</span><span class="sxs-lookup"><span data-stu-id="b04f3-143">In this example, a transaction is started.</span></span>
<span data-ttu-id="b04f3-144">Ett New-Item-kommando med parametern *UseTransaction* lägger till en ny nyckel i registret som en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-144">A New-Item command with the *UseTransaction* parameter adds a new key to the registry as part of the transaction.</span></span>

<span data-ttu-id="b04f3-145">Eftersom den nya register nyckeln inte läggs till i registret förrän kommandot **Slutför transaktion** körs, visar ett enkelt dir-kommando ( **Get-ChildItem** ) registret utan den nya nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b04f3-145">Because the new registry key is not added to the registry until the **Complete-Transaction** command is run, a simple dir ( **Get-ChildItem** ) command shows the registry without the new key.</span></span>

<span data-ttu-id="b04f3-146">Men när du lägger till parametern *UseTransaction* till kommandot dir blir kommandot en del av transaktionen och det hämtar objekten i transaktionen även om de inte har lagts till i data.</span><span class="sxs-lookup"><span data-stu-id="b04f3-146">However, when you add the *UseTransaction* parameter to the dir command, the command becomes part of the transaction, and it gets the items in the transaction even if they are not yet added to the data.</span></span>

## <span data-ttu-id="b04f3-147">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="b04f3-147">PARAMETERS</span></span>

### <span data-ttu-id="b04f3-148">-Confirm</span><span class="sxs-lookup"><span data-stu-id="b04f3-148">-Confirm</span></span>
<span data-ttu-id="b04f3-149">Uppmanar dig att bekräfta innan du kör cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b04f3-149">Prompts you for confirmation before running the cmdlet.</span></span>

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

### <span data-ttu-id="b04f3-150">-WhatIf</span><span class="sxs-lookup"><span data-stu-id="b04f3-150">-WhatIf</span></span>
<span data-ttu-id="b04f3-151">Visar vad som skulle hända om cmdleten kördes.</span><span class="sxs-lookup"><span data-stu-id="b04f3-151">Shows what would happen if the cmdlet runs.</span></span>
<span data-ttu-id="b04f3-152">Cmdleten körs inte.</span><span class="sxs-lookup"><span data-stu-id="b04f3-152">The cmdlet is not run.</span></span>

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

### <span data-ttu-id="b04f3-153">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="b04f3-153">CommonParameters</span></span>
<span data-ttu-id="b04f3-154">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="b04f3-154">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="b04f3-155">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="b04f3-155">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="b04f3-156">INDATA</span><span class="sxs-lookup"><span data-stu-id="b04f3-156">INPUTS</span></span>

### <span data-ttu-id="b04f3-157">Inget</span><span class="sxs-lookup"><span data-stu-id="b04f3-157">None</span></span>
<span data-ttu-id="b04f3-158">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b04f3-158">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="b04f3-159">UTDATA</span><span class="sxs-lookup"><span data-stu-id="b04f3-159">OUTPUTS</span></span>

### <span data-ttu-id="b04f3-160">Inget</span><span class="sxs-lookup"><span data-stu-id="b04f3-160">None</span></span>
<span data-ttu-id="b04f3-161">Denna cmdlet genererar inga utdata.</span><span class="sxs-lookup"><span data-stu-id="b04f3-161">This cmdlet does not generate any output.</span></span>

## <span data-ttu-id="b04f3-162">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="b04f3-162">NOTES</span></span>

* <span data-ttu-id="b04f3-163">Du kan inte återställa en transaktion som har genomförts eller allokera en transaktion som har återställts.</span><span class="sxs-lookup"><span data-stu-id="b04f3-163">You cannot roll back a transaction that has been committed, or commit a transaction that has been rolled back.</span></span>

  <span data-ttu-id="b04f3-164">Du kan inte återställa någon annan transaktion än den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-164">You cannot roll back any transaction other than the active transaction.</span></span>
<span data-ttu-id="b04f3-165">Om du vill återställa en annan transaktion måste du först genomföra eller återställa den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-165">To roll back a different transaction, you must first commit or roll back the active transaction.</span></span>

  <span data-ttu-id="b04f3-166">Om någon del av en transaktion inte kan genomföras, till exempel när ett kommando i transaktionen resulterar i ett fel, återställs hela transaktionen.</span><span class="sxs-lookup"><span data-stu-id="b04f3-166">By default, if any part of a transaction cannot be committed, such as when a command in the transaction results in an error, the entire transaction is rolled back.</span></span>

*

## <span data-ttu-id="b04f3-167">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="b04f3-167">RELATED LINKS</span></span>

[<span data-ttu-id="b04f3-168">Hämta transaktion</span><span class="sxs-lookup"><span data-stu-id="b04f3-168">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="b04f3-169">Starta transaktion</span><span class="sxs-lookup"><span data-stu-id="b04f3-169">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="b04f3-170">Ångra-transaktion</span><span class="sxs-lookup"><span data-stu-id="b04f3-170">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="b04f3-171">Använd transaktion</span><span class="sxs-lookup"><span data-stu-id="b04f3-171">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="b04f3-172">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="b04f3-172">Get-ChildItem</span></span>](Get-ChildItem.md)

[<span data-ttu-id="b04f3-173">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="b04f3-173">New-Item</span></span>](New-Item.md)

[<span data-ttu-id="b04f3-174">New-ItemProperty</span><span class="sxs-lookup"><span data-stu-id="b04f3-174">New-ItemProperty</span></span>](New-ItemProperty.md)
