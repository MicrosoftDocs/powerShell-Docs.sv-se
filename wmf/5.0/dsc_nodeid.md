---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a><span data-ttu-id="8009e-102">Uppdelning av noden och konfigurations-ID</span><span class="sxs-lookup"><span data-stu-id="8009e-102">Separation of Node and Configuration IDs</span></span>

## <a name="overview"></a><span data-ttu-id="8009e-103">Översikt</span><span class="sxs-lookup"><span data-stu-id="8009e-103">Overview</span></span>

<span data-ttu-id="8009e-104">För att ge en mer flexibel och effektiviserad upplevelse när du använder DSC i Pull-läge, har vi lagt till ett antal funktioner i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="8009e-104">In order to provide a more flexible and streamlined experience when using DSC in Pull mode, we have added a number of features in this release.</span></span> <span data-ttu-id="8009e-105">Dessa funktioner är avsedda att ge dig möjlighet att enkelt konfigurera och distribuera konfigurationer över flera noder samtidigt fortfarande spåra status och rapportera information för varje nod individuellt.</span><span class="sxs-lookup"><span data-stu-id="8009e-105">These features are intended to allow you to have the flexibility to easily setup and deploy configurations across multiple nodes, while still tracking status and reporting information for each node individually.</span></span> <span data-ttu-id="8009e-106">Dessa funktioner är följande:</span><span class="sxs-lookup"><span data-stu-id="8009e-106">These features are as follows:</span></span>

* <span data-ttu-id="8009e-107">Konfigurationsnamnet som identifierar konfigurationen för en dator.</span><span class="sxs-lookup"><span data-stu-id="8009e-107">A configuration name which identifies the configuration for a computer.</span></span> <span data-ttu-id="8009e-108">Det här namnet kan delas av flera målnoder</span><span class="sxs-lookup"><span data-stu-id="8009e-108">This name can be shared by multiple target nodes</span></span> 
* <span data-ttu-id="8009e-109">En agent-ID som unikt identifierar en enskild nod</span><span class="sxs-lookup"><span data-stu-id="8009e-109">An agent ID which uniquely identifies a single node</span></span>
* <span data-ttu-id="8009e-110">En registreringssteget som första gången inträffar bara målnoden ansluter till en pull-server</span><span class="sxs-lookup"><span data-stu-id="8009e-110">A registration step which only occurs the first time a target node connects to a pull server</span></span>

<span data-ttu-id="8009e-111">**Obs:** dessa egenskaper och funktioner har lagts till och Ersätt inte befintliga pull-funktioner och begrepp.</span><span class="sxs-lookup"><span data-stu-id="8009e-111">**Note:** These features and functionality have been added and do not replace the existing pull features and concepts.</span></span> <span data-ttu-id="8009e-112">Du kan använda dessa nya funktioner eller äldsta med den nya pull-servern som levereras i den här versionen.</span><span class="sxs-lookup"><span data-stu-id="8009e-112">You can use these new features or the older ones with the new pull server shipping in this release.</span></span>

<span data-ttu-id="8009e-113">Mer information finns i [ställa in en pull-klient som använder konfigurationsnamn](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span><span class="sxs-lookup"><span data-stu-id="8009e-113">For more information, see [Setting up a pull client using configuration names](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)</span></span>

