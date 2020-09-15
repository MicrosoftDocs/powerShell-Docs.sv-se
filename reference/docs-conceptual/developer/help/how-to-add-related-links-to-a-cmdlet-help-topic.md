---
title: Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt
ms.date: 09/12/2016
ms.openlocfilehash: 7557b3856d8470434070dd286cd7e30c9ba015c5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893381"
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
