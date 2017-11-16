---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 5dbaa126cf9ae3917c3a8787ffc5ef5ac77b19c1
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="declare-base-class"></a><span data-ttu-id="922e3-102">Deklarera basklass</span><span class="sxs-lookup"><span data-stu-id="922e3-102">Declare Base Class</span></span>
<span data-ttu-id="922e3-103">Du kan deklarera en Windows PowerShell-klass som bastyp för en annan Windows PowerShell-klass.</span><span class="sxs-lookup"><span data-stu-id="922e3-103">You can declare a Windows PowerShell class as a base type for another Windows PowerShell class.</span></span>

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

<span data-ttu-id="922e3-104">Du kan också använda befintliga .NET Framework-typer som basklasser:</span><span class="sxs-lookup"><span data-stu-id="922e3-104">You can also use existing .NET Framework types as base classes:</span></span>

```powershell
class MyIntList : system.collections.generic.list[int]
{
    
}

$list = [MyIntList]::new()

$list.Add(100)

$list[0] # return 100
```

