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
