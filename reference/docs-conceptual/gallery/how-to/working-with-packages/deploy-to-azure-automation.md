---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: 5d09a0777c59b642400d683c8cb6f881319fb881
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "78278761"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="a8c15-103">Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="a8c15-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="a8c15-104">Knappen distribuera till Azure Automation på sidan med paket information kommer att distribuera paketet från PowerShell-galleriet till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="a8c15-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Knappen distribuera till Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

<span data-ttu-id="a8c15-106">När du klickar på det omdirigeras du till Azure-Hanteringsportal där du loggar in med dina autentiseringsuppgifter för Azure-kontot.</span><span class="sxs-lookup"><span data-stu-id="a8c15-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="a8c15-107">Om paketet innehåller beroenden kommer alla beroenden att distribueras till Azure Automation även.</span><span class="sxs-lookup"><span data-stu-id="a8c15-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="a8c15-108">Om samma paket och version redan finns i ditt Automation-konto skriver du över paketet i ditt Automation-konto genom att distribuera det igen från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="a8c15-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="a8c15-109">Om du distribuerar en modul visas den i avsnittet moduler i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="a8c15-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="a8c15-110">Om du distribuerar ett skript visas det i Runbooks-avsnittet i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="a8c15-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="a8c15-111">Knappen distribuera till Azure Automation kan inaktive ras genom att AzureAutomationNotSupported-taggen läggs till i paketets metadata.</span><span class="sxs-lookup"><span data-stu-id="a8c15-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="a8c15-112">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="a8c15-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="a8c15-113">Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande.</span><span class="sxs-lookup"><span data-stu-id="a8c15-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="a8c15-114">Genom att klicka på OK godkänner du licens villkoren.</span><span class="sxs-lookup"><span data-stu-id="a8c15-114">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver licens godkännande](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="a8c15-116">Mer information</span><span class="sxs-lookup"><span data-stu-id="a8c15-116">More details</span></span>

- [<span data-ttu-id="a8c15-117">Kräv licens godkännande i PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="a8c15-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="a8c15-118">Kräv licens godkännande i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="a8c15-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="a8c15-119">Azure Automation webbplats</span><span class="sxs-lookup"><span data-stu-id="a8c15-119">Azure Automation website</span></span>](https://azure.microsoft.com/services/automation/)
