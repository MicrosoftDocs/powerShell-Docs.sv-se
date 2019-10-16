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
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353279"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterat till ett Windows PowerShell®-cmdlet-hjälp ämne. Eftersom dessa referenser visas i ett kommando fönster, länkas de inte direkt till det innehåll som refereras till.

I cmdleten hjälp avsnitt som ingår i Windows PowerShell® refererar dessa länkar till andra cmdletar, konceptuellt innehåll ("about_") och andra dokument och hjälpfiler som inte är relaterade till Windows PowerShell®.

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



