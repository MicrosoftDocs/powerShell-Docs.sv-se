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
# <a name="declare-implemented-interface"></a>Deklarera implementerat gränssnitt

Du kan deklarera implementerade gränssnitt efter bastyper, eller omedelbart efter ett kolon (:), om det inte finns några bastypen som angetts. Avgränsa alla typnamn med kommatecken. Det är mycket likt C#-syntax.

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

