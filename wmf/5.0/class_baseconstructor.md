---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 3269c8cc871f22488b64fb072dac72698983f360
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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