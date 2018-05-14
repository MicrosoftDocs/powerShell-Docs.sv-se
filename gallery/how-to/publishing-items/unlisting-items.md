---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Avlista objekt
ms.openlocfilehash: 35dcd283ddace5aec62d692b0ede12ae0bada765
ms.sourcegitcommit: e9ad4d85fd7eb72fb5bc37f6ca3ae1282ae3c6d7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/10/2018
---
# <a name="unlisting-items"></a>Avlista objekt

**Anledningen att ta bort ett objekt från PowerShell-galleriet som inte visas som ett alternativ?**

PowerShell-galleriet stöder inte användarna sina objekt tas bort permanent.
Detta gör det möjligt för andra att ta beroenden på objekten utan att bekymra dig om eventuella radbrytningar i framtiden.
Om modulen Pester beror på Azure-modulen och Azure-modulen tas bort från galleriet, och sedan kan användaren inte längre använder exempelvis modulen Pester.

I stället för att ta bort ett objekt, men du kan ta bort den i stället.

**Vad gör Användarhanteraren ett objekt i PowerShell-galleriet göra?**

Ett objekt, till exempel modulen eller skript på PowerShell-galleriet Användarhanteraren tas det bort från fliken objekt. Dessutom är olistade objekt inte kan identifieras med hjälp av sökfältet.
Det enda sättet att hämta ett objekt som inte finns i listan är att ange den exakta namnet och versionen av objektet.
Därför bryts Användarhanteraren för ett objekt inte andra moduler eller skript som är beroende av den.

Om du vill ta bort objektet finns på informationssidan för objektet och väljer Ta bort objekt. Avmarkera kryssrutan om-listan, och klicka på Spara.

**Hur kan jag ta bort ett objekt**

Om du får ett scenario där borttagning av objekt är nödvändiga, kontakta administratörer för PowerShell-galleriet.
Ogiltig borttagning scenarier är:
- Frågor om upphovsrättsintrång.
- Objektet innehåller potentiellt skadligt innehåll.
- Objektet innehåller känsliga data.

Om du vill skicka en ta bort objektet begäran till PowerShell-galleriet administratörer finns objektet detaljsida och välj kontakta Support.