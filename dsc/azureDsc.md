---
ms.date: 03/15/2018
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 5b0d577e1fecdeac38c2c5f8e955a2d23b1eb707
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-dsc-on-microsoft-azure"></a>Använda DSC på Microsoft Azure

Önskat tillstånd Configuration (DSC) stöds i Microsoft Azure via den [Azure Desired State Configuration-tillägget hanteraren](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Azure önskade tillstånd Configuration tillägget hanterare

Azure DSC-tillägg kan virtuella datorer finns i Microsoft Azure som ska hanteras med DSC.
Mer information finns i följande avsnitt:

- [Azure önskade tillstånd Configuration tillägget hanterare](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-overview)
- [Windows VMSS och Desired State Configuration med Azure Resource Manager-mallar](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-template)
- [Autentiseringsuppgifter skickas till Azure DSC-tillägg-hanterare](/azure/virtual-machines/virtual-machines-windows-extensions-dsc-credentials)
- [Azure önskat Configuration tillägget tillståndshistorik](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

Den [Azure Automation-tjänsten](https://azure.microsoft.com/services/automation/) kan du hantera DSC-konfigurationer, resurser och hanterade noder från i Azure. Mer information finns i följande avsnitt:

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Komma igång med Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Onboarding-datorer för hantering av Azure Automation DSC](/azure/automation/automation-dsc-onboarding)