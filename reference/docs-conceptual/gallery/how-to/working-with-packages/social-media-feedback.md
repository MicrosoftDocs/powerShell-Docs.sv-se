---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Ge feedback via sociala medier eller kommentarer
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328758"
---
# <a name="providing-feedback-via-social-media-or-comments"></a>Ge feedback via sociala medier eller kommentarer

PowerShell-galleriet har stöd för två sätt för användare att tillhandahålla offentlig feedback i ett paket:

- Använd länkarna till vänster om du vill dela ett paket på Facebook-, LinkedIn-eller Twitter-sociala medie platser.
- Använd kommentar funktionen för att publicera kommentarer om ett paket och för att tillåta att författare tittar på kommentarer om paket som publicerats.

## <a name="social-media-feedback"></a>Feedback från sociala medier

På vänster sida av sidan för varje paket i PowerShell-galleriet finns det länkar till Facebook, LinkedIn och Twitter.
Om du klickar på de här länkarna öppnas webbplatsen för sociala medier och du får snabbt dela en länk till paketet.

Användarna måste logga in på den plats som de har valt för att kunna dela PowerShell-galleriet-paketet.

Användarna uppmanas att göra detta om de upptäcker att ett paket är något som de rekommenderar till andra.
Den PowerShell-galleriet kommer att kontrol lera om det finns "resurser" i paketet och visa hur många gånger paketet har delats på var och en av de sociala media platserna.
Eftersom detta bara visar hur många gånger något har delats, kommer det att tolkas som andra användare som "gilla"-paketet.

## <a name="comments"></a>Kommentarer

> [!IMPORTANT]
> Livefyre-kommentarer tillhandahålls av en tredjepartsleverantör och stöds inte längre.
> Livefyre-kommentarer kommer inte längre vara tillgängliga på PowerShell-galleriet med start 05/01/2019. 

PowerShell-galleriet använder LiveFyre-tjänsten för att tillåta användare att kommentera paket.
Användare som har rekommendationer eller feedback kan använda den här funktionen för att ge feedback som är synlig för alla som besöker paket sidan.
Paket ägare kan följa den här feedbacken och meddelas när någon publicerar en kommentar.

Kommentar systemet baseras på LiveFyre, som är en separat tjänst som inte hanteras av Microsoft och som kräver att unika inloggningar används.
Första gången du väljer att lämna en kommentar eller följa kommentarer om ett av dina paket, uppmanas du att skapa ett LiveFyre-konto.

Om du har skapat ett LiveFyre-konto och loggat in, kan du skapa en kommentar som ger feedback om paketet och sedan klicka på "Skicka kommentar..." Kommentaren visas inte omedelbart.
Kommentarer för Galleri paket förvaras av PowerShell-galleriet-administratörer och alla inlägg granskas av moderatorerna innan de publiceras och visas för andra.
Syftet med att kontrol lera kommentarerna är att se till att de överensstämmer med det offentliga beteendet i överensstämmelse med PowerShell-galleriet [användnings villkor](https://www.powershellgallery.com/policies/Terms).

Paket ägare uppmanas att följa kommentarer som publiceras i LiveFyre.
Ett LiveFyre-konto krävs och vi rekommenderar att du använder samma e-postadress som du använder för att publicera ditt paket i LiveFyre.
Om du vill följa kommentarer loggar du in på LiveFyre och navigerar till alla paket där du visas som ägare.
Under kommentars rutan längst ned i varje paket visas "+ Följ".
När du klickar på det här skickar LiveFyre ett e-postmeddelande till den registrerade e-postadressen varje gång nya kommentarer görs i paketet.
