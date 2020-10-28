---
ms.date: 06/12/2017
title: Kräv godkännande av licens
description: Så här visar du paket licensen på sidan objekt information
ms.openlocfilehash: 0d8a9ed671f7993726bc3fa41d11159b366e5a28
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662296"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="dd11a-103">Kräv godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="dd11a-103">Require license acceptance</span></span>

<span data-ttu-id="dd11a-104">Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="dd11a-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="dd11a-105">Du kan visa licensen för modulen genom att klicka på **visa License.txt** länk.</span><span class="sxs-lookup"><span data-stu-id="dd11a-105">License for module can be viewed by clicking on **View License.txt** link.</span></span>

![Kräv godkännande av licens](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="dd11a-107">Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="dd11a-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="dd11a-108">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="dd11a-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="dd11a-109">Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="dd11a-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="dd11a-110">Genom att klicka på OK godkänner du licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="dd11a-110">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver licens godkännande](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="dd11a-112">Mer information</span><span class="sxs-lookup"><span data-stu-id="dd11a-112">More details</span></span>

<span data-ttu-id="dd11a-113">[Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md) 
 [Azure Automation webbplats](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="dd11a-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
