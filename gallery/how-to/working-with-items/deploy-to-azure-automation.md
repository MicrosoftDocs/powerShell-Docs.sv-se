---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: 1efdc289228d3a6962302d12ccf44143ce63a806
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
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
