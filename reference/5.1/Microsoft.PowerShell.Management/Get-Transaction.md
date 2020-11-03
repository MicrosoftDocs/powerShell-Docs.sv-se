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
# <span data-ttu-id="9897c-103">Get-Transaction</span><span class="sxs-lookup"><span data-stu-id="9897c-103">Get-Transaction</span></span>

## <span data-ttu-id="9897c-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="9897c-104">SYNOPSIS</span></span>
<span data-ttu-id="9897c-105">Hämtar den aktuella (aktiva) transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-105">Gets the current (active) transaction.</span></span>

## <span data-ttu-id="9897c-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="9897c-106">SYNTAX</span></span>

```
Get-Transaction [<CommonParameters>]
```

## <span data-ttu-id="9897c-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="9897c-107">DESCRIPTION</span></span>
<span data-ttu-id="9897c-108">Cmdleten **Get-Transaction** hämtar ett objekt som representerar den aktuella transaktionen i sessionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-108">The **Get-Transaction** cmdlet gets an object that represents the current transaction in the session.</span></span>

<span data-ttu-id="9897c-109">Denna cmdlet returnerar aldrig fler än ett objekt, eftersom endast en transaktion är aktiv i taget.</span><span class="sxs-lookup"><span data-stu-id="9897c-109">This cmdlet never returns more than one object, because only one transaction is active at a time.</span></span>
<span data-ttu-id="9897c-110">Om du startar en eller flera oberoende transaktioner (genom att använda den oberoende parametern för start transaktion) är den senast startade transaktionen aktiv och det är den transaktion som **erhåller transaktions** returer.</span><span class="sxs-lookup"><span data-stu-id="9897c-110">If you start one or more independent transactions (by using the Independent parameter of Start-Transaction), the most recently started transaction is active, and that is the transaction that **Get-Transaction** returns.</span></span>

<span data-ttu-id="9897c-111">När alla aktiva transaktioner antingen har återställts eller bekräftats, visar denna cmdlet den transaktion som senast var aktiv i sessionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-111">When all active transactions have either been rolled back or committed, this cmdlet shows the transaction that was most recently active in the session.</span></span>

<span data-ttu-id="9897c-112">Denna cmdlet är en uppsättning cmdletar som har stöd för funktionen Transactions i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="9897c-112">This cmdlet is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="9897c-113">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="9897c-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="9897c-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="9897c-114">EXAMPLES</span></span>

### <span data-ttu-id="9897c-115">Exempel 1: hämta den aktuella transaktionen</span><span class="sxs-lookup"><span data-stu-id="9897c-115">Example 1: Get the current transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> Get-Transaction

RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="9897c-116">Det här kommandot använder cmdleten Get-Transaction för att hämta den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-116">This command uses the Get-Transaction cmdlet to get the current transaction.</span></span>

### <span data-ttu-id="9897c-117">Exempel 2: Visa egenskaper och metoder för Transaction-objektet</span><span class="sxs-lookup"><span data-stu-id="9897c-117">Example 2: Show the properties and methods of the transaction object</span></span>

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

<span data-ttu-id="9897c-118">Det här kommandot använder Get-Member-cmdleten för att visa egenskaper och metoder för Transaction-objektet.</span><span class="sxs-lookup"><span data-stu-id="9897c-118">This command uses the Get-Member cmdlet to show the properties and methods of the transaction object.</span></span>

### <span data-ttu-id="9897c-119">Exempel 3: Visa egenskapsvärdena för en återställd back transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-119">Example 3: Show the property values of a rolled back transaction</span></span>

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

<span data-ttu-id="9897c-120">Det här kommandot visar egenskaps värden för ett transaktions objekt för en transaktion som har återställts.</span><span class="sxs-lookup"><span data-stu-id="9897c-120">This command shows the property values of a transaction object for a transaction that has been rolled back.</span></span>

### <span data-ttu-id="9897c-121">Exempel 4: Visa egenskaps värden för en allokerad transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-121">Example 4: Show the property values of a committed transaction</span></span>

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

<span data-ttu-id="9897c-122">Det här kommandot visar egenskaps värden för ett transaktions objekt för en transaktion som har genomförts.</span><span class="sxs-lookup"><span data-stu-id="9897c-122">This command shows the property values of a transaction object for a transaction that has been committed.</span></span>

### <span data-ttu-id="9897c-123">Exempel 5: starta en transaktion medan en annan pågår</span><span class="sxs-lookup"><span data-stu-id="9897c-123">Example 5: Start a transaction while another is in progress</span></span>

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

<span data-ttu-id="9897c-124">I det här exemplet visas effekterna av transaktions objekt som startar en transaktion medan en annan transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="9897c-124">This example shows the effect on the transaction object of starting a transaction while another transaction is in progress.</span></span>
<span data-ttu-id="9897c-125">Detta inträffar vanligt vis när ett skript som kör en transaktion innehåller en funktion eller anropar ett skript som innehåller en annan fullständig transaktion.</span><span class="sxs-lookup"><span data-stu-id="9897c-125">Typically, this happens when a script that runs a transaction includes a function or calls a script that contains another complete transaction.</span></span>

<span data-ttu-id="9897c-126">Om inte det andra **Start transaktions** kommandot innehåller den *oberoende* parametern, skapas ingen ny transaktion vid **Start transaktion** .</span><span class="sxs-lookup"><span data-stu-id="9897c-126">Unless the second **Start-Transaction** command includes the *Independent* parameter, **Start-Transaction** does not create a new transaction.</span></span>
<span data-ttu-id="9897c-127">Istället lägger den till en andra prenumerant till den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-127">Instead, it adds a second subscriber to the original transaction.</span></span>

<span data-ttu-id="9897c-128">Det första **Start transaktions** kommandot startar transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-128">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="9897c-129">Ett New-Item-kommando med parametern *UseTransaction* är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-129">A New-Item command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="9897c-130">Ett andra **Start transaktions** kommando lägger till en prenumerant i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-130">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="9897c-131">Nästa New-Item-kommandot ingår också i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-131">The next New-Item command is also part of the transaction.</span></span>

<span data-ttu-id="9897c-132">Det första kommandot **Get-Transaction** visar multi-Subscriber-transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-132">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="9897c-133">Observera att antalet prenumeranter är 2.</span><span class="sxs-lookup"><span data-stu-id="9897c-133">Notice that the subscriber count is 2.</span></span>

<span data-ttu-id="9897c-134">Det första Complete-Transaction kommandot genomför inte transaktionen, men minskar antalet prenumeranter till 1.</span><span class="sxs-lookup"><span data-stu-id="9897c-134">The first Complete-Transaction command does not commit the transaction, but it reduces the subscriber count to 1.</span></span>

<span data-ttu-id="9897c-135">Det andra **slutförda transaktions** kommandot genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-135">The second **Complete-Transaction** command commits the transaction.</span></span>

### <span data-ttu-id="9897c-136">Exempel 6: starta en oberoende transaktion medan en annan pågår</span><span class="sxs-lookup"><span data-stu-id="9897c-136">Example 6: Start an independent transaction while another is in progress</span></span>

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

<span data-ttu-id="9897c-137">I det här exemplet visas effekterna av transaktions objekt för att starta en oberoende transaktion medan en annan transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="9897c-137">This example shows the effect on the transaction object of starting an independent transaction while another transaction is in progress.</span></span>

<span data-ttu-id="9897c-138">Det första **Start transaktions** kommandot startar transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-138">The first **Start-Transaction** command starts the transaction.</span></span>
<span data-ttu-id="9897c-139">Ett **nytt-objekt-** kommando med parametern *UseTransaction* är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-139">A **New-Item** command with the *UseTransaction* parameter is part of the transaction.</span></span>

<span data-ttu-id="9897c-140">Ett andra **Start transaktions** kommando lägger till en prenumerant i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-140">A second **Start-Transaction** command adds a subscriber to the transaction.</span></span>
<span data-ttu-id="9897c-141">Nästa **nya-objekt-** kommandot ingår också i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-141">The next **New-Item** command is also part of the transaction.</span></span>

<span data-ttu-id="9897c-142">Det första kommandot **Get-Transaction** visar multi-Subscriber-transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-142">The first **Get-Transaction** command shows the multi-subscriber transaction.</span></span>
<span data-ttu-id="9897c-143">Observera att antalet prenumeranter är 2.</span><span class="sxs-lookup"><span data-stu-id="9897c-143">Note that the subscriber count is 2.</span></span>

<span data-ttu-id="9897c-144">Kommandot **fullständig transaktion** minskar antalet prenumeranter till 1, men transaktionen slutförs inte.</span><span class="sxs-lookup"><span data-stu-id="9897c-144">The **Complete-Transaction** command reduces the subscriber count to 1, but it does not commit the transaction.</span></span>

<span data-ttu-id="9897c-145">Det andra **slutförda transaktions** kommandot genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-145">The second **Complete-Transaction** command commits the transaction.</span></span>

## <span data-ttu-id="9897c-146">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="9897c-146">PARAMETERS</span></span>

### <span data-ttu-id="9897c-147">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="9897c-147">CommonParameters</span></span>
<span data-ttu-id="9897c-148">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="9897c-148">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="9897c-149">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="9897c-149">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="9897c-150">INDATA</span><span class="sxs-lookup"><span data-stu-id="9897c-150">INPUTS</span></span>

### <span data-ttu-id="9897c-151">Inget</span><span class="sxs-lookup"><span data-stu-id="9897c-151">None</span></span>
<span data-ttu-id="9897c-152">Det går inte att skicka pipe-objekt till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="9897c-152">You cannot pipe objects to this cmdlet.</span></span>

## <span data-ttu-id="9897c-153">UTDATA</span><span class="sxs-lookup"><span data-stu-id="9897c-153">OUTPUTS</span></span>

### <span data-ttu-id="9897c-154">System. Management. Automation. PSTransaction</span><span class="sxs-lookup"><span data-stu-id="9897c-154">System.Management.Automation.PSTransaction</span></span>
<span data-ttu-id="9897c-155">Denna cmdlet returnerar ett objekt som representerar den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="9897c-155">This cmdlet returns an object that represents the current transaction.</span></span>

## <span data-ttu-id="9897c-156">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="9897c-156">NOTES</span></span>

## <span data-ttu-id="9897c-157">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="9897c-157">RELATED LINKS</span></span>

[<span data-ttu-id="9897c-158">Slutförd transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-158">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="9897c-159">Starta transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-159">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="9897c-160">Ångra-transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-160">Undo-Transaction</span></span>](Undo-Transaction.md)

[<span data-ttu-id="9897c-161">Använd transaktion</span><span class="sxs-lookup"><span data-stu-id="9897c-161">Use-Transaction</span></span>](Use-Transaction.md)

[<span data-ttu-id="9897c-162">Nytt objekt</span><span class="sxs-lookup"><span data-stu-id="9897c-162">New-Item</span></span>](New-Item.md)
