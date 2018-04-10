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
# <a name="convert-string"></a>Convert-String
**Konvertera strängen** exponerar ”ersätts med magic” funktioner. Ange före och efter exempel på hur du vill ska söka, och **konvertera strängen** formatering av text automatiskt. Här är en demo - tar någon och efternamn och ersätter den med efternamn, ett kommatecken, den första första efternamn och en punkt. Försök med en regex och se hur lång tid det tar du.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```