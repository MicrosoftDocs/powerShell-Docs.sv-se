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
# <a name="deploy-to-azure-automation"></a>Distribuera till Azure Automation

För att distribuera till Azure Automation-knappen på sidan med paketet distribuerar paketet från PowerShell-galleriet i Azure Automation.

![Distribuera till Azure Automation-knappen](../../Images/DeployToAzureAutomationButton.png)

När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina autentiseringsuppgifter för Azure-konto.
Om paketet innehåller beroenden, kommer alla beroenden som att distribueras till Azure Automation även.

> [!WARNING]
> Om samma paket och versionen finns redan i ditt Automation-konto, skrivs distribuera den igen från PowerShell-galleriet paketet i ditt Automation-konto.

Om du distribuerar en modul, visas den i avsnittet moduler i Azure Automation.  Om du distribuerar ett skript, visas den i avsnittet Runbooks i Azure Automation.

För att distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported paketmetadata.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras på Azure Automation kräver godkännande av licensen, portalens användargränssnitt att visa en friskrivning som säger ”den här modulen kräver godkännande av licensen. Genom att klicka på OK, godkänner licensvillkoren ”.

![Distribuera till Azure Automation kräver godkännande av licensen](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

- [Kräv godkännande av licensen i PowerShellGet](../../concepts/module-license-acceptance.md)
- [Kräv godkännande av licensen i PowerShell-galleriet](packages-that-require-license-acceptance.md)
- [Azure Automation-webbplats](http://azure.microsoft.com/services/automation/)
