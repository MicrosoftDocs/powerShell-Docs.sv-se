---
title: Lägga till anteckningar till en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851200"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="799dc-102">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="799dc-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="799dc-103">Det här avsnittet beskrivs hur du lägger till avsnittet anteckningar till en Windows PowerShell® cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="799dc-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="799dc-104">Avsnittet med anteckningar används för att förklara information som inte passar enkelt i andra strukturerade avsnitt, till exempel en mer detaljerad förklaring av en parameter.</span><span class="sxs-lookup"><span data-stu-id="799dc-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="799dc-105">Det här innehållet kan omfatta kommentarer om hur cmdlet: en fungerar med en viss leverantör, några unika, men viktiga, användningsområden för cmdlet eller sätt att undvika möjlig felvillkor.</span><span class="sxs-lookup"><span data-stu-id="799dc-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="799dc-106">Det finns ingen gräns för hur många anteckningar som du kan lägga till avsnittet Anteckningar.</span><span class="sxs-lookup"><span data-stu-id="799dc-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="799dc-107">Observera att varje lägger du till ett par \<maml:alert > etiketter till den \<maml:alertset > noden.</span><span class="sxs-lookup"><span data-stu-id="799dc-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="799dc-108">Innehållet i varje anteckning har lagts till i en uppsättning \<maml:para > taggar.</span><span class="sxs-lookup"><span data-stu-id="799dc-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="799dc-109">Använd tomt \<maml:para >-taggar för avstånd.</span><span class="sxs-lookup"><span data-stu-id="799dc-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="799dc-110">I följande XML-visas en \<maml:alertset > noden med två anteckningar.</span><span class="sxs-lookup"><span data-stu-id="799dc-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="799dc-111">Observera att varje anteckning har en valfri \<maml:title > taggen (rubriker som kan användas för att gruppera en uppsättning \<maml:alert > taggar), och att varje anteckning har en tom rad efter innehållet för avstånd.</span><span class="sxs-lookup"><span data-stu-id="799dc-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



