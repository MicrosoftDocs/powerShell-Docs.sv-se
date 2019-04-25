---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 31fde15e644455dbe77f68bca713bf026544fdc7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62057578"
---
# <a name="on-demand-pull-of-dsc-configurations"></a>PULL på begäran av DSC-konfigurationer

Den nya uppdatering-DscConfiguration-cmdleten utlöser en hämtning från pull-servrar som definierats i metadata-konfigurationen. Beteende är ofta kallas ”Hämta nu”.


När utlöses, pull fungerar likadant som den skulle ha när utlöses under den regelbundna frekvensen:

1. Kontrollsumman för nuvarande konfiguration jämförs kontrollsumma för konfigurationen på hämtningsservern.
2. Om de är likadana, den har slutförts utan att tillämpa konfigurationen.
3. Om de skiljer sig är konfigurationen hämtade från pull-servern och tillämpas.

**Obs:** Om Meta-konfiguration-RefreshMode = ”Push” returneras ett fel av denna cmdlet så att denna cmdlet alltid händer ingenting när en Målnoden är i ”Push”-läge.

```powershell
Update-DscConfiguration     [[-ComputerName] <string[]>]
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-Credential<pscredential>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]

Update-DscConfiguration     -CimSession <CimSession[]>
                            [-Wait]
                            [-Force]
                            [-JobName <string>]
                            [-ThrottleLimit <int>]
                            [-WhatIf]
                            [-Confirm]
                            [<CommonParameters>]
```
