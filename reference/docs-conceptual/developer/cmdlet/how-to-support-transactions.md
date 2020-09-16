---
title: Så här stöder du transaktioner | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 6fda27394091195b589afef5ee53c6d3bec4efc0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87786619"
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
