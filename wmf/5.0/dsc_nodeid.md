---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685762"
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="da8d8-102">Separation av nod- och konfigurations-ID:er</span><span class="sxs-lookup"><span data-stu-id="da8d8-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="da8d8-103">Översikt</span><span class="sxs-lookup"><span data-stu-id="da8d8-103">Overview</span></span>

<span data-ttu-id="da8d8-104">För att tillhandahålla en mer flexibel och smidig upplevelse när du använder DSC i Pull-läge, har vi lagt till ett antal funktioner i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="da8d8-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="da8d8-105">Dessa funktioner är avsedda att ha flexibiliteten att enkelt konfigurera och distribuera konfigurationer över flera noder, medan du fortfarande spåra status och rapportera information för varje nod individuellt.</span><span class="sxs-lookup"><span data-stu-id="da8d8-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span>
<span data-ttu-id="da8d8-106">Dessa funktioner är följande:</span><span class="sxs-lookup"><span data-stu-id="da8d8-106">These features are as follows:</span></span>

* <span data-ttu-id="da8d8-107">Ett namn som identifierar konfigurationen för en dator.</span><span class="sxs-lookup"><span data-stu-id="da8d8-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="da8d8-108">Det här namnet kan delas av flera målnoder</span><span class="sxs-lookup"><span data-stu-id="da8d8-108">This name can be shared by multiple target nodes</span></span>
* <span data-ttu-id="da8d8-109">En agent-ID som unikt identifierar en enskild nod</span><span class="sxs-lookup"><span data-stu-id="da8d8-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="da8d8-110">En registreringssteget som bara en målnoden sker första gången ansluter till en pull-server</span><span class="sxs-lookup"><span data-stu-id="da8d8-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="da8d8-111">**Obs:** Dessa egenskaper och funktioner har lagts till och Ersätt inte den befintliga pull-funktioner och koncept.</span><span class="sxs-lookup"><span data-stu-id="da8d8-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="da8d8-112">Du kan använda dessa nya funktioner eller äldsta med den nya pull-servern som levereras i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="da8d8-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="da8d8-113">Mer information finns i [konfigurera en hämtningsklient med konfigurationsnamn](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="da8d8-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>
