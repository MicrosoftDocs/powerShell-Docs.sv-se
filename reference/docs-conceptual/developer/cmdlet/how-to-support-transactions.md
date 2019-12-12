---
title: Så här stöder du transaktioner | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4732e38c-b1a0-4de7-b6de-75dbde850488
caps.latest.revision: 8
ms.openlocfilehash: c5eea216efd8048aee5768c78c0b48617670f091
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72356303"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="2fce7-102">Ge stöd för transaktioner</span><span class="sxs-lookup"><span data-stu-id="2fce7-102">How to Support Transactions</span></span>

<span data-ttu-id="2fce7-103">I det här exemplet visas de grundläggande kod element som lägger till stöd för transaktioner i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="2fce7-103">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="2fce7-104">Mer information om hur Windows PowerShell hanterar transaktioner finns i [About Transactions][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="2fce7-104">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="2fce7-105">För att stödja transaktioner</span><span class="sxs-lookup"><span data-stu-id="2fce7-105">To support transactions</span></span>

1. <span data-ttu-id="2fce7-106">När du deklarerar cmdlet-attributet anger du att cmdleten stöder transaktioner.</span><span class="sxs-lookup"><span data-stu-id="2fce7-106">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="2fce7-107">När cmdleten stöder transaktioner lägger Windows PowerShell till `UseTransaction`-parametern i cmdleten när den körs.</span><span class="sxs-lookup"><span data-stu-id="2fce7-107">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="2fce7-108">I en av metoderna för indata-bearbetning lägger du till ett `if`-block för att avgöra om en transaktion är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="2fce7-108">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="2fce7-109">Om `if`-instruktionen matchar `true`kan åtgärderna i den här instruktionen utföras inom kontexten för den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="2fce7-109">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="2fce7-110">Se även</span><span class="sxs-lookup"><span data-stu-id="2fce7-110">See Also</span></span>

[<span data-ttu-id="2fce7-111">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="2fce7-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
