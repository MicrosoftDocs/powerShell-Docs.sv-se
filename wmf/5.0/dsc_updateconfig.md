---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 27f8fab6a72e7f3a3f510f5a9e503bbfb8a8f618
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="4149a-102">PULL på begäran av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="4149a-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="4149a-103">Cmdlet Update DscConfiguration utlöser en pull från pull-servrar som definierats i metadata-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4149a-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="4149a-104">Hur kallas ofta 'Hämtar nu'.</span><span class="sxs-lookup"><span data-stu-id="4149a-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="4149a-105">När det utlöses, pull uppträder på exakt samma som den skulle ha när utlöses under regelbunden frekvens:</span><span class="sxs-lookup"><span data-stu-id="4149a-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="4149a-106">Kontrollsumman för aktuell konfiguration jämförs med kontrollsumman för konfigurationen på pull-servern.</span><span class="sxs-lookup"><span data-stu-id="4149a-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="4149a-107">Om de är likadana, den har slutförts utan att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4149a-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="4149a-108">Om de skiljer sig hämtas från hämtningsservern i konfigurationen och tillämpas.</span><span class="sxs-lookup"><span data-stu-id="4149a-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="4149a-109">**Obs:** om Meta Configuration RefreshMode = 'Push ”ett fel returneras av denna cmdlet så att denna cmdlet alltid gör ingenting när Målnoden är i” Push-läge.</span><span class="sxs-lookup"><span data-stu-id="4149a-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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