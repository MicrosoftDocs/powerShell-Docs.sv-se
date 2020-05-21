---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Hantera paket ägare
ms.openlocfilehash: 72a3ff72818c5461c74d46de5689e2d6c59b19bf
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564677"
---
# <a name="managing-package-owners"></a>Hantera paket ägare

Ägarskapet av ett paket i PowerShell-galleriet definieras av vem som publicerade paketet i galleriet.
Ibland måste dessa metadata hanteras bortom den inledande paket publiceringen, vilket innebär att föränderligt måste vara medan själva paketet inte är det.

Alla paket ägare är peer-datorer.
Det innebär att alla paket ägare kan publicera en ny version av ett paket. Det innebär också att alla paket ägare kan ta bort alla andra paket ägare.
Ingen ägare har fler utfärdare än andra ägare.

## <a name="setting-a-packages-initial-owner"></a>Ange ett pakets initiala ägare

När ett nytt paket publiceras till PowerShell-galleriet definieras den ursprungliga ägaren av den användare som publicerade paketet. Detta bestäms av vars API-nyckel användes i Publishing-module-cmdleten.

## <a name="adding-owners"></a>Lägga till ägare

När ett paket har publicerats till PowerShell-galleriet är det enkelt att bjuda in fler användare att bli ägare till ett paket.

1. [Logga](https://powershellgallery.com/users/account/LogOn) in på PowerShell-galleriet med det konto som är den aktuella ägaren till ett paket.
2. Gå till sidan paket genom att använda fliken objekt, söka eller klicka på ditt användar namn och sedan [**hantera mina paket**](https://www.powershellgallery.com/account/Packages).
3. När du är inloggad som ett pakets ägare finns länken "Hantera ägare" på vänster sida för att klicka.
4. Ange användar namnet för den person som ska läggas till som ägare och klicka på Lägg till.
5. Ett e-postmeddelande skickas sedan till den nya medägaren som en inbjudan att bli ägare till ett paket.
6. När användaren klickar på länken är de en fullständig samägare med fullständig kontroll över ett paket, inklusive möjligheten att ta bort andra användare som ägare.

**Obs!** tills den nya ägaren bekräftar ägarskapet visas de *inte* som ägare till ett paket.
När du visar sidan **Hantera ägare** visas posten "väntar på godkännande" i aktuella ägare.
Den inbjudan kan tas bort. precis som andra ägare kan tas bort.
Den här processen av inbjudningar förhindrar att användare lägger till andra användare felaktigt som ägare till sina paket.

Observera att metadata för "författare" är en helt fri hands text. endast "ägare" kontrol leras.

## <a name="removing-owners"></a>Ta bort ägare

När ett paket har flera ägare och en måste tas bort är processen enkel:

1. [Logga in](https://powershellgallery.com/users/account/LogOn) på PowerShell-galleriet med det konto som är den aktuella ägaren till ett paket.
2. Gå till sidan paket på fliken paket, Sök eller klicka på ditt användar namn och [**hantera mina paket**](https://www.powershellgallery.com/account/Packages).
3. När du är inloggad som ett pakets ägare finns länken "Hantera ägare" på vänster sida för att klicka.
4. Klicka på länken Ta bort bredvid den ägare som ska tas bort.

## <a name="transferring-package-ownership"></a>Överför paket ägarskap

Vi får ibland support förfrågningar om att överföra paket ägarskap från en användare till en annan, men du kan nästan alltid göra detta själv.
Överföring av ägarskap från en användare till en annan är bara en kombination av de två funktionerna ovan.

1. Den aktuella ägaren bjuder in den nya användaren att bli en medägare och den nya användaren godkänner inbjudan.
2. Den nya användaren tar bort den gamla användaren från listan över ägare.

Den här begäran har kommit under ett par formulär, men processen fungerar på samma sätt.

- Paketets ägarskap ändras från en utvecklare till en annan
- Paketet publicerades av misstag med fel konto

## <a name="orphaned-packages"></a>Överblivna paket

Ett sista scenario har inträffat, men inte många gånger.
Paketen har blivit överblivna och det enda paket ägar kontot kan inte användas för att lägga till nya ägare.
Här följer några exempel på det här scenariot:

- Ägarens konto är associerat med en e-postadress som inte längre finns och användaren har glömt sitt lösen ord
- Den registrerade ägaren har lämnat företaget som tillverkar paketet och kan inte nås för att uppdatera paket ägarskapet
- På grund av ett fel som endast har påverkat en fåtal av paket, är paketet insamlat på ett inaktivt sätt i galleriet

PowerShell-galleriet-administratörer kan komma åt länken "Hantera ägare" för alla paket.
Om du är Rightful-ägare till ett paket och inte kan nå den aktuella ägaren för att få ägande behörighet, använder du länken "rapportera missbruk" i galleriet för att nå PowerShell-galleriet-administratörer.
Vi följer sedan en process för att verifiera din ägande av paketet.
Om vi fastställer att du ska vara ägare till paketet använder vi länken "Hantera ägare" för paketets skapar och skickar dig inbjudan att bli ägare.
Vi kommer bara att göra detta när du har verifierat att du bör vara en ägare och processen för detta beror på omständigheter.
Ofta kommer vi att använda paketets projekt-URL för att hitta ett sätt att kontakta projekt ägaren, men vi kan också använda Twitter, e-post eller andra sätt för att kontakta projekt ägaren.
