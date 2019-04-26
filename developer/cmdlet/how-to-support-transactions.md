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
# <a name="how-to-support-transactions"></a>Ge stöd för transaktioner

Det här exemplet visar de grundläggande kodelement som lägger till stöd för transaktioner i en cmdlet.

> [!IMPORTANT]
> Läs mer om hur Windows PowerShell hanterar transaktioner [om transaktioner][about_Transactions].

## <a name="to-support-transactions"></a>Stöd för transaktioner

1. När du deklarerar Cmdlet-attributet kan du ange att cmdleten stöder transaktioner.
   När cmdleten har stöd för transaktioner, Windows PowerShell lägger till den `UseTransaction` parameter till cmdleten när den körs.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. Inom ett indata metoderna, lägger du till en `if` blockera att avgöra om en transaktion är tillgänglig.
   Om den `if` instruktionen matchar `true`, åtgärderna i den här instruktionen kan utföras inom ramen för den aktuella transaktionen.

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)

<!-- External URLs -->

[about_Transactions]: /powershell/module/Microsoft.PowerShell.Core/About/about_Transactions
