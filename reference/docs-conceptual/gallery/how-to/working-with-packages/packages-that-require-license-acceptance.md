---
ms.date: 06/12/2017
title: Kräv godkännande av licens
description: Så här visar du paket licensen på sidan objekt information
ms.openlocfilehash: 0d8a9ed671f7993726bc3fa41d11159b366e5a28
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662296"
---
# <a name="require-license-acceptance"></a>Kräv godkännande av licens

Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande. Du kan visa licensen för modulen genom att klicka på **visa License.txt** länk.

![Kräv godkännande av licens](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande. Genom att klicka på OK godkänner du licens villkoren.

![Distribuera till Azure Automation kräver licens godkännande](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

[Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md) 
 [Azure Automation webbplats](/azure/automation)
