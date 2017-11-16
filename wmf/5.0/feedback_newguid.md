---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: bb2e7b99d14c790bdd3df2f5c729275b96a659fc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="new-guid"></a>Nytt Guid
Ofta skript (eller kanske skriva en DSC-resurs) kan du inte har behov av en unik identifierare. GUID fungerar bra, och det är lätt att anropa .NET Framework Guid-klassen för att generera en, men med en cmdlet gör det lättare att hitta för slutanvändare som inte är redan bekant med .NET Framework-klass:

PS C:\\ &gt; nytt Guid

GUID

----

e19d6ea5-3cc2-4db9-8095-0cdaed5a703d

