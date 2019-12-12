---
title: Så här lägger du till anteckningar i hjälp avsnittet om cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2bea35e5-b680-4f86-b928-176890aac99d
caps.latest.revision: 5
ms.openlocfilehash: 4e9ca9a3bbcbc900d079b9275bc47d21de9e2996
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353314"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="a1e29-102">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="a1e29-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="a1e29-103">I det här avsnittet beskrivs hur du lägger till en anteckning-sektion i hjälp avsnittet om Windows PowerShell® cmdlet.</span><span class="sxs-lookup"><span data-stu-id="a1e29-103">This section describes how to add a Notes section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="a1e29-104">Avsnittet anteckningar används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter.</span><span class="sxs-lookup"><span data-stu-id="a1e29-104">The Notes section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="a1e29-105">Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="a1e29-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="a1e29-106">Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar.</span><span class="sxs-lookup"><span data-stu-id="a1e29-106">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="a1e29-107">För varje anteckning lägger du till ett par med \<MAML: Alert >-taggar till noden \<MAML: alertset >.</span><span class="sxs-lookup"><span data-stu-id="a1e29-107">For each note, add a pair of \<maml:alert> tags to the \<maml:alertset> node.</span></span> <span data-ttu-id="a1e29-108">Innehållet i varje anteckning läggs till i en uppsättning \<MAML: stycke > taggar.</span><span class="sxs-lookup"><span data-stu-id="a1e29-108">The content of each note is added within a set of \<maml:para> tags.</span></span> <span data-ttu-id="a1e29-109">Använd blank \<MAML: stycke > taggar för avstånd.</span><span class="sxs-lookup"><span data-stu-id="a1e29-109">Use blank \<maml:para> tags for spacing.</span></span>

<span data-ttu-id="a1e29-110">Följande XML visar en \<MAML: alertset >-nod med två anteckningar.</span><span class="sxs-lookup"><span data-stu-id="a1e29-110">The following XML shows an \<maml:alertset> node with two notes.</span></span> <span data-ttu-id="a1e29-111">Observera att varje anteckning har en valfri \<MAML: title >-tagg (titlar kan användas för att gruppera valfri uppsättning \<MAML: varning > taggar) och att varje anteckning har en tom rad som följer innehållet för avstånd.</span><span class="sxs-lookup"><span data-stu-id="a1e29-111">Notice that each note has an optional \<maml:title> tag (titles can be used to group any set of \<maml:alert> tags), and that each note has a blank line following the content for spacing.</span></span>

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



