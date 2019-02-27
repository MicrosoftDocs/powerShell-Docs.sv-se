---
title: Lägga till länkarna till Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 5aadb730-4eb7-4936-b8df-3b0c0ca04fd5
caps.latest.revision: 5
ms.openlocfilehash: aa46cbc5bfcfdfec9fcf9d2581ff641baa532860
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846391"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a>Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt

Det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterade till en Windows PowerShell® cmdlet-hjälpavsnittet. Eftersom dessa referenser visas i ett kommandofönster, länka de inte direkt till refererat innehåll.

I hjälpavsnitten cmdlet som ingår i Windows PowerShell® referera dessa länkar till andra cmdlet: ar, konceptuellt innehåll (”about_”), och andra dokument och hjälpfiler som inte är relaterade till Windows PowerShell®.

Följande XML-koden visar hur du lägger till en RelatedLinks-nod som innehåller två referenser till närliggande ämnen.

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



