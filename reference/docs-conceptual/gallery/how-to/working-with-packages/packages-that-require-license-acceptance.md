---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galleri, PowerShell, psgallery
title: Kräv godkännande av licens
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328989"
---
# <a name="require-license-acceptance"></a><span data-ttu-id="d7cb9-103">Kräv godkännande av licens</span><span class="sxs-lookup"><span data-stu-id="d7cb9-103">Require license acceptance</span></span>

<span data-ttu-id="d7cb9-104">Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="d7cb9-104">Require License Acceptance text shows up on item details page for modules that require license acceptance.</span></span> <span data-ttu-id="d7cb9-105">Du kan visa licensen för modulen genom att klicka på länken Visa licens. txt.</span><span class="sxs-lookup"><span data-stu-id="d7cb9-105">License for module can be viewed by clicking on 'View License.txt' link.</span></span>

![Kräv godkännande av licens](../../Images/RequireLicenseAcceptance.png)

<span data-ttu-id="d7cb9-107">Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="d7cb9-107">Users will be prompted to accept the license when installing, saving or updating the module through PowerShellGet or when deploying to Azure Automation.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="d7cb9-108">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="d7cb9-108">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="d7cb9-109">Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="d7cb9-109">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="d7cb9-110">Genom att klicka på OK godkänner du licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="d7cb9-110">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver licens godkännande](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="d7cb9-112">Mer information</span><span class="sxs-lookup"><span data-stu-id="d7cb9-112">More details</span></span>

<span data-ttu-id="d7cb9-113">[Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation webbplats](/azure/automation)</span><span class="sxs-lookup"><span data-stu-id="d7cb9-113">[Require License Acceptance in PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation website](/azure/automation)</span></span>
