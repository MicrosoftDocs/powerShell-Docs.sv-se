---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: ce60b240045acf538edae1a08007971e538588ca
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a><span data-ttu-id="6fd59-102">Testa DscConfiguration cmdlet har stöd för konfigurationer som referens</span><span class="sxs-lookup"><span data-stu-id="6fd59-102">Test-DscConfiguration cmdlet supports Reference Configurations</span></span>

<span data-ttu-id="6fd59-103">Cmdleten Test-DscConfiguration har uppdaterats för att tillåta testning av önskad konfigurationstillståndet för en eller flera målnoder genom att ange en konfiguration referensdokumentet att jämföra med.</span><span class="sxs-lookup"><span data-stu-id="6fd59-103">The Test-DscConfiguration cmdlet has been updated to allow testing of desired configuration state of one or more target nodes by specifying a reference configuration document to compare against.</span></span>

<span data-ttu-id="6fd59-104">Följande nya parameteruppsättningar använder DSC-konfigurationer i sökvägen som angetts för att testa endast och tillämpa aldrig varje konfiguration på angiven mål-noder.</span><span class="sxs-lookup"><span data-stu-id="6fd59-104">The following new parameter sets use DSC configurations in the path specified to only test and never apply each configuration on the specified target node(s).</span></span> <span data-ttu-id="6fd59-105">Precis som med Start DscConfiguration och andra DSC-cmdlets används namnet på varje MOF för att avgöra vilka målnoden för att testa konfigurationen på.</span><span class="sxs-lookup"><span data-stu-id="6fd59-105">As with Start-DscConfiguration and other DSC cmdlets, the name of each MOF is used to determine which target node to test the configuration on.</span></span> 

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

<span data-ttu-id="6fd59-106">Följande nya parameteruppsättningar använda en enda DSC-konfiguration för att bara testa och aldrig tillämpa konfigurationen på de angivna mål noderna.</span><span class="sxs-lookup"><span data-stu-id="6fd59-106">The following new parameter sets use a single DSC configuration to only test and never apply the configuration on the specified target node(s).</span></span> 

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

