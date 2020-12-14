---
description: Kör en instruktions lista en eller flera gånger, beroende på ett while eller ett villkor.
Locale: en-US
ms.date: 06/09/2017
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_do?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Do
ms.openlocfilehash: 412a13669e86df5804dd74d75fcb5b4389192c79
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710633"
---
# <a name="about-do"></a>Om gör

## <a name="short-description"></a>KORT BESKRIVNING
Kör en instruktions lista en eller flera gånger, beroende på ett while eller ett villkor.

## <a name="long-description"></a>LÅNG BESKRIVNING

Nyckelordet Keyword fungerar med nyckelordet while eller till nyckelordet until för att köra instruktionerna i ett-skript block, beroende på ett villkor. Till skillnad från den relaterade while-loopen körs skript blocket i en loop-slinga alltid minst en gång.

En while-loop är en mängd av while **-** slingan. I en **while-** loop utvärderas villkoret när skript blocket har körts. Som i en while-slinga upprepas skript blocket så länge villkoret utvärderas till sant.

Som en **while-** slinga körs en upprepa **-tills-** loop alltid minst en gång innan villkoret utvärderas. Skript blocket körs dock bara när villkoret är falskt.

Nyckelorden *Continue* och *Break* Flow kan användas i en **while-** loop eller i en sling **-until-** slinga.

### <a name="syntax"></a>Syntax

Nedan visas syntaxen för instruktionen **while** .

```powershell
do {<statement list>} while (<condition>)
```

Nedan visas syntaxen för instruktionen **-until** :

```powershell
do {<statement list>} until (<condition>)
```

Instruktions listan innehåller en eller flera instruktioner som körs varje gången loopen anges eller upprepas.

Villkors delen i instruktionen matchar värdet sant eller falskt.

### <a name="example"></a>Exempel

Följande exempel på en Statement-instruktion räknar objekten i en matris tills den når ett objekt med värdet 0.

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } while ($x[$a] -ne 0)
C:\PS> $count
3
```

I följande exempel används nyckelordet until. Observera att operatorn som inte är lika med ( `-ne` ) ersätts av operatorn lika med ( `-eq` ).

```powershell
C:\PS> $x = 1,2,78,0
C:\PS> do { $count++; $a++; } until ($x[$a] -eq 0)
C:\PS> $count
3
```

I följande exempel skrivs alla värden i en matris, vilket hoppar över värden som är mindre än noll.

```powershell
do {
  if ($x[$a] -lt 0) { continue }
  Write-Host $x[$a]
}
while (++$a -lt 10)
```

## <a name="see-also"></a>SE ÄVEN

[about_While](about_While.md)

[about_Operators](about_Operators.md)

[about_Assignment_Operators](about_Assignment_Operators.md)

[about_Comparison_Operators](about_Comparison_Operators.md)

[about_Break](about_Break.md)

[about_Continue](about_Continue.md)

