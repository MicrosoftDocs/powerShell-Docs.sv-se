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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Anropa skript inuti en cmdlet

Det här exemplet visar hur du anropar ett skript som anges för en cmdlet. Skriptet körs av cmdleten och resultatet returneras till-cmdleten som en samling [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt.

## <a name="to-invoke-a-script-block"></a>Anropa ett skript block

1. Kommandot verifierar att ett skript block angavs för cmdleten. Om ett skript block angavs anropar kommandot skript blocket med de parametrar som krävs.

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

2. Skriptet itererar sedan igenom den returnerade samlingen av [system. Management. Automation. PSObject](/dotnet/api/System.Management.Automation.PSObject) -objekt och utför nödvändiga åtgärder.

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

## <a name="see-also"></a>Se även

[Skriva en Windows PowerShell-cmdlet](./writing-a-windows-powershell-cmdlet.md)
