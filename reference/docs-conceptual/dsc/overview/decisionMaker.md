---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941763"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Desired State Configuration-översikt för beslutsfattare

Det här dokumentet beskriver affärs fördelarna med att använda Windows PowerShell Desired State Configuration (DSC). Det är inte en teknisk guide.

## <a name="what-is-desired-state-configuration"></a>Vad är önskad tillstånds konfiguration?

PowerShell Desired State Configuration är en plattform för konfigurations hantering som är inbyggd i Windows och som baseras på öppna standarder. DSC är tillräckligt flexibelt för att fungera på ett tillförlitligt och konsekvent sätt i varje steg i livs cykel för distributionen (utveckling, testning, för produktion, produktion) samt vid utskalning.

DSC-Center runt [konfigurationer](../configurations/configurations.md).
En konfiguration är ett lättläst dokument som beskriver en miljö som består av datorer ("noder") med särskilda egenskaper.
Dessa egenskaper kan vara så enkla som att se till att en speciell Windows-funktion är aktive rad eller så komplex som att distribuera SharePoint.

DSC har även inbyggd övervakning och rapportering.
Om ett system inte längre är kompatibelt kan DSC utlösa en avisering och agera för att korrigera systemet.

## <a name="benefits-of-using-desired-state-configuration"></a>Fördelar med att använda önskad tillstånds konfiguration

Konfigurationer är utformade för att enkelt kunna läsas, lagras och uppdateras.
Konfigurationer deklarerar de tillstånds mål enheterna ska vara i, i stället för att skriva instruktioner för hur de ska placeras i det aktuella läget.
Detta gör det mycket billigare att lära sig, införa, implementera och underhålla konfigurationen via DSC.

Att skapa konfigurationer innebär att komplexa distributions steg samlas in som en "sanningen"-källa på en enda plats.
Detta gör upprepade distributioner av en speciell uppsättning datorer mycket mindre fel känsliga.
I sin tur gör distributioner snabbare och mer tillförlitligt vilket gör det enklare att utföra komplexa distributioner.

Konfigurationer kan också delas via [PowerShell-galleriet](https://powershellgallery.com) betydelse vanliga scenarier och bästa praxis kanske redan finns för det arbete som måste utföras.


## <a name="desired-state-configuration-and-devops"></a>Önskad tillstånds konfiguration och DevOps

DSC utformades med [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) i åtanke, en kombination av personer, processer och verktyg som möjliggör snabb distribution och upprepning fokuserar på att leverera värde för slutanvändare, oavsett om de är interna eller externa.
Att ha en enda konfiguration definiera en miljö innebär att utvecklare kan koda sina krav i en konfiguration, kontrol lera konfigurationen i käll kontrollen och att åtgärds team enkelt kan distribuera kod utan att behöva gå igenom fel känsliga manuella processer.

Konfigurationer är också [data drivna](../configurations/configData.md), vilket gör det enklare för OPS att identifiera och ändra miljöer utan utvecklarens medverkan.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Önskad tillstånds konfiguration lokalt och lokalt
DSC kan användas för att hantera både lokala och lokala distributioner.
För lokala lösningar har DSC en [pull-server](../pull-server/pullServer.md) som kan användas för att centralisera hanteringen av datorer och rapportera om deras status.
För moln lösningar kan DSC användas överallt där Windows kan användas.
Det finns också speciella erbjudanden från Azure som bygger på önskad tillstånds konfiguration, till exempel [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), som centraliserar rapportering av DSC.

## <a name="dsc-and-compatibility"></a>DSC och kompatibilitet

Även om DSC introducerades i Windows Server 2012 R2, är det tillgängligt för äldre operativ system via Windows Management Framework (WMF)-paketet.
Mer information om WMF finns på [Start sidan för PowerShell](/powershell/).

DSC kan också användas för att hantera Linux. Mer information finns i [komma igång med DSC för Linux](../getting-started/lnxGettingStarted.md).
