---
ms.date: 03/15/2018
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404654"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="7dcec-103">Använda DSC på Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="7dcec-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="7dcec-104">Desired State Configuration (DSC) stöds i Microsoft Azure via den [Azure Desired State Configuration-tilläggshanterare](/azure/virtual-machines/extensions/dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="7dcec-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="7dcec-105">Azure Desired State Configuration-tilläggshanterare</span><span class="sxs-lookup"><span data-stu-id="7dcec-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="7dcec-106">Azure DSC-tillägget kan virtuella datorer i Microsoft Azure som ska hanteras med DSC.</span><span class="sxs-lookup"><span data-stu-id="7dcec-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="7dcec-107">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="7dcec-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7dcec-108">Azure Desired State Configuration-tilläggshanterare</span><span class="sxs-lookup"><span data-stu-id="7dcec-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="7dcec-109">Windows VMSS och Desired State Configuration med Azure Resource Manager-mallar</span><span class="sxs-lookup"><span data-stu-id="7dcec-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="7dcec-110">Skicka autentiseringsuppgifter till Azure DSC-tilläggshanterare</span><span class="sxs-lookup"><span data-stu-id="7dcec-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="7dcec-111">Azure Desired State Configuration-tillägget historik</span><span class="sxs-lookup"><span data-stu-id="7dcec-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="7dcec-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7dcec-112">Azure Automation DSC</span></span>

<span data-ttu-id="7dcec-113">Den [Azure Automation-tjänsten](https://azure.microsoft.com/en-us/services/automation/) låter dig hantera DSC-konfigurationer, resurser och hanterade noder från i Azure.</span><span class="sxs-lookup"><span data-stu-id="7dcec-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="7dcec-114">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="7dcec-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="7dcec-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7dcec-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="7dcec-116">Komma igång med Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7dcec-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="7dcec-117">Konfigurera datorer för hantering av Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="7dcec-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)