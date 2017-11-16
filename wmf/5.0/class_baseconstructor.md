---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 1fd6d80d6b7effb4bd98c1594d64e531c4e5c9b5
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="call-base-class-constructor"></a>Anropa konstruktorn basklass

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

