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
# <a name="call-base-class-constructor"></a><span data-ttu-id="a2787-102">Anropa basklasskonstruktorn</span><span class="sxs-lookup"><span data-stu-id="a2787-102">Call Base Class Constructor</span></span>

<span data-ttu-id="a2787-103">För att anropa en Basklasskonstruktorn från en underklass, använder du nyckelordet **grundläggande**:</span><span class="sxs-lookup"><span data-stu-id="a2787-103">To call a base class constructor from a subclass, use the keyword **base**:</span></span>

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

<span data-ttu-id="a2787-104">Om en basklass har en standardkonstruktor (ingen parameter), kan du utesluta ett explicit konstruktorsanrop:</span><span class="sxs-lookup"><span data-stu-id="a2787-104">If a base class has a default (no parameter) constructor, you can omit an explicit constructor call:</span></span>

```powershell
class C : B
{
    C([int]$c) {}
}
```
