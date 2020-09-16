---
title: Så här anropar du skript i en cmdlet | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 248ad7e2e35fe53682836d094a391023007fa0b7
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784137"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="3e76e-102">Anropa skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e76e-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="3e76e-103">Det här exemplet visar hur du anropar ett skript som anges för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="3e76e-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="3e76e-104">Skriptet körs av cmdleten och resultatet returneras till-cmdleten som en samling [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt.</span><span class="sxs-lookup"><span data-stu-id="3e76e-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="3e76e-105">Anropa ett skript block</span><span class="sxs-lookup"><span data-stu-id="3e76e-105">To invoke a script block</span></span>

1. <span data-ttu-id="3e76e-106">Kommandot verifierar att ett skript block angavs för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="3e76e-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="3e76e-107">Om ett skript block angavs anropar kommandot skript blocket med de parametrar som krävs.</span><span class="sxs-lookup"><span data-stu-id="3e76e-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="3e76e-108">Skriptet itererar sedan igenom den returnerade samlingen av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt och utför nödvändiga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="3e76e-108">Then, the script iterates through the returned collection of [System.Management.Automation.PSObject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3e76e-109">Se även</span><span class="sxs-lookup"><span data-stu-id="3e76e-109">See Also</span></span>

[<span data-ttu-id="3e76e-110">Skriva en Windows PowerShell-cmdlet</span><span class="sxs-lookup"><span data-stu-id="3e76e-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
