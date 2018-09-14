---
ms.date: 09/05/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: PowerShell-galleriet kontoinställningar
ms.openlocfilehash: dd7b8b3a99b5b7fbfec5d7f82b81dd6d5cfb906c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45523391"
---
# <a name="powershell-gallery-account-settings"></a><span data-ttu-id="356da-103">PowerShell-galleriet kontoinställningar</span><span class="sxs-lookup"><span data-stu-id="356da-103">PowerShell Gallery Account Settings</span></span>

<span data-ttu-id="356da-104">Ditt konto med PowerShell-galleriet är ett offentligt namn som är länkad till en identitet.</span><span class="sxs-lookup"><span data-stu-id="356da-104">Your PowerShell Gallery account is a publicly visible name that is linked to an identity.</span></span> <span data-ttu-id="356da-105">Det identitet som är antingen en Microsoft-ID, `user@hotmail.com` eller `user@outlook.com`, eller ett Azure Active Directory (AAD)-konto.</span><span class="sxs-lookup"><span data-stu-id="356da-105">That identity is either a Microsoft ID, like `user@hotmail.com` or `user@outlook.com`, or an Azure Active Directory (AAD) account.</span></span>

<span data-ttu-id="356da-106">PowerShell-galleriet innehåller följande kontoinställningar:</span><span class="sxs-lookup"><span data-stu-id="356da-106">The PowerShell Gallery provides the following account settings:</span></span>

- <span data-ttu-id="356da-107">E-postkontot som är associerade med ditt konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="356da-107">The email account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="356da-108">Alternativ för e-postmeddelanden som skickas från PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="356da-108">Options for email notifications sent from the PowerShell Gallery</span></span>
- <span data-ttu-id="356da-109">Det användarkonto som är associerat med ditt konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="356da-109">The user account associated with your PowerShell Gallery account</span></span>
- <span data-ttu-id="356da-110">Bild som är associerade med ditt konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="356da-110">The picture associated with your PowerShell Gallery account</span></span>

## <a name="email-address"></a><span data-ttu-id="356da-111">E-postadress</span><span class="sxs-lookup"><span data-stu-id="356da-111">Email address</span></span>

<span data-ttu-id="356da-112">E-postadressen är målet för PowerShell-galleriet meddelanden.</span><span class="sxs-lookup"><span data-stu-id="356da-112">The email address is the destination for PowerShell Gallery notifications.</span></span> <span data-ttu-id="356da-113">Det behöver inte matcha du inloggningskontot.</span><span class="sxs-lookup"><span data-stu-id="356da-113">It does not have to match the login account.</span></span> <span data-ttu-id="356da-114">Du kan använda valfri e-postkonto som du har åtkomst till.</span><span class="sxs-lookup"><span data-stu-id="356da-114">You may use any email account you have access to.</span></span> <span data-ttu-id="356da-115">Din e-postadress kommer aldrig direkt från PowerShell-galleriet till andra användare.</span><span class="sxs-lookup"><span data-stu-id="356da-115">Your email address is never directly provided by the PowerShell Gallery to other users.</span></span>

![Ändra e-postadress](../../Images/PSGallery_AcccountEmailAddress.png)

<span data-ttu-id="356da-117">När du anger en ny e-postadress skickar ett e-postmeddelande för verifiering i PowerShell-galleriet till adressen.</span><span class="sxs-lookup"><span data-stu-id="356da-117">When you enter a new email address, the PowerShell Gallery sends a verification mail to that address.</span></span> <span data-ttu-id="356da-118">Verifiering av e-postmeddelandet innehåller en länk tillbaka till PowerShell-galleriet för att slutföra ändringen.</span><span class="sxs-lookup"><span data-stu-id="356da-118">The verification mail contains a link back to the PowerShell Gallery to complete the change process.</span></span> <span data-ttu-id="356da-119">Förrän du har slutfört verifieringen skickas alla meddelanden till den tidigare adressen.</span><span class="sxs-lookup"><span data-stu-id="356da-119">Until you complete the verification process, all notifications are sent to the previous address.</span></span>

## <a name="email-notifications"></a><span data-ttu-id="356da-120">E-postaviseringar</span><span class="sxs-lookup"><span data-stu-id="356da-120">Email notifications</span></span>

<span data-ttu-id="356da-121">PowerShell-galleriet innehåller följande meddelandealternativ:</span><span class="sxs-lookup"><span data-stu-id="356da-121">PowerShell Gallery provides the following notification options:</span></span>

- <span data-ttu-id="356da-122">Användarna kan kontakta mig via PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="356da-122">Users can contact me through the PowerShell Gallery</span></span>
- <span data-ttu-id="356da-123">Meddela mig när ett objekt skickas till PowerShell-galleriet med hjälp av mitt konto</span><span class="sxs-lookup"><span data-stu-id="356da-123">Notify me when an item is pushed to the PowerShell Gallery using my account</span></span>

![Ändra e-postadress](../../Images/PSGallery_AccountEmailOptions.png)

<span data-ttu-id="356da-125">Enligt vad som anges på sidan, kan inte kritiska aviseringar från PowerShell-galleriet inaktiveras.</span><span class="sxs-lookup"><span data-stu-id="356da-125">As noted on the page, critical notifications from the PowerShell Gallery can't be disabled.</span></span>
<span data-ttu-id="356da-126">Dessa omfattar:</span><span class="sxs-lookup"><span data-stu-id="356da-126">These include:</span></span>

- <span data-ttu-id="356da-127">Säkerhetsmeddelanden</span><span class="sxs-lookup"><span data-stu-id="356da-127">Security notifications</span></span>
- <span data-ttu-id="356da-128">Hantering av kontomeddelanden från PowerShell-galleriet administratörer</span><span class="sxs-lookup"><span data-stu-id="356da-128">Account management notifications from PowerShell Gallery administrators</span></span>
- <span data-ttu-id="356da-129">Meddelanden om testerna som körs av PowerShell-galleriet för bidrag som du har gjort</span><span class="sxs-lookup"><span data-stu-id="356da-129">Notifications about the tests run by the PowerShell Gallery for submissions you have made</span></span>

## <a name="change-your-login-account"></a><span data-ttu-id="356da-130">Ändra ditt inloggningskonto</span><span class="sxs-lookup"><span data-stu-id="356da-130">Change your login account</span></span>

<span data-ttu-id="356da-131">Om du vill ändra inloggningskontot, måste du vara inloggad med det aktuella kontot.</span><span class="sxs-lookup"><span data-stu-id="356da-131">To change the login account, you must be signed in with the current account.</span></span> <span data-ttu-id="356da-132">Använd följande steg för att slutföra ändringen.</span><span class="sxs-lookup"><span data-stu-id="356da-132">Use the following steps to complete the change.</span></span>

![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountSettings.png)

1. <span data-ttu-id="356da-134">Klicka på **ändra konto**.</span><span class="sxs-lookup"><span data-stu-id="356da-134">Click on **Change Account**.</span></span> <span data-ttu-id="356da-135">Ett popup-fönster förklarar att ändrar du inloggningskontot gäller för all användning av kontot i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="356da-135">A pop-up window explains that changing the login account applies to all uses of that account in the PowerShell Gallery.</span></span> <span data-ttu-id="356da-136">Granska informationen och klicka sedan på **OK** att fortsätta.</span><span class="sxs-lookup"><span data-stu-id="356da-136">Review the information, then click **OK** to continue.</span></span>

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-1.png)

2. <span data-ttu-id="356da-138">Du uppmanas sedan att logga in med den _nytt konto_.</span><span class="sxs-lookup"><span data-stu-id="356da-138">You are then prompted to sign in using the _new account_.</span></span>

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-2.png)

3. <span data-ttu-id="356da-140">När du klickar på **nästa**, visas ett meddelande att du har loggat in med det aktuella kontot.</span><span class="sxs-lookup"><span data-stu-id="356da-140">When you click **Next**, you see a message that you are signed in using the current account.</span></span>
   <span data-ttu-id="356da-141">Klicka på **logga ut och logga in med ett annat konto**.</span><span class="sxs-lookup"><span data-stu-id="356da-141">Click **Sign out and sign in with a different account**.</span></span>

   ![Kontoinställningar för inloggning](../../Images/PSGallery_LoginAccountChange-3.png)

4. <span data-ttu-id="356da-143">Ange lösenordet för det nya kontot.</span><span class="sxs-lookup"><span data-stu-id="356da-143">Enter the password of the new account.</span></span> <span data-ttu-id="356da-144">När du har angett lösenordet, kommer du tillbaka till sidan kontoinställningar som visar att du inloggningskontot har uppdaterats.</span><span class="sxs-lookup"><span data-stu-id="356da-144">After entering the password, you are returned to the Account Settings page showing you that the login account has been updated.</span></span>


## <a name="enable-two-factor-authentication-2fa"></a><span data-ttu-id="356da-145">Aktivera tvåfaktorautentisering (2FA)</span><span class="sxs-lookup"><span data-stu-id="356da-145">Enable Two-Factor Authentication (2FA)</span></span>

<span data-ttu-id="356da-146">Tvåfaktorautentisering rekommenderas för alla användare som publicerar manuellt i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="356da-146">Two-factor authentication is recommended for all users who publish manually to the PowerShell Gallery.</span></span> <span data-ttu-id="356da-147">Om du vill aktivera tvåfaktorsautentisering måste du inloggningskontot ha minst två typer av autentisering som har registrerats.</span><span class="sxs-lookup"><span data-stu-id="356da-147">To enable two-factor authentication, the login account must have at least two forms of authentication registered.</span></span> <span data-ttu-id="356da-148">Ett är ett lösenord och andra former kan vara:</span><span class="sxs-lookup"><span data-stu-id="356da-148">One is a password and the other forms can be:</span></span>

- <span data-ttu-id="356da-149">Ett telefonnummer som kan ta emot textmeddelanden</span><span class="sxs-lookup"><span data-stu-id="356da-149">A phone number that can receive text messages</span></span>
- <span data-ttu-id="356da-150">En registrerad authenticator-program, till exempel Microsoft Authenticator för din mobiltelefon</span><span class="sxs-lookup"><span data-stu-id="356da-150">A registered authenticator application, such as Microsoft Authenticator for your mobile phone</span></span>

<span data-ttu-id="356da-151">Dessa typer av autentisering måste konfigureras i din AAD-kontoinformation eller i säkerhetsinställningarna för Microsoft-ID-konto.</span><span class="sxs-lookup"><span data-stu-id="356da-151">These forms of authentication must be configured in your AAD account information or in your Microsoft ID Account Security settings.</span></span>

<span data-ttu-id="356da-152">När 2FA är aktiverad, måste du autentiseras med de konfigurerade formerna av autentisering varje gång du loggar in på PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="356da-152">Once 2FA is enabled, you are required to authenticate using the configured forms of authentication every time you sign in to the PowerShell Gallery.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="356da-153">Aktivera tvåfaktorsautentisering för PowerShell-galleriet platsen behöver du inte att aktivera 2FA för all användning av ditt inloggningskonto.</span><span class="sxs-lookup"><span data-stu-id="356da-153">Enabling two-factor authentication for the PowerShell Gallery site does not require you to enable 2FA for all uses of your login account.</span></span> <span data-ttu-id="356da-154">Mer information finns i [om tvåstegsverifiering](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span><span class="sxs-lookup"><span data-stu-id="356da-154">For more information, see [About two-step verification](https://support.microsoft.com/help/12408/microsoft-account-about-two-step-verification).</span></span>

## <a name="change-your-profile-picture"></a><span data-ttu-id="356da-155">Ändra din profilbild</span><span class="sxs-lookup"><span data-stu-id="356da-155">Change your profile picture</span></span>

<span data-ttu-id="356da-156">PowerShell-galleriet bygger på Gravatar att lagra och visa en bild som är associerade med din profil.</span><span class="sxs-lookup"><span data-stu-id="356da-156">The PowerShell Gallery relies on Gravatar to store and display the picture associated with your profile.</span></span> <span data-ttu-id="356da-157">Om du vill uppdatera din profilbild, besök [Gravatar.com](http://www.gravatar.com/).</span><span class="sxs-lookup"><span data-stu-id="356da-157">To update your profile image, visit [Gravatar.com](http://www.gravatar.com/).</span></span>
