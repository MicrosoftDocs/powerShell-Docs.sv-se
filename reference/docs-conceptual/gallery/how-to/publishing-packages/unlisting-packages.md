---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Avlista paket
ms.openlocfilehash: fb66fd23dae1d4640056a764c31426f61f56d910
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71329031"
---
# <a name="unlisting-packages"></a>Avlista paket

**Varför tar jag bort ett paket från PowerShell-galleriet som inte visas som ett alternativ?**

PowerShell-galleriet stöder inte att användare tar bort sina paket permanent.
Detta gör det möjligt för andra att ta beroenden i dina paket utan att oroa dig för eventuella avbrott i framtiden.
Om pester-modulen exempelvis är beroende av Azure-modulen och Azure-modulen tas bort från galleriet, kan användaren inte längre använda pester-modulen.

I stället för att ta bort ett paket kan du dock ta bort listan i stället.

**Vad ingår i en lista med ett paket på PowerShell-galleriet?**

Om du avvisar ett paket som modul eller skript på PowerShell-galleriet tas det bort från fliken paket. Dessutom går det inte att identifiera paket som inte finns i listan med hjälp av Sök fältet.
Det enda sättet att ladda ned ett paket som inte finns på är att ange det exakta namnet och versionen av paketet.
På grund av detta kommer avregistrering av ett paket inte att dela upp andra moduler eller skript som är beroende av det.

Om du vill ta bort en lista över ditt paket går du till sidan med paket information och väljer Ta bort modul. Avmarkera kryss rutan i listan och klicka på Spara.

**Hur kan jag ta bort ett paket?**

Kontakta PowerShell-galleriet-administratörer om du får ett scenario där borttagning av paketet är nödvändigt.
Giltiga borttagnings scenarier är:
- Problem med upphovs rätts intrång.
- Paketet innehåller potentiellt skadligt innehåll.
- Paketet innehåller känsliga data.

Om du vill skicka en begäran om att ta bort paket till PowerShell-galleriet-administratörer besöker du paketets informations sida och väljer kontakta support.
