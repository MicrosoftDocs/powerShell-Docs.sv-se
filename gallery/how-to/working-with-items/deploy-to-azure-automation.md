---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: ced67809387a85e089259edf6b091d68e58ba6a7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="deploy-to-azure-automation"></a>Distribuera till Azure Automation

Distribuera till Azure Automation-knappen på informationssidan för objektet ska distribuera objekt från PowerShell-galleriet till Azure Automation.

![Distribuera till Azure Automation-knappen](../../Images/DeployToAzureAutomationButton.png)

När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina inloggningsuppgifter för Azure-konto.
Om objektet innehåller beroenden, ska alla beroenden distribueras till Azure Automation samt.

> [!WARNING]
> Om samma objekt och versionen finns redan i ditt Automation-konto, över distribuera den igen från PowerShell-galleriet objekt i ditt Automation-konto.

Om du distribuerar en modul, kommer att visas i avsnittet moduler i Azure Automation.  Om du distribuerar ett skript, kommer att visas i avsnittet Runbooks i Azure Automation.

Distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported objektmetadata.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras på Azure Automation kräver godkännande av licens, portalens användargränssnitt visar en friskrivning som säger ”den här modulen kräver godkännande av licens. Genom att klicka på OK, accepterar licensvillkoren ”.

![Distribuera till Azure Automation kräver godkännande av licens](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

- [Kräv godkännande av licens i PowerShellGet](../../concepts/module-license-acceptance.md)
- [Kräv godkännande av licens i PowerShell-galleriet](items-that-require-license-acceptance.md)
- [Azure Automation-webbplatsen](http://azure.microsoft.com/services/automation/)
