---
ms.date: 06/12/2017
contributor: Farehar
keywords: Galleri, PowerShell, psgallery
title: Kräv godkännande av licens
ms.openlocfilehash: eaed248895d14bd455d2d8d3c2222d8848eeccae
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71328989"
---
# <a name="require-license-acceptance"></a>Kräv godkännande av licens

Kräv att licens godkännande text visas på sidan objekt information för moduler som kräver licens godkännande. Du kan visa licensen för modulen genom att klicka på länken Visa licens. txt.

![Kräv godkännande av licens](../../Images/RequireLicenseAcceptance.png)

Användarna uppmanas att godkänna licensen när de installerar, sparar eller uppdaterar modulen via PowerShellGet eller när de distribuerar till Azure Automation.

## <a name="require-license-acceptance-on-deploy-to-azure-automation"></a>Kräv godkännande av licensen vid distribution till Azure Automation

Om modulen som distribueras till Azure Automation kräver licens godkännande, visar Portal gränssnittet en fri skrivning som säger att den här modulen kräver licens godkännande. Genom att klicka på OK godkänner du licens villkoren.

![Distribuera till Azure Automation kräver licens godkännande](../../Images/DeployToAzureAutomationRequireLicenseAcceptanceDisclaimer.png)

## <a name="more-details"></a>Mer information

[Kräv licens godkännande i PowerShellGet](../../concepts/module-license-acceptance.md)
[Azure Automation webbplats](/azure/automation)
