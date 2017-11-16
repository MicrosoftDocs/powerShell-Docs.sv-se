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
# <a name="convert-string"></a>Konvertera strängen
**Konvertera strängen** exponerar ”ersätts med magic” funktioner. Ange före och efter exempel på hur du vill ska söka, och **konvertera strängen** formatering av text automatiskt. Här är en demo - tar någon och efternamn och ersätter den med efternamn, ett kommatecken, den första första efternamn och en punkt. Försök med en regex och se hur lång tid det tar du.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```

