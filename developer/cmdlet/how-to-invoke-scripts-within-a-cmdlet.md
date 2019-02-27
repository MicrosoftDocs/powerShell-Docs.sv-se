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
# <a name="how-to-invoke-scripts-within-a-cmdlet"></a>Anropa skript inuti en cmdlet

Det här exemplet visar hur du anropar ett skript som har angetts för en cmdlet. Skriptet har körts av cmdlet: en och resultaten returneras till cmdlet: en som en samling [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objekt.

## <a name="to-invoke-a-script-block"></a>Anropa ett skriptblock

1. Kommandot verifierar att ett skriptblock har angetts till cmdleten. Om ett skriptblock, anropar kommandot skriptblocket med dess obligatoriska parametrar.

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

2. Sedan skriptet upprepas returnerade insamling av [System.Management.Automation.Psobject](/dotnet/api/System.Management.Automation.PSObject) objekt och utföra nödvändiga åtgärder.

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

[Skriva en Windows PowerShell-Cmdlet](./writing-a-windows-powershell-cmdlet.md)
