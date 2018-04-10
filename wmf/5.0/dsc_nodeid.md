---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 6d94de2d3f2c551219d8fbe5badb6e5bb913d796
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="separation-of-node-and-configuration-ids"></a>Separation av nod- och konfigurations-ID:er

## <a name="overview"></a>Översikt

För att ge en mer flexibel och effektiviserad upplevelse när du använder DSC i Pull-läge, har vi lagt till ett antal funktioner i den här versionen. Dessa funktioner är avsedda att ge dig möjlighet att enkelt konfigurera och distribuera konfigurationer över flera noder samtidigt fortfarande spåra status och rapportera information för varje nod individuellt.
Dessa funktioner är följande:

* Konfigurationsnamnet som identifierar konfigurationen för en dator. Det här namnet kan delas av flera målnoder
* En agent-ID som unikt identifierar en enskild nod
* En registreringssteget som första gången inträffar bara målnoden ansluter till en pull-server

**Obs:** dessa egenskaper och funktioner har lagts till och Ersätt inte befintliga pull-funktioner och begrepp. Du kan använda dessa nya funktioner eller äldsta med den nya pull-servern som levereras i den här versionen.

Mer information finns i [ställa in en pull-klient som använder konfigurationsnamn](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)