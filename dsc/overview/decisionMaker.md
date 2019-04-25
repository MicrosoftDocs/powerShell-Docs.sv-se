---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Desired State Configuration-översikt för beslutsfattare
ms.openlocfilehash: ce554d4bb994d4b1816d9d9c24599e4ef0e1c593
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079599"
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Desired State Configuration-översikt för beslutsfattare

Det här dokumentet beskriver fördelarna med hjälp av Windows PowerShell Desired State Configuration (DSC). Det är inte en teknisk vägledning.

## <a name="what-is-desired-state-configuration"></a>Vad är Desired State Configuration?

PowerShell Desired State Configuration är en plattform för hantering av konfiguration som är inbyggda i Windows som baseras på öppna standarder. DSC är tillräckligt flexibelt för att fungera på ett tillförlitligt och konsekvent i varje steg i livscykeln för distribution (utveckling, testning, före produktion, produktion), samt vid skala ut.

DSC fokuserad på [konfigurationer](../configurations/configurations.md).
En konfiguration är ett enkelt att läsa dokument som beskriver en miljö som består av datorer (”noder”) med specifika egenskaper.
Följande egenskaper kan vara lika enkelt som att se till att en specifik Windows-funktion är aktiverat eller så komplext som distribution av SharePoint.

DSC har också övervakning och rapportering inbyggda.
Om ett system inte längre kompatibel, DSC utlösa en avisering och vidta åtgärder för att korrigera systemet.

## <a name="benefits-of-using-desired-state-configuration"></a>Fördelarna med att använda Desired State Configuration

Konfigurationer som är utformade för att vara enkelt läsa, lagras och uppdaterade.
Konfigurationer deklarera målenheter tillstånd ska vara i, istället för att skriva instruktioner för hur du placerar dem i det aktuella tillståndet.
På så sätt blir det mycket billigare att lära dig, använda, implementera och underhålla konfiguration via DSC.

Skapar konfigurationer innebär att komplexa distributionsstegen avbildas som en ”enda sanningskällan” på en enda plats.
Upprepade distributioner av en specifik uppsättning datorer blir mycket mindre felbenägna.
I sin tur gör distributioner snabbare och mer tillförlitlig som gör det möjligt för kort tid på komplexa distributioner.

Det går också att dela via konfigurationer i [PowerShell-galleriet](https://powershellgallery.com) vilket innebär att vanliga scenarier och bästa praxis kanske redan finns för det arbete som behöver göras.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration och DevOps

DSC utformades med [DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) i åtanke, en kombination av personer, processer och verktyg som gör det lätt att implementera och iteration fokuserar på att leverera värde till slutanvändare om interna eller externa.
Med en enda konfiguration definiera en miljö innebär att utvecklare kan koda sina krav till en konfiguration, kontrollera att konfigurationen till källkontroll och åtgärden utvecklingsteam kan enkelt distribuera kod utan att behöva gå igenom felbenägna manuella processer.

Konfigurationer är också [datadrivna](../configurations/configData.md), vilket gör det lättare för ops att identifiera och ändra miljöer utan inblandning av utvecklare.

## <a name="desired-state-configuration-on-premises-and-off-premises"></a>Desired State Configuration för lokala och annan plats
DSC kan användas för att hantera både lokala och av lokala distributioner.
Lokala lösningar, DSC har en [hämtningsservern](../pull-server/pullServer.md) som kan användas för att centralisera hanteringen av datorer och rapportera om deras status.
Molnlösningar kan DSC användas var Windows kommer att kunna användas.
Det finns även specifika erbjudanden från Azure bygger på Desired State Configuration, till exempel [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), vilket centraliserar rapportering av DSC.

## <a name="dsc-and-compatibility"></a>DSC och kompatibilitet

Även om DSC introducerades i Windows Server 2012 R2, är den tillgänglig för äldre operativsystem via paketet Windows Management Framework (WMF).
Mer information om WMF kan hittas på den [PowerShell startsidan](/powershell/).

DSC kan också användas för att hantera Linux. Mer information finns i [komma igång med DSC för Linux](../getting-started/lnxGettingStarted.md).
