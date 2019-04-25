---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4b593e9a1eca43ee7ad85fc921ae3c1d62722db9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085872"
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="4db9f-102">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="4db9f-102">Declare Implemented Interface</span></span>

<span data-ttu-id="4db9f-103">Du kan deklarera implementerade gränssnitt efter bastyper eller omedelbart efter ett kolon (:), om det finns inga bastypen som angetts.</span><span class="sxs-lookup"><span data-stu-id="4db9f-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="4db9f-104">Separera namn för alla med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="4db9f-104">Separate all type names by using commas.</span></span> <span data-ttu-id="4db9f-105">Det är mycket lik C# syntax.</span><span class="sxs-lookup"><span data-stu-id="4db9f-105">It’s very similar to C# syntax.</span></span>

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
