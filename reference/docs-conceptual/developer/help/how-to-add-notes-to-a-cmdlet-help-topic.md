---
title: Lägga till anteckningar i ett cmdlet-hjälpavsnitt
ms.date: 10/20/2020
ms.openlocfilehash: 7f8be34a82de2c12cfd2a05deed139ddb30da95f
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "92298314"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="0f073-102">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="0f073-102">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="0f073-103">I det här avsnittet beskrivs hur du lägger till en **anteckning** -sektion i hjälp avsnittet om PowerShell-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0f073-103">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="0f073-104">Avsnittet **anteckningar** används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter.</span><span class="sxs-lookup"><span data-stu-id="0f073-104">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="0f073-105">Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="0f073-105">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="0f073-106">Avsnittet **anteckningar** definieras med en enda `<maml:alertset>` nod.</span><span class="sxs-lookup"><span data-stu-id="0f073-106">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="0f073-107">Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar.</span><span class="sxs-lookup"><span data-stu-id="0f073-107">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="0f073-108">Lägg till ett par `<maml:alert>` taggar till noden för varje anteckning `<maml:alertset>` .</span><span class="sxs-lookup"><span data-stu-id="0f073-108">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="0f073-109">Innehållet i varje anteckning läggs till i en uppsättning `<maml:para>` taggar.</span><span class="sxs-lookup"><span data-stu-id="0f073-109">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="0f073-110">Använd tomma `<maml:para>` taggar för avstånd.</span><span class="sxs-lookup"><span data-stu-id="0f073-110">Use blank `<maml:para>` tags for spacing.</span></span>

```xml
<maml:alertSet>
  <maml:title>Optional title for Note</maml:title>
  <maml:alert>
    <maml:para>Note 1</maml:para>
    <maml:para>Note a</maml:para>
  </maml:alert>
  <maml:alert>
    <maml:para>Note 2</maml:para>
  </maml:alert>
</maml:alertSet>
```
