---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: psgallery_deploy_to_azure_automation
ms.openlocfilehash: 91f48fb43d7fb099e34ce5d3b3b632e3cb119d64
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
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

Läs mer om Azure Automation i Azure Automation-webbplatsen [Azure Automation-webbplatsen](http://azure.microsoft.com/en-us/services/automation/).

