---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 968e78beb8df77588a08a9ce8732e4abcadde4d0
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="declare-implemented-interface"></a><span data-ttu-id="074fb-102">Deklarera implementerat gränssnitt</span><span class="sxs-lookup"><span data-stu-id="074fb-102">Declare Implemented Interface</span></span>

<span data-ttu-id="074fb-103">Du kan deklarera implementerade gränssnitt efter bastyper, eller omedelbart efter ett kolon (:), om det inte finns några bastypen som angetts.</span><span class="sxs-lookup"><span data-stu-id="074fb-103">You can declare implemented interfaces after base types, or immediately after a colon (:), if there is no base type specified.</span></span> <span data-ttu-id="074fb-104">Avgränsa alla typnamn med kommatecken.</span><span class="sxs-lookup"><span data-stu-id="074fb-104">Separate all type names by using commas.</span></span> <span data-ttu-id="074fb-105">Det är mycket likt C#-syntax.</span><span class="sxs-lookup"><span data-stu-id="074fb-105">It’s very similar to C# syntax.</span></span>

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

