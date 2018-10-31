---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: dc382b1cf3ceaa787f54c555d01e6bd9ba70e680
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50004141"
---
# <a name="deploy-to-azure-automation"></a><span data-ttu-id="6fa7f-103">Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="6fa7f-103">Deploy to Azure Automation</span></span>

<span data-ttu-id="6fa7f-104">För att distribuera till Azure Automation-knappen på sidan med paketet distribuerar paketet från PowerShell-galleriet i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-104">The Deploy to Azure Automation button on the package details page will deploy the package from the PowerShell Gallery to Azure Automation.</span></span>

![Distribuera till Azure Automation-knappen](../../Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="6fa7f-106">När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="6fa7f-107">Om paketet innehåller beroenden, kommer alla beroenden som att distribueras till Azure Automation även.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-107">If the package includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

> [!WARNING]
> <span data-ttu-id="6fa7f-108">Om samma paket och versionen finns redan i ditt Automation-konto, skrivs distribuera den igen från PowerShell-galleriet paketet i ditt Automation-konto.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-108">If the same package and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the package in your Automation account.</span></span>

<span data-ttu-id="6fa7f-109">Om du distribuerar en modul, visas den i avsnittet moduler i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="6fa7f-110">Om du distribuerar ett skript, visas den i avsnittet Runbooks i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="6fa7f-111">För att distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported paketmetadata.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the package metadata.</span></span>

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a><span data-ttu-id="6fa7f-112">Kräv godkännande av licensen vid distribution till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="6fa7f-112">Require License Acceptance on Deploy to Azure Automation</span></span>

<span data-ttu-id="6fa7f-113">Om modulen som distribueras på Azure Automation kräver godkännande av licensen, portalens användargränssnitt att visa en friskrivning som säger ”den här modulen kräver godkännande av licensen.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-113">If the module being deployed to Azure Automation requires license acceptance, portal UI will show a disclaimer saying 'This module requires license acceptance.</span></span> <span data-ttu-id="6fa7f-114">Genom att klicka på OK, godkänner licensvillkoren ”.</span><span class="sxs-lookup"><span data-stu-id="6fa7f-114">By clicking OK, you are accepting license terms.'</span></span>

![Distribuera till Azure Automation kräver godkännande av licensen](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a><span data-ttu-id="6fa7f-116">Mer information</span><span class="sxs-lookup"><span data-stu-id="6fa7f-116">More details</span></span>

- [<span data-ttu-id="6fa7f-117">Kräv godkännande av licensen i PowerShellGet</span><span class="sxs-lookup"><span data-stu-id="6fa7f-117">Require License Acceptance in PowerShellGet</span></span>](../../concepts/module-license-acceptance.md)
- [<span data-ttu-id="6fa7f-118">Kräv godkännande av licensen i PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="6fa7f-118">Require License Acceptance in PowerShell Gallery</span></span>](packages-that-require-license-acceptance.md)
- [<span data-ttu-id="6fa7f-119">Azure Automation-webbplats</span><span class="sxs-lookup"><span data-stu-id="6fa7f-119">Azure Automation website</span></span>](http://azure.microsoft.com/services/automation/)
