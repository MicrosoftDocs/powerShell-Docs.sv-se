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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Testa DscConfiguration cmdlet har stöd för konfigurationer som referens

Cmdleten Test-DscConfiguration har uppdaterats för att tillåta testning av önskad konfigurationstillståndet för en eller flera målnoder genom att ange en konfiguration referensdokumentet att jämföra med.

Följande nya parameteruppsättningar använder DSC-konfigurationer i sökvägen som angetts för att testa endast och tillämpa aldrig varje konfiguration på angiven mål-noder. Precis som med Start DscConfiguration och andra DSC-cmdlets används namnet på varje MOF för att avgöra vilka målnoden för att testa konfigurationen på. 

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

Följande nya parameteruppsättningar använda en enda DSC-konfiguration för att bara testa och aldrig tillämpa konfigurationen på de angivna mål noderna. 

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

