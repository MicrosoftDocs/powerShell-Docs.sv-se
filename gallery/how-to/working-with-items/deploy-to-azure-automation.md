---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="327ac-103">Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="327ac-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="327ac-104">Distribuera till Azure Automation-knappen på informationssidan för objektet ska distribuera objekt från PowerShell-galleriet till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="327ac-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Distribuera till Azure Automation-knappen](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="327ac-106">När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina inloggningsuppgifter för Azure-konto.</span><span class="sxs-lookup"><span data-stu-id="327ac-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="327ac-107">Om objektet innehåller beroenden, ska alla beroenden distribueras till Azure Automation samt.</span><span class="sxs-lookup"><span data-stu-id="327ac-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="327ac-108">Om samma objekt och versionen finns redan i ditt Automation-konto, över distribuera den igen från PowerShell-galleriet objekt i ditt Automation-konto.</span><span class="sxs-lookup"><span data-stu-id="327ac-108">If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="327ac-109">Om du distribuerar en modul, kommer att visas i avsnittet moduler i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="327ac-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="327ac-110">Om du distribuerar ett skript, kommer att visas i avsnittet Runbooks i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="327ac-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="327ac-111">Distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported objektmetadata.</span><span class="sxs-lookup"><span data-stu-id="327ac-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="327ac-112">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="327ac-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="327ac-113">Om modulen som distribueras på Azure Automation kräver godkännande av licens, portalens användargränssnitt visar en friskrivning som säger ”den här modulen kräver godkännande av licens.</span><span class="sxs-lookup"><span data-stu-id="327ac-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="327ac-114">Genom att klicka på OK, accepterar licensvillkoren ”.</span><span class="sxs-lookup"><span data-stu-id="327ac-114">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver godkännande av licens](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="327ac-116">Mer information</span><span class="sxs-lookup"><span data-stu-id="327ac-116">More details</span></span>

- [<span data-ttu-id="327ac-117">Kräv godkännande av licens i PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="327ac-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="327ac-118">Kräv godkännande av licens i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="327ac-118">Require License Acceptance in PowerShell Gallery</span></span>](items-that-require-license-acceptance.md)
- [<span data-ttu-id="327ac-119">Azure Automation-webbplatsen</span><span class="sxs-lookup"><span data-stu-id="327ac-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
