---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7730912707bb14e90a9926b387fb3a859d7ca26d
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="convert-string"></a>Convert-String
**Konvertera strängen** exponerar ”ersätts med magic” funktioner. Ange före och efter exempel på hur du vill ska söka, och **konvertera strängen** formatering av text automatiskt. Här är en demo - tar någon och efternamn och ersätter den med efternamn, ett kommatecken, den första första efternamn och en punkt. Försök med en regex och se hur lång tid det tar du.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
