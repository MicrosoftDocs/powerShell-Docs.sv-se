---
ms.date: 03/15/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 54a317a415ff12c3d270897f414cba88716f0728
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941952"
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="e8a5d-103">Använda DSC på Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="e8a5d-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="e8a5d-104">Önskad tillstånds konfiguration (DSC) stöds i Microsoft Azure via den [önskade Azures tilläggs hanterare för tillstånds konfiguration](/azure/virtual-machines/extensions/dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="e8a5d-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/extensions/dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="e8a5d-105">Tilläggs hanterare för önskad tillstånds konfiguration i Azure</span><span class="sxs-lookup"><span data-stu-id="e8a5d-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="e8a5d-106">Med Azure DSC-tillägget kan virtuella datorer som finns i Microsoft Azure hanteras med DSC.</span><span class="sxs-lookup"><span data-stu-id="e8a5d-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="e8a5d-107">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="e8a5d-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="e8a5d-108">Tilläggs hanterare för önskad tillstånds konfiguration i Azure</span><span class="sxs-lookup"><span data-stu-id="e8a5d-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/extensions/dsc-overview)
- [<span data-ttu-id="e8a5d-109">Windows-VMSS och önskad tillstånds konfiguration med Azure Resource Manager mallar</span><span class="sxs-lookup"><span data-stu-id="e8a5d-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/extensions/dsc-template)
- [<span data-ttu-id="e8a5d-110">Skicka autentiseringsuppgifter till tillägg hanteraren för Azure DSC</span><span class="sxs-lookup"><span data-stu-id="e8a5d-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/extensions/dsc-credentials)
- [<span data-ttu-id="e8a5d-111">Historik över Azure Desired State Configuration-tillägg</span><span class="sxs-lookup"><span data-stu-id="e8a5d-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="e8a5d-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="e8a5d-112">Azure Automation DSC</span></span>

<span data-ttu-id="e8a5d-113">Med [tjänsten Azure Automation](https://azure.microsoft.com/en-us/services/automation/) kan du hantera DSC-konfigurationer, resurser och hanterade noder inifrån Azure.</span><span class="sxs-lookup"><span data-stu-id="e8a5d-113">The [Azure Automation service](https://azure.microsoft.com/en-us/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="e8a5d-114">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="e8a5d-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="e8a5d-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="e8a5d-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="e8a5d-116">Komma igång med Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="e8a5d-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="e8a5d-117">Onboarding Machines for Management by Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="e8a5d-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)