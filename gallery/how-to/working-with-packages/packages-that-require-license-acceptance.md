---
ms.date: 06/12/2017
contributor: Farehar
keywords: galleriet, powershell, psgallery
title: Kräv godkännande av licensen
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076216"
---
# <a name="require-license-acceptance"></a>Kräv godkännande av licensen

Kräv godkännande av licensen text som visas på informationssidan för objektet för moduler som kräver godkännande av licensen. Licens för modulen kan visas genom att klicka på ”Visa License.txt”-länken.

![Kräv godkännande av licensen](../../Images/RequireLicenseAcceptance.png)

Användare uppmanas att acceptera licensen när du installerar, spara eller uppdatera modulen via PowerShellGet eller när du distribuerar till Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras på Azure Automation kräver godkännande av licensen, portalens användargränssnitt att visa en friskrivning som säger ”den här modulen kräver godkännande av licensen. Genom att klicka på OK, godkänner licensvillkoren ”.

![Distribuera till Azure Automation kräver godkännande av licensen](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

[Kräv godkännande av licensen i PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation-webbplats](/azure/automation)
