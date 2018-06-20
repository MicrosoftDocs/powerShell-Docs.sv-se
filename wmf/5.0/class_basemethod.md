---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219750"
---
# <a name="call-base-class-method"></a><span data-ttu-id="477e1-102">Anropa basklassmetoden</span><span class="sxs-lookup"><span data-stu-id="477e1-102">Call Base Class Method</span></span>

<span data-ttu-id="477e1-103">Du kan åsidosätta befintliga metoder i underklasser.</span><span class="sxs-lookup"><span data-stu-id="477e1-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="477e1-104">Gör detta genom att deklarera metoder med samma namn och signatur:</span><span class="sxs-lookup"><span data-stu-id="477e1-104">To do this, declare methods by using the same name and signature:</span></span>

```powershell
class baseClass
{
    [int]foo() {return 100500}
}

class childClass1 : baseClass
{
    [int]foo() {return 200600}
}

[childClass1]::new().foo() # return 200600
```

<span data-ttu-id="477e1-105">För att anropa metoder i basklassen från åsidosatt implementeringar omvandlas till basklassen ([baseClass] $detta) på anrop:</span><span class="sxs-lookup"><span data-stu-id="477e1-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

```powershell
class childClass2 : baseClass
{
    [int]foo()
    {
        return 3 * ([baseClass]$this).foo()
    }
}

[childClass2]::new().foo() # return 301500
```

<span data-ttu-id="477e1-106">Alla PowerShell metoder är virtuella.</span><span class="sxs-lookup"><span data-stu-id="477e1-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="477e1-107">Du kan dölja icke-virtuell .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning: bara deklarera metoder med samma namn och denna signatur.</span><span class="sxs-lookup"><span data-stu-id="477e1-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    # Add is final in system.collections.generic.list
    [void] Add([int]$arg)
    {
        ([system.collections.generic.list[int]]$this).Add($arg * 2)
    }
}

$list = [MyIntList]::new()
$list.Add(100)
$list[0] # return 200
```
