---
title: Syntax för kommenterings-baserad hjälp | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: e8adc997-1a71-48e9-9383-513ef13da7cf
caps.latest.revision: 4
ms.openlocfilehash: 584e5923008e8369a83c699478844f0e0c295adc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72357836"
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

 Kommenterad hjälp skrivs som en rad kommentarer. Du kan skriva en kommentars symbol (#) före varje rad med kommentarer, eller så kan du använda symbolerna "\<#" och "# >" för att skapa ett kommentar block. Alla rader i kommentars blocket tolkas som kommentarer.

 Varje del av den kommenterade hjälpen definieras av ett nyckelord och varje nyckelord föregås av en punkt (.). Nyckelorden kan visas i vilken ordning som helst. Nyckelords namnen är inte Skift läges känsliga.

 Ett kommentar block måste innehålla minst ett hjälp nyckelord. Några av nyckelorden, till exempel, kan visas många gånger i samma kommentars block. Hjälp innehållet för varje nyckelord börjar på raden efter nyckelordet och kan omfatta flera rader.

 Alla rader i ett kommenterat hjälp avsnitt måste vara sammanhängande. Om ett kommenterat hjälp avsnitt följer en kommentar som inte är en del av hjälp avsnittet, måste det finnas minst en tom rad mellan den sista raden för icke-hjälp-kommentarer och början av den kommenterade hjälpen.

 Till exempel innehåller följande kommenterings-baserade hjälp avsnitt. Nyckelordet Description och dess värde, som är en beskrivning av en funktion eller ett skript.

```powershell
<#
    .Description
    The Get-Function function displays the name and syntax of all functions in the session.
#>
```