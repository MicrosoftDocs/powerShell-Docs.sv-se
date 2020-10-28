---
ms.date: 09/13/2016
ms.topic: reference
title: Anropa skript inuti en cmdlet
description: Anropa skript inuti en cmdlet
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667036"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="1437f-103">Anropa skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="1437f-103">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="1437f-104">Det här exemplet visar hur du anropar ett skript som anges för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1437f-104">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="1437f-105">Skriptet körs av cmdleten och resultatet returneras till-cmdleten som en samling [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt.</span><span class="sxs-lookup"><span data-stu-id="1437f-105">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="1437f-106">Anropa ett skript block</span><span class="sxs-lookup"><span data-stu-id="1437f-106">To invoke a script block</span></span>

1. <span data-ttu-id="1437f-107">Kommandot verifierar att ett skript block angavs för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="1437f-107">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="1437f-108">Om ett skript block angavs anropar kommandot skript blocket med de parametrar som krävs.</span><span class="sxs-lookup"><span data-stu-id="1437f-108">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="1437f-109">Skriptet itererar sedan igenom den returnerade samlingen av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt och utför nödvändiga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="1437f-109">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="1437f-110">Se även</span><span class="sxs-lookup"><span data-stu-id="1437f-110">See Also</span></span>

[<span data-ttu-id="1437f-111">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="1437f-111">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
