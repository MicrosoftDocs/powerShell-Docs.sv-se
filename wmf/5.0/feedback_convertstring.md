---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 27541d903748738675917941dc6b60bc9acdc3f4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684502"
---
# <a name="convert-string"></a>Convert-String
**Konvertera sträng** innehåller ”ersätta med magic” funktioner. Ange före och efter exempel på hur du vill att texten ska se ut, och **Convert-String** formaterar texten automatiskt. Här är en demo - tar någon förnamn, efternamn och ersätta den med sina efternamn, kommatecken, den första första efternamn och en punkt. Prova med ett regex och se hur lång tid det tar.

```powershell
"Lee Holmes", "Steve Lee", "Jeffrey Snover" | Convert-String -Example "Bill Gates=Gates, B.","John Smith=Smith, J."

Holmes, L.
Lee, S.
Snover, J.
```
