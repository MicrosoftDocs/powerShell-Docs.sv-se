---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085338"
---
# <a name="new-guid"></a>New-Guid
Ofta skript (eller kanske skriva en DSC-resurs) du har behov av en unik identifierare. GUID fungerar bra, och det är enkelt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det enklare för slutanvändare som inte är redan bekant med .NET Framework-klassen:

PS C:\\&gt; New-Guid

Guid

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
