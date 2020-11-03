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
# <a name="about-transactions"></a><span data-ttu-id="4da75-104">Om transaktioner</span><span class="sxs-lookup"><span data-stu-id="4da75-104">About Transactions</span></span>

## <a name="short-description"></a><span data-ttu-id="4da75-105">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4da75-105">SHORT DESCRIPTION</span></span>

<span data-ttu-id="4da75-106">Beskriver hur du hanterar överförda åtgärder i PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4da75-106">Describes how to manage transacted operations in PowerShell.</span></span>

## <a name="long-description"></a><span data-ttu-id="4da75-107">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="4da75-107">LONG DESCRIPTION</span></span>

<span data-ttu-id="4da75-108">Transaktioner stöds i PowerShell som börjar i PowerShell 2,0.</span><span class="sxs-lookup"><span data-stu-id="4da75-108">Transactions are supported in PowerShell beginning in PowerShell 2.0.</span></span> <span data-ttu-id="4da75-109">Med den här funktionen kan du starta en transaktion, för att ange vilka kommandon som ingår i transaktionen och för att genomföra eller återställa en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-109">This feature enables you to start a transaction, to indicate which commands are part of the transaction, and to commit or roll back a transaction.</span></span>

## <a name="about-transactions"></a><span data-ttu-id="4da75-110">OM TRANSAKTIONER</span><span class="sxs-lookup"><span data-stu-id="4da75-110">ABOUT TRANSACTIONS</span></span>

<span data-ttu-id="4da75-111">I PowerShell är en transaktion en uppsättning av ett eller flera kommandon som hanteras som en logisk enhet.</span><span class="sxs-lookup"><span data-stu-id="4da75-111">In PowerShell, a transaction is a set of one or more commands that are managed as a logical unit.</span></span> <span data-ttu-id="4da75-112">En transaktion kan slutföras ("bekräftad"), vilket ändrar data som påverkas av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-112">A transaction can be completed ("committed"), which changes data affected by the transaction.</span></span> <span data-ttu-id="4da75-113">Eller så kan en transaktion helt ångras ("återställd") så att de berörda data inte ändras av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-113">Or, a transaction can be completely undone ("rolled back") so that the affected data is not changed by the transaction.</span></span>

<span data-ttu-id="4da75-114">Eftersom kommandona i en transaktion hanteras som en enhet, utförs antingen alla kommandon eller också återställs alla kommandon.</span><span class="sxs-lookup"><span data-stu-id="4da75-114">Because the commands in a transaction are managed as a unit, either all commands are committed, or all commands are rolled back.</span></span>

<span data-ttu-id="4da75-115">Transaktioner används ofta i data bearbetning, främst i databas åtgärder och för ekonomiska transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-115">Transactions are widely used in data processing, most notably in database operations and for financial transactions.</span></span> <span data-ttu-id="4da75-116">Transaktioner används oftast när värsta fall scenariot för en uppsättning kommandon inte är att de Miss lyckas, men att vissa kommandon lyckas medan andra Miss lyckas, lämnar systemet i ett skadat, falskt eller avtolknings tillstånd som är svårt att reparera.</span><span class="sxs-lookup"><span data-stu-id="4da75-116">Transactions are most often used when the worst-case scenario for a set of commands is not that they all fail, but that some commands succeed while others fail, leaving the system in a damaged, false, or uninterpretable state that is difficult to repair.</span></span>

## <a name="transaction-cmdlets"></a><span data-ttu-id="4da75-117">TRANSAKTIONS-CMDLETAR</span><span class="sxs-lookup"><span data-stu-id="4da75-117">TRANSACTION CMDLETS</span></span>

<span data-ttu-id="4da75-118">PowerShell innehåller flera cmdletar utformade för att hantera transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-118">PowerShell includes several cmdlets designed for managing transactions.</span></span>

- <span data-ttu-id="4da75-119">Starta transaktion: startar en ny transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-119">Start-Transaction: Starts a new transaction.</span></span>
- <span data-ttu-id="4da75-120">Använd-Transaction: lägger till ett kommando eller uttryck i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-120">Use-Transaction: Adds a command or expression to the transaction.</span></span> <span data-ttu-id="4da75-121">Kommandot måste använda transaktions aktiverade objekt.</span><span class="sxs-lookup"><span data-stu-id="4da75-121">The command must use transaction-enabled objects.</span></span>
- <span data-ttu-id="4da75-122">Ångra-transaktion: återställer transaktionen så att inga data ändras av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-122">Undo-Transaction: Rolls back the transaction so that no data is changed by the transaction.</span></span>
- <span data-ttu-id="4da75-123">Slutförd-transaktion: genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-123">Complete-Transaction: Commits the transaction.</span></span> <span data-ttu-id="4da75-124">De data som påverkas av transaktionen ändras.</span><span class="sxs-lookup"><span data-stu-id="4da75-124">The data affected by the transaction is changed.</span></span>
- <span data-ttu-id="4da75-125">Get-Transaction: hämtar information om den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-125">Get-Transaction: Gets information about the active transaction.</span></span>

<span data-ttu-id="4da75-126">Om du vill visa en lista över transaktions-cmdletar skriver du:</span><span class="sxs-lookup"><span data-stu-id="4da75-126">For a list of transaction cmdlets, type:</span></span>

```powershell
get-command *transaction
```

<span data-ttu-id="4da75-127">Om du vill ha detaljerad information om cmdletarna skriver du:</span><span class="sxs-lookup"><span data-stu-id="4da75-127">For detailed information about the cmdlets, type:</span></span>

```powershell
get-help use-transaction -detailed
```

## <a name="transaction-enabled-elements"></a><span data-ttu-id="4da75-128">TRANSAKTIONS AKTIVERADE ELEMENT</span><span class="sxs-lookup"><span data-stu-id="4da75-128">TRANSACTION-ENABLED ELEMENTS</span></span>

<span data-ttu-id="4da75-129">För att delta i en transaktion måste både cmdleten och providern ha stöd för transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-129">To participate in a transaction, both the cmdlet and the provider must support transactions.</span></span> <span data-ttu-id="4da75-130">Den här funktionen är inbyggd i de objekt som påverkas av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-130">This feature is built in to the objects that are affected by the transaction.</span></span>

<span data-ttu-id="4da75-131">PowerShell-dataprovidern stöder transaktioner i Windows Vista.</span><span class="sxs-lookup"><span data-stu-id="4da75-131">The PowerShell Registry provider supports transactions in Windows Vista.</span></span> <span data-ttu-id="4da75-132">TransactedString-objektet (Microsoft. PowerShell. commands. Management. TransactedString) fungerar med alla operativ system som kör PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4da75-132">The TransactedString object (Microsoft.PowerShell.Commands.Management.TransactedString) works with any operating system that runs PowerShell.</span></span>

<span data-ttu-id="4da75-133">Andra PowerShell-leverantörer kan stödja transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-133">Other PowerShell providers can support transactions.</span></span> <span data-ttu-id="4da75-134">Om du vill hitta PowerShell-providers i sessionen som stöder transaktioner använder du följande kommando för att hitta värdet "transaktioner" i egenskapen Capabilities för providers:</span><span class="sxs-lookup"><span data-stu-id="4da75-134">To find the PowerShell providers in your session that support transactions, use the following command to find the "Transactions" value in the Capabilities property of providers:</span></span>

```powershell
get-psprovider | where {$_.Capabilities -like "*transactions*"}
```

<span data-ttu-id="4da75-135">Mer information om en provider finns i hjälpen för providern.</span><span class="sxs-lookup"><span data-stu-id="4da75-135">For more information about a provider, see the Help for the provider.</span></span> <span data-ttu-id="4da75-136">Om du vill ha hjälp för leverantören skriver du:</span><span class="sxs-lookup"><span data-stu-id="4da75-136">To get provider Help, type:</span></span>

```
get-help <provider-name>
```

<span data-ttu-id="4da75-137">Om du till exempel vill få hjälp med register leverantören skriver du:</span><span class="sxs-lookup"><span data-stu-id="4da75-137">For example, to get Help for the Registry provider, type:</span></span>

```powershell
get-help registry
```

## <a name="the-usetransaction-parameter"></a><span data-ttu-id="4da75-138">PARAMETERN USETRANSACTION</span><span class="sxs-lookup"><span data-stu-id="4da75-138">THE USETRANSACTION PARAMETER</span></span>

<span data-ttu-id="4da75-139">-Cmdletar som kan stödja transaktioner har en UseTransaction-parameter.</span><span class="sxs-lookup"><span data-stu-id="4da75-139">Cmdlets that can support transactions have a UseTransaction parameter.</span></span> <span data-ttu-id="4da75-140">Den här parametern inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-140">This parameter includes the command in the active transaction.</span></span> <span data-ttu-id="4da75-141">Du kan använda det fullständiga parameter namnet eller dess alias, "usetx".</span><span class="sxs-lookup"><span data-stu-id="4da75-141">You can use the full parameter name or its alias, "usetx".</span></span>

<span data-ttu-id="4da75-142">Parametern kan endast användas när sessionen innehåller en aktiv transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-142">The parameter can be used only when the session contains an active transaction.</span></span> <span data-ttu-id="4da75-143">Om du anger ett kommando med parametern UseTransaction när det inte finns någon aktiv transaktion, Miss lyckas kommandot.</span><span class="sxs-lookup"><span data-stu-id="4da75-143">If you enter a command with the UseTransaction parameter when there is no active transaction, the command fails.</span></span>

<span data-ttu-id="4da75-144">Om du vill hitta cmdletar med parametern UseTransaction skriver du:</span><span class="sxs-lookup"><span data-stu-id="4da75-144">To find cmdlets with the UseTransaction parameter, type:</span></span>

```powershell
get-help * -parameter UseTransaction
```

<span data-ttu-id="4da75-145">I PowerShell Core har alla cmdletar utformats för att fungera med PowerShell-leverantörer som stöder transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-145">In PowerShell core, all of the cmdlets designed to work with PowerShell providers support transactions.</span></span> <span data-ttu-id="4da75-146">Därför kan du använda Provider-cmdletar för att hantera transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-146">As a result, you can use the provider cmdlets to manage transactions.</span></span>

<span data-ttu-id="4da75-147">Mer information om PowerShell-leverantörer finns [about_Providers](about_Providers.md).</span><span class="sxs-lookup"><span data-stu-id="4da75-147">For more information about PowerShell providers, see [about_Providers](about_Providers.md).</span></span>

## <a name="the-transaction-object"></a><span data-ttu-id="4da75-148">TRANSAKTIONS OBJEKT</span><span class="sxs-lookup"><span data-stu-id="4da75-148">THE TRANSACTION OBJECT</span></span>

<span data-ttu-id="4da75-149">Transaktioner visas i PowerShell av ett transaktions objekt, system. Management. Automation. Transaction.</span><span class="sxs-lookup"><span data-stu-id="4da75-149">Transactions are represented in PowerShell by a transaction object, System.Management.Automation.Transaction.</span></span>

<span data-ttu-id="4da75-150">Objektet har följande egenskaper:</span><span class="sxs-lookup"><span data-stu-id="4da75-150">The object has the following properties:</span></span>

- <span data-ttu-id="4da75-151">RollbackPreference: innehåller återställnings inställnings uppsättningen för den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-151">RollbackPreference: Contains the rollback preference set for the current transaction.</span></span> <span data-ttu-id="4da75-152">Du kan ställa in återställnings inställningen när du använder Start-Transaction för att starta transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-152">You can set the rollback preference when you use Start-Transaction to start the transaction.</span></span>

  <span data-ttu-id="4da75-153">Återställnings inställningen avgör under vilka omständigheter som transaktionen återställs automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4da75-153">The rollback preference determines the conditions under which the transaction is rolled back automatically.</span></span> <span data-ttu-id="4da75-154">Giltiga värden är error, TerminatingError och Never.</span><span class="sxs-lookup"><span data-stu-id="4da75-154">Valid values are Error, TerminatingError, and Never.</span></span> <span data-ttu-id="4da75-155">Standardvärdet är error.</span><span class="sxs-lookup"><span data-stu-id="4da75-155">The default value is Error.</span></span>

- <span data-ttu-id="4da75-156">Status: innehåller transaktionens aktuella status.</span><span class="sxs-lookup"><span data-stu-id="4da75-156">Status: Contains the current status of the transaction.</span></span> <span data-ttu-id="4da75-157">Giltiga värden är Active, Committed och återställd.</span><span class="sxs-lookup"><span data-stu-id="4da75-157">Valid values are Active, Committed, and RolledBack.</span></span>

- <span data-ttu-id="4da75-158">SubscriberCount: innehåller antalet prenumeranter för transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-158">SubscriberCount: Contains the number of subscribers to the transaction.</span></span> <span data-ttu-id="4da75-159">En prenumerant läggs till i en transaktion när du startar en transaktion medan en annan transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="4da75-159">A subscriber is added to a transaction when you start a transaction while another transaction is in progress.</span></span> <span data-ttu-id="4da75-160">Antalet prenumeranter minskas när en prenumerant genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-160">The subscriber count is decremented when a subscriber commits the transaction.</span></span>

## <a name="active-transactions"></a><span data-ttu-id="4da75-161">AKTIVA TRANSAKTIONER</span><span class="sxs-lookup"><span data-stu-id="4da75-161">ACTIVE TRANSACTIONS</span></span>

<span data-ttu-id="4da75-162">I PowerShell är det bara en transaktion som är aktiv i taget och du kan bara hantera den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-162">In PowerShell, only one transaction is active at a time, and you can manage only the active transaction.</span></span> <span data-ttu-id="4da75-163">Flera transaktioner kan pågå i samma session samtidigt, men det är bara den senast startade transaktionen som är aktiv.</span><span class="sxs-lookup"><span data-stu-id="4da75-163">Multiple transactions can be in progress in the same session at the same time, but only the most-recently started transaction is active.</span></span>

<span data-ttu-id="4da75-164">Därför kan du inte ange en viss transaktion när du använder transaktions-cmdletar.</span><span class="sxs-lookup"><span data-stu-id="4da75-164">As a result, you cannot specify a particular transaction when using the transaction cmdlets.</span></span> <span data-ttu-id="4da75-165">Kommandon gäller alltid för den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-165">Commands always apply to the active transaction.</span></span>

<span data-ttu-id="4da75-166">Detta är mest uppenbart i beteendet för Get-Transaction-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4da75-166">This is most evident in the behavior of the Get-Transaction cmdlet.</span></span> <span data-ttu-id="4da75-167">När du anger ett Get-Transaction kommando får Get-Transaction alltid bara ett transaktions objekt.</span><span class="sxs-lookup"><span data-stu-id="4da75-167">When you enter a Get-Transaction command, Get-Transaction always gets only one transaction object.</span></span> <span data-ttu-id="4da75-168">Det här objektet är det objekt som representerar den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-168">This object is the object that represents the active transaction.</span></span>

<span data-ttu-id="4da75-169">Om du vill hantera en annan transaktion måste du först avsluta den aktiva transaktionen, antingen genom att utföra den eller återställa den.</span><span class="sxs-lookup"><span data-stu-id="4da75-169">To manage a different transaction, you must first finish the active transaction, either by committing it or rolling it back.</span></span> <span data-ttu-id="4da75-170">När du gör det aktive ras den tidigare transaktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4da75-170">When you do this, the previous transaction becomes active automatically.</span></span> <span data-ttu-id="4da75-171">Transaktioner aktive ras i omvänd ordning för de startas, så att den senast startade transaktionen alltid är aktiv.</span><span class="sxs-lookup"><span data-stu-id="4da75-171">Transactions become active in the reverse of order of which they are started, so that the most recently started transaction is always active.</span></span>

## <a name="subscribers-and-independent-transactions"></a><span data-ttu-id="4da75-172">PRENUMERANTER OCH OBEROENDE TRANSAKTIONER</span><span class="sxs-lookup"><span data-stu-id="4da75-172">SUBSCRIBERS AND INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="4da75-173">Om du startar en transaktion medan en annan transaktion pågår, startar inte PowerShell en ny transaktion som standard.</span><span class="sxs-lookup"><span data-stu-id="4da75-173">If you start a transaction while another transaction is in progress, by default, PowerShell does not start a new transaction.</span></span> <span data-ttu-id="4da75-174">Istället lägger den till en "prenumerant" i den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-174">Instead, it adds a "subscriber" to the current transaction.</span></span>

<span data-ttu-id="4da75-175">När en transaktion har flera prenumeranter, återställer ett enda Undo-Transaction-kommando åt hela transaktionen för alla prenumeranter.</span><span class="sxs-lookup"><span data-stu-id="4da75-175">When a transaction has multiple subscribers, a single Undo-Transaction command at any point rolls back the entire transaction for all subscribers.</span></span> <span data-ttu-id="4da75-176">Men för att genomföra transaktionen måste du ange ett Complete-Transaction-kommando för varje prenumerant.</span><span class="sxs-lookup"><span data-stu-id="4da75-176">However, to commit the transaction, you must enter a Complete-Transaction command for every subscriber.</span></span>

<span data-ttu-id="4da75-177">Om du vill hitta antalet prenumeranter för en transaktion kontrollerar du egenskapen SubscriberCount för objektet.</span><span class="sxs-lookup"><span data-stu-id="4da75-177">To find the number of subscribers to a transaction, check the SubscriberCount property of the transaction object.</span></span> <span data-ttu-id="4da75-178">Följande kommando använder exempelvis cmdleten Get-Transaction för att hämta värdet för egenskapen SubscriberCount för den aktiva transaktionen:</span><span class="sxs-lookup"><span data-stu-id="4da75-178">For example, the following command uses the Get-Transaction cmdlet to get the value of the SubscriberCount property of the active transaction:</span></span>

```powershell
(Get-Transaction).SubscriberCount
```

<span data-ttu-id="4da75-179">Att lägga till en prenumerant är standard beteendet eftersom de flesta transaktioner som startas medan en annan transaktion pågår är relaterade till den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-179">Adding a subscriber is the default behavior because most transactions that are started while another transaction is in progress are related to the original transaction.</span></span> <span data-ttu-id="4da75-180">I den typiska modellen anropar ett skript som innehåller en transaktion ett hjälp skript som innehåller en egen transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-180">In the typical model, a script that contains a transaction calls a helper script that contains its own transaction.</span></span> <span data-ttu-id="4da75-181">Eftersom transaktionerna är relaterade bör de återställas eller allokeras som en enhet.</span><span class="sxs-lookup"><span data-stu-id="4da75-181">Because the transactions are related, they should be rolled back or committed as a unit.</span></span>

<span data-ttu-id="4da75-182">Du kan dock starta en transaktion som är oberoende av den aktuella transaktionen genom att använda den oberoende parametern i Start-Transaction-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4da75-182">However, you can start a transaction that is independent of the current transaction by using the Independent parameter of the Start-Transaction cmdlet.</span></span>

<span data-ttu-id="4da75-183">När du startar en oberoende transaktion skapar Start-Transaction ett nytt transaktions objekt och den nya transaktionen blir den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-183">When you start an independent transaction, Start-Transaction creates a new transaction object, and the new transaction becomes the active transaction.</span></span>
<span data-ttu-id="4da75-184">Den oberoende transaktionen kan allokeras eller återställas utan att den ursprungliga transaktionen påverkas.</span><span class="sxs-lookup"><span data-stu-id="4da75-184">The independent transaction can be committed or rolled back without affecting the original transaction.</span></span>

<span data-ttu-id="4da75-185">När den oberoende transaktionen är slutförd (allokerad eller återställd) blir den ursprungliga transaktionen den aktiva transaktionen igen.</span><span class="sxs-lookup"><span data-stu-id="4da75-185">When the independent transaction is finished (committed or rolled back), the original transaction becomes the active transaction again.</span></span>

## <a name="changing-data"></a><span data-ttu-id="4da75-186">ÄNDRA DATA</span><span class="sxs-lookup"><span data-stu-id="4da75-186">CHANGING DATA</span></span>

<span data-ttu-id="4da75-187">När du använder transaktioner för att ändra data, ändras inte data som påverkas av transaktionen förrän du genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-187">When you use transactions to change data, the data that is affected by the transaction is not changed until you commit the transaction.</span></span> <span data-ttu-id="4da75-188">Samma data kan dock ändras av kommandon som inte ingår i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-188">However, the same data can be changed by commands that are not part of the transaction.</span></span>

<span data-ttu-id="4da75-189">Tänk på detta när du använder transaktioner för att hantera delade data.</span><span class="sxs-lookup"><span data-stu-id="4da75-189">Keep this in mind when you are using transactions to manage shared data.</span></span>
<span data-ttu-id="4da75-190">Normalt har databaser en mekanism som låser data medan du arbetar med den, vilket förhindrar andra användare och andra kommandon, skript och funktioner, från att ändra den.</span><span class="sxs-lookup"><span data-stu-id="4da75-190">Typically, databases have mechanisms that lock the data while you are working on it, preventing other users, and other commands, scripts, and functions, from changing it.</span></span>

<span data-ttu-id="4da75-191">Låset är dock en funktion i databasen.</span><span class="sxs-lookup"><span data-stu-id="4da75-191">However, the lock is a feature of the database.</span></span> <span data-ttu-id="4da75-192">Den är inte relaterad till transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-192">It is not related to transactions.</span></span> <span data-ttu-id="4da75-193">Om du arbetar i ett transaktions aktiverat fil system eller ett annat data lager, kan data ändras medan transaktionen pågår.</span><span class="sxs-lookup"><span data-stu-id="4da75-193">If you are working in a transaction-enabled file system or other data store, the data can be changed while the transaction is in progress.</span></span>

## <a name="examples"></a><span data-ttu-id="4da75-194">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="4da75-194">EXAMPLES</span></span>

<span data-ttu-id="4da75-195">I exemplen i det här avsnittet används PowerShell-registernyckeln och vi antar att du är bekant med den.</span><span class="sxs-lookup"><span data-stu-id="4da75-195">The examples in this section use the PowerShell Registry provider and assume that you are familiar with it.</span></span> <span data-ttu-id="4da75-196">Om du vill ha mer information om register leverantören skriver du "Get-Help Registry".</span><span class="sxs-lookup"><span data-stu-id="4da75-196">For information about the Registry provider, type "get-help registry".</span></span>

### <a name="example-1-committing-a-transaction"></a><span data-ttu-id="4da75-197">EXEMPEL 1: GENOMFÖR EN TRANSAKTION</span><span class="sxs-lookup"><span data-stu-id="4da75-197">EXAMPLE 1: COMMITTING A TRANSACTION</span></span>

<span data-ttu-id="4da75-198">Använd Start-Transaction-cmdleten om du vill skapa en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-198">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="4da75-199">Följande kommando startar en transaktion med standardinställningarna.</span><span class="sxs-lookup"><span data-stu-id="4da75-199">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-200">Om du vill inkludera kommandon i transaktionen använder du parametern UseTransaction för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="4da75-200">To include commands in the transaction, use the UseTransaction parameter of the cmdlet.</span></span> <span data-ttu-id="4da75-201">Som standard ingår inte kommandon i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-201">By default, commands are not included in the transaction,</span></span>

<span data-ttu-id="4da75-202">Följande kommando, som anger den aktuella platsen i program varu nyckeln för HKCU: Drive, ingår inte i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-202">For example, the following command, which sets the current location in the Software key of the HKCU: drive, is not included in the transaction.</span></span>

```powershell
cd hkcu:\Software
```

<span data-ttu-id="4da75-203">Följande kommando, som skapar nyckeln för företags nyckeln, använder parametern UseTransaction i cmdleten New-Item för att inkludera kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-203">The following command, which creates the MyCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="4da75-204">Kommandot returnerar ett objekt som representerar den nya nyckeln, men eftersom kommandot är en del av transaktionen har registret inte ändrats än.</span><span class="sxs-lookup"><span data-stu-id="4da75-204">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyCompany                      {}
```

<span data-ttu-id="4da75-205">Använd Complete-Transaction-cmdleten för att genomföra transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-205">To commit the transaction, use the Complete-Transaction cmdlet.</span></span> <span data-ttu-id="4da75-206">Eftersom den alltid påverkar den aktiva transaktionen kan du inte ange transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-206">Because it always affects the active transaction, you cannot specify the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-207">Det innebär att nyckeln för företags nyckeln läggs till i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-207">As a result, the MyCompany key is added to the registry.</span></span>

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

### <a name="example-2-rolling-back-a-transaction"></a><span data-ttu-id="4da75-208">EXEMPEL 2: ÅTERSTÄLLA EN TRANSAKTION</span><span class="sxs-lookup"><span data-stu-id="4da75-208">EXAMPLE 2: ROLLING BACK A TRANSACTION</span></span>

<span data-ttu-id="4da75-209">Använd Start-Transaction-cmdleten om du vill skapa en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-209">To create a transaction, use the Start-Transaction cmdlet.</span></span> <span data-ttu-id="4da75-210">Följande kommando startar en transaktion med standardinställningarna.</span><span class="sxs-lookup"><span data-stu-id="4da75-210">The following command starts a transaction with the default settings.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-211">Följande kommando, som skapar MyOtherCompany-nyckeln, använder parametern UseTransaction för cmdleten New-Item för att inkludera kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-211">The following command, which creates the MyOtherCompany key, uses the UseTransaction parameter of the New-Item cmdlet to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -UseTransaction
```

<span data-ttu-id="4da75-212">Kommandot returnerar ett objekt som representerar den nya nyckeln, men eftersom kommandot är en del av transaktionen har registret inte ändrats än.</span><span class="sxs-lookup"><span data-stu-id="4da75-212">The command returns an object that represents the new key, but because the command is part of the transaction, the registry is not yet changed.</span></span>

```
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
  0   0 MyOtherCompany                 {}
```

<span data-ttu-id="4da75-213">Använd Undo-Transaction-cmdleten om du vill återställa transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-213">To roll back the transaction, use the Undo-Transaction cmdlet.</span></span> <span data-ttu-id="4da75-214">Eftersom det alltid påverkar den aktiva transaktionen anger du inte transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-214">Because it always affects the active transaction, you do not specify the transaction.</span></span>

```powershell
Undo-transaction
```

<span data-ttu-id="4da75-215">Resultatet är att nyckeln MyOtherCompany inte har lagts till i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-215">The result is that the MyOtherCompany key is not added to the registry.</span></span>

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

### <a name="example-3-previewing-a-transaction"></a><span data-ttu-id="4da75-216">EXEMPEL 3: FÖR HANDS GRANS KAR EN TRANSAKTION</span><span class="sxs-lookup"><span data-stu-id="4da75-216">EXAMPLE 3: PREVIEWING A TRANSACTION</span></span>

<span data-ttu-id="4da75-217">Normalt används de kommandon som används i en transaktion för att ändra data.</span><span class="sxs-lookup"><span data-stu-id="4da75-217">Typically, the commands used in a transaction change data.</span></span> <span data-ttu-id="4da75-218">De kommandon som hämtar data är dock användbara i en transaktion, även om de hämtar data i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-218">However, the commands that get data are useful in a transaction, too, because they get data inside of the transaction.</span></span> <span data-ttu-id="4da75-219">Detta ger en förhands granskning av de ändringar som genomför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-219">This provides a preview of the changes that committing the transaction would cause.</span></span>

<span data-ttu-id="4da75-220">I följande exempel visas hur du använder kommandot Get-ChildItem (aliaset är "dir") för att förhandsgranska ändringarna i en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-220">The following example shows how to use the Get-ChildItem command (the alias is "dir") to preview the changes in a transaction.</span></span>

<span data-ttu-id="4da75-221">Följande kommando startar en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-221">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-222">Följande kommando använder cmdleten New-ItemProperty för att lägga till register posten MyKey i företags nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4da75-222">The following command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="4da75-223">Kommandot använder parametern UseTransaction för att inkludera kommandot i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-223">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -Name MyKey -value 123 -UseTransaction
```

<span data-ttu-id="4da75-224">Kommandot returnerar ett objekt som representerar den nya register posten, men register posten har inte ändrats.</span><span class="sxs-lookup"><span data-stu-id="4da75-224">The command returns an object representing the new registry entry, but the registry entry is not changed.</span></span>

```
MyKey
-----
123
```

<span data-ttu-id="4da75-225">Om du vill hämta de objekt som för närvarande finns i registret använder du ett Get-ChildItem kommando ("dir") utan parametern UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="4da75-225">To get the items that are currently in the registry, use a Get-ChildItem command ("dir") without the UseTransaction parameter.</span></span> <span data-ttu-id="4da75-226">Följande kommando hämtar objekt som börjar med "M".</span><span class="sxs-lookup"><span data-stu-id="4da75-226">The following command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="4da75-227">Resultatet visar att inga poster ännu har lagts till i företags nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4da75-227">The result shows that no entries have yet been added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   0 MyCompany                      {}
```

<span data-ttu-id="4da75-228">Om du vill förhandsgranska resultatet av transaktionen anger du ett Get-ChildItem (dir)-kommando med parametern UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="4da75-228">To preview the effect of committing the transaction, enter a Get-ChildItem ("dir") command with the UseTransaction parameter.</span></span> <span data-ttu-id="4da75-229">Det här kommandot innehåller en vy över data i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-229">This command has a view of the data from within the transaction.</span></span>

```powershell
dir m* -useTransaction
```

<span data-ttu-id="4da75-230">Resultatet visar att om transaktionen är genomförd, läggs MyKey-posten till i företags nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4da75-230">The result shows that, if the transaction is committed, the MyKey entry will be added to the MyCompany key.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0   1 MyCompany                      {MyKey}
```

### <a name="example-4-combining-transacted-and-non-transacted-commands"></a><span data-ttu-id="4da75-231">EXEMPEL 4: KOMBINERA ÖVERFÖRDA OCH ICKE-ÖVERFÖRDA KOMMANDON</span><span class="sxs-lookup"><span data-stu-id="4da75-231">EXAMPLE 4: COMBINING TRANSACTED AND NON-TRANSACTED COMMANDS</span></span>

<span data-ttu-id="4da75-232">Du kan ange icke-överförda kommandon under en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-232">You can enter non-transacted commands during a transaction.</span></span> <span data-ttu-id="4da75-233">De ej överförda kommandona påverkar data direkt, men de påverkar inte transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-233">The non-transacted commands affect the data immediately, but they do not affect the transaction.</span></span>
<span data-ttu-id="4da75-234">Följande kommando startar en transaktion i register nyckeln HKCU: \ Software.</span><span class="sxs-lookup"><span data-stu-id="4da75-234">The following command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-235">Följande tre kommandon använder cmdleten New-Item för att lägga till nycklar i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-235">The next three commands use the New-Item cmdlet to add keys to the registry.</span></span>
<span data-ttu-id="4da75-236">De första och tredje kommandona använder parametern UseTransaction för att inkludera kommandona i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-236">The first and third commands use the UseTransaction parameter to include the commands in the transaction.</span></span> <span data-ttu-id="4da75-237">Det andra kommandot utesluter parametern.</span><span class="sxs-lookup"><span data-stu-id="4da75-237">The second command omits the parameter.</span></span> <span data-ttu-id="4da75-238">Eftersom det andra kommandot inte ingår i transaktionen börjar det gälla omedelbart.</span><span class="sxs-lookup"><span data-stu-id="4da75-238">Because the second command is not included in the transaction, it is effective immediately.</span></span>

```powershell
new-item MyCompany1 -UseTransaction
new-item MyCompany2
new-item MyCompany3 -UseTransaction
```

<span data-ttu-id="4da75-239">Om du vill visa det aktuella status för registret använder du kommandot Get-ChildItem (dir) utan parametern UseTransaction.</span><span class="sxs-lookup"><span data-stu-id="4da75-239">To view the current state of the registry, use a Get-ChildItem ("dir") command without the UseTransaction parameter.</span></span> <span data-ttu-id="4da75-240">Det här kommandot hämtar objekt som börjar med "M".</span><span class="sxs-lookup"><span data-stu-id="4da75-240">This command gets items that begin with "M."</span></span>

```powershell
dir m*
```

<span data-ttu-id="4da75-241">Resultatet visar att nyckeln MyCompany2 har lagts till i registret, men att nycklarna MyCompany1 och MyCompany3, som ingår i transaktionen, inte läggs till.</span><span class="sxs-lookup"><span data-stu-id="4da75-241">The result shows that the MyCompany2 key is added to the registry, but the MyCompany1 and MyCompany3 keys, which are part of the transaction, are not added.</span></span>

```output
Hive: HKEY_CURRENT_USER\Software

SKC  VC Name                           Property
---  -- ----                           --------
 83   1 Microsoft                      {(default)}
  0    0 MyCompany2                     {}
```

<span data-ttu-id="4da75-242">Följande kommando utför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-242">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-243">Nu visas nycklarna som lades till som en del av transaktionen i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-243">Now, the keys that were added as part of the transaction appear in the registry.</span></span>

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

### <a name="example-5-using-automatic-rollback"></a><span data-ttu-id="4da75-244">EXEMPEL 5: ANVÄNDA AUTOMATISK ÅTERSTÄLLNING</span><span class="sxs-lookup"><span data-stu-id="4da75-244">EXAMPLE 5: USING AUTOMATIC ROLLBACK</span></span>

<span data-ttu-id="4da75-245">När ett kommando i en transaktion genererar ett fel av någon typ återställs transaktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4da75-245">When a command in a transaction generates an error of any kind, the transaction is automatically rolled back.</span></span>

<span data-ttu-id="4da75-246">Det här standard beteendet är utformat för skript som kör transaktioner.</span><span class="sxs-lookup"><span data-stu-id="4da75-246">This default behavior is designed for scripts that run transactions.</span></span> <span data-ttu-id="4da75-247">Skript är vanligt vis väl testade och innehåller fel hanterings logik, så fel förväntas inte och bör avslutas med transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-247">Scripts are typically well tested and include error-handling logic, so errors are not expected and should terminate the transaction.</span></span>

<span data-ttu-id="4da75-248">Det första kommandot startar en transaktion i register nyckeln HKCU: \ Software.</span><span class="sxs-lookup"><span data-stu-id="4da75-248">The first command starts a transaction in the HKCU:\Software registry key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-249">Följande kommando använder cmdleten New-Item för att lägga till företagets nyckel i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-249">The following command uses the New-Item cmdlet to add the MyCompany key to the registry.</span></span> <span data-ttu-id="4da75-250">Kommandot använder parametern UseTransaction (aliaset är "usetx") för att inkludera kommandot i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-250">The command uses the UseTransaction parameter (the alias is "usetx") to include the command in the transaction.</span></span>

```powershell
New-Item MyCompany -UseTX
```

<span data-ttu-id="4da75-251">Eftersom det redan finns en företags nyckel i registret, Miss lyckas kommandot och transaktionen återställs.</span><span class="sxs-lookup"><span data-stu-id="4da75-251">Because the MyCompany key already exists in the registry, the command fails, and the transaction is rolled back.</span></span>

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="4da75-252">Ett Get-Transaction-kommando bekräftar att transaktionen har återställts och att SubscriberCount är 0.</span><span class="sxs-lookup"><span data-stu-id="4da75-252">A Get-Transaction command confirms that the transaction has been rolled back and that the SubscriberCount is 0.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 RolledBack
```

### <a name="example-6-changing-the-rollback-preference"></a><span data-ttu-id="4da75-253">EXEMPEL 6: ÄNDRA ÅTERSTÄLLNINGS INSTÄLLNINGEN</span><span class="sxs-lookup"><span data-stu-id="4da75-253">EXAMPLE 6: CHANGING THE ROLLBACK PREFERENCE</span></span>

<span data-ttu-id="4da75-254">Om du vill att transaktionen ska vara mer feltolerant kan du använda RollbackPreference-parametern för Start-Transaction för att ändra inställningen.</span><span class="sxs-lookup"><span data-stu-id="4da75-254">If you want the transaction to be more error tolerant, you can use the RollbackPreference parameter of Start-Transaction to change the preference.</span></span>

<span data-ttu-id="4da75-255">Följande kommando startar en transaktion med återställnings inställningen "Never".</span><span class="sxs-lookup"><span data-stu-id="4da75-255">The following command starts a transaction with a rollback preference of "Never".</span></span>

```powershell
start-transaction -rollbackpreference Never
```

<span data-ttu-id="4da75-256">I det här fallet när kommandot Miss lyckas återställs inte transaktionen automatiskt.</span><span class="sxs-lookup"><span data-stu-id="4da75-256">In this case, when the command fails, the transaction is not automatically rolled back.</span></span>

```powershell
New-Item MyCompany -UseTX
```

```output
New-Item : A key at this path already exists
At line:1 char:9
+ new-item <<<<  MyCompany -usetx
```

<span data-ttu-id="4da75-257">Eftersom transaktionen fortfarande är aktiv kan du skicka kommandot igen som en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-257">Because the transaction is still active, you can resubmit the command as part of the transaction.</span></span>

```powershell
New-Item MyOtherCompany -UseTX
```

### <a name="example-7-using-the-use-transaction-cmdlet"></a><span data-ttu-id="4da75-258">EXEMPEL 7: ANVÄNDA CMDLETEN USE-TRANSACTION</span><span class="sxs-lookup"><span data-stu-id="4da75-258">EXAMPLE 7: USING THE USE-TRANSACTION CMDLET</span></span>

<span data-ttu-id="4da75-259">Med hjälp av cmdleten Use-Transaction kan du göra direkta skript mot transaktionsskyddade Microsoft .NET Ramverks objekt.</span><span class="sxs-lookup"><span data-stu-id="4da75-259">The Use-Transaction cmdlet enables you to do direct scripting against transaction-enabled Microsoft .NET Framework objects.</span></span> <span data-ttu-id="4da75-260">Use-Transaction tar ett skript block som bara kan innehålla kommandon och uttryck som använder transaktions aktiverade .NET Framework objekt, till exempel instanser av klassen Microsoft. PowerShell. commands. TransactedString.</span><span class="sxs-lookup"><span data-stu-id="4da75-260">Use-Transaction takes a script block that can only contain commands and expressions that use transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="4da75-261">Följande kommando startar en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-261">The following command starts a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-262">Följande New-Object-kommando skapar en instans av klassen TransactedString och sparar den i variabeln $t.</span><span class="sxs-lookup"><span data-stu-id="4da75-262">The following New-Object command creates an instance of the TransactedString class and saves it in the $t variable.</span></span>

```powershell
$t = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
```

<span data-ttu-id="4da75-263">Följande kommando använder metoden append för TransactedString-objektet för att lägga till text i strängen.</span><span class="sxs-lookup"><span data-stu-id="4da75-263">The following command uses the Append method of the TransactedString object to add text to the string.</span></span> <span data-ttu-id="4da75-264">Eftersom kommandot inte är en del av transaktionen börjar ändringen gälla omedelbart.</span><span class="sxs-lookup"><span data-stu-id="4da75-264">Because the command is not part of the transaction, the change is effective immediately.</span></span>

```powershell
$t.append("Windows")
```

<span data-ttu-id="4da75-265">Följande kommando använder samma append-metod för att lägga till text, men den lägger till texten som en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-265">The following command uses the same Append method to add text, but it adds the text as part of the transaction.</span></span> <span data-ttu-id="4da75-266">Kommandot omges av klammerparenteser och anges som värdet för parametern script block för use-Transaction.</span><span class="sxs-lookup"><span data-stu-id="4da75-266">The command is enclosed in braces, and it is set as the value of the ScriptBlock parameter of Use-Transaction.</span></span> <span data-ttu-id="4da75-267">UseTransaction-parametern (UseTx) krävs.</span><span class="sxs-lookup"><span data-stu-id="4da75-267">The UseTransaction parameter (UseTx) is required.</span></span>

```powershell
use-transaction {$t.append(" PowerShell")} -usetx
```

<span data-ttu-id="4da75-268">Om du vill se det aktuella innehållet i den överförda strängen i $t använder du metoden ToString för TransactedString-objektet.</span><span class="sxs-lookup"><span data-stu-id="4da75-268">To see the current content of the transacted string in $t, use the ToString method of the TransactedString object.</span></span>

```powershell
$t.tostring()
```

<span data-ttu-id="4da75-269">Utdata visar att endast de icke-överförda ändringarna är effektiva.</span><span class="sxs-lookup"><span data-stu-id="4da75-269">The output shows that only the non-transacted changes are effective.</span></span>

```output
Windows
```

<span data-ttu-id="4da75-270">Om du vill se det aktuella innehållet i den överförda strängen i $t inifrån transaktionen, bäddar du in uttrycket i ett Use-Transaction-kommando.</span><span class="sxs-lookup"><span data-stu-id="4da75-270">To see the current content of the transacted string in $t from within the transaction, embed the expression in a Use-Transaction command.</span></span>

```powershell
use-transaction {$s.tostring()} -usetx
```

<span data-ttu-id="4da75-271">Utdata visar datakällvyn.</span><span class="sxs-lookup"><span data-stu-id="4da75-271">The output shows the transaction view.</span></span>

```output
PowerShell
```

<span data-ttu-id="4da75-272">Följande kommando utför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-272">The following command commits the transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-273">Så här visar du den sista strängen:</span><span class="sxs-lookup"><span data-stu-id="4da75-273">To see the final string:</span></span>

```
$t.tostring()
PowerShell
```

### <a name="example-8-managing-multi-subscriber-transactions"></a><span data-ttu-id="4da75-274">EXEMPEL 8: HANTERA MULTI-SUBSCRIBER-TRANSAKTIONER</span><span class="sxs-lookup"><span data-stu-id="4da75-274">EXAMPLE 8: MANAGING MULTI-SUBSCRIBER TRANSACTIONS</span></span>

<span data-ttu-id="4da75-275">När du startar en transaktion medan en annan transaktion pågår, skapar inte PowerShell en andra transaktion som standard.</span><span class="sxs-lookup"><span data-stu-id="4da75-275">When you start a transaction while another transaction is in progress, PowerShell does not create a second transaction by default.</span></span> <span data-ttu-id="4da75-276">Istället lägger den till en prenumerant till den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-276">Instead, it adds a subscriber to the current transaction.</span></span>

<span data-ttu-id="4da75-277">Det här exemplet visar hur du visar och hanterar en transaktion med flera prenumerationer.</span><span class="sxs-lookup"><span data-stu-id="4da75-277">This example shows how to view and manage a multi-subscriber transaction.</span></span>

<span data-ttu-id="4da75-278">Börja med att starta en transaktion i program varu nyckeln HKCU: \.</span><span class="sxs-lookup"><span data-stu-id="4da75-278">Begin by starting a transaction in the HKCU:\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-279">Följande kommando använder kommandot Get-Transaction för att hämta den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-279">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="4da75-280">Resultatet visar det objekt som representerar den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-280">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4da75-281">Följande kommando lägger till företags nyckeln till registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-281">The following command adds the MyCompany key to the registry.</span></span> <span data-ttu-id="4da75-282">Kommandot använder parametern UseTransaction för att inkludera kommandot i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-282">The command uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-item MyCompany -UseTransaction
```

<span data-ttu-id="4da75-283">Följande kommando använder kommandot Start-Transaction för att starta en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-283">The following command uses the Start-Transaction command to start a transaction.</span></span> <span data-ttu-id="4da75-284">Även om det här kommandot skrivs i kommando tolken, är det mer sannolikt att det här scenariot inträffar när du kör ett skript som innehåller en transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-284">Although this command is typed at the command prompt, this scenario is more likely to happen when you run a script that contains a transaction.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-285">Ett Get-Transaction-kommando visar att antalet prenumeranter för Transaction-objektet ökar.</span><span class="sxs-lookup"><span data-stu-id="4da75-285">A Get-Transaction command shows that the subscriber count on the transaction object is incremented.</span></span> <span data-ttu-id="4da75-286">Värdet är nu 2.</span><span class="sxs-lookup"><span data-stu-id="4da75-286">The value is now 2.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                2                 Active
```

<span data-ttu-id="4da75-287">Nästa kommando använder cmdleten New-ItemProperty för att lägga till register posten MyKey i företags nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4da75-287">The next command uses the New-ItemProperty cmdlet to add the MyKey registry entry to the MyCompany key.</span></span> <span data-ttu-id="4da75-288">Parametern UseTransaction används för att inkludera kommandot i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-288">It uses the UseTransaction parameter to include the command in the transaction.</span></span>

```powershell
new-itemproperty -path MyCompany -name MyKey -UseTransaction
```

<span data-ttu-id="4da75-289">Min företags nyckel finns inte i registret, men det här kommandot lyckas eftersom de två kommandona ingår i samma transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-289">The MyCompany key does not exist in the registry, but this command succeeds because the two commands are part of the same transaction.</span></span>

<span data-ttu-id="4da75-290">Följande kommando utför transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-290">The following command commits the transaction.</span></span> <span data-ttu-id="4da75-291">Om transaktionen återställdes återställs transaktionen för alla prenumeranter.</span><span class="sxs-lookup"><span data-stu-id="4da75-291">If it rolled back the transaction, the transaction would be rolled back for all the subscribers.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-292">Ett Get-Transaction-kommando visar att antalet prenumeranter för transaktionsobjektet är 1, men värdet för status är fortfarande aktivt (inte dedikerat).</span><span class="sxs-lookup"><span data-stu-id="4da75-292">A Get-Transaction command shows that the subscriber count on the transaction object is 1, but the value of Status is still Active (not Committed).</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4da75-293">Slutför transaktionen genom att ange ett andra kommando för fullständig transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-293">To finish committing the transaction, enter a second Complete- Transaction command.</span></span> <span data-ttu-id="4da75-294">Om du vill genomföra en transaktion med flera prenumerationer måste du ange ett Complete-Transaction-kommando för varje Start-Transaction-kommando.</span><span class="sxs-lookup"><span data-stu-id="4da75-294">To commit a multi-subscriber transaction, you must enter one Complete-Transaction command for each Start-Transaction command.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-295">Ett annat Get-Transaction kommando visar att transaktionen har genomförts.</span><span class="sxs-lookup"><span data-stu-id="4da75-295">Another Get-Transaction command shows that the transaction has been committed.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                0                 Committed
```

### <a name="example-9-managing-independent-transactions"></a><span data-ttu-id="4da75-296">EXEMPEL 9: HANTERA OBEROENDE TRANSAKTIONER</span><span class="sxs-lookup"><span data-stu-id="4da75-296">EXAMPLE 9: MANAGING INDEPENDENT TRANSACTIONS</span></span>

<span data-ttu-id="4da75-297">När du startar en transaktion medan en annan transaktion pågår kan du använda den oberoende parametern för Start-Transaction för att skapa den nya transaktionen oberoende av den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-297">When you start a transaction while another transaction is in progress, you can use the Independent parameter of Start-Transaction to make the new transaction independent of the original transaction.</span></span>

<span data-ttu-id="4da75-298">När du gör det skapar Start-Transaction ett nytt transaktions objekt och gör den nya transaktionen till aktiv transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-298">When you do, Start-Transaction creates a new transaction object and makes the new transaction the active transaction.</span></span>

<span data-ttu-id="4da75-299">Börja med att starta en transaktion i HKCU: \\ Software-nyckeln.</span><span class="sxs-lookup"><span data-stu-id="4da75-299">Begin by starting a transaction in the HKCU:\\Software key.</span></span>

```powershell
start-transaction
```

<span data-ttu-id="4da75-300">Följande kommando använder kommandot Get-Transaction för att hämta den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-300">The following command uses the Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="4da75-301">Resultatet visar det objekt som representerar den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-301">The result shows the object that represents the active transaction.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4da75-302">Följande kommando lägger till register nyckeln min företag som en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-302">The following command adds the MyCompany registry key as part of the transaction.</span></span> <span data-ttu-id="4da75-303">Den använder UseTransaction-parametern (UseTx) för att inkludera kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-303">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyCompany -use
```

<span data-ttu-id="4da75-304">Följande kommando startar en ny transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-304">The following command starts a new transaction.</span></span> <span data-ttu-id="4da75-305">Kommandot använder den oberoende parametern för att ange att transaktionen inte är en prenumerant på den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-305">The command uses the Independent parameter to indicate that this transaction is not a subscriber to the active transaction.</span></span>

```powershell
start-transaction -independent
```

<span data-ttu-id="4da75-306">När du skapar en oberoende transaktion blir den nya transaktionen (senast skapade) den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-306">When you create an independent transaction, the new (most-recently created) transaction becomes the active transaction.</span></span> <span data-ttu-id="4da75-307">Du kan använda ett Get-Transaction-kommando för att hämta den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-307">You can use a Get-Transaction command to get the active transaction.</span></span>

```powershell
get-transaction
```

<span data-ttu-id="4da75-308">Observera att SubscriberCount för transaktionen är 1, vilket indikerar att det inte finns några andra prenumeranter och att transaktionen är ny.</span><span class="sxs-lookup"><span data-stu-id="4da75-308">Note that the SubscriberCount of the transaction is 1, indicating that there are no other subscribers and that the transaction is new.</span></span>

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4da75-309">Den nya transaktionen måste vara slutförd (antingen allokerad eller återställd) innan du kan hantera den ursprungliga transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-309">The new transaction must be finished (either committed or rolled back) before you can manage the original transaction.</span></span>

<span data-ttu-id="4da75-310">Följande kommando lägger till nyckeln MyOtherCompany i registret.</span><span class="sxs-lookup"><span data-stu-id="4da75-310">The following command adds the MyOtherCompany key to the registry.</span></span> <span data-ttu-id="4da75-311">Den använder UseTransaction-parametern (UseTx) för att inkludera kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-311">It uses the UseTransaction parameter (UseTx) to include the command in the active transaction.</span></span>

```powershell
new-item MyOtherCompany -usetx
```

<span data-ttu-id="4da75-312">Återställ nu transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-312">Now, roll back the transaction.</span></span> <span data-ttu-id="4da75-313">Om det fanns en enda transaktion med två prenumeranter återställs hela transaktionen för alla prenumeranter om du återställer transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-313">If there were a single transaction with two subscribers, rolling back the transaction would roll back the entire transaction for all the subscribers.</span></span>

<span data-ttu-id="4da75-314">Men eftersom dessa transaktioner är oberoende, avbryter den senaste transaktionen register ändringarna och gör den ursprungliga transaktionen till en aktiv transaktion.</span><span class="sxs-lookup"><span data-stu-id="4da75-314">However, because these transactions are independent, rolling back the newest transaction cancels the registry changes and makes the original transaction the active transaction.</span></span>

```powershell
undo-transaction
```

<span data-ttu-id="4da75-315">Ett Get-Transaction-kommando bekräftar att den ursprungliga transaktionen fortfarande är aktiv i sessionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-315">A Get-Transaction command confirms that the original transaction is still active in the session.</span></span>

```powershell
get-transaction
```

```output
RollbackPreference   SubscriberCount   Status
------------------   ---------------   ------
Error                1                 Active
```

<span data-ttu-id="4da75-316">Följande kommando utför den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="4da75-316">The following command commits the active transaction.</span></span>

```powershell
complete-transaction
```

<span data-ttu-id="4da75-317">Ett Get-ChildItem-kommando visar att registret har ändrats.</span><span class="sxs-lookup"><span data-stu-id="4da75-317">A Get-ChildItem command shows that the registry has been changed.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="4da75-318">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="4da75-318">SEE ALSO</span></span>

[<span data-ttu-id="4da75-319">Starta transaktion</span><span class="sxs-lookup"><span data-stu-id="4da75-319">Start-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Start-Transaction)

[<span data-ttu-id="4da75-320">Hämta transaktion</span><span class="sxs-lookup"><span data-stu-id="4da75-320">Get-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Get-Transaction)

[<span data-ttu-id="4da75-321">Slutförd transaktion</span><span class="sxs-lookup"><span data-stu-id="4da75-321">Complete-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Complete-Transaction)

[<span data-ttu-id="4da75-322">Ångra-transaktion</span><span class="sxs-lookup"><span data-stu-id="4da75-322">Undo-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Undo-Transaction)

[<span data-ttu-id="4da75-323">Använd transaktion</span><span class="sxs-lookup"><span data-stu-id="4da75-323">Use-Transaction</span></span>](xref:Microsoft.PowerShell.Management.Use-Transaction)

[<span data-ttu-id="4da75-324">Get-PSProvider</span><span class="sxs-lookup"><span data-stu-id="4da75-324">Get-PSProvider</span></span>](xref:Microsoft.PowerShell.Management.Get-PSProvider)

[<span data-ttu-id="4da75-325">Get-ChildItem</span><span class="sxs-lookup"><span data-stu-id="4da75-325">Get-ChildItem</span></span>](xref:Microsoft.PowerShell.Management.Get-ChildItem)

[<span data-ttu-id="4da75-326">about_Providers</span><span class="sxs-lookup"><span data-stu-id="4da75-326">about_Providers</span></span>](about_Providers.md)
