---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Ge Feedback via sociala medier eller kommentarer
ms.openlocfilehash: a7cdcc2ff2c18fb606d077adf0bdecf57c90703f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684355"
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Ge Feedback via sociala medier eller kommentarer

Powershell-galleriet stöder två metoder för användare med offentliga feedback på ett paket:

- Använd länkarna på den vänstra kanten ”dela” ett paket i Facebook, LinkedIn och Twitter sociala webbplatser;
- Använd funktionen kommentaren att publicera kommentarer för ett paket, så att redigerare att se upp för kommentarer på paket som de publicerar.

## <a name="social-media-feedback"></a>Sociala medier Feedback

Till vänster på sidan för varje paket i PowerShell-galleriet finns länkar till Facebook, LinkedIn och Twitter.
När du klickar på länkarna öppnas webbplatsen sociala medier och Tillåt att snabbt kunna dela en länk till paketet.

Användarna måste logga in på den plats som de har valt för att kunna dela paketets PowerShell-galleriet.

Användarna uppmanas att göra detta om de tycker att ett paket är något de skulle rekommendera andra.
PowerShell-galleriet kontrolleras varje plats för sociala medier för ”resurser” på paketet och visa hur många gånger det paketet har delats i var och en av webbplatser för sociala medier.
Eftersom detta visar antalet gånger som något har delats blir systemkodsidan andra användare som ”liking” paketet.


## <a name="comments"></a>Kommentar

PowerShell-galleriet använder tjänsten LiveFyre så att användarna kan kommentera paket.
Användare som har rekommendationer eller kommentarer kan använda den här funktionen för att ge feedback som är synlig för alla som besöker sidan package.
Paketet ägare kan följa denna feedback och meddelas när någon lägger upp en kommentar.

Kommentar systemet baseras på LiveFyre, som är en separat tjänst som inte hanteras av Microsoft och kräver unika inloggning som ska användas.
Första gången du väljer att lämna en kommentar eller följ kommentarer på en av dina paket, uppmanas du att skapa ett LiveFyre-konto.

Om du har skapat ett LiveFyre-konto och loggat in kan du skapa en kommentar som ger feedback om paketet, sedan klickar du på ”Skicka kommentar...” Kommentaren visas inte direkt.
Kommentarer för gallery-paket är kontrollerade av PowerShell-galleriet-administratörer och alla inlägg granskas av moderatorerna innan den publicerade och synliga för andra.
Vårt syfte i Kontrollera kommentarerna är att säkerställa att de överensstämmer med offentliga beteende som är konsekvent med PowerShell-galleriet [användningsvillkor](https://www.powershellgallery.com/policies/Terms).

Paketet ägare uppmuntras att följa kommentarer som publiceras på LiveFyre.
Ett LiveFyre-konto är obligatoriskt och bör använda samma e-postadress som du använder för att publicera ditt paket i LiveFyre.
Om du vill följa kommentarer, logga in på LiveFyre och navigera till alla paket som där du står som ägare.
Nedan i kommentarsfältet längst ned i varje paket kommer du se ”+ följer”.
När du klickar på det här skickar LiveFyre ett e-postmeddelande till den registrerade e-postadressen tid nya kommentar på förpackningen.
