---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 91c115c7f0553cd5edf7fecf04e6a5c71c0a1aa2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="new-guid"></a>New-Guid
Ofta skript (eller kanske skriva en DSC-resurs) kan du inte har behov av en unik identifierare. GUID fungerar bra, och det är lätt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det lättare att hitta för slutanvändare som inte är redan bekant med .NET Framework-klass:

PS C:\\ &gt; nytt Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d