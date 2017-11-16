---
ms.date: 2017-06-05
keywords: PowerShell-cmdlet
title: "Med Windows PowerShell för Administration"
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: fa87745b9be04d14de37a308d870b73c5a98cf83
ms.sourcegitcommit: 74255f0b5f386a072458af058a15240140acb294
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/03/2017
---
# <a name="using-windows-powershell-for-administration"></a>Med Windows PowerShell för Administration
Grundläggande målet med Windows PowerShell tillhandahåller bättre och enklare administrativ kontroll över system, interaktivt eller från skript. Det här kapitlet innehåller stegvisa lösningar på många specifika problem administrera Windows-datorer med Windows PowerShell. Även om vi inte har talat om skript eller funktioner i Windows PowerShell användarhandboken, kan lösningarna användas av skript eller funktioner senare. Vi visar exempel som innehåller funktioner som en del av lösningen för att lösa problem.

I hela lösningen beskrivningar visas en blandning av lösningar med hjälp av specifika cmdletar, allmänna Get-WmiObject cmdlet och även externa verktyg som ingår i Windows och .NET Framework-infrastrukturer. Användning av externa verktyg är en del av långsiktiga design syftet med Windows PowerShell. Även om systemet växer uppstår användare kontinuerligt situationer där tillgängliga verktygsuppsättning inte gör allt de behöver. I stället för att sprida beroendet av cmdlet implementeringar enbart försöker Windows PowerShell stöder integrerande lösningar från varje möjligt alternativa scenario.

