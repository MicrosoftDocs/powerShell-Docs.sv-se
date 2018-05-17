---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 10f8dd0f5097260eb4a8516f9662df3d219bdfe5
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
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
