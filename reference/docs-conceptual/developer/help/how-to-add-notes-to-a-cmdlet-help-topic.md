---
title: Så här lägger du till anteckningar i hjälp avsnittet om cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353314"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Lägga till anteckningar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till en anteckning-sektion i hjälp avsnittet om Windows PowerShell® cmdlet. Avsnittet anteckningar används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter. Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.

Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar. För varje anteckning lägger du till ett par med \<maml: Alert >-taggar till noden \<maml: alertset >. Innehållet i varje anteckning läggs till i en uppsättning \<maml: stycke > taggar. Använd blank \<maml: stycke > taggar för avstånd.

Följande XML visar en \<maml: alertset >-nod med två anteckningar. Observera att varje anteckning har en valfri \<maml: title >-tagg (titlar kan användas för att gruppera valfri uppsättning \<maml: Alert >-taggar) och att varje anteckning har en tom rad som följer innehållet för avstånd.

```xml
<maml:alertSet>
  <maml:title>title for Note 1</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
  <maml:title>title for Note 2</maml:title>
  <maml:alert>
    <maml:para> Note 1</maml:para>
    <maml:para></maml:para>
  </maml:alert>
</maml:alertSet>
```



