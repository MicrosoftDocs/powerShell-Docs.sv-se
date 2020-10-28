---
ms.date: 06/12/2017
title: Distribuera till Azure Automation
description: Den här artikeln beskriver hur du använder PowerShell-galleriet för att distribuera ett paket till Azure Automation.
ms.openlocfilehash: e9de079ee6cc950c8a268423b9eabd515959b718
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662377"
---
# <a name="deploy-to-azure-automation"></a>Distribuera till Azure Automation

Knappen distribuera till Azure Automation på sidan med paket information kommer att distribuera paketet från PowerShell-galleriet till Azure Automation.

![Knappen distribuera till Azure Automation](media/deploy-to-azure-automation/DeployToAzureAutomationButton.png)

När du klickar på det omdirigeras du till Azure-Hanteringsportal där du loggar in med dina autentiseringsuppgifter för Azure-kontot. Om paketet innehåller beroenden kommer alla beroenden att distribueras till Azure Automation även.

> [!WARNING]
> Om samma paket och version redan finns i ditt Automation-konto skriver du över paketet i ditt Automation-konto genom att distribuera det igen från PowerShell-galleriet.

Om du distribuerar en modul visas den i avsnittet moduler i Azure Automation. Om du distribuerar ett skript visas det i Runbooks-avsnittet i Azure Automation.

Knappen distribuera till Azure Automation kan inaktive ras genom att AzureAutomationNotSupported-taggen läggs till i paketets metadata.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande. Genom att klicka på OK godkänner du licens villkoren.

![Distribuera till Azure Automation kräver licens godkännande](media/deploy-to-azure-automation/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

- [Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md)
- [Kräv licens godkännande i PowerShell-galleriet](packages-that-require-license-acceptance.md)
- [Azure Automation webbplats](https://azure.microsoft.com/services/automation/)
