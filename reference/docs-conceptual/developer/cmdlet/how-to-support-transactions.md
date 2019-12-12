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
# <a name="how-to-support-transactions"></a>Ge stöd för transaktioner

I det här exemplet visas de grundläggande kod element som lägger till stöd för transaktioner i en cmdlet.

> [!IMPORTANT]
> Mer information om hur Windows PowerShell hanterar transaktioner finns i [About Transactions][about_Transactions].

## <a name="to-support-transactions"></a>För att stödja transaktioner

1. När du deklarerar cmdlet-attributet anger du att cmdleten stöder transaktioner.
   När cmdleten stöder transaktioner lägger Windows PowerShell till `UseTransaction`-parametern i cmdleten när den körs.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. I en av metoderna för indata-bearbetning lägger du till ett `if`-block för att avgöra om en transaktion är tillgänglig.
   Om `if`-instruktionen matchar `true`kan åtgärderna i den här instruktionen utföras inom kontexten för den aktuella transaktionen.

    ```csharp
    if (TransactionAvailable())
    {
      using (CurrentPSTransaction)
      {
        WriteObject("Hello " + name + "  from within a transaction.");
      }
    }
    ```

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
