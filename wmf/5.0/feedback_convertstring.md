---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 302a347b0f4c9c322f7701e8d6a721f9ffba9b59
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="convert-string"></a><span data-ttu-id="009cb-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="009cb-102">Convert-String</span></span>
<span data-ttu-id="009cb-103">**Konvertera strängen** exponerar ”ersätts med magic” funktioner.</span><span class="sxs-lookup"><span data-stu-id="009cb-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="009cb-104">Ange före och efter exempel på hur du vill ska söka, och **konvertera strängen** formatering av text automatiskt.</span><span class="sxs-lookup"><span data-stu-id="009cb-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="009cb-105">Här är en demo - tar någon och efternamn och ersätter den med efternamn, ett kommatecken, den första första efternamn och en punkt.</span><span class="sxs-lookup"><span data-stu-id="009cb-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="009cb-106">Försök med en regex och se hur lång tid det tar du.</span><span class="sxs-lookup"><span data-stu-id="009cb-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```