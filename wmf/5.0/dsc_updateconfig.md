---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a>PULL på begäran av DSC-konfigurationer

Cmdlet Update DscConfiguration utlöser en pull från pull-servrar som definierats i metadata-konfigurationen. Hur kallas ofta 'Hämtar nu'.


När det utlöses, pull uppträder på exakt samma som den skulle ha när utlöses under regelbunden frekvens:

1. Kontrollsumman för aktuell konfiguration jämförs med kontrollsumman för konfigurationen på pull-servern.
2. Om de är likadana, den har slutförts utan att tillämpa konfigurationen.
3. Om de skiljer sig hämtas från hämtningsservern i konfigurationen och tillämpas.

**Obs:** om Meta Configuration RefreshMode = 'Push ”ett fel returneras av denna cmdlet så att denna cmdlet alltid gör ingenting när Målnoden är i” Push-läge.

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
