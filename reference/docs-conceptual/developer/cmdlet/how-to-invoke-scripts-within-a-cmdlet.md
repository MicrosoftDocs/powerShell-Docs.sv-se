---
title: Så här anropar du skript i en cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 7dcb8bc20ab56225764854f9dc6fdfd858ed7451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355512"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="557f2-102">Anropa skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="557f2-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="557f2-103">Det här exemplet visar hur du anropar ett skript som anges för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="557f2-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="557f2-104">Skriptet körs av cmdleten och resultatet returneras till-cmdleten som en samling [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt.</span><span class="sxs-lookup"><span data-stu-id="557f2-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="557f2-105">Anropa ett skript block</span><span class="sxs-lookup"><span data-stu-id="557f2-105">To invoke a script block</span></span>

1. <span data-ttu-id="557f2-106">Kommandot verifierar att ett skript block angavs för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="557f2-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="557f2-107">Om ett skript block angavs anropar kommandot skript blocket med de parametrar som krävs.</span><span class="sxs-lookup"><span data-stu-id="557f2-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

    ```csharp
    if (script != null)
    {
      WriteDebug("Executing script block.");

      // Invoke the script block with the required arguments.
      Collection<PSObject> PSObjects =
                     script.Invoke(
                                   line,
                                   simpleMatch,
                                   caseSensitive
                                  );
    ```

2. <span data-ttu-id="557f2-108">Skriptet itererar sedan igenom den returnerade samlingen av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt och utför nödvändiga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="557f2-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

    ```c
    foreach (PSObject psObject in psObjects)
    {
      if (LanguagePrimitives.IsTrue(psObject))
      {
        result = new MatchInfo();
        result.Line = line;
        result.IgnoreCase = !caseSensitive;

        break;
      }
    }

    ```

## <a name="see-also"></a><span data-ttu-id="557f2-109">Se även</span><span class="sxs-lookup"><span data-stu-id="557f2-109">See Also</span></span>

[<span data-ttu-id="557f2-110">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="557f2-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
