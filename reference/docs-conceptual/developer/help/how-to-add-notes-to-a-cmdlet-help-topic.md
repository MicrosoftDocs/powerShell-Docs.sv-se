---
title: Lägga till anteckningar i ett cmdlet-hjälpavsnitt
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298314"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a>Lägga till anteckningar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till en **anteckning** -sektion i hjälp avsnittet om PowerShell-cmdleten. Avsnittet **anteckningar** används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter. Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.

Avsnittet **anteckningar** definieras med en enda `<maml:alertset>` nod. Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar. Lägg till ett par `<maml:alert>` taggar till noden för varje anteckning `<maml:alertset>` . Innehållet i varje anteckning läggs till i en uppsättning `<maml:para>` taggar. Använd tomma `<maml:para>` taggar för avstånd.

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
