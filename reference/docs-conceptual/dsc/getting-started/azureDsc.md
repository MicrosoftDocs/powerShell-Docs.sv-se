---
ms.date: 03/15/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870837"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="bb3a9-103">Använda DSC på Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="bb3a9-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="bb3a9-104">Önskad tillstånds konfiguration (DSC) stöds i Microsoft Azure via den [önskade Azures tilläggs hanterare för tillstånds konfiguration](/azure/virtual-machines/extensions/dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="bb3a9-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="bb3a9-105">Tilläggs hanterare för önskad tillstånds konfiguration i Azure</span><span class="sxs-lookup"><span data-stu-id="bb3a9-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="bb3a9-106">Med Azure DSC-tillägget kan virtuella datorer som finns i Microsoft Azure hanteras med DSC.</span><span class="sxs-lookup"><span data-stu-id="bb3a9-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span> <span data-ttu-id="bb3a9-107">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="bb3a9-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="bb3a9-108">Tilläggs hanterare för önskad tillstånds konfiguration i Azure</span><span class="sxs-lookup"><span data-stu-id="bb3a9-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="bb3a9-109">Windows-VMSS och önskad tillstånds konfiguration med Azure Resource Manager mallar</span><span class="sxs-lookup"><span data-stu-id="bb3a9-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="bb3a9-110">Skicka autentiseringsuppgifter till tillägg hanteraren för Azure DSC</span><span class="sxs-lookup"><span data-stu-id="bb3a9-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="bb3a9-111">Historik över Azure Desired State Configuration-tillägg</span><span class="sxs-lookup"><span data-stu-id="bb3a9-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="bb3a9-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="bb3a9-112">Azure Automation DSC</span></span>

<span data-ttu-id="bb3a9-113">Med [tjänsten Azure Automation](https://azure.microsoft.com/services/automation/) kan du hantera DSC-konfigurationer, resurser och hanterade noder inifrån Azure.</span><span class="sxs-lookup"><span data-stu-id="bb3a9-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="bb3a9-114">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="bb3a9-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="bb3a9-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="bb3a9-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="bb3a9-116">Komma igång med Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="bb3a9-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="bb3a9-117">Onboarding Machines for Management by Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="bb3a9-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)