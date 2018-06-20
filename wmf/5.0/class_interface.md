---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 116f79a95126d0a1c579a95ec99eb5d8b75cc1e0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34225495"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="4b12d-102">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="4b12d-102">Declare Implemented Interface</span></span>

<span data-ttu-id="4b12d-103">Du kan deklarera implementerade gränssnitt efter bastyper, eller omedelbart efter ett kolon (:), om det inte finns några bastypen som angetts.</span><span class="sxs-lookup"><span data-stu-id="4b12d-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="4b12d-104">Avgränsa alla typnamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="4b12d-104">Separate all type names by using commas.</span></span> <span data-ttu-id="4b12d-105">Det är mycket likt C#-syntax.</span><span class="sxs-lookup"><span data-stu-id="4b12d-105">It’s very similar to C# syntax.</span></span>

```powershell
class MyComparable : system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}

class MyComparableBar : bar, system.IComparable
{
    [int] CompareTo([object] $obj)
    {
        return 0;
    }
}
```
