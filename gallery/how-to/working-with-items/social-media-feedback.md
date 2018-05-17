---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skicka Feedback via sociala medier eller kommentarer
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Skicka Feedback via sociala medier eller kommentarer

Powershell-galleriet stöder två metoder för användare med offentliga feedback om ett objekt:

- Använd länkarna på den vänstra kanten ”delar” ett objekt i Facebook, LinkedIn och Twitter sociala medier platser;
- Använd funktionen kommentar lämna kommentarer om ett objekt och Tillåt redigerare att bevaka för kommentarer om objekt som de publicerar.

## <a name="social-media-feedback"></a>Sociala medier Feedback

På vänster sida av sidan för varje objekt i PowerShell-galleriet finns länkar till Facebook, LinkedIn och Twitter.
Klicka på länkarna öppnas webbplatsen sociala medier, och att snabbt dela en länk till objektet.

Användarna måste logga in till webbplatsen som de har valt för att kunna dela PowerShell galleriobjektet.

Användarna uppmanas att göra om de hitta ett objekt är något de skulle rekommendera andra.
PowerShell-galleriet kontrollerar varje plats för sociala medier för ”resurser” på objektet och visa hur många gånger som objektet har delat i var och en av platserna sociala medier.
Eftersom det visar antalet gånger som något har delats blir systemkodsidan andra användare som ”liking”-objektet.


## <a name="comments"></a>Kommentar

PowerShell-galleriet använder tjänsten LiveFyre så att användarna kan kommentera objekt.
Användare som har rekommendationer eller feedback kan använda den här funktionen för att ge feedback som är synliga för alla som besöker sidan artikel.
Objektet ägare kan följa denna feedback och meddelas när någon publicerar en kommentar.

Systemets kommentar baseras på LiveFyre, vilket är en separat tjänst som inte hanteras av Microsoft och kräver unika inloggning som ska användas.
Första gången du väljer att lämna en kommentar eller följa kommentarer på ett av objekten, uppmanas du att skapa ett LiveFyre-konto.

Om du har skapat ett konto för LiveFyre loggat in kan du skapa en kommentar som ger feedback på objektet och klicka sedan på ”... Post comment” Kommentaren visas inte direkt.
Kommentarer till galleriobjekt är kontrollerade administratörer PowerShell-galleriet och alla inlägg granskas av kontrollanten innan du publicerade och synliga för andra.
Vår i Kontrollera kommentarerna syftar till att säkerställa att de överensstämmer med offentliga beteende som är konsekventa med PowerShell-galleriet [användningsvillkoren](https://www.powershellgallery.com/policies/Terms).

Objektet ägare uppmuntras att följa kommentarer som upp på LiveFyre.
Krävs ett LiveFyre konto och det rekommenderas att använda samma e-postadress som du använder för att publicera objektet i LiveFyre.
Logga in på LiveFyre om du vill följa kommentarer och navigera till ett objekt där du räknas som en ägare.
Under rutan kommentarer längst ned på varje objekt kommer du se ”+ följer”.
När du klickar på den här skickar LiveFyre ett e-postmeddelande till registrerade e-postadressen tid nya synpunkter på objektet.