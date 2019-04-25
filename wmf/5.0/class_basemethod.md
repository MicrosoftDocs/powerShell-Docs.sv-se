---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 0e79127faf3f9bf6fe7d525db5bb946daf3b93e1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058632"
---
# <a name="call-base-class-method"></a><span data-ttu-id="80446-102">Anropa basklassmetoden</span><span class="sxs-lookup"><span data-stu-id="80446-102">Call Base Class Method</span></span>

<span data-ttu-id="80446-103">Du kan åsidosätta befintliga metoder i underklasser.</span><span class="sxs-lookup"><span data-stu-id="80446-103">You can override existing methods in subclasses.</span></span> <span data-ttu-id="80446-104">Gör detta genom att deklarera metoder med samma namn och signatur:</span><span class="sxs-lookup"><span data-stu-id="80446-104">To do this, declare methods by using the same name and signature:</span></span>

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

<span data-ttu-id="80446-105">För att anropa basklass från åsidosatt implementeringar, konvertera till basklassen ([baseClass] $detta) på anrop:</span><span class="sxs-lookup"><span data-stu-id="80446-105">To call base class methods from overridden implementations, cast to the base class ([baseClass]$this) on invocation:</span></span>

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

<span data-ttu-id="80446-106">Alla PowerShell-metoder är virtuella.</span><span class="sxs-lookup"><span data-stu-id="80446-106">All PowerShell methods are virtual.</span></span> <span data-ttu-id="80446-107">Du kan dölja icke-virtuell .NET-metoder i en underklass med hjälp av samma syntax som du gör en åsidosättning: bara deklarera metoder med samma namn och signatur.</span><span class="sxs-lookup"><span data-stu-id="80446-107">You can hide non-virtual .NET methods in a subclass by using the same syntax as you do for an override: just declare methods with same name and signature.</span></span>

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
