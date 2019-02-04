---
ms.date: 09/05/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Kontoinställningar för PowerShell-galleriet
ms.openlocfilehash: ebe784ec5aae5ff3a4d444d12a168ef38aaef65f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687428"
---
# <a name="powershell-gallery-account-settings"></a>Kontoinställningar för PowerShell-galleriet

Ditt konto med PowerShell-galleriet är ett offentligt namn som är länkad till en identitet. Det identitet som är antingen en Microsoft-ID, `user@hotmail.com` eller `user@outlook.com`, eller ett Azure Active Directory (AAD)-konto.

PowerShell-galleriet innehåller följande kontoinställningar:

- E-postkontot som är associerade med ditt konto med PowerShell-galleriet
- Alternativ för e-postmeddelanden som skickas från PowerShell-galleriet
- Det användarkonto som är associerat med ditt konto med PowerShell-galleriet
- Bild som är associerade med ditt konto med PowerShell-galleriet

## <a name="email-address"></a>E-postadress

E-postadressen är målet för PowerShell-galleriet meddelanden. Det behöver inte matcha du inloggningskontot. Du kan använda valfri e-postkonto som du har åtkomst till. Din e-postadress kommer aldrig direkt från PowerShell-galleriet till andra användare.

![Ändra e-postadress](../../Images/PSGallery_AcccountEmailAddress.png)

När du anger en ny e-postadress skickar ett e-postmeddelande för verifiering i PowerShell-galleriet till adressen. Verifiering av e-postmeddelandet innehåller en länk tillbaka till PowerShell-galleriet för att slutföra ändringen. Förrän du har slutfört verifieringen skickas alla meddelanden till den tidigare adressen.

## <a name="email-notifications"></a>E-postaviseringar

PowerShell-galleriet innehåller följande meddelandealternativ:

- Användarna kan kontakta mig via PowerShell-galleriet
- Meddela mig när ett paket som skickas till PowerShell-galleriet med hjälp av mitt konto

![Ändra e-postadress](../../Images/PSGallery_AccountEmailOptions.png)

Enligt vad som anges på sidan, kan inte kritiska aviseringar från PowerShell-galleriet inaktiveras.
Dessa omfattar:

- Säkerhetsmeddelanden
- Hantering av kontomeddelanden från PowerShell-galleriet administratörer
- Meddelanden om testerna som körs av PowerShell-galleriet för bidrag som du har gjort

## <a name="change-your-login-account"></a>Ändra ditt inloggningskonto

Om du vill ändra inloggningskontot, måste du vara inloggad med det aktuella kontot. Använd följande steg för att slutföra ändringen.

![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountSettings.png)

1. Klicka på **ändra konto**. Ett popup-fönster förklarar att ändrar du inloggningskontot gäller för all användning av kontot i PowerShell-galleriet. Granska informationen och klicka sedan på **OK** att fortsätta.

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-1.png)

2. Du uppmanas sedan att logga in med den _nytt konto_.

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-2.png)

3. När du klickar på **nästa**, visas ett meddelande att du har loggat in med det aktuella kontot.
   Klicka på **logga ut och logga in med ett annat konto**.

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-3.png)

4. Ange lösenordet för det nya kontot. När du har angett lösenordet, kommer du tillbaka till sidan kontoinställningar som visar att du inloggningskontot har uppdaterats.


## <a name="enable-two-factor-authentication-2fa"></a>Aktivera tvåfaktorautentisering (2FA)

Tvåfaktorautentisering rekommenderas för alla användare som publicerar manuellt i PowerShell-galleriet. Om du vill aktivera tvåfaktorsautentisering måste du inloggningskontot ha minst två typer av autentisering som har registrerats. Ett är ett lösenord och andra former kan vara:

- Ett telefonnummer som kan ta emot textmeddelanden
- En registrerad authenticator-program, till exempel Microsoft Authenticator för din mobiltelefon

Dessa typer av autentisering måste konfigureras i din AAD-kontoinformation eller i säkerhetsinställningarna för Microsoft-ID-konto.

När 2FA är aktiverad, måste du autentiseras med de konfigurerade formerna av autentisering varje gång du loggar in på PowerShell-galleriet.

> [!IMPORTANT]
> Aktivera tvåfaktorsautentisering för PowerShell-galleriet platsen behöver du inte att aktivera 2FA för all användning av ditt inloggningskonto. Mer information finns i [om tvåstegsverifiering](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).

## <a name="change-your-profile-picture"></a>Ändra din profilbild

PowerShell-galleriet bygger på Gravatar att lagra och visa en bild som är associerade med din profil. Om du vill uppdatera din profilbild, besök [Gravatar.com](http://www.gravatar.com/).
