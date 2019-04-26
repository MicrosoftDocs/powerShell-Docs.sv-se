---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 424e0b7a4d62fc35e5040a7e425950e887021d7e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085889"
---
# <a name="call-base-class-constructor"></a>Anropa basklasskonstruktorn

För att anropa en Basklasskonstruktorn från en underklass, använder du nyckelordet **grundläggande**:

```powershell
class A
{
    [int]$a

    A([int]$a)
    {
        $this.a = $a
    }
}

class B : A
{
    B() : base(103) {}
}

[B]::new().a # return 103
```

Om en basklass har en standardkonstruktor (ingen parameter), kan du utesluta ett explicit konstruktorsanrop:

```powershell
class C : B
{
    C([int]$c) {}
}
```
