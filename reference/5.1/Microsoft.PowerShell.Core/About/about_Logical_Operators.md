---
description: Beskriver de operatorer som ansluter instruktioner i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_logical_operators?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Logical_Operators
ms.openlocfilehash: 21a2e759c4672baca9fab9a9eeb3bbb851c5e691
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93271533"
---
# <a name="about_logical_operators"></a>about_Logical_Operators

## <a name="short-description"></a>KORT BESKRIVNING

Beskriver de operatorer som ansluter instruktioner i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

De logiska PowerShell-operatörerna ansluter uttryck och uttryck, så att du kan använda ett enda uttryck för att testa flera villkor.

Följande uttryck använder till exempel operatorn och och för att ansluta tre villkors satser. Instruktionen är endast sann när värdet för $a är större än värdet för $b och antingen $a eller $b är mindre än
20.

```powershell
($a -gt $b) -and (($a -lt 20) -or ($b -lt 20))
```

PowerShell stöder följande logiska operatorer.

|Operator|Beskrivning                        |Exempel                   |
|--------|-----------------------------------|--------------------------|
|`-and`  |Logiska och. SANT när båda        |`(1 -eq 1) -and (1 -eq 2)`|
|        |-instruktioner är sanna.               |`False`                   |
|`-or`   |Logiskt eller. SANT när antingen       |`(1 -eq 1) -or (1 -eq 2)` |
|        |instruktionen är TRUE.                 |`True`                    |
|`-xor`  |Logisk exklusiv eller. SANT när    |`(1 -eq 1) -xor (2 -eq 2)`|
|        |endast en instruktion är sann         |`False`                   |
|`-not`  |Logiskt not. Negerar instruktionen |`-not (1 -eq 1)`          |
|        |som följer.                      |`False`                   |
|`!`     |Samma som `-not`                     |`!(1 -eq 1)`              |
|        |                                   |`False`                   |

 Obs!

I de föregående exemplen används även operatorn Equal to `-eq` . Mer information finns i [about_Comparison_Operators](about_Comparison_Operators.md). Exemplen använder också booleska värden för heltal. Heltalet 0 har värdet FALSe. Alla andra heltal har värdet sant.

De logiska operatorernas syntax är följande:

```
<statement> {-AND | -OR | -XOR} <statement>
{! | -NOT} <statement>
```

Instruktioner som använder logiska operatorer returnerar booleska värden (TRUE eller FALSe).

Logiska operatorer för PowerShell utvärderar bara de instruktioner som krävs för att fastställa sanningen-värdet för instruktionen. Om den vänstra operanden i en instruktion som innehåller operatorn och är FALSe, utvärderas inte den högra operanden.
Om den vänstra operanden i en instruktion som innehåller instruktionen or är TRUE utvärderas inte den högra operanden. Därför kan du använda dessa instruktioner på samma sätt som du använder `If` instruktionen.

## <a name="see-also"></a>SE ÄVEN

[about_Operators](about_Operators.md)

[Jämför objekt](xref:Microsoft.PowerShell.Utility.Compare-Object)

[about_Comparison_operators](about_Comparison_Operators.md)

[about_If](about_If.md)
