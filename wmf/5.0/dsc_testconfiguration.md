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
# <a name="test-dscconfiguration-cmdlet-supports-reference-configurations"></a>Test-DscConfiguration-cmdleten stöder Referenskonfigurationer

Test-DscConfiguration-cmdleten har uppdaterats för att tillåta testning av önskad konfigurationstillståndet för en eller flera målnoder genom att ange en referens konfigurationsdokumentet att jämföra med.

Följande nya parameteruppsättningar använda DSC-konfigurationer i sökvägen till endast testet och tillämpa aldrig varje konfiguration för angivna noder. Precis som med Start-DscConfiguration och andra DSC-cmdletar, används namnet på varje MOF för att avgöra vilka målnoden att testa konfigurationen på.

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

Följande nya parameteruppsättningar använder en enda DSC-konfiguration för att bara testa och aldrig tillämpa konfigurationen på den angivna målsökvägen nod(er).

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
