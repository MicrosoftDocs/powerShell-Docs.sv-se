---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a><span data-ttu-id="23f37-103">Använda DSC på Microsoft Azure</span><span class="sxs-lookup"><span data-stu-id="23f37-103">Using DSC on Microsoft Azure</span></span>

<span data-ttu-id="23f37-104">Önskat tillstånd Configuration (DSC) stöds i Microsoft Azure via den [Azure Desired State Configuration-tillägget hanteraren](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span><span class="sxs-lookup"><span data-stu-id="23f37-104">Desired State Configuration (DSC) is supported in Microsoft Azure through the [Azure Desired State Configuration extension handler](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) and through [Azure Automation DSC](/azure/automation/automation-dsc-overview).</span></span>

## <a name="azure-desired-state-configuration-extension-handler"></a><span data-ttu-id="23f37-105">Azure önskade tillstånd Configuration tillägget hanterare</span><span class="sxs-lookup"><span data-stu-id="23f37-105">Azure Desired State Configuration extension handler</span></span>

<span data-ttu-id="23f37-106">Azure DSC-tillägg kan virtuella datorer finns i Microsoft Azure som ska hanteras med DSC.</span><span class="sxs-lookup"><span data-stu-id="23f37-106">The Azure DSC extension allows VMs hosted in Microsoft Azure to be managed with DSC.</span></span>
<span data-ttu-id="23f37-107">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="23f37-107">For more information, see the following topics:</span></span>

- [<span data-ttu-id="23f37-108">Azure önskade tillstånd Configuration tillägget hanterare</span><span class="sxs-lookup"><span data-stu-id="23f37-108">Azure Desired State Configuration extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [<span data-ttu-id="23f37-109">Windows VMSS och Desired State Configuration med Azure Resource Manager-mallar</span><span class="sxs-lookup"><span data-stu-id="23f37-109">Windows VMSS and Desired State Configuration with Azure Resource Manager templates</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [<span data-ttu-id="23f37-110">Autentiseringsuppgifter skickas till Azure DSC-tillägg-hanterare</span><span class="sxs-lookup"><span data-stu-id="23f37-110">Passing credentials to the Azure DSC extension handler</span></span>](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [<span data-ttu-id="23f37-111">Azure önskat Configuration tillägget tillståndshistorik</span><span class="sxs-lookup"><span data-stu-id="23f37-111">Azure Desired State Configuration extension history</span></span>](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a><span data-ttu-id="23f37-112">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="23f37-112">Azure Automation DSC</span></span>

<span data-ttu-id="23f37-113">Den [Azure Automation-tjänsten](https://azure.microsoft.com/services/automation/) kan du hantera DSC-konfigurationer, resurser och hanterade noder från i Azure.</span><span class="sxs-lookup"><span data-stu-id="23f37-113">The [Azure Automation service](https://azure.microsoft.com/services/automation/) allows you to manage DSC configurations, resources, and managed nodes from within Azure.</span></span> <span data-ttu-id="23f37-114">Mer information finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="23f37-114">For more information, see the following topics:</span></span>

- [<span data-ttu-id="23f37-115">Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="23f37-115">Azure Automation DSC</span></span>](/azure/automation/automation-dsc-overview)
- [<span data-ttu-id="23f37-116">Komma igång med Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="23f37-116">Getting started with Azure Automation DSC</span></span>](/azure/automation/automation-dsc-getting-started)
- [<span data-ttu-id="23f37-117">Onboarding-datorer för hantering av Azure Automation DSC</span><span class="sxs-lookup"><span data-stu-id="23f37-117">Onboarding machines for management by Azure Automation DSC</span></span>](/azure/automation/automation-dsc-onboarding)