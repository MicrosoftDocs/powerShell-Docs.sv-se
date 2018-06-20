---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 188ede0c558210a746ad0f6c6cef6f571b280878
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34219913"
---
# <a name="declare-base-class"></a><span data-ttu-id="2ae0a-102">Deklarera basklass</span><span class="sxs-lookup"><span data-stu-id="2ae0a-102">Declare Base Class</span></span>
<span data-ttu-id="2ae0a-103">Du kan deklarera en Windows PowerShell-klass som bastyp för en annan Windows PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="2ae0a-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="2ae0a-104">Du kan också använda befintliga .NET Framework-typer som basklasser:</span><span class="sxs-lookup"><span data-stu-id="2ae0a-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{

}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```
