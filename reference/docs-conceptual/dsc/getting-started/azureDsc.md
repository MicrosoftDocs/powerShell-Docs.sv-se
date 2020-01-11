---
ms.date: 03/15/2018
keywords: DSC, PowerShell, konfiguration, installation
title: Använda DSC på Microsoft Azure
ms.openlocfilehash: 6d71b69eea78e775a3e5aaac64bccfa10092b8e6
ms.sourcegitcommit: d97b200e7a49315ce6608cd619e3e2fd99193edd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/10/2020
ms.locfileid: "75870837"
---
# <a name="using-dsc-on-microsoft-azure"></a>Använda DSC på Microsoft Azure

Önskad tillstånds konfiguration (DSC) stöds i Microsoft Azure via den [önskade Azures tilläggs hanterare för tillstånds konfiguration](/azure/virtual-machines/extensions/dsc-overview) och via [Azure Automation DSC](/azure/automation/automation-dsc-overview).

## <a name="azure-desired-state-configuration-extension-handler"></a>Tilläggs hanterare för önskad tillstånds konfiguration i Azure

Med Azure DSC-tillägget kan virtuella datorer som finns i Microsoft Azure hanteras med DSC. Mer information finns i följande avsnitt:

- [Tilläggs hanterare för önskad tillstånds konfiguration i Azure](/azure/virtual-machines/extensions/dsc-overview)
- [Windows-VMSS och önskad tillstånds konfiguration med Azure Resource Manager mallar](/azure/virtual-machines/extensions/dsc-template)
- [Skicka autentiseringsuppgifter till tillägg hanteraren för Azure DSC](/azure/virtual-machines/extensions/dsc-credentials)
- [Historik över Azure Desired State Configuration-tillägg](azureDscexthistory.md)

## <a name="azure-automation-dsc"></a>Azure Automation DSC

Med [tjänsten Azure Automation](https://azure.microsoft.com/services/automation/) kan du hantera DSC-konfigurationer, resurser och hanterade noder inifrån Azure. Mer information finns i följande avsnitt:

- [Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Komma igång med Azure Automation DSC](/azure/automation/automation-dsc-getting-started)
- [Onboarding Machines for Management by Azure Automation DSC](/azure/automation/automation-dsc-onboarding)