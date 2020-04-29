---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galleri, PowerShell, psgallery
title: Kräv godkännande av licens
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278674"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="41f83-103">Kräv godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="41f83-103">Require license acceptance</span></span>

<span data-ttu-id="41f83-104">Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="41f83-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="41f83-105">Du kan visa licensen för modulen genom att klicka på länken Visa licens. txt.</span><span class="sxs-lookup"><span data-stu-id="41f83-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Kräv godkännande av licens](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

<span data-ttu-id="41f83-107">Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="41f83-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="41f83-108">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="41f83-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="41f83-109">Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="41f83-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="41f83-110">Genom att klicka på OK godkänner du licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="41f83-110">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver licens godkännande](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="41f83-112">Mer information</span><span class="sxs-lookup"><span data-stu-id="41f83-112">More details</span></span>

<span data-ttu-id="41f83-113">[Kräv licens godkännande på PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation webbplats](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="41f83-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
