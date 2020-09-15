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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="1e19f-102">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="1e19f-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="1e19f-103">I det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterat till ett hjälp avsnitt med PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1e19f-103">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="1e19f-104">Eftersom dessa referenser visas i ett kommando fönster, länkas de inte direkt till det innehåll som refereras till.</span><span class="sxs-lookup"><span data-stu-id="1e19f-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="1e19f-105">I cmdleten hjälp ämnen som ingår i PowerShell refererar dessa länkar till andra cmdlets, konceptuellt innehåll ( `about_` ) och andra dokument och hjälpfiler som inte är relaterade till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="1e19f-105">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="1e19f-106">Följande XML visar hur du lägger till en **RelatedLinks** -nod som innehåller två referenser till närliggande ämnen.</span><span class="sxs-lookup"><span data-stu-id="1e19f-106">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
