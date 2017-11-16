---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 6caff8c06174a1dcb990ed8e5062ccca5848dbb8
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="convert-string"></a><span data-ttu-id="a425f-102">Konvertera strängen</span><span class="sxs-lookup"><span data-stu-id="a425f-102">Convert-String</span></span>
<span data-ttu-id="a425f-103">**Konvertera strängen** exponerar ”ersätts med magic” funktioner.</span><span class="sxs-lookup"><span data-stu-id="a425f-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="a425f-104">Ange före och efter exempel på hur du vill ska söka, och **konvertera strängen** formatering av text automatiskt.</span><span class="sxs-lookup"><span data-stu-id="a425f-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="a425f-105">Här är en demo - tar någon och efternamn och ersätter den med efternamn, ett kommatecken, den första första efternamn och en punkt.</span><span class="sxs-lookup"><span data-stu-id="a425f-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="a425f-106">Försök med en regex och se hur lång tid det tar du.</span><span class="sxs-lookup"><span data-stu-id="a425f-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

