---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 8da4eabead6a419dc0c01c74335c06bf8be25d0c
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
<a name="deploy-to-azure-automation"></a><span data-ttu-id="bb3f6-103">Distribuera till Azure Automation</span><span class="sxs-lookup"><span data-stu-id="bb3f6-103">Deploy to Azure Automation</span></span>
===========================

<span data-ttu-id="bb3f6-104">Distribuera till Azure Automation-knappen på informationssidan för objektet ska distribuera objekt från PowerShell-galleriet till Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-104">The Deploy to Azure Automation button on the item details page will deploy the item from the PowerShell Gallery to Azure Automation.</span></span>

![Distribuera till Azure Automation-knappen](Images/DeployToAzureAutomationButton.png)

<span data-ttu-id="bb3f6-106">När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina inloggningsuppgifter för Azure-konto.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-106">When clicked, it will redirect you to the Azure Management Portal, where you sign in using your Azure account credentials.</span></span>
<span data-ttu-id="bb3f6-107">Om objektet innehåller beroenden, ska alla beroenden distribueras till Azure Automation samt.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-107">If the item includes dependencies, all the dependencies will be deployed to Azure Automation as well.</span></span>

<span data-ttu-id="bb3f6-108">Varning: Om samma objekt och versionen finns redan i ditt Automation-konto, distribuera den igen från PowerShell-galleriet över objekt i ditt Automation-konto.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-108">WARNING:  If the same item and version already exist in your Automation account, deploying it again from the PowerShell Gallery will overwrite the item in your Automation account.</span></span>

<span data-ttu-id="bb3f6-109">Om du distribuerar en modul, kommer att visas i avsnittet moduler i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-109">If you deploy a module, it will appear in the Modules section of Azure Automation.</span></span>  <span data-ttu-id="bb3f6-110">Om du distribuerar ett skript, kommer att visas i avsnittet Runbooks i Azure Automation.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-110">If you deploy a script, it will appear in the Runbooks section of Azure Automation.</span></span>

<span data-ttu-id="bb3f6-111">Distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported objektmetadata.</span><span class="sxs-lookup"><span data-stu-id="bb3f6-111">The Deploy to Azure Automation button can be disabled by adding the AzureAutomationNotSupported tag to the item metadata.</span></span>

<span data-ttu-id="bb3f6-112">Läs mer om Azure Automation i Azure Automation-webbplatsen [Azure Automation-webbplatsen](http://azure.microsoft.com/services/automation/).</span><span class="sxs-lookup"><span data-stu-id="bb3f6-112">To learn more about Azure Automation, see the Azure Automation website [Azure Automation website](http://azure.microsoft.com/services/automation/).</span></span>