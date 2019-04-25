---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera paket ägare
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084155"
---
# <a name="managing-package-owners"></a>Hantera paket ägare

Ägarskap för ett paket i PowerShell-galleriet definieras av vem som publicerade paketet i galleriet.
Ibland måste dessa metadata hanteras utöver publicering initialt paket, vilket innebär att metadata som ägare måste vara föränderliga själva paketet är inte.

Alla paket ägare är peer-datorer.
Det innebär att alla paket-ägare kan publicera en ny version av ett paket. Det innebär också att alla paket-ägare kan ta bort paketets ägare.
Ingen ägare har mer behörighet än andra ägare.

## <a name="setting-a-packages-initial-owner"></a>Ange ett paket ursprunglig ägare

När ett nytt paket har publicerats i PowerShell-galleriet, har ursprunglig ägare definierats av användaren som publicerade paketet. Detta bestäms av vars API: et nyckel har använts i cmdlet Publish-Module.

## <a name="adding-owners"></a>Att lägga till ägare

När ett paket har publicerats i PowerShell-galleriet, är det enkelt att bjuda in fler användare att bli ägare till ett paket.

1. [Logga in](https://powershellgallery.com/users/account/LogOn) PowerShell-galleriet med det konto som är den nuvarande ägaren av ett paket.
2. Inloggningsinformationen för ett paket med hjälp av fliken ”Items”, söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina paket**](https://www.powershellgallery.com/account/Packages).
3. När du loggat in som ägare för ett paket, finns det en hantera ägare-länk på vänster sida för att klicka på.
4. Ange användarnamnet för personen att lägga till som ägare och klicka på ”Lägg till”.
5. Ett e-postmeddelande skickas sedan till den nya Medägare som en inbjudan att bli ägare till ett paket.
6. När användaren klickar på länken, är de fullständiga Medägare med fullständig kontroll över ett paket, inklusive möjligheten att ta bort andra användare som ägare.

**OBS**: Tills den nya ägaren bekräftar ägarskapet, de *inte* anges som ägare av ett paket.
När du visar den **hantera ägare** sidan visas en ”väntar på godkännande”-post i aktuell ägare.
Den inbjudan kan tas bort; precis som andra ägare kan tas bort.
Processen att inbjudningar förhindrar användare från att lägga till andra användare som ägare till sina paket.

Observera att ”författarna” metadata är helt och hållet Friform text. endast ”ägare” styrs.


## <a name="removing-owners"></a>Ta bort ägare

När ett paket har flera ägare och en måste tas bort, är processen enkel:

1. [Logga in](https://powershellgallery.com/users/account/LogOn) PowerShell-galleriet med det konto som är den nuvarande ägaren av ett paket;
2. Inloggningsinformationen för ett paket med paket-fliken, söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina paket**](https://www.powershellgallery.com/account/Packages).
3. När du loggat in som ägare för ett paket, finns det en länk för hantera ägare på vänster sida för att klicka på;
4. Klicka på länken ”ta bort' bredvid ägare som ska tas bort.



## <a name="transferring-package-ownership"></a>Överföra ägarskapet för paketet

Vi kommer ibland supportärenden att överföra äganderätten för paket från en användare till en annan, men du kan nästan alltid göra det själv.
Överföra ägarskapet från en användare till en annan är helt enkelt en kombination av de två funktionerna som ovan.

1. Den nuvarande ägaren bjuder in den nya användaren att bli en Medägare och den nya användaren accepterar inbjudan;
2. Den nya användaren tar bort den gamla användaren från listan över ägare.

Den här begäran har aktiverats under ett par formulär, men processen fungerar på samma.

- Paketet ägarskap ändras från en utvecklare till en annan
- Paketet publicerades av misstag använda fel konto


## <a name="orphaned-packages"></a>Överblivna paket

Ett senaste scenario har inträffat, men inte många gånger.
Paket har blivit överblivna och det enda kontot för paketet ägare kan inte användas för att lägga till nya ägare.
Här följer några exempel på det här scenariot:

- Ägarens konto är kopplat till en e-postadress som inte längre finns och att användaren har glömt sitt lösenord
- Registrerad ägare har lämnat företaget som tillverkar paketet och går inte att nå för att uppdatera paketet ägarskap
- På grund av ett fel som påverkar endast en handfull paket finns paketet på något sätt ownerless i galleriet

PowerShell-galleriet administratörer kan använda länken hantera ägare för valfritt paket.
Om du är berättigat ägaren av ett paket och inte går att nå den nuvarande ägaren för att få ägarskap behörigheter, använder du länken ”Rapportera missbruk' i galleriet för att nå administratörer för PowerShell-galleriet.
Vi sedan följer en process för att verifiera ditt ägarskap för paketet.
Om vi fastställer bör du vara ägare till paketet, vi använder länken hantera ägare för paketet skapar och skickar inbjudan att bli ägare.
Vi kommer endast göra detta när du har verifierat att du ska vara ägare och processen för detta varierar beroende på omständigheter.
Ofta vi använder paketets projekt-URL för att hitta ett sätt att kontakta Projektägaren, men vi kan också använda Twitter, e-post, eller på annat sätt för att kontakta Projektägaren.
