---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt
description: Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: 7f1baefea69310bdf835c52461f8d3f49c4d94e8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92661995"
---
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="89287-103">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="89287-103">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="89287-104">I det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterat till ett hjälp avsnitt med PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="89287-104">This section describes how to add references to other content that is related to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="89287-105">Eftersom dessa referenser visas i ett kommando fönster, länkas de inte direkt till det innehåll som refereras till.</span><span class="sxs-lookup"><span data-stu-id="89287-105">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="89287-106">I cmdleten hjälp ämnen som ingår i PowerShell refererar dessa länkar till andra cmdlets, konceptuellt innehåll ( `about_` ) och andra dokument och hjälpfiler som inte är relaterade till PowerShell.</span><span class="sxs-lookup"><span data-stu-id="89287-106">In the cmdlet Help topics that are included in PowerShell, these links reference other cmdlets, conceptual content (`about_`), and other documents and Help files that are not related to PowerShell.</span></span>

<span data-ttu-id="89287-107">Följande XML visar hur du lägger till en **RelatedLinks** -nod som innehåller två referenser till närliggande ämnen.</span><span class="sxs-lookup"><span data-stu-id="89287-107">The following XML shows how to add a **RelatedLinks** node that contains two references to related topics.</span></span>

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
