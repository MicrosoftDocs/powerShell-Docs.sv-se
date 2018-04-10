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
# <a name="call-base-class-constructor"></a><span data-ttu-id="633e9-102">Anropa basklasskonstruktorn</span><span class="sxs-lookup"><span data-stu-id="633e9-102">Call Base Class Constructor</span></span>

<span data-ttu-id="633e9-103">För att anropa en basklasskonstruktor från en underklass, använder du nyckelordet **grundläggande**:</span><span class="sxs-lookup"><span data-stu-id="633e9-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="633e9-104">Om en basklass har en standardkonstruktor (ingen parameter), kan du utelämna en explicit konstruktoranrop:</span><span class="sxs-lookup"><span data-stu-id="633e9-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```