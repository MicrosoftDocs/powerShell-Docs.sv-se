---
ms.date: 09/05/2018
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Kontoinställningar för PowerShell-galleriet
ms.openlocfilehash: b71c7f0658c24ec2eeddb050e48b777a37c11917
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87771795"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="ae801-103">Kontoinställningar för PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="ae801-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="ae801-104">Ditt PowerShell-galleriet-konto är ett offentligt synligt namn som är länkat till en identitet.</span><span class="sxs-lookup"><span data-stu-id="ae801-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="ae801-105">Identiteten är antingen ett Microsoft-ID, `user@hotmail.com` t `user@outlook.com` . ex., eller ett Azure Active Directory-konto (AAD).</span><span class="sxs-lookup"><span data-stu-id="ae801-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="ae801-106">PowerShell-galleriet innehåller följande konto inställningar:</span><span class="sxs-lookup"><span data-stu-id="ae801-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="ae801-107">E-postkontot som är kopplat till ditt PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="ae801-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="ae801-108">Alternativ för e-postaviseringar som skickas från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="ae801-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="ae801-109">Det användar konto som är associerat med ditt PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="ae801-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="ae801-110">Den bild som är kopplad till ditt PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="ae801-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="ae801-111">E-postadress</span><span class="sxs-lookup"><span data-stu-id="ae801-111">Email address</span></span>

<span data-ttu-id="ae801-112">E-postadressen är målet för PowerShell-galleriet-meddelanden.</span><span class="sxs-lookup"><span data-stu-id="ae801-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="ae801-113">Det behöver inte matcha inloggnings kontot.</span><span class="sxs-lookup"><span data-stu-id="ae801-113">It does not have to match the login account.</span></span> <span data-ttu-id="ae801-114">Du kan använda ett e-postkonto som du har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="ae801-114">You may use any email account you have access to.</span></span> <span data-ttu-id="ae801-115">Din e-postadress tillhandahålls aldrig direkt av PowerShell-galleriet till andra användare.</span><span class="sxs-lookup"><span data-stu-id="ae801-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Ändra e-postadress](media/managing-account/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="ae801-117">När du anger en ny e-postadress skickar PowerShell-galleriet e-postbekräftelsen till den adressen.</span><span class="sxs-lookup"><span data-stu-id="ae801-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="ae801-118">Verifierings-e-postmeddelandet innehåller en länk tillbaka till PowerShell-galleriet för att slutföra ändrings processen.</span><span class="sxs-lookup"><span data-stu-id="ae801-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="ae801-119">Tills du har slutfört verifierings processen skickas alla meddelanden till den tidigare adressen.</span><span class="sxs-lookup"><span data-stu-id="ae801-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="ae801-120">E-postmeddelanden</span><span class="sxs-lookup"><span data-stu-id="ae801-120">Email notifications</span></span>

<span data-ttu-id="ae801-121">PowerShell-galleriet innehåller följande meddelande alternativ:</span><span class="sxs-lookup"><span data-stu-id="ae801-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="ae801-122">Användarna kan kontakta mig via PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="ae801-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="ae801-123">Meddela mig när ett paket skickas till PowerShell-galleriet med mitt konto</span><span class="sxs-lookup"><span data-stu-id="ae801-123">Notify me when an package is pushed to the PowerShell Gallery using my account</span></span>

![Välj alternativ för e-postadress](media/managing-account/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="ae801-125">Som anges på sidan kan inte kritiska meddelanden från PowerShell-galleriet inaktive ras.</span><span class="sxs-lookup"><span data-stu-id="ae801-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="ae801-126">Dessa omfattar:</span><span class="sxs-lookup"><span data-stu-id="ae801-126">These include:</span></span>

- <span data-ttu-id="ae801-127">Säkerhets meddelanden</span><span class="sxs-lookup"><span data-stu-id="ae801-127">Security notifications</span></span>
- <span data-ttu-id="ae801-128">Meddelanden om konto hantering från PowerShell-galleriet administratörer</span><span class="sxs-lookup"><span data-stu-id="ae801-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="ae801-129">Aviseringar om testerna som körs av PowerShell-galleriet för de bidrag som du har gjort</span><span class="sxs-lookup"><span data-stu-id="ae801-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="ae801-130">Ändra ditt inloggnings konto</span><span class="sxs-lookup"><span data-stu-id="ae801-130">Change your login account</span></span>

<span data-ttu-id="ae801-131">Om du vill ändra inloggnings kontot måste du vara inloggad med det aktuella kontot.</span><span class="sxs-lookup"><span data-stu-id="ae801-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="ae801-132">Använd följande steg för att slutföra ändringen.</span><span class="sxs-lookup"><span data-stu-id="ae801-132">Use the following steps to complete the change.</span></span>

![Ändra inställningar för inloggnings konto](media/managing-account/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="ae801-134">Klicka på **Ändra konto**.</span><span class="sxs-lookup"><span data-stu-id="ae801-134">Click on **Change Account**.</span></span> <span data-ttu-id="ae801-135">Ett popup-fönster förklarar att ändringar av inloggnings kontot gäller för all användning av kontot i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ae801-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="ae801-136">Granska informationen och klicka sedan på **OK** för att fortsätta.</span><span class="sxs-lookup"><span data-stu-id="ae801-136">Review the information, then click **OK** to continue.</span></span>

   ![Ändrings bekräftelse – OK/Avbryt](media/managing-account/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="ae801-138">Du uppmanas sedan att logga in med det _nya kontot_.</span><span class="sxs-lookup"><span data-stu-id="ae801-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Logga in med det nya kontot](media/managing-account/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="ae801-140">När du klickar på **Nästa**visas ett meddelande om att du har loggat in med det aktuella kontot.</span><span class="sxs-lookup"><span data-stu-id="ae801-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="ae801-141">Klicka på **Logga ut och logga in med ett annat konto**.</span><span class="sxs-lookup"><span data-stu-id="ae801-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Logga ut och logga in med ett annat konto](media/managing-account/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="ae801-143">Ange lösen ordet för det nya kontot.</span><span class="sxs-lookup"><span data-stu-id="ae801-143">Enter the password of the new account.</span></span> <span data-ttu-id="ae801-144">När du har angett lösen ordet kommer du tillbaka till sidan konto inställningar som visar att inloggnings kontot har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="ae801-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>

## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="ae801-145">Aktivera tvåfaktorautentisering (2FA)</span><span class="sxs-lookup"><span data-stu-id="ae801-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="ae801-146">Tvåfaktorautentisering rekommenderas för alla användare som publicerar manuellt till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ae801-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="ae801-147">För att möjliggöra tvåfaktorautentisering måste inloggnings kontot ha minst två typer av autentisering registrerade.</span><span class="sxs-lookup"><span data-stu-id="ae801-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="ae801-148">Ett är ett lösen ord och de andra formulären kan vara:</span><span class="sxs-lookup"><span data-stu-id="ae801-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="ae801-149">Ett telefonnummer som kan ta emot SMS-meddelanden</span><span class="sxs-lookup"><span data-stu-id="ae801-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="ae801-150">Ett registrerat Authenticator-program, till exempel Microsoft Authenticator för din mobil telefon</span><span class="sxs-lookup"><span data-stu-id="ae801-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="ae801-151">Dessa former av autentisering måste konfigureras i din AAD-kontoinformation eller i säkerhets inställningarna för ditt Microsoft ID-konto.</span><span class="sxs-lookup"><span data-stu-id="ae801-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="ae801-152">När 2FA har Aktiver ATS måste du autentisera med hjälp av de konfigurerade formarna för autentisering varje gång du loggar in på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ae801-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ae801-153">Om du aktiverar tvåfaktorautentisering för PowerShell-galleriets platsen behöver du inte aktivera 2FA för all användning av ditt inloggnings konto.</span><span class="sxs-lookup"><span data-stu-id="ae801-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="ae801-154">Mer information finns i [om](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification)tvåstegsverifiering.</span><span class="sxs-lookup"><span data-stu-id="ae801-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="ae801-155">Ändra din profilbild</span><span class="sxs-lookup"><span data-stu-id="ae801-155">Change your profile picture</span></span>

<span data-ttu-id="ae801-156">PowerShell-galleriet förlitar sig på Gravatar för att lagra och visa den bild som är associerad med din profil.</span><span class="sxs-lookup"><span data-stu-id="ae801-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="ae801-157">Om du vill uppdatera din profil avbildning går du till [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="ae801-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
