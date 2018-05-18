---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 6d37fbc5091d69925d60349f3acbdecc92da1b95
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="b5b46-102">PULL på begäran av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="b5b46-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="b5b46-103">Cmdlet Update DscConfiguration utlöser en pull från pull-servrar som definierats i metadata-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b5b46-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="b5b46-104">Hur kallas ofta 'Hämtar nu'.</span><span class="sxs-lookup"><span data-stu-id="b5b46-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="b5b46-105">När det utlöses, pull uppträder på exakt samma som den skulle ha när utlöses under regelbunden frekvens:</span><span class="sxs-lookup"><span data-stu-id="b5b46-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="b5b46-106">Kontrollsumman för aktuell konfiguration jämförs med kontrollsumman för konfigurationen på pull-servern.</span><span class="sxs-lookup"><span data-stu-id="b5b46-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="b5b46-107">Om de är likadana, den har slutförts utan att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="b5b46-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="b5b46-108">Om de skiljer sig hämtas från hämtningsservern i konfigurationen och tillämpas.</span><span class="sxs-lookup"><span data-stu-id="b5b46-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="b5b46-109">**Obs:** om Meta Configuration RefreshMode = 'Push ”ett fel returneras av denna cmdlet så att denna cmdlet alltid gör ingenting när Målnoden är i” Push-läge.</span><span class="sxs-lookup"><span data-stu-id="b5b46-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
