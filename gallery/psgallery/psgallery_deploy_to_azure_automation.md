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
<a name="deploy-to-azure-automation"></a>Distribuera till Azure Automation
===========================

Distribuera till Azure Automation-knappen på informationssidan för objektet ska distribuera objekt från PowerShell-galleriet till Azure Automation.

![Distribuera till Azure Automation-knappen](Images/DeployToAzureAutomationButton.png)

När du klickar på ska den omdirigera dig till Azure-hanteringsportalen där du loggar in med dina inloggningsuppgifter för Azure-konto.
Om objektet innehåller beroenden, ska alla beroenden distribueras till Azure Automation samt.

Varning: Om samma objekt och versionen finns redan i ditt Automation-konto, distribuera den igen från PowerShell-galleriet över objekt i ditt Automation-konto.

Om du distribuerar en modul, kommer att visas i avsnittet moduler i Azure Automation.  Om du distribuerar ett skript, kommer att visas i avsnittet Runbooks i Azure Automation.

Distribuera till Azure Automation-knappen kan inaktiveras genom att lägga till taggen AzureAutomationNotSupported objektmetadata.

Läs mer om Azure Automation i Azure Automation-webbplatsen [Azure Automation-webbplatsen](http://azure.microsoft.com/services/automation/).