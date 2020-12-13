---
ms.date: 09/13/2016
ms.topic: reference
title: Anropa skript inuti en cmdlet
description: Anropa skript inuti en cmdlet
ms.openlocfilehash: f4a43a1e1240854e57deac5721e1e070c1a45a51
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667036"
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
