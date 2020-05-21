---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Kontoinställningar för PowerShell-galleriet
ms.openlocfilehash: 7f67311b42123f247a00a9c7a5bf775685b64d48
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83560465"
---
# <a name="powershell-gallery-account-settings"></a>Kontoinställningar för PowerShell-galleriet

Ditt PowerShell-galleriet-konto är ett offentligt synligt namn som är länkat till en identitet. Identiteten är antingen ett Microsoft-ID, `user@hotmail.com` t `user@outlook.com` . ex., eller ett Azure Active Directory-konto (AAD).

PowerShell-galleriet innehåller följande konto inställningar:

- E-postkontot som är kopplat till ditt PowerShell-galleriet konto
- Alternativ för e-postaviseringar som skickas från PowerShell-galleriet
- Det användar konto som är associerat med ditt PowerShell-galleriet konto
- Den bild som är kopplad till ditt PowerShell-galleriet konto

## <a name="email-address"></a>E-postadress

E-postadressen är målet för PowerShell-galleriet-meddelanden. Det behöver inte matcha inloggnings kontot. Du kan använda ett e-postkonto som du har åtkomst till. Din e-postadress tillhandahålls aldrig direkt av PowerShell-galleriet till andra användare.

![Ändra e-postadress](media/managing-account/PSGallery_AcccountEmailAddress.png)

När du anger en ny e-postadress skickar PowerShell-galleriet e-postbekräftelsen till den adressen. Verifierings-e-postmeddelandet innehåller en länk tillbaka till PowerShell-galleriet för att slutföra ändrings processen. Tills du har slutfört verifierings processen skickas alla meddelanden till den tidigare adressen.

## <a name="email-notifications"></a>E-postmeddelanden

PowerShell-galleriet innehåller följande meddelande alternativ:

- Användarna kan kontakta mig via PowerShell-galleriet
- Meddela mig när ett paket skickas till PowerShell-galleriet med mitt konto

![Ändra e-postadress](media/managing-account/PSGallery_AccountEmailOptions.png)

Som anges på sidan kan inte kritiska meddelanden från PowerShell-galleriet inaktive ras.
Dessa omfattar:

- Säkerhets meddelanden
- Meddelanden om konto hantering från PowerShell-galleriet administratörer
- Aviseringar om testerna som körs av PowerShell-galleriet för de bidrag som du har gjort

## <a name="change-your-login-account"></a>Ändra ditt inloggnings konto

Om du vill ändra inloggnings kontot måste du vara inloggad med det aktuella kontot. Använd följande steg för att slutföra ändringen.

![Inställningar för inloggnings konto](media/managing-account/PSGallery_LoginAccountSettings.png)

1. Klicka på **Ändra konto**. Ett popup-fönster förklarar att ändringar av inloggnings kontot gäller för all användning av kontot i PowerShell-galleriet. Granska informationen och klicka sedan på **OK** för att fortsätta.

   ![Inställningar för inloggnings konto](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. Du uppmanas sedan att logga in med det _nya kontot_.

   ![Inställningar för inloggnings konto](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. När du klickar på **Nästa**visas ett meddelande om att du har loggat in med det aktuella kontot.
   Klicka på **Logga ut och logga in med ett annat konto**.

   ![Inställningar för inloggnings konto](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. Ange lösen ordet för det nya kontot. När du har angett lösen ordet kommer du tillbaka till sidan konto inställningar som visar att inloggnings kontot har uppdaterats.

## <a name="enable-two-factor-authentication-2fa"></a>Aktivera tvåfaktorautentisering (2FA)

Tvåfaktorautentisering rekommenderas för alla användare som publicerar manuellt till PowerShell-galleriet. För att möjliggöra tvåfaktorautentisering måste inloggnings kontot ha minst två typer av autentisering registrerade. Ett är ett lösen ord och de andra formulären kan vara:

- Ett telefonnummer som kan ta emot SMS-meddelanden
- Ett registrerat Authenticator-program, till exempel Microsoft Authenticator för din mobil telefon

Dessa former av autentisering måste konfigureras i din AAD-kontoinformation eller i säkerhets inställningarna för ditt Microsoft ID-konto.

När 2FA har Aktiver ATS måste du autentisera med hjälp av de konfigurerade formarna för autentisering varje gång du loggar in på PowerShell-galleriet.

> [!IMPORTANT]
> Om du aktiverar tvåfaktorautentisering för PowerShell-galleriets platsen behöver du inte aktivera 2FA för all användning av ditt inloggnings konto. Mer information finns i [om](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)tvåstegsverifiering.

## <a name="change-your-profile-picture"></a>Ändra din profilbild

PowerShell-galleriet förlitar sig på Gravatar för att lagra och visa den bild som är associerad med din profil. Om du vill uppdatera din profil avbildning går du till [Gravatar.com](http://www.gravatar.com/).
