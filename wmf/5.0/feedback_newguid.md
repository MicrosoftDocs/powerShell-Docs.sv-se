---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 90fd26f9f27d2398da839b309c17b921bb3b8521
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685111"
---
# <a name="new-guid"></a>New-Guid
Ofta skript (eller kanske skriva en DSC-resurs) du har behov av en unik identifierare. GUID fungerar bra, och det är enkelt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det enklare för slutanvändare som inte är redan bekant med .NET Framework-klassen:

PS C:\\&gt; New-Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
