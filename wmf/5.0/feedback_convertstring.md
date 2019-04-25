---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057799"
---
# <a name="convert-string"></a><span data-ttu-id="53e84-102">Convert-String</span><span class="sxs-lookup"><span data-stu-id="53e84-102">Convert-String</span></span>
<span data-ttu-id="53e84-103">**Konvertera sträng** innehåller ”ersätta med magic” funktioner.</span><span class="sxs-lookup"><span data-stu-id="53e84-103">**Convert-String** exposes "replace by magic" functionality.</span></span> <span data-ttu-id="53e84-104">Ange före och efter exempel på hur du vill att texten ska se ut, och **Convert-String** formaterar texten automatiskt.</span><span class="sxs-lookup"><span data-stu-id="53e84-104">Provide before and after examples of how you want text to look, and **Convert-String** formats your text automatically.</span></span> <span data-ttu-id="53e84-105">Här är en demo - tar någon förnamn, efternamn och ersätta den med sina efternamn, kommatecken, den första första efternamn och en punkt.</span><span class="sxs-lookup"><span data-stu-id="53e84-105">Here's a demo - taking somebody's first and last name, and replacing it with their last name, a comma, the first initial of their last name, and a dot.</span></span> <span data-ttu-id="53e84-106">Prova med ett regex och se hur lång tid det tar.</span><span class="sxs-lookup"><span data-stu-id="53e84-106">Try it with a regex, and see how long it takes you.</span></span>

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
