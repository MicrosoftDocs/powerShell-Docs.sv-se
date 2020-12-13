---
ms.date: 09/13/2016
ms.topic: reference
title: Ge stöd för transaktioner
description: Ge stöd för transaktioner
ms.openlocfilehash: 5691c246830dab9f4808801c04353ebfb2c3e981
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666968"
---
# <a name="how-to-support-transactions"></a><span data-ttu-id="f7a9b-103">Ge stöd för transaktioner</span><span class="sxs-lookup"><span data-stu-id="f7a9b-103">How to Support Transactions</span></span>

<span data-ttu-id="f7a9b-104">I det här exemplet visas de grundläggande kod element som lägger till stöd för transaktioner i en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="f7a9b-104">This example shows the basic code elements that add support for transactions to a cmdlet.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="f7a9b-105">Mer information om hur Windows PowerShell hanterar transaktioner finns i [About Transactions][about_Transactions].</span><span class="sxs-lookup"><span data-stu-id="f7a9b-105">For more information about how Windows PowerShell handles transactions, see [About Transactions][about_Transactions].</span></span>

## <a name="to-support-transactions"></a><span data-ttu-id="f7a9b-106">För att stödja transaktioner</span><span class="sxs-lookup"><span data-stu-id="f7a9b-106">To support transactions</span></span>

1. <span data-ttu-id="f7a9b-107">När du deklarerar cmdlet-attributet anger du att cmdleten stöder transaktioner.</span><span class="sxs-lookup"><span data-stu-id="f7a9b-107">When you declare the Cmdlet attribute, specify that the cmdlet supports transactions.</span></span>
   <span data-ttu-id="f7a9b-108">När cmdleten stöder transaktioner lägger Windows PowerShell till- `UseTransaction` parametern i cmdleten när den körs.</span><span class="sxs-lookup"><span data-stu-id="f7a9b-108">When the cmdlet supports transactions, Windows PowerShell adds the `UseTransaction` parameter to the cmdlet when it is run.</span></span>

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. <span data-ttu-id="f7a9b-109">I en av metoderna för indata-bearbetning lägger `if` du till ett block för att avgöra om en transaktion är tillgänglig.</span><span class="sxs-lookup"><span data-stu-id="f7a9b-109">Within one of the input processing methods, add an `if` block to determine if a transaction is available.</span></span>
   <span data-ttu-id="f7a9b-110">Om `if` instruktionen matchas till `true` kan åtgärderna i den här instruktionen utföras inom kontexten för den aktuella transaktionen.</span><span class="sxs-lookup"><span data-stu-id="f7a9b-110">If the `if` statement resolves to `true`, the actions within this statement can be performed within the context of the current transaction.</span></span>

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a><span data-ttu-id="f7a9b-111">Se även</span><span class="sxs-lookup"><span data-stu-id="f7a9b-111">See Also</span></span>

[<span data-ttu-id="f7a9b-112">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="f7a9b-112">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
