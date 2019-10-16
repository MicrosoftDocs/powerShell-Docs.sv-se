---
ms.date: 10/11/2019
keywords: DSC, PowerShell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: 271ec04035feb17e932acd0ac80f32213a4e018b
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72352122"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Översikt över önskad tillstånds konfiguration för besluts fattare

Det här dokumentet beskriver affärs fördelarna med att använda PowerShell-tjänsten för önskad tillstånds konfiguration (DSC) och är inte en teknisk guide.

## <a name="what-is-dsc"></a>Vad är DSC?

PowerShell DSC är en plattform för konfigurations hantering som är inbyggd i Windows och som baseras på öppna standarder. DSC är tillräckligt flexibelt för att fungera på ett tillförlitligt och konsekvent sätt i varje steg i livs cykel för distributionen (utveckling, testning, för produktion, produktion) och vid utskalning.

DSC-Center runt [konfigurationer](../configurations/configurations.md). En konfiguration är ett PowerShell-skript som beskriver en miljö som består av datorer, eller noder, med särskilda egenskaper. Dessa egenskaper kan vara så enkla som att se till att en speciell Windows-funktion är aktive rad eller så komplex som att distribuera SharePoint.

DSC har övervakning och rapportering inbyggd. Om ett system inte längre är kompatibelt kan DSC utlösa en avisering och agera för att korrigera systemet.

## <a name="benefits-of-using-dsc"></a>Fördelar med att använda DSC

Konfigurationens design fören klar hur de läses, lagras och uppdateras. Konfigurationer deklarerar status för mål enheter i stället för att skriva instruktioner för att placera enheter i det aktuella läget. Dessa faktorer minskar kostnaderna för att lära sig, införa, implementera och underhålla konfigurationen via DSC.

Att skapa konfigurationer innebär att komplexa distributions steg samlas in som en **enda källa för sanningen** på en enda plats. Konfigurationer gör upprepade distributioner av en speciell uppsättning datorer mindre fel känsliga. Och kan distribueras snabbare och mer tillförlitligt, vilket ger en snabb genom utveckling av komplexa distributioner.

Konfigurationer kan delas via [PowerShell-galleriet](https://powershellgallery.com). Det är möjligt att vanliga scenarier och bästa praxis kanske redan finns för det arbete du behöver göra.

## <a name="dsc-and-devops"></a>DSC och DevOps

DSC utformades med [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) i åtanke. En kombination av personer, processer och verktyg som möjliggör snabb distribution och upprepning fokuserat på att leverera värde för slutanvändare, oavsett om de är interna eller externa. En enda konfiguration som definierar en miljö innebär att utvecklare kan koda sina krav i en konfiguration och kontrol lera konfigurationen i käll kontrollen. Drifts grupper kan sedan distribuera kod utan att gå igenom fel känsliga manuella processer.

Konfigurationer är [data drivna](../configurations/configData.md). De definierade data gör det enklare för åtgärder att identifiera och ändra miljöer utan utvecklarens medverkan.

## <a name="dsc-on-premises-and-off-premises"></a>DSC lokalt och lokalt

DSC kan hantera lokala och lokala distributioner. För lokala lösningar har DSC en [pull-server](../pull-server/pullServer.md) som används för att centralisera hanteringen av datorer och rapportera om deras status. För lokala moln lösningar kan DSC användas, vilket innebär att det går att använda Windows.
Det finns vissa erbjudanden från Azure byggd på DSC, till exempel [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), som centraliserar DSC-rapporter.

## <a name="dsc-and-compatibility"></a>DSC och kompatibilitet

DSC introducerades i Windows Server 2012 R2, men det är tillgängligt för äldre operativ system via Windows Management Framework (WMF). Mer information om WMF finns i [Windows Management Framework](/powershell/scripting/wmf/overview).

DSC kan användas för att hantera Linux. Mer information finns i [komma igång med DSC för Linux](../getting-started/lnxGettingStarted.md).
