---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 5b9eea1c90bfd5a8cee3897d832bf7775a750308
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="separation-of-node-and-configuration-ids"></a>Uppdelning av noden och konfigurations-ID

## <a name="overview"></a>Översikt

För att ge en mer flexibel och effektiviserad upplevelse när du använder DSC i Pull-läge, har vi lagt till ett antal funktioner i den här versionen. Dessa funktioner är avsedda att ge dig möjlighet att enkelt konfigurera och distribuera konfigurationer över flera noder samtidigt fortfarande spåra status och rapportera information för varje nod individuellt. Dessa funktioner är följande:

* Konfigurationsnamnet som identifierar konfigurationen för en dator. Det här namnet kan delas av flera målnoder 
* En agent-ID som unikt identifierar en enskild nod
* En registreringssteget som första gången inträffar bara målnoden ansluter till en pull-server

**Obs:** dessa egenskaper och funktioner har lagts till och Ersätt inte befintliga pull-funktioner och begrepp. Du kan använda dessa nya funktioner eller äldsta med den nya pull-servern som levereras i den här versionen.

Mer information finns i [ställa in en pull-klient som använder konfigurationsnamn](https://msdn.microsoft.com/powershell/dsc/pullclientconfignames)

