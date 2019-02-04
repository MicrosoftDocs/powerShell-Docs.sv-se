---
ms.date: 10/16/2017
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 2a40f2055dda78cc0cb6cb05a5e14dce48be9d00
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684180"
---
# <a name="enacting-configurations"></a>Tillämpa konfigurationer

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Det finns två sätt att införa PowerShell Desired State Configuration (DSC) konfigurationer: push och pull-läge.

## <a name="push-mode"></a>Push-läge

![Push-läget](../images/pushModel.png "push hur fungerar det")

Push-läge refererar till en användare som aktivt använder en konfiguration till målnoden genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet.

När du skapar och kompilera en konfiguration, du kan införa det i push-läget genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) cmdlet, ange parametern - Path för cmdlet: en till sökvägen där konfigurationen MOF finns.
Exempel: om konfigurationen MOF finns på `C:\DSC\Configurations\localhost.mof`, du vill tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Obs__: Som standard körs DSC en konfiguration i bakgrunden. Du kan köra konfigurationen interaktivt genom att anropa den [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) med den __-vänta__ parametern.

## <a name="pull-mode"></a>Pull-läge

![Pull-läge](../images/pullModel.png "hämta hur fungerar det")

Pull-klienter är konfigurerade för att få sina konfigurationer av önskat tillstånd från en fjärransluten hämtningstjänst i pull-läge.
På samma sätt, pull-tjänsten har ställts in till värdtjänsten DSC och har etablerats med konfigurationer och resurser som krävs av pull-klienter.
Varje pull-klienter har en schemalagd händelse som utför en regelbunden kompatibilitetskontrollen på konfigurationen av noden.
När händelsen utlöses för första gången, gör en begäran till pull-tjänsten för att hämta den konfiguration som har angetts i LCM i den lokala Configuration Manager (LCM) på pull-klienten.
Om konfigurationen finns på pull-tjänsten och den skickar sin första verifieringskontroller, laddas konfigurationen ned till pull-klienten, där det sedan körs av LCM.

LCM kontrollerar att klienten är kompatibel med konfigurationen med jämna mellanrum som anges av den **ConfigurationModeFrequencyMins** egenskapen för LCM.
LCM söker efter uppdaterade konfigurationer på pull-tjänsten med jämna mellanrum som anges av den **RefreshModeFrequency** egenskapen för LCM.
Information om hur du konfigurerar LCM finns i [konfigurerar den lokala Konfigurationshanteraren](../managing-nodes/metaConfig.md).

Den rekommenderade lösningen som värd för en Pull-tjänst är molntjänst DSC [Azure Automation](https://azure.microsoft.com/services/automation/).
Detta är värd för lösningen ger grafisk hantering, rapportering och centraliserad administration.

Mer information om hur du konfigurerar en Pull-tjänst på Windows Server finns i [att konfigurera en DSC-webbpullserver](pullServer.md).
Förstå men att den här implementeringen har begränsade funktioner och kräver vissa ”gör det själv”-integrering.

I följande avsnitt förklarar hämtningstjänsten och klienter:

- [Översikt över Azure Automation DSC](https://docs.microsoft.com/azure/automation/automation-dsc-overview)
- [Konfigurera en SMB-pullserver](pullServerSMB.md)
- [Konfigurera en pullklient](pullClientConfigID.md)
