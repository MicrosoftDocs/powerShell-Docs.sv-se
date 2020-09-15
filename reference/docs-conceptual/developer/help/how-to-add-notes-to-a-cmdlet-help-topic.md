---
title: Lägga till anteckningar i ett cmdlet-hjälpavsnitt
ms.date: 09/12/2016
ms.openlocfilehash: d3679126ea34d7e86bcda700d0d050d8312a7aa2
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893415"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Lägga till anteckningar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till en **anteckning** -sektion i hjälp avsnittet om PowerShell-cmdleten. Avsnittet **anteckningar** används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter. Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.

Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar. Lägg till ett par `<maml:alert>` taggar till noden för varje anteckning `<maml:alertset>` . Innehållet i varje anteckning läggs till i en uppsättning `<maml:para>` taggar. Använd tomma `<maml:para>` taggar för avstånd.

Följande XML visar en `<maml:alertset>` nod med två anteckningar. Observera att varje anteckning har en valfri `<maml:title>` tagg (titlar kan användas för att gruppera valfri uppsättning `<maml:alert>` taggar) och att varje anteckning har en tom rad som följer innehållet för avstånd.

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
