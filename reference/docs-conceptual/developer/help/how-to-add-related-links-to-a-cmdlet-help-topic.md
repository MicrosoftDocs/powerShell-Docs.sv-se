---
title: Så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: 0a6403e2dea16d73e2fdcb8cf5df39b2aa5b5dae
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560278"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterat till ett Windows PowerShell®-cmdlet-hjälp ämne. Eftersom dessa referenser visas i ett kommando fönster, länkas de inte direkt till det innehåll som refereras till.

I cmdleten hjälp avsnitt som ingår i Windows PowerShell® refererar dessa länkar till andra cmdlets, konceptuellt innehåll ("about_") och andra dokument och hjälpfiler som inte är relaterade till Windows PowerShell-®.

Följande XML visar hur du lägger till en RelatedLinks-nod som innehåller två referenser till närliggande ämnen.

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
