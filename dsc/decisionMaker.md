---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Desired State Configuration-översikt för beslutsfattare"
ms.openlocfilehash: e39ab5138b20653e46ac35fa32b99d268f96b2df
ms.sourcegitcommit: f069ff0689006fece768f178c10e3e3eeaee09f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2017
---
# <a name="desired-state-configuration-overview-for-decision-makers"></a>Desired State Configuration-översikt för beslutsfattare

Det här dokumentet beskriver fördelarna med hjälp av PowerShell önskad tillstånd Configuration (DSC). Det är inte en teknisk guide.

## <a name="what-is-desired-state-configuration"></a>Vad är Desired State Configuration?

Windows PowerShell önskad tillstånd Configuration (DSC) är en plattform för hantering av konfiguration inbyggd i Windows som baseras på öppna standarder. DSC är tillräckligt flexibelt för att fungera på ett tillförlitligt sätt och konsekvent i varje steg i livscykeln för distributionen (utveckling, testa, Förproduktion, produktion) samt under skalbar. 

DSC fokuserad på ”[konfigurationer](https://msdn.microsoft.com/en-us/powershell/dsc/configurations)”.
En konfiguration är en lätt att läsa dokumentet som beskriver en miljö som består av datorer (”noder”) med specifika egenskaper. Dessa egenskaper kan vara så enkelt som att säkerställa en specifik Windows-funktionen är aktiverad eller så komplicerad som distribuerar SharePoint. 

DSC har också övervakning och rapportering inbyggda. Om ett system som inte längre är kompatibel, DSC rera en avisering och vidta åtgärder för att korrigera systemet. 

## <a name="benefits-of-using-desired-state-configuration"></a>Fördelarna med att använda Desired State Configuration

Konfigurationer som är utformade för att enkelt läsa, lagras och uppdateras. Konfigurationer deklarera tillstånd målenheterna måste vara i, i stället för att skriva instruktioner för hur du placerar dem i det aktuella tillståndet. Detta gör det mycket kostnadseffektivare att läsa, antar, implementera och underhålla konfigurationen med hjälp av DSC. 

När du skapar konfigurationer innebär att komplexa distributionssteg avbildas som en ”enskild källa för sanningen” i en enda plats. Upprepade distributioner för en specifik uppsättning datorer blir mycket mindre felbenägna. I sin tur gör distributioner snabbare och mer tillförlitlig som gör det möjligt för kort tid på distributioner.

Konfigurationer är också delas via den [PowerShell-galleriet](https://powershellgallery.com) vilket innebär att vanliga scenarier och bästa praxis kanske redan finns för det arbete du behöver.


## <a name="desired-state-configuration-and-devops"></a>Desired State Configuration och DevOps

[DevOps](http://blogs.technet.com/b/ashleymcglone/archive/2015/11/20/devops-for-n00bs-ie-windows-people.aspx) är en kombination av personer, tekniker och kultur som ger snabb distribution och iteration. DSC har utformats med DevOps i åtanke. Med en enda konfiguration definiera en miljö innebär att utvecklare kan koda deras krav till en konfiguration, kontrollera att konfigurationen till källkontroll och team kan enkelt distribuera kod utan att behöva gå igenom felbenägna manuella processer. 

Konfigurationer är också [datadrivna](https://msdn.microsoft.com/en-us/powershell/dsc/configdata), vilket gör det enklare för ops team att identifiera och ändra miljöer utan åtgärder från utvecklare. 

## <a name="desired-state-configuration-on--and-off-premises"></a>Desired State Configuration och inaktivera-lokalt

DSC kan användas för att hantera både lokala och ej lokala distributioner. Lokala lösningar kan DSC har en [hämtningsservern](https://msdn.microsoft.com/en-us/powershell/dsc/pullserver) som kan användas för att centralisera hanteringen av datorer och rapportera om deras status. För molnlösningar kan DSC användas överallt där Windows kan användas. Det finns särskilda erbjudanden från Azure som bygger på Desired State Configuration [Azure Automation](https://azure.microsoft.com/en-us/documentation/services/automation/), vilket centraliserar rapportering av DSC. 

## <a name="dsc-and-compatibility"></a>Kompatibilitet och DSC

Även om DSC introducerades i Windows Server 2012 R2, är den tillgänglig för äldre operativsystem via Windows Management Framework (WMF)-paketet. Mer information om WMF kan hittas på den [PowerShell webbsida](https://msdn.microsoft.com/en-us/powershell/). 

DSC kan också användas för att hantera Linux. Mer information finns i [komma igång med DSC för Linux](https://msdn.microsoft.com/en-us/powershell/dsc/lnxgettingstarted).

