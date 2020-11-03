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
# <span data-ttu-id="5e035-103">Use-Transaction</span><span class="sxs-lookup"><span data-stu-id="5e035-103">Use-Transaction</span></span>

## <span data-ttu-id="5e035-104">SAMMANFATTNING</span><span class="sxs-lookup"><span data-stu-id="5e035-104">SYNOPSIS</span></span>
<span data-ttu-id="5e035-105">Lägger till skript blocket i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-105">Adds the script block to the active transaction.</span></span>

## <span data-ttu-id="5e035-106">SYNTAX</span><span class="sxs-lookup"><span data-stu-id="5e035-106">SYNTAX</span></span>

```
Use-Transaction [-TransactedScript] <ScriptBlock> [-UseTransaction] [<CommonParameters>]
```

## <span data-ttu-id="5e035-107">BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="5e035-107">DESCRIPTION</span></span>
<span data-ttu-id="5e035-108">Cmdleten **use-Transaction** lägger till ett skript block i en aktiv transaktion.</span><span class="sxs-lookup"><span data-stu-id="5e035-108">The **Use-Transaction** cmdlet adds a script block to an active transaction.</span></span>
<span data-ttu-id="5e035-109">På så sätt kan du utföra överförda skript med hjälp av transaktions-aktiverade Microsoft .NET Ramverks objekt.</span><span class="sxs-lookup"><span data-stu-id="5e035-109">This enables you to do transacted scripting by using transaction-enabled Microsoft .NET Framework objects.</span></span>
<span data-ttu-id="5e035-110">Skript blocket kan bara innehålla transaktions aktiverade .NET Framework objekt, till exempel instanser av klassen Microsoft. PowerShell. commands. Management. TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-110">The script block can contain only transaction-enabled .NET Framework objects, such as instances of the Microsoft.PowerShell.Commands.Management.TransactedString class.</span></span>

<span data-ttu-id="5e035-111">Parametern *UseTransaction* , som är valfri för de flesta cmdletar, krävs när du använder den här cmdleten.</span><span class="sxs-lookup"><span data-stu-id="5e035-111">The *UseTransaction* parameter, which is optional for most cmdlets, is required when you use this cmdlet.</span></span>

<span data-ttu-id="5e035-112">**Use-Transaction** är en uppsättning cmdletar som stöder funktionen transaktioner i Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5e035-112">**Use-Transaction** is one of a set of cmdlets that support the transactions feature in Windows PowerShell.</span></span>
<span data-ttu-id="5e035-113">Mer information finns i about_Transactions.</span><span class="sxs-lookup"><span data-stu-id="5e035-113">For more information, see about_Transactions.</span></span>

## <span data-ttu-id="5e035-114">EXEMPEL</span><span class="sxs-lookup"><span data-stu-id="5e035-114">EXAMPLES</span></span>

### <span data-ttu-id="5e035-115">Exempel 1: skript med hjälp av ett transaktions aktiverat objekt</span><span class="sxs-lookup"><span data-stu-id="5e035-115">Example 1: Script by using a transaction-enabled object</span></span>

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

<span data-ttu-id="5e035-116">Det här exemplet visar hur du använder **use-Transaction** för att skript mot ett transaktions aktiverat .NET Framework-objekt.</span><span class="sxs-lookup"><span data-stu-id="5e035-116">This example shows how to use **Use-Transaction** to script against a transaction-enabled .NET Framework object.</span></span>
<span data-ttu-id="5e035-117">I det här fallet är objektet ett **TransactedString** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5e035-117">In this case, the object is a **TransactedString** object.</span></span>

<span data-ttu-id="5e035-118">Det första kommandot använder Start-Transaction-cmdlet för att starta en transaktion.</span><span class="sxs-lookup"><span data-stu-id="5e035-118">The first command uses the Start-Transaction cmdlet to start a transaction.</span></span>

<span data-ttu-id="5e035-119">Det andra kommandot använder kommandot New-Object för att skapa ett **TransactedString** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5e035-119">The second command uses the New-Object command to create a **TransactedString** object.</span></span>
<span data-ttu-id="5e035-120">Objektet lagras i variabeln $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-120">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="5e035-121">De tredje och fjärde kommandona använder båda metoden **APPEND** för **TransactedString** -objektet för att lägga till text till värdet för $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-121">The third and fourth commands both use the **Append** method of the **TransactedString** object to add text to the value of $TransactedString.</span></span>
<span data-ttu-id="5e035-122">Ett kommando är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-122">One command is part of the transaction.</span></span>
<span data-ttu-id="5e035-123">Det andra kommandot är inte.</span><span class="sxs-lookup"><span data-stu-id="5e035-123">The other command is not.</span></span>

<span data-ttu-id="5e035-124">Det tredje kommandot använder metoden **APPEND** i den överförda strängen för att lägga till Hej till värdet för $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-124">The third command uses the **Append** method of the transacted string to add Hello to the value of $TransactedString.</span></span>
<span data-ttu-id="5e035-125">Eftersom kommandot inte är en del av transaktionen tillämpas ändringen omedelbart.</span><span class="sxs-lookup"><span data-stu-id="5e035-125">Because the command is not part of the transaction, the change is applied immediately.</span></span>

<span data-ttu-id="5e035-126">Det fjärde kommandot använder **use-Transaction** för att lägga till text i strängen i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-126">The fourth command uses **Use-Transaction** to add text to the string in the transaction.</span></span>
<span data-ttu-id="5e035-127">Kommandot använder metoden **APPEND** för att lägga till ", World" till värdet för $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-127">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>
<span data-ttu-id="5e035-128">Kommandot omges av klammerparenteser ( {} ) för att göra det till ett skript block.</span><span class="sxs-lookup"><span data-stu-id="5e035-128">The command is enclosed in braces ( {} ) to make it a script block.</span></span>
<span data-ttu-id="5e035-129">Parametern *UseTransaction* krävs i det här kommandot.</span><span class="sxs-lookup"><span data-stu-id="5e035-129">The *UseTransaction* parameter is required in this command.</span></span>

<span data-ttu-id="5e035-130">De femte och sjätte kommandona använder metoden **toString** för **TransactedString** -objektet för att visa värdet för **TransactedString** som en sträng.</span><span class="sxs-lookup"><span data-stu-id="5e035-130">The fifth and sixth commands use the **ToString** method of the **TransactedString** object to display the value of the **TransactedString** as a string.</span></span>
<span data-ttu-id="5e035-131">Ett nytt kommando är en del av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-131">Again, one command is part of the transaction.</span></span>
<span data-ttu-id="5e035-132">Den andra transaktionen är inte.</span><span class="sxs-lookup"><span data-stu-id="5e035-132">The other transaction is not.</span></span>

<span data-ttu-id="5e035-133">Det femte kommandot använder metoden **toString** för att visa det aktuella värdet för variabeln $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-133">The fifth command uses the **ToString** method to display the current value of the $TransactedString variable.</span></span>
<span data-ttu-id="5e035-134">Eftersom den inte är en del av transaktionen visas bara det aktuella status för strängen.</span><span class="sxs-lookup"><span data-stu-id="5e035-134">Because it is not part of the transaction, it displays only the current state of the string.</span></span>

<span data-ttu-id="5e035-135">Det sjätte kommandot använder **use-Transaction** för att köra samma kommando i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-135">The sixth command uses **Use-Transaction** to run the same command in the transaction.</span></span>
<span data-ttu-id="5e035-136">Eftersom kommandot är en del av transaktionen, visas det aktuella värdet för strängen i transaktionen, ungefär som en förhands granskning av transaktionens ändringar.</span><span class="sxs-lookup"><span data-stu-id="5e035-136">Because the command is part of the transaction, it displays the current value of the string in the transaction, much like a preview of the transaction changes.</span></span>

<span data-ttu-id="5e035-137">Det sjunde kommandot använder Complete-Transaction-cmdlet för att genomföra transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-137">The seventh command uses the Complete-Transaction cmdlet to commit the transaction.</span></span>

<span data-ttu-id="5e035-138">Det sista kommandot använder metoden **toString** för att Visa resultatvärdet för variabeln som en sträng.</span><span class="sxs-lookup"><span data-stu-id="5e035-138">The final command uses the **ToString** method to display the resulting value of the variable as a string.</span></span>

### <span data-ttu-id="5e035-139">Exempel 2: återställa en transaktion</span><span class="sxs-lookup"><span data-stu-id="5e035-139">Example 2: Roll back a transaction</span></span>

```
PS C:\> Start-Transaction
PS C:\> $transactedString = New-Object Microsoft.PowerShell.Commands.Management.TransactedString
PS C:\> $transactedString.Append("Hello")
PS C:\> Use-Transaction -TransactedScript { $transactedString.Append(", World") } -UseTransaction
PS C:\> Undo-Transaction
PS C:\> $transactedString.ToString()
Hello
```

<span data-ttu-id="5e035-140">I det här exemplet visas effekterna av att återställa en transaktion som innehåller kommandon för att **använda transaktioner** .</span><span class="sxs-lookup"><span data-stu-id="5e035-140">This example shows the effect of rolling back a transaction that includes **Use-Transaction** commands.</span></span>
<span data-ttu-id="5e035-141">Precis som med alla kommandon i en transaktion ignoreras de överförda ändringarna och data är oförändrade när transaktionen återställs.</span><span class="sxs-lookup"><span data-stu-id="5e035-141">Like all commands in a transaction, when the transaction is rolled back, the transacted changes are discarded and the data is unchanged.</span></span>

<span data-ttu-id="5e035-142">Det första kommandot använder **Start transaktion** för att starta en transaktion.</span><span class="sxs-lookup"><span data-stu-id="5e035-142">The first command uses **Start-Transaction** to start a transaction.</span></span>

<span data-ttu-id="5e035-143">Det andra kommandot använder **New-Object** för att skapa ett **TransactedString** -objekt.</span><span class="sxs-lookup"><span data-stu-id="5e035-143">The second command uses **New-Object** to create a **TransactedString** object.</span></span>
<span data-ttu-id="5e035-144">Objektet lagras i variabeln $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-144">It stores the object in the $TransactedString variable.</span></span>

<span data-ttu-id="5e035-145">Det tredje kommandot, som inte är en del av transaktionen, använder metoden **APPEND** för att lägga till "Hej" till värdet för $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-145">The third command, which is not part of the transaction, uses the **Append** method to add "Hello" to the value of $TransactedString.</span></span>

<span data-ttu-id="5e035-146">Det fjärde kommandot använder **use-Transaction** för att köra ett annat kommando som använder metoden **APPEND** i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-146">The fourth command uses **Use-Transaction** to run another command that uses the **Append** method in the transaction.</span></span>
<span data-ttu-id="5e035-147">Kommandot använder metoden **APPEND** för att lägga till ", World" till värdet för $TransactedString.</span><span class="sxs-lookup"><span data-stu-id="5e035-147">The command uses the **Append** method to add ", World" to the value of $TransactedString.</span></span>

<span data-ttu-id="5e035-148">Det femte kommandot använder Undo-Transaction-cmdlet: en för att återställa transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-148">The fifth command uses the Undo-Transaction cmdlet to roll back the transaction.</span></span>
<span data-ttu-id="5e035-149">Därför återställs alla kommandon som utförs i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-149">As a result, all commands performed in the transaction are reversed.</span></span>

<span data-ttu-id="5e035-150">Det sista kommandot använder metoden **toString** för att Visa resultatvärdet för $TransactedString som en sträng.</span><span class="sxs-lookup"><span data-stu-id="5e035-150">The final command uses the **ToString** method to display the resulting value of $TransactedString as a string.</span></span>
<span data-ttu-id="5e035-151">Resultaten visar att endast ändringar som gjorts utanför transaktionen tillämpades på objektet.</span><span class="sxs-lookup"><span data-stu-id="5e035-151">The results show that only the changes that were made outside the transaction were applied to the object.</span></span>

## <span data-ttu-id="5e035-152">PARAMETRAR</span><span class="sxs-lookup"><span data-stu-id="5e035-152">PARAMETERS</span></span>

### <span data-ttu-id="5e035-153">-TransactedScript</span><span class="sxs-lookup"><span data-stu-id="5e035-153">-TransactedScript</span></span>
<span data-ttu-id="5e035-154">Anger det skript block som körs i transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-154">Specifies the script block that is run in the transaction.</span></span>
<span data-ttu-id="5e035-155">Ange ett giltigt skript block som omges av klammerparenteser ({}).</span><span class="sxs-lookup"><span data-stu-id="5e035-155">Enter any valid script block enclosed in braces ( { } ).</span></span>
<span data-ttu-id="5e035-156">Den här parametern är obligatorisk.</span><span class="sxs-lookup"><span data-stu-id="5e035-156">This parameter is required.</span></span>

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

### <span data-ttu-id="5e035-157">– UseTransaction</span><span class="sxs-lookup"><span data-stu-id="5e035-157">-UseTransaction</span></span>
<span data-ttu-id="5e035-158">Inkluderar kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-158">Includes the command in the active transaction.</span></span>
<span data-ttu-id="5e035-159">Den här parametern är bara giltig medan en transaktion pågår.</span><span class="sxs-lookup"><span data-stu-id="5e035-159">This parameter is valid only when a transaction is in progress.</span></span>
<span data-ttu-id="5e035-160">Mer information finns i about_transactions.</span><span class="sxs-lookup"><span data-stu-id="5e035-160">For more information, see about_transactions.</span></span>

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

### <span data-ttu-id="5e035-161">CommonParameters</span><span class="sxs-lookup"><span data-stu-id="5e035-161">CommonParameters</span></span>
<span data-ttu-id="5e035-162">Denna cmdlet har stöd för parametrarna -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction och -WarningVariable.</span><span class="sxs-lookup"><span data-stu-id="5e035-162">This cmdlet supports the common parameters: -Debug, -ErrorAction, -ErrorVariable, -InformationAction, -InformationVariable, -OutVariable, -OutBuffer, -PipelineVariable, -Verbose, -WarningAction, and -WarningVariable.</span></span> <span data-ttu-id="5e035-163">Mer information finns i [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span><span class="sxs-lookup"><span data-stu-id="5e035-163">For more information, see [about_CommonParameters](https://go.microsoft.com/fwlink/?LinkID=113216).</span></span>

## <span data-ttu-id="5e035-164">INDATA</span><span class="sxs-lookup"><span data-stu-id="5e035-164">INPUTS</span></span>

### <span data-ttu-id="5e035-165">Inget</span><span class="sxs-lookup"><span data-stu-id="5e035-165">None</span></span>
<span data-ttu-id="5e035-166">Du kan inte skicka pipe-ininformation till denna cmdlet.</span><span class="sxs-lookup"><span data-stu-id="5e035-166">You cannot pipe input to this cmdlet.</span></span>

## <span data-ttu-id="5e035-167">UTDATA</span><span class="sxs-lookup"><span data-stu-id="5e035-167">OUTPUTS</span></span>

### <span data-ttu-id="5e035-168">PSObject</span><span class="sxs-lookup"><span data-stu-id="5e035-168">PSObject</span></span>
<span data-ttu-id="5e035-169">Den här cmdleten returnerar resultatet av transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-169">This cmdlet returns the result of the transaction.</span></span>

## <span data-ttu-id="5e035-170">ANTECKNINGAR</span><span class="sxs-lookup"><span data-stu-id="5e035-170">NOTES</span></span>

* <span data-ttu-id="5e035-171">Parametern *UseTransaction* innehåller kommandot i den aktiva transaktionen.</span><span class="sxs-lookup"><span data-stu-id="5e035-171">The *UseTransaction* parameter includes the command in the active transaction.</span></span> <span data-ttu-id="5e035-172">Eftersom cmdleten **use-Transaction** alltid används i transaktioner, krävs den här parametern för att använda kommandot **-Transaction-** kommando gällande.</span><span class="sxs-lookup"><span data-stu-id="5e035-172">Because the **Use-Transaction** cmdlet is always used in transactions, this parameter is required to make any **Use-Transaction** command effective.</span></span>

*

## <span data-ttu-id="5e035-173">RELATERADE LÄNKAR</span><span class="sxs-lookup"><span data-stu-id="5e035-173">RELATED LINKS</span></span>

[<span data-ttu-id="5e035-174">Slutförd transaktion</span><span class="sxs-lookup"><span data-stu-id="5e035-174">Complete-Transaction</span></span>](Complete-Transaction.md)

[<span data-ttu-id="5e035-175">Hämta transaktion</span><span class="sxs-lookup"><span data-stu-id="5e035-175">Get-Transaction</span></span>](Get-Transaction.md)

[<span data-ttu-id="5e035-176">Starta transaktion</span><span class="sxs-lookup"><span data-stu-id="5e035-176">Start-Transaction</span></span>](Start-Transaction.md)

[<span data-ttu-id="5e035-177">Ångra-transaktion</span><span class="sxs-lookup"><span data-stu-id="5e035-177">Undo-Transaction</span></span>](Undo-Transaction.md)
