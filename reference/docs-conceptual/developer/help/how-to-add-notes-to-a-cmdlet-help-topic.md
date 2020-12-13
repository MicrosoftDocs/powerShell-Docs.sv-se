---
ms.date: 10/20/2020
ms.topic: reference
title: Lägga till anteckningar i ett cmdlet-hjälpavsnitt
description: Lägga till anteckningar i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: 61363c26ab0172277d1332ed1e9de080d8da200c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659573"
---
# <a name="how-to-add-notes-to-a-cmdlet-help-topic"></a><span data-ttu-id="b8d27-103">Lägga till anteckningar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b8d27-103">How to Add Notes to a Cmdlet Help Topic</span></span>

<span data-ttu-id="b8d27-104">I det här avsnittet beskrivs hur du lägger till en **anteckning** -sektion i hjälp avsnittet om PowerShell-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b8d27-104">This section describes how to add a **NOTES** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="b8d27-105">Avsnittet **anteckningar** används för att förklara information som inte passar enkelt i de andra strukturerade avsnitten, till exempel en mer detaljerad förklaring av en parameter.</span><span class="sxs-lookup"><span data-stu-id="b8d27-105">The **NOTES** section is used to explain details that do not fit easily into the other structured sections, such as a more detailed explanation of a parameter.</span></span> <span data-ttu-id="b8d27-106">Det här innehållet kan innehålla kommentarer om hur cmdleten fungerar med en viss Provider, en del unika, ännu viktiga, användning av cmdleten eller sätt att undvika möjliga fel tillstånd.</span><span class="sxs-lookup"><span data-stu-id="b8d27-106">This content could include comments on how the cmdlet works with a specific provider, some unique, yet important, uses of the cmdlet, or ways to avoid possible error conditions.</span></span>

<span data-ttu-id="b8d27-107">Avsnittet **anteckningar** definieras med en enda `<maml:alertset>` nod.</span><span class="sxs-lookup"><span data-stu-id="b8d27-107">The **NOTES** section is defined using a single `<maml:alertset>` node.</span></span> <span data-ttu-id="b8d27-108">Det finns inga begränsningar för antalet anteckningar som du kan lägga till i avsnittet anteckningar.</span><span class="sxs-lookup"><span data-stu-id="b8d27-108">There are no limits to the number of notes that you can add to a Notes section.</span></span> <span data-ttu-id="b8d27-109">Lägg till ett par `<maml:alert>` taggar till noden för varje anteckning `<maml:alertset>` .</span><span class="sxs-lookup"><span data-stu-id="b8d27-109">For each note, add a pair of `<maml:alert>` tags to the `<maml:alertset>` node.</span></span> <span data-ttu-id="b8d27-110">Innehållet i varje anteckning läggs till i en uppsättning `<maml:para>` taggar.</span><span class="sxs-lookup"><span data-stu-id="b8d27-110">The content of each note is added within a set of `<maml:para>` tags.</span></span> <span data-ttu-id="b8d27-111">Använd tomma `<maml:para>` taggar för avstånd.</span><span class="sxs-lookup"><span data-stu-id="b8d27-111">Use blank `<maml:para>` tags for spacing.</span></span>

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
