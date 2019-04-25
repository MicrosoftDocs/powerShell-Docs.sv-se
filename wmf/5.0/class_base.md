---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 8b3ebd22e03bf9bdd5f26965137a1b1ce9f47c3e
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058785"
---
# <a name="declare-base-class"></a>Deklarera basklass
Du kan deklarera en Windows PowerShell-klass som bastyp för en annan Windows PowerShell-klass.

```powershell
class bar
{
   [int]foo()
       {
           return 100500
       }
}

class baz : bar {}

[baz]::new().foo() # return 100500
```

Du kan också använda befintliga .NET Framework-typer som basklasser:

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
