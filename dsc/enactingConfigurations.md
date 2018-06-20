---
ms.date: 10/16/2017
keywords: DSC, powershell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 3d938d14a4da645bbea7ba30ab41e0af72c4b94e
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188487"
---
# <a name="enacting-configurations"></a>Tillämpa konfigurationer

>Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Det finns två sätt att införa PowerShell önskad tillstånd Configuration (DSC) konfigurationer: push och pull-läge.

## <a name="push-mode"></a>Push-läge

![Push-läge](images/pushModel.png "hur push läge fungerar")

Push-läge som refererar till en användare som aktivt tillämpa en konfiguration på målnoden genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet.

När du skapar och sammanställa en konfiguration, kan genomför den i push-läge genom att anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) cmdlet, ange parametern - Path för sökvägen konfigurationen MOF-cmdlet.
Om konfigurationen MOF finns i till exempel `C:\DSC\Configurations\localhost.mof`, du vill tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> __Obs__: som standard körs DSC en konfiguration i bakgrunden. Om du vill köra konfigurationen interaktivt anropa den [Start DscConfiguration](https://technet.microsoft.com/library/dn521623.aspx) med den __-vänta__ parameter.

## <a name="pull-mode"></a>Pull-läge

![Hämtar läget](images/pullModel.png "så här fungerar pull-")

Pull-klienter konfigureras i pull-läge för att få sina konfigurationer tillstånd från en fjärransluten pull-tjänst.
På samma sätt pull-tjänsten har ställts in att värdtjänsten för DSC och har etablerats med konfigurationer och resurser som krävs av pull-klienter.
Varje pull-klienter har en schemalagd händelse som utför en regelbunden kompatibilitetskontrollen på konfigurationen av noden.
När händelsen utlöses för första gången, gör en begäran till pull-tjänsten för att hämta den konfiguration som angetts i MGM om den lokala Configuration Manager (MGM) på pull-klienten.
Om konfigurationen finns på pull-tjänsten och överförs inledande kontroller, hämtas konfigurationen som pull-klienten, där den sedan körs av MGM.

MGM kontrollerar att klienten är kompatibla med konfigurationen med regelbundna intervall som anges av den **ConfigurationModeFrequencyMins** -egenskapen för MGM.
MGM om du söker efter uppdaterade konfigurationer på pull-tjänsten med regelbundna intervall som anges av den **RefreshModeFrequency** -egenskapen för MGM.
Information om hur du konfigurerar MGM finns [konfigurera den lokala Configuration Manager](metaConfig.md).

Den rekommenderade lösningen för värd för en Pull-tjänsten är molntjänst DSC [Azure Automation](https://azure.microsoft.com/services/automation/).
Detta är värd för lösningen ger grafiska management, rapportering och centraliserad administration.

Mer information om hur du skapar en Pull-tjänst på Windows Server finns [ställer in en pull webbserver DSC](pullServer.md).
Förstå dock att den här implementeringen har begränsad funktioner och kräver vissa ”gör det själv”-integration.

I följande avsnitt förklaras pull-tjänsten och -klienter:

- [Azure Automation DSC-översikt](https://docs.microsoft.com/en-us/azure/automation/automation-dsc-overview)
- [Konfigurera en SMB-pull-server](pullServerSMB.md)
- [Konfigurera en pull-klient](pullClientConfigID.md)