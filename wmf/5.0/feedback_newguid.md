---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 2d6b4e3045bc8cff90576c345d1ccb97b2487426
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="new-guid"></a>New-Guid
Ofta skript (eller kanske skriva en DSC-resurs) kan du inte har behov av en unik identifierare. GUID fungerar bra, och det är lätt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det lättare att hitta för slutanvändare som inte är redan bekant med .NET Framework-klass:

PS C:\\ &gt; nytt Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d
