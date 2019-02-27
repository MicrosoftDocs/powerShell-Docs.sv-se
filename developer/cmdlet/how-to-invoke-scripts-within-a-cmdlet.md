---
title: Hur du anropar skript i en Cmdlet | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cc0bc6ce-48a5-4d9c-927e-636bca743e9f
caps.latest.revision: 9
ms.openlocfilehash: 4b4d5645785b751eb1390e196f5b9437b4a1e13b
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846699"
---
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a><span data-ttu-id="b50e8-102">Anropa skript inuti en cmdlet</span><span class="sxs-lookup"><span data-stu-id="b50e8-102">How to Invoke Scripts Within a Cmdlet</span></span>

<span data-ttu-id="b50e8-103">Det här exemplet visar hur du anropar ett skript som har angetts för en cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b50e8-103">This example shows how to invoke a script that is supplied to a cmdlet.</span></span> <span data-ttu-id="b50e8-104">Skriptet har körts av cmdlet: en och resultaten returneras till cmdlet: en som en samling [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objekt.</span><span class="sxs-lookup"><span data-stu-id="b50e8-104">The script is executed by the cmdlet, and its results are returned to the cmdlet as a collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects.</span></span>

## <a name="to-invoke-a-script-block"></a><span data-ttu-id="b50e8-105">Anropa ett skriptblock</span><span class="sxs-lookup"><span data-stu-id="b50e8-105">To invoke a script block</span></span>

1. <span data-ttu-id="b50e8-106">Kommandot verifierar att ett skriptblock har angetts till cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b50e8-106">The command verifies that a script block was supplied to the cmdlet.</span></span> <span data-ttu-id="b50e8-107">Om ett skriptblock, anropar kommandot skriptblocket med dess obligatoriska parametrar.</span><span class="sxs-lookup"><span data-stu-id="b50e8-107">If a script block was supplied, the command invokes the script block with its required parameters.</span></span>

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

2. <span data-ttu-id="b50e8-108">Sedan skriptet upprepas returnerade insamling av [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objekt och utföra nödvändiga åtgärder.</span><span class="sxs-lookup"><span data-stu-id="b50e8-108">Then, the script iterates through the returned collection of [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objects and perform the necessary operations.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b50e8-109">Se även</span><span class="sxs-lookup"><span data-stu-id="b50e8-109">See Also</span></span>

[<span data-ttu-id="b50e8-110">Skriva en Windows PowerShell-Cmdlet</span><span class="sxs-lookup"><span data-stu-id="b50e8-110">Writing a Windows PowerShell Cmdlet</span></span>](./writing-a-windows-powershell-cmdlet.md)
