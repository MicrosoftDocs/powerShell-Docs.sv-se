---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 9486fdbaeca66c83551564c76ce47482f77c36b9
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-constructor"></a>Anropa basklasskonstruktorn

För att anropa en basklasskonstruktor från en underklass, använder du nyckelordet **grundläggande**:

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

Om en basklass har en standardkonstruktor (ingen parameter), kan du utelämna en explicit konstruktoranrop:

```powershell
class C : B
{
    C([int]$c) {}
}
```
