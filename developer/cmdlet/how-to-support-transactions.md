---
title: Ge stöd för transaktioner | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067866"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="e8717-102">Ge stöd för transaktioner</span><span class="sxs-lookup"><span data-stu-id="e8717-102">How to Support Transactions</span></span>

<span data-ttu-id="e8717-103">Det här exemplet visar de grundläggande kodelement som lägger till stöd för transaktioner i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="e8717-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e8717-104">Läs mer om hur Windows PowerShell hanterar transaktioner [om transaktioner][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="e8717-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="e8717-105">Stöd för transaktioner</span><span class="sxs-lookup"><span data-stu-id="e8717-105">To support transactions</span></span>

1. <span data-ttu-id="e8717-106">När du deklarerar Cmdlet-attributet kan du ange att cmdleten stöder transaktioner.</span><span class="sxs-lookup"><span data-stu-id="e8717-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="e8717-107">När cmdleten har stöd för transaktioner, Windows PowerShell lägger till den `UseTransaction` parameter till cmdleten när den körs.</span><span class="sxs-lookup"><span data-stu-id="e8717-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="e8717-108">Inom ett indata metoderna, lägger du till en `if` blockera att avgöra om en transaktion är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="e8717-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="e8717-109">Om den `if` instruktionen matchar `true`, åtgärderna i den här instruktionen kan utföras inom ramen för den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="e8717-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="e8717-110">Se även</span><span class="sxs-lookup"><span data-stu-id="e8717-110">See Also</span></span>

[<span data-ttu-id="e8717-111">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="e8717-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
