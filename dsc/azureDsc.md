---
ms.date: 03/15/2018
keywords: DSC, powershell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: d35488c3f66895e930eaa84360f3d3ec9d74e9c7
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34221892"
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