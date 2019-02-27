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
# <a name="how-to-add-related-links-to-a-cmdlet-help-topic"></a><span data-ttu-id="4c511-102">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="4c511-102">How to Add Related Links to a Cmdlet Help Topic</span></span>

<span data-ttu-id="4c511-103">Det här avsnittet beskrivs hur du lägger till referenser till annat innehåll som är relaterade till en Windows PowerShell® cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="4c511-103">This section describes how to add references to other content that is related to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="4c511-104">Eftersom dessa referenser visas i ett kommandofönster, länka de inte direkt till refererat innehåll.</span><span class="sxs-lookup"><span data-stu-id="4c511-104">Because these references appear in a command window, they do not link directly to the referenced content.</span></span>

<span data-ttu-id="4c511-105">I hjälpavsnitten cmdlet som ingår i Windows PowerShell® referera dessa länkar till andra cmdlet: ar, konceptuellt innehåll (”about_”), och andra dokument och hjälpfiler som inte är relaterade till Windows PowerShell®.</span><span class="sxs-lookup"><span data-stu-id="4c511-105">In the cmdlet Help topics that are included in Windows PowerShell®, these links reference other cmdlets, conceptual content ("about_"), and other documents and Help files that are not related to Windows PowerShell®.</span></span>

<span data-ttu-id="4c511-106">Följande XML-koden visar hur du lägger till en RelatedLinks-nod som innehåller två referenser till närliggande ämnen.</span><span class="sxs-lookup"><span data-stu-id="4c511-106">The following XML shows how to add a RelatedLinks node that contains two references to related topics.</span></span>

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



