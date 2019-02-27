---
title: Syntaxen för Kommentarbaserad hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846496"
---
# <a name="syntax-of-comment-based-help"></a>Syntax för kommentarsbaserad hjälp

Det här avsnittet beskrivs syntaxen för kommentarbaserad hjälp.

## <a name="syntax-diagram"></a>Syntaxdiagrammet

 Syntaxen för kommentarbaserad hjälp är följande:

```
# .< help keyword>
# <help content>

-or -

<#
.< help keyword>
< help content>
#>
```

## <a name="syntax-description"></a>Syntax beskrivning

 Kommentarbaserad hjälp skrivs som en serie med kommentarer. Du kan skriva en kommentarsymbolen (#) före varje rad med kommentarer eller du kan använda den ”\<#” och ”#>” symboler för att skapa en kommentarblocket. Alla rader inom kommentarblocket tolkas som kommentarer.

 Varje avsnitt på kommentarbaserad hjälp definieras av ett nyckelord och varje nyckelord föregås av en punkt (.). Nyckelord kan visas i valfri ordning. Nyckelordet namnen är inte skiftlägeskänsliga.

 En kommentarblocket måste innehålla minst ett nyckelord för hjälp. Några av nyckelord som exempel, kan visas flera gånger i samma kommentarblocket. Hjälpinnehåll för varje nyckelord börjar på raden efter nyckelordet och kan sträcka sig över flera rader.

 Alla rader i ett kommentarbaserad hjälpavsnitt måste vara sammanhängande. Om ett kommentarbaserad hjälpavsnitt följer en kommentar som inte ingår i hjälpavsnittet, måste det finnas minst en tom rad mellan den sista kommentarraden i icke-Help och början av kommentarbaserad hjälp.

 I följande kommentarbaserad hjälpavsnittet innehåller exempelvis den. Beskrivning av nyckelord och dess värde, som är en beskrivning av en funktion eller ett skript.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```