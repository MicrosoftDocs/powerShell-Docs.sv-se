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
# <a name="on-demand-pull-of-dsc-configurations"></a><span data-ttu-id="03d5a-102">PULL på begäran av DSC-konfigurationer</span><span class="sxs-lookup"><span data-stu-id="03d5a-102">On-demand PULL of DSC Configurations</span></span>

<span data-ttu-id="03d5a-103">Den nya uppdatering-DscConfiguration-cmdleten utlöser en hämtning från pull-servrar som definierats i metadata-konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="03d5a-103">The new Update-DscConfiguration cmdlet triggers a pull from the pull server(s) defined in the meta-configuration.</span></span> <span data-ttu-id="03d5a-104">Beteende är ofta kallas ”Hämta nu”.</span><span class="sxs-lookup"><span data-stu-id="03d5a-104">The behavior is often referred to as 'Pull Now'.</span></span>


<span data-ttu-id="03d5a-105">När utlöses, pull fungerar likadant som den skulle ha när utlöses under den regelbundna frekvensen:</span><span class="sxs-lookup"><span data-stu-id="03d5a-105">Once triggered, the pull behaves exactly the same as it would have when triggered during the regular frequency:</span></span>

1. <span data-ttu-id="03d5a-106">Kontrollsumman för nuvarande konfiguration jämförs kontrollsumma för konfigurationen på hämtningsservern.</span><span class="sxs-lookup"><span data-stu-id="03d5a-106">The checksum for current configuration is compared to the checksum for the configuration on the pull server.</span></span>
2. <span data-ttu-id="03d5a-107">Om de är likadana, den har slutförts utan att tillämpa konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="03d5a-107">If they are the same, it completes successfully without applying the configuration.</span></span>
3. <span data-ttu-id="03d5a-108">Om de skiljer sig är konfigurationen hämtade från pull-servern och tillämpas.</span><span class="sxs-lookup"><span data-stu-id="03d5a-108">If they are different, the configuration is pulled down from the pull server and applied.</span></span>

<span data-ttu-id="03d5a-109">**Obs:** Om Meta-konfiguration-RefreshMode = ”Push” returneras ett fel av denna cmdlet så att denna cmdlet alltid händer ingenting när en Målnoden är i ”Push”-läge.</span><span class="sxs-lookup"><span data-stu-id="03d5a-109">**Note:** If the Meta-Configuration RefreshMode = 'Push' an error is returned by this cmdlet so this cmdlet will always do nothing when a target node is in 'Push' Mode.</span></span>

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
