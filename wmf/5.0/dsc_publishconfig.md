---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: db4543b788ad0a5c7aa32706246446533b901d09
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085821"
---
# <a name="deliver-a-configuration-document-without-applying"></a><span data-ttu-id="91533-102">Leverera en konfigurationsdokumentet utan att tillämpa</span><span class="sxs-lookup"><span data-stu-id="91533-102">Deliver a configuration document without applying</span></span>

<span data-ttu-id="91533-103">Den [publicera-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet kopierar en MOF-konfigurationsfilen till en målnod, men gäller inte konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="91533-103">The [Publish-DscConfiguration](https://technet.microsoft.com/library/mt517875.aspx) cmdlet copies a configuration MOF file to a target node, but does not apply the configuration.</span></span>
<span data-ttu-id="91533-104">Den här konfigurationen tillämpas under nästa konsekvens passet eller när du kör den [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span><span class="sxs-lookup"><span data-stu-id="91533-104">This configuration is applied during the next consistency pass, or when you run the [Update-DscConfiguration](https://technet.microsoft.com/library/mt143541.aspx) cmdlet.</span></span>
