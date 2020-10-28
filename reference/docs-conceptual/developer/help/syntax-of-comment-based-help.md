---
ms.date: 09/12/2016
ms.topic: reference
title: Syntax för kommentarsbaserad hjälp
description: Syntax för kommentarsbaserad hjälp
ms.openlocfilehash: 3866f25b40fc970e8d219af6f423b7a25f5b875c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659509"
---
# <a name="syntax-of-comment-based-help"></a>Syntax för kommentarsbaserad hjälp

I det här avsnittet beskrivs syntaxen för en kommenterings-baserad hjälp.

## <a name="syntax-diagram"></a>Syntax-diagram

 Syntaxen för kommenterings-baserad hjälp är följande:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Beskrivning av syntax

 Kommenterad hjälp skrivs som en rad kommentarer. Du kan skriva en kommentars symbol ( `#` ) före varje rad med kommentarer, eller så kan du använda- `<#` och- `#>` symbolerna för att skapa ett kommentar block. Alla rader i kommentars blocket tolkas som kommentarer.

 Varje del av den kommenterade hjälpen definieras av ett nyckelord och varje nyckelord föregås av en punkt ( `.` ). Nyckelorden kan visas i vilken ordning som helst. Nyckelords namnen är inte Skift läges känsliga.

 Ett kommentar block måste innehålla minst ett hjälp nyckelord. Några av nyckelorden, till **exempel** , kan visas många gånger i samma kommentars block. Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.

 Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande. Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.

 Till exempel innehåller följande kommenterings-baserade hjälp avsnitt. Nyckelordet Description och dess värde, som är en beskrivning av en funktion eller ett skript.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```
