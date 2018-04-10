---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 18c1dab7412b8e9d31960507b612dd6cc56d31d5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
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