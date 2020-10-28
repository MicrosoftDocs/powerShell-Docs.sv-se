---
ms.date: 09/13/2016
ms.topic: reference
title: Ge stöd för transaktioner
description: Ge stöd för transaktioner
ms.openlocfilehash: 5691c246830dab9f4808801c04353ebfb2c3e981
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666968"
---
# <a name="how-to-support-transactions"></a>Ge stöd för transaktioner

I det här exemplet visas de grundläggande kod element som lägger till stöd för transaktioner i en cmdlet.

> [!IMPORTANT]
> Mer information om hur Windows PowerShell hanterar transaktioner finns i [About Transactions][about_Transactions].

## <a name="to-support-transactions"></a>För att stödja transaktioner

1. När du deklarerar cmdlet-attributet anger du att cmdleten stöder transaktioner.
   När cmdleten stöder transaktioner lägger Windows PowerShell till- `UseTransaction` parametern i cmdleten när den körs.

    ```csharp
    [Cmdlet(VerbsCommunications.Send, "GreetingTx",
            SupportsTransactions=true )]
    ```

2. I en av metoderna för indata-bearbetning lägger `if` du till ett block för att avgöra om en transaktion är tillgänglig.
   Om `if` instruktionen matchas till `true` kan åtgärderna i den här instruktionen utföras inom kontexten för den aktuella transaktionen.

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
