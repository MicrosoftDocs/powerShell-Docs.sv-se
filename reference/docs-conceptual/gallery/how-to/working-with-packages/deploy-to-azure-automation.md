---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Distribuera till Azure Automation
ms.openlocfilehash: 707691e24a77647064e60da0d9a31ad5eece1c59
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328779"
---
# <a name="deploy-to-azure-automation"></a>Distribuera till Azure Automation

Knappen distribuera till Azure Automation på sidan med paket information kommer att distribuera paketet från PowerShell-galleriet till Azure Automation.

![Knappen distribuera till Azure Automation](../../Images/DeployToAzureAutomationButton.png)

När du klickar på det omdirigeras du till Azure-Hanteringsportal där du loggar in med dina autentiseringsuppgifter för Azure-kontot.
Om paketet innehåller beroenden kommer alla beroenden att distribueras till Azure Automation även.

> [!WARNING]
> Om samma paket och version redan finns i ditt Automation-konto skriver du över paketet i ditt Automation-konto genom att distribuera det igen från PowerShell-galleriet.

Om du distribuerar en modul visas den i avsnittet moduler i Azure Automation.  Om du distribuerar ett skript visas det i Runbooks-avsnittet i Azure Automation.

Knappen distribuera till Azure Automation kan inaktive ras genom att AzureAutomationNotSupported-taggen läggs till i paketets metadata.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande. Genom att klicka på OK godkänner du licens villkoren.

![Distribuera till Azure Automation kräver licens godkännande](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

- [Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md)
- [Kräv licens godkännande i PowerShell-galleriet](packages-that-require-license-acceptance.md)
- [Azure Automation webbplats](https://azure.microsoft.com/services/automation/)
