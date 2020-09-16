---
ms.date: 10/16/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Tillämpa konfigurationer
ms.openlocfilehash: 1437521471d95fd80dc6a6cec62a0b75df4224ec
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783083"
---
# <a name="enacting-configurations"></a>Tillämpa konfigurationer

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5,0

Det finns två sätt att dra i PowerShell-konfigurationer för Desired State Configuration (DSC): push-läge och pull-läge.

## <a name="push-mode"></a>Push-läge

![Översikt över push-läge](media/enactingConfigurations/pushModel.png "Så här fungerar push-läget")

Push-läge refererar till en användare som aktivt använder en konfiguration på en målnod genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) .

När du har skapat och kompilerat en konfiguration kan du använda den i push-läge genom att anropa cmdleten [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) , ange parametern-Path för cmdleten till den sökväg där MOF-konfigurationsfilen finns. Om t. ex. konfigurations-MOF finns på `C:\DSC\Configurations\localhost.mof` kan du tillämpa den på den lokala datorn med följande kommando: `Start-DscConfiguration -Path 'C:\DSC\Configurations'`

> [!NOTE]
> Som standard kör DSC en konfiguration som ett bakgrunds jobb. Anropa [Start-DscConfiguration](/powershell/module/psdesiredstateconfiguration/start-dscconfiguration) med parametern **wait** för att köra konfigurationen interaktivt.

## <a name="pull-mode"></a>Pull-läge

![Översikt över pull-läge](media/enactingConfigurations/pullModel.png "Så här fungerar pull-läget")

I pull-läge konfigureras pull-klienter för att hämta sina önskade tillstånds konfigurationer från en fjärran sluten pull-tjänst. På samma sätt har pull-tjänsten kon figurer ATS som värd för DSC-tjänsten och har etablerats med de konfigurationer och resurser som krävs av pull-klienterna. Varje pull-klient har en schemalagd händelse som utför en periodisk kontroll av nodens konfiguration. När händelsen utlöses första gången gör den lokala Configuration Manager (LCM) på mottagar klienten en begäran till pull-tjänsten för att hämta konfigurationen som anges i LCM. Om konfigurationen finns i pull-tjänsten och den skickar inledande verifierings kontroller, hämtas konfigurationen till pull-klienten, där den körs av LCM.

LCM kontrollerar att klienten följer konfigurationen med jämna mellanrum som anges av egenskapen **ConfigurationModeFrequencyMins** för LCM. LCM söker efter uppdaterade konfigurationer i pull-tjänsten med jämna mellanrum som anges av egenskapen **RefreshModeFrequency** för LCM. Information om hur du konfigurerar LCM finns i [Konfigurera den lokala Configuration Manager](../managing-nodes/metaConfig.md).

Den rekommenderade lösningen för att vara värd för en pull-tjänst är DSC-molnet, [Azure Automation](https://azure.microsoft.com/services/automation/). Detta är en värdbaserad lösning som ger grafisk hantering, rapportering och centraliserad administration.

Mer information om hur du konfigurerar en pull-tjänst på Windows Server finns i [Konfigurera en DSC-webb hämtnings Server](pullServer.md). Vi förstår dock att den här implementeringen har begränsade funktioner och kräver en del "gör det själv"-integrering.

I följande avsnitt förklaras hämtnings tjänsten och klienter:

- [Översikt över Azure Automation DSC](/azure/automation/automation-dsc-overview)
- [Konfigurera en SMB-pull-server](pullServerSMB.md)
- [Konfigurera en pull-klient](pullClientConfigID.md)
