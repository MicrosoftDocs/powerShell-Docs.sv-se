---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 2c007321789ae22b4a2e048d2d64162b065f9a75
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="eb67f-102">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="eb67f-102">Declare Implemented Interface</span></span>

<span data-ttu-id="eb67f-103">Du kan deklarera implementerade gränssnitt efter bastyper, eller omedelbart efter ett kolon (:), om det inte finns några bastypen som angetts.</span><span class="sxs-lookup"><span data-stu-id="eb67f-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="eb67f-104">Avgränsa alla typnamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="eb67f-104">Separate all type names by using commas.</span></span> <span data-ttu-id="eb67f-105">Det är mycket likt C#-syntax.</span><span class="sxs-lookup"><span data-stu-id="eb67f-105">It’s very similar to C# syntax.</span></span>

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