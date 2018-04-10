---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Använd Windows PowerShell för administration
ms.assetid: db6334ec-ace6-436d-ab88-77aefc817511
ms.openlocfilehash: 69790ddd6bae26dd18e30af860bad4c749cd86a5
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="using-windows-powershell-for-administration"></a>Använd Windows PowerShell för administration
Grundläggande målet med Windows PowerShell tillhandahåller bättre och enklare administrativ kontroll över system, interaktivt eller från skript. Det här kapitlet innehåller stegvisa lösningar på många specifika problem administrera Windows-datorer med Windows PowerShell. Även om vi inte har talat om skript eller funktioner i Windows PowerShell användarhandboken, kan lösningarna användas av skript eller funktioner senare. Vi visar exempel som innehåller funktioner som en del av lösningen för att lösa problem.

I hela lösningen beskrivningar visas en blandning av lösningar med hjälp av specifika cmdletar, allmänna Get-WmiObject cmdlet och även externa verktyg som ingår i Windows och .NET Framework-infrastrukturer. Användning av externa verktyg är en del av långsiktiga design syftet med Windows PowerShell. Även om systemet växer uppstår användare kontinuerligt situationer där tillgängliga verktygsuppsättning inte gör allt de behöver. I stället för att sprida beroendet av cmdlet implementeringar enbart försöker Windows PowerShell stöder integrerande lösningar från varje möjligt alternativa scenario.