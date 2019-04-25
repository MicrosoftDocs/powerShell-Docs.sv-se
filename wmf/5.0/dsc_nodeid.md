---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7a1725e3858c59a6d31699add22b042359c48463
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058207"
---
# <a name="separation-of-node-and-configuration-ids"></a>Separation av nod- och konfigurations-ID:er

## <a name="overview"></a>Översikt

För att tillhandahålla en mer flexibel och smidig upplevelse när du använder DSC i Pull-läge, har vi lagt till ett antal funktioner i den här versionen. Dessa funktioner är avsedda att ha flexibiliteten att enkelt konfigurera och distribuera konfigurationer över flera noder, medan du fortfarande spåra status och rapportera information för varje nod individuellt.
Dessa funktioner är följande:

* Ett namn som identifierar konfigurationen för en dator. Det här namnet kan delas av flera målnoder
* En agent-ID som unikt identifierar en enskild nod
* En registreringssteget som bara en målnoden sker första gången ansluter till en pull-server

**Obs:** Dessa egenskaper och funktioner har lagts till och Ersätt inte den befintliga pull-funktioner och koncept. Du kan använda dessa nya funktioner eller äldsta med den nya pull-servern som levereras i den här versionen.

Mer information finns i [konfigurera en hämtningsklient med konfigurationsnamn](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)
