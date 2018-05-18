---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="9650f-102">Testa DscConfiguration cmdlet har stöd för konfigurationer som referens</span><span class="sxs-lookup"><span data-stu-id="9650f-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="9650f-103">Cmdleten Test-DscConfiguration har uppdaterats för att tillåta testning av önskad konfigurationstillståndet för en eller flera målnoder genom att ange en konfiguration referensdokumentet att jämföra med.</span><span class="sxs-lookup"><span data-stu-id="9650f-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="9650f-104">Följande nya parameteruppsättningar använder DSC-konfigurationer i sökvägen som angetts för att testa endast och tillämpa aldrig varje konfiguration på angiven mål-noder.</span><span class="sxs-lookup"><span data-stu-id="9650f-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="9650f-105">Precis som med Start DscConfiguration och andra DSC-cmdlets används namnet på varje MOF för att avgöra vilka målnoden för att testa konfigurationen på.</span><span class="sxs-lookup"><span data-stu-id="9650f-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span>

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

<span data-ttu-id="9650f-106">Följande nya parameteruppsättningar använda en enda DSC-konfiguration för att bara testa och aldrig tillämpa konfigurationen på de angivna mål noderna.</span><span class="sxs-lookup"><span data-stu-id="9650f-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span>

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
