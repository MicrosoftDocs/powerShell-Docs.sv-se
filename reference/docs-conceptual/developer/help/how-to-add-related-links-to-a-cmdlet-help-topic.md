---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt
description: Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: 7f1baefea69310bdf835c52461f8d3f49c4d94e8
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92661995"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterat till ett hjälp avsnitt med PowerShell-cmdlet. Eftersom dessa referenser visas i ett kommando fönster, länkas de inte direkt till det innehåll som refereras till.

I cmdleten hjälp ämnen som ingår i PowerShell refererar dessa länkar till andra cmdlets, konceptuellt innehåll ( `about_` ) och andra dokument och hjälpfiler som inte är relaterade till PowerShell.

Följande XML visar hur du lägger till en **RelatedLinks** -nod som innehåller två referenser till närliggande ämnen.

```xml
<maml:relatedLinks>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
  <maml:navigationLink>
    <maml:linkText>Topic-name</maml:linkText>
  </maml:navigationLink>
</ maml:relatedLinks >
```
