---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: d7aec1a2ba8964e877ddd7406609fe135b1eb462
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="call-base-class-method"></a>Anropa basklassmetoden

Du kan åsidosätta befintliga metoder i underklasser. Gör detta genom att deklarera metoder med samma namn och signatur:

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

För att anropa metoder i basklassen från åsidosatt implementeringar omvandlas till basklassen ([baseClass] $detta) på anrop:

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

Alla PowerShell metoder är virtuella. Du kan dölja icke-virtuell .NET-metoder i en underklass med samma syntax som du gör för en åsidosättning: bara deklarera metoder med samma namn och denna signatur.

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
