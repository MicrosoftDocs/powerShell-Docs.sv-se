---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Avlista paket
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084121"
---
# <a name="unlisting-packages"></a>Avlista paket

**Varför tar bort ett paket från PowerShell-galleriet visas inte som ett alternativ?**

PowerShell-galleriet har inte stöd för användare som har sina paket tas bort permanent.
Detta gör att andra kan ta beroenden på dina paket utan att behöva bekymra dig om möjligt radbrytningar i framtiden.
Om modulen Pester beror på Azure-modulen och Azure-modulen tas bort från galleriet, och användaren kan inte längre använder exempelvis modulen Pester.

I stället för att ta bort ett paket, men du kan ta bort den i stället.

**Vad kostar avlista ett paket på PowerShell-galleriet göra?**

Avlista ett paket, till exempel modulen eller skript i PowerShell-galleriet tas den bort från fliken paket. Dessutom är olistade paket inte synliga i sökfältet.
Det enda sättet att ladda ned ett paket som inte finns i listan är att ange de exakta namnet och versionen av paketet.
Därför som avlista av ett paket påverkar andra moduler och skript som är beroende av den.

Om du vill ta bort ditt paket, gå till sidan med paket och välj Ta bort modulen. Avmarkera kryssrutan ”listan” och klicka på Spara.

**Hur tar jag bort ett paket?**

Om det uppstår ett scenario där det är nödvändigt att ta bort paketet kan du kontakta administratörer för PowerShell-galleriet.
Giltigt borttagning scenarier är:
- Problem med upphovsrättsintrång.
- Paketet innehåller potentiellt skadligt innehåll.
- Paketet innehåller känsliga data.

Ditt paket information på sidan för att skicka en ta bort paketet begäran till administratörer för PowerShell-galleriet, och välj kontakta Support.
