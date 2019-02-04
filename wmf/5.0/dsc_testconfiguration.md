---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 4008a7f91af41150f26c4147135b30aa8835281c
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688562"
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="d0d44-102">Test-DscConfiguration-cmdleten stöder Referenskonfigurationer</span><span class="sxs-lookup"><span data-stu-id="d0d44-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="d0d44-103">Test-DscConfiguration-cmdleten har uppdaterats för att tillåta testning av önskad konfigurationstillståndet för en eller flera målnoder genom att ange en referens konfigurationsdokumentet att jämföra med.</span><span class="sxs-lookup"><span data-stu-id="d0d44-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="d0d44-104">Följande nya parameteruppsättningar använda DSC-konfigurationer i sökvägen till endast testet och tillämpa aldrig varje konfiguration för angivna noder.</span><span class="sxs-lookup"><span data-stu-id="d0d44-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="d0d44-105">Precis som med Start-DscConfiguration och andra DSC-cmdletar, används namnet på varje MOF för att avgöra vilka målnoden att testa konfigurationen på.</span><span class="sxs-lookup"><span data-stu-id="d0d44-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

```powershell
Test-DscConfiguration   [-Path] <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   [-Path] <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```

<span data-ttu-id="d0d44-106">Följande nya parameteruppsättningar använder en enda DSC-konfiguration för att bara testa och aldrig tillämpa konfigurationen på den angivna målsökvägen nod(er).</span><span class="sxs-lookup"><span data-stu-id="d0d44-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

```powershell
Test-DscConfiguration   -ReferenceConfiguration <string>
                        [[-ComputerName] <string[]>]
                        [-Credential <pscredential>]
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]

Test-DscConfiguration   -ReferenceConfiguration <string>
                        -CimSession <CimSession[]>
                        [-ThrottleLimit <int>]
                        [-AsJob]
                        [<CommonParameters>]
```
