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
# <a name="declare-implemented-interface"></a>Deklarera implementerat gränssnitt

Du kan deklarera implementerade gränssnitt efter bastyper eller omedelbart efter ett kolon (:), om det finns inga bastypen som angetts. Separera namn för alla med kommatecken. Det är mycket lik C# syntax.

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
