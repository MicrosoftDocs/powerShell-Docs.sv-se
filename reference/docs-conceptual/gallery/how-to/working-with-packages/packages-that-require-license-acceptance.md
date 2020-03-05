---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galleri, PowerShell, psgallery
title: Kräv godkännande av licens
ms.openlocfilehash: 4b293ea693062cf9717fa4ca913c3eb9abaf7014
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78278674"
---
# <a name="require-license-acceptance"></a>Kräv godkännande av licens

Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande. Du kan visa licensen för modulen genom att klicka på länken Visa licens. txt.

![Kräv godkännande av licens](media/packages-that-require-license-acceptance/RequireLicenseAcceptance.png)

Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande. Genom att klicka på OK godkänner du licens villkoren.

![Distribuera till Azure Automation kräver licens godkännande](media/packages-that-require-license-acceptance/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

[Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation webbplats](/azure/automation)
