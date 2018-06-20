---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera objektägare
ms.openlocfilehash: 10d2a433253162847028e157b5bac47b23406469
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222119"
---
# <a name="managing-item-owners"></a>Hantera objektägare

Ägare till ett objekt i PowerShell-galleriet definieras av vem som publicerade artikeln i galleriet.
Ibland behöver dessa metadata hanteras utöver publicering inledande objektet, vilket innebär att metadata för ägare måste vara föränderliga själva objektet är inte.

Alla användare som har objekt är likvärdiga.
Det innebär att alla objekt ägare kan publicera en ny version av ett objekt. Det innebär också att alla objekt ägaren kan ta bort andra element-ägare.
Ingen ägare har flera utfärdare än andra ägare.

## <a name="setting-an-items-initial-owner"></a>Ange ett objekt inledande ägare

När ett nytt objekt publiceras till PowerShell-galleriet, definieras den ursprungliga ägaren av användaren som publicerade artikeln. Detta bestäms genom vars API nyckel användes i Publicera modul-cmdlet.

## <a name="adding-owners"></a>Lägga till ägare

När ett objekt har publicerats till PowerShell-galleriet, är det enkelt att bjuda in ytterligare användare att bli ägare till ett objekt.

1. [Logga in](https://powershellgallery.com/users/account/LogOn) i PowerShell-galleriet med det konto som är den nuvarande ägaren av ett objekt.
2. Navigera till ett objekt-sida på fliken 'Element', söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina objekt**](https://www.powershellgallery.com/account/Packages).
3. När inloggad som en artikel ägare, finns en hantera ägare länk till vänster på.
4. Ange användarnamnet för personen att lägga till som ägare och klicka på ”Lägg till'.
5. Ett e-postmeddelande skickas sedan till den nya Medägare som en inbjudan ska bli ägare till ett objekt.
6. När användaren klickar på länken, är de en fullständig Medägare med fullständig kontroll över ett objekt, inklusive möjligheten att ta bort andra användare som ägare.

**Obs**: tills den nya ägaren bekräftar ägarskapet, de *inte* visas som en ägare av ett objekt.
När du visar den **hantera ägare** sidan visas en ”väntar på godkännande” post i de aktuella ägarna.
Den inbjudan som kan tas bort; precis som andra ägare kan tas bort.
Den här processen att inbjudningar hindrar användare från att lägga till andra användare som ägare till sina objekt.

Observera att ”författarna” metadata är rent frihandsfigurer text. endast ”ägare” kontrolleras.


## <a name="removing-owners"></a>Ta bort ägare

När ett objekt har flera ägare och en måste tas bort, är processen enkel:

1. [Logga in](https://powershellgallery.com/users/account/LogOn) till PowerShell-galleriet med det konto som är den nuvarande ägaren av ett objekt.
2. Navigera till ett objekt-sida på fliken objekt, söker eller klicka på ditt användarnamn och sedan [ **Hantera Mina objekt**](https://www.powershellgallery.com/account/Packages).
3. När inloggad som en artikel ägare, finns det en länk för hantera ägare till vänster på;
4. Klicka på länken ”ta bort' bredvid ägaren som ska tas bort.



## <a name="transferring-item-ownership"></a>Överföra ägarskap för objektet

Vi hämta ibland supportärenden att överföra objektet ägarskap från en användare till en annan, men du kan nästan alltid utföra den själv.
Överföra ägarskap från en användare till en annan är helt enkelt en kombination av de två funktionerna som ovan.

1. Den nuvarande ägaren inbjuder den nya användaren ska bli en Medägare och den nya användaren accepterar inbjudan;
2. Den nya användaren tar bort den gamla användaren från listan över ägare.

Denna begäran har kommit i under några formulär, men processen fungerar på samma sätt.

- Objektet ägarskap ändras från en utvecklare till en annan
- Artikeln publicerades av misstag med fel konto


## <a name="orphaned-items"></a>Överblivna objekt

En sista scenariot har inträffat, men inte många gånger.
Objekt har blivit överblivna och det enda objekt ägare kontot kan inte användas för att lägga till nya ägare.
Här följer några exempel på det här scenariot:

- Ägarens konto är kopplat till en e-postadress som inte längre finns och att användaren har glömt sitt lösenord
- Registrerad ägare har lämnat företaget som producerar objektet och går inte att nå för att uppdatera objektet ägarskap
- På grund av ett fel som påverkar bara ett fåtal objekt finns objektet på något sätt ownerless på galleriet

PowerShell-galleriet administratörer har åtkomst till länken hantera ägare för ett objekt.
Om du är berättigat ägaren till ett objekt och kan inte nå den nuvarande ägaren för att få ägarskap behörigheter Använd länken Rapportera missbruk på galleriet för att nå PowerShell-galleriet administratörer.
Vi sedan följer en process för att verifiera ditt ägarskap för objektet.
Om vi anser att du ska vara ägare till objektet kommer att använda länken hantera ägare för objektet oss själva och skicka inbjudan ska bli ägare.
Vi kommer bara göra det när du har verifierat att du ska vara en ägare och processen för detta varierar beroende på omständigheter.
Ofta URL för objektet ska användas för att hitta ett sätt att kontakta Projektägaren, men vi kan också använda Twitter, e-post, eller på annat sätt för att kontakta Projektägaren.