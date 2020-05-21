---
title: Kom igång och bidra till PowerShell-dokumentationen
description: Den här artikeln är en översikt över hur du kommer igång som en deltagare i PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 989605f21685decda5f916298a05ec7f5600e575
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560686"
---
# <a name="get-started-contributing-to-powershell-documentation"></a>Kom igång och bidra till PowerShell-dokumentationen

Den här artikeln är en översikt över hur du kommer igång som en deltagare i PowerShell-dokumentationen.

## <a name="powershell-docs-structure"></a>PowerShell – dokument struktur

[Databasen PowerShell-dok][psdocs] är uppdelad i två grupper med innehåll. Git-grenar används för att hantera hur och när en dokumentation publiceras.

### <a name="reference-content"></a>Referens innehåll

Referens innehållet är PowerShell-cmdlet-referensen för de cmdletar som levereras i PowerShell.
[Referensen][ref] samlas in i mapparna versioner (5,1, 6, 7,0 och 7,1). Det här innehållet innehåller endast cmdlet-referenser för moduler som levereras med PowerShell. Det här innehållet används också för att skapa hjälp informationen som visas av `Get-Help` cmdleten.

> [!NOTE]
> Innehålls förteckningen (TOC) för referens innehåll genereras automatiskt av publicerings systemet. Du behöver inte uppdatera innehålls förteckningen.

### <a name="conceptual-content"></a>Konceptuellt innehåll

Den konceptuella dokumentationen innehåller följande innehåll:

- Viktig information
- Installations anvisningar
- Exempel skript och instruktions artiklar
- DSC-dokumentation
- SDK-dokumentation

Den [konceptuella dokumentationen][conceptual] ordnas inte efter version. Alla artiklar visas för alla versioner av PowerShell. Vi arbetar för att skapa versions bara artiklar. När den här funktionen är tillgänglig i vår dokumentation kommer den här hand boken att uppdateras med lämplig information.

> [!NOTE]
> När en konceptuell artikel läggs till, tas bort eller ändras, måste innehålls förteckningen uppdateras och tas med i pull-begäran.

## <a name="using-git-branches"></a>Använda Git-grenar

Standard grenen för PowerShell-dokument är `staging` grenen. Ändringar som görs i arbets grenar sammanfogas i `staging` grenen innan de publiceras. Ungefär en gång i veckan `staging` slås grenen samman i `live` grenen. `live`Grenen innehåller det innehåll som har publicerats till docs.Microsoft.com. Ändringar ska aldrig göras direkt i `live` grenen.

Om du skickar en ändring i dokumentationen som bara gäller för en version av PowerShell som inte har släppts, kontrollerar du om det finns en versionsgren för den versionen. Alla ändringar som avser en specifik, framtida version bör riktas mot versionsgrenen. Versionsgrenar har följande namnmönster: `release-<version>`.

Innan du påbörjar ändringarna skapar du en arbets gren i din lokala kopia av databasen PowerShell-dok. Detta bör vara en [klon av din förgrening][fork]. Se till att synkronisera din lokala lagrings plats innan du skapar din arbets gren. Arbets grenen ska skapas från en uppdatering till en uppdaterad kopia av-eller- `staging` `release` grenen.

Gör de ändringar som du vill skicka efter processen i avsnittet [göra din ändring][making-changes] i den centrala bidrags guiden.

### <a name="creating-new-articles"></a>Skapa nya artiklar

Ett GitHub-problem måste skapas för alla nya dokument som du vill bidra. Sök efter befintliga problem för att se till att du inte duplicerar aktiviteter. Ärenden som tilldelas till någon anses vara "pågående". Om du vill samar beta om ett problem kontaktar du personen som har tilldelats problemet.

Precis som i PowerShell [RFC-processen][rfc], vilket innebär att du skapar ett problem innan du skriver innehållet garanterar att du inte tillbringar mycket tid och ansträngning på något som avvisas av PowerShell-dokument-teamet. Detta gör det också möjligt för oss att kontakta dig med innehålls området och var det ska få plats i PowerShell-dokumentationen.

### <a name="updating-existing-articles"></a>Befintliga artiklar uppdateras

I tillämpliga fall dupliceras cmdlet Reference-artikeln i alla versioner av PowerShell. När du rapporterar ett problem med en cmdlet-referens eller en `About_` artikel, måste du ange vilka versioner som påverkas av problemet. Issue-mallen i GitHub innehåller en check lista för versioner. Använd kryss rutorna för att ange vilka versioner av innehållet som påverkas. När du skickar en ändring av en artikel för ett problem som påverkar flera versioner av innehållet, måste du tillämpa lämplig ändring för varje version av filen.

## <a name="next-steps"></a>Nästa steg

Se [skicka en pull-begäran](pull-requests.md)

<!--link refs-->
[conceptual]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference/docs-conceptual
[fork]: /contribute/get-started-setup-local#fork-the-repository
[making-changes]: /contribute/how-to-write-workflows-major#making-your-changes
[psdocs]: https://github.com/MicrosoftDocs/PowerShell-Docs
[ref]: https://github.com/MicrosoftDocs/PowerShell-Docs/tree/staging/reference
[rfc]: https://github.com/PowerShell/powershell-rfc/blob/master/RFC0000-RFC-Process.md
