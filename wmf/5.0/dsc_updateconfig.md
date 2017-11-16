---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: f2ddde78f436e6f03f521a9a8246dbda93e7a57a
ms.sourcegitcommit: a5c0795ca6ec9332967bff9c151a8572feb1a53a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/27/2017
---
# <a name="on-demand-pull-of-dsc-configurations"></a>PULL begäran av DSC-konfigurationer

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

