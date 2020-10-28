---
ms.date: 09/11/2018
title: Skapa ett PowerShell-galleriet konto
description: Den här artikeln beskriver användar konto kraven för PowerShell-galleriet
ms.openlocfilehash: 24c7531e61128415a284d1b438b43f3af0d1053a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92662615"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="ac2fa-103">Skapa ett PowerShell-galleriet konto</span><span class="sxs-lookup"><span data-stu-id="ac2fa-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="ac2fa-104">Du måste skapa ett PowerShell-galleriet konto innan du publicerar något till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="ac2fa-105">PowerShell-galleriet konton måste vara länkade till ett e-postaktiverat inloggnings konto.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="ac2fa-106">Det här kontot kan vara ett Azure Active Directory konto eller ett Microsoft-ID, t. ex. ett e-postkonto från outlook.com eller hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="ac2fa-107">Om du vill skapa ett PowerShell-galleriet konto går du till [https://PowerShellGallery.com](https://PowerShellGallery.com) och klickar på **Logga** in som visas i följande bild.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrera nytt konto](media/creating-an-account/CreateAccount-Register.png)

<span data-ttu-id="ac2fa-109">Om du vill använda ett Azure Active Directory konto väljer du **arbets-eller skol konto** och loggar in med ditt konto.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-109">To use an Azure Active Directory account, select **Work or School Account** , and sign in with your account.</span></span> <span data-ttu-id="ac2fa-110">Om du vill använda ett Microsoft-ID väljer du **personligt konto** och loggar in.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="ac2fa-111">Därefter uppmanas du att skapa ett användar namn för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="ac2fa-112">Granska användnings villkoren och sekretess policyn, ange ett användar namn och klicka sedan på **Registrera** .</span><span class="sxs-lookup"><span data-stu-id="ac2fa-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register** .</span></span>

> [!NOTE]
> <span data-ttu-id="ac2fa-113">Det går inte att ändra konto namnet när det har skapats.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="ac2fa-114">Mer information finns i [Hantera paket ägare](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="ac2fa-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="ac2fa-115">Rekommenderade metoder för PowerShell-galleriet konton</span><span class="sxs-lookup"><span data-stu-id="ac2fa-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="ac2fa-116">Det är viktigt att aktivt övervaka det e-postkonto som används med ditt PowerShell-galleriet-konto.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="ac2fa-117">All kommunikation med ägare av PowerShell-galleriet-paket är via den här e-postadressen.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="ac2fa-118">Om PowerShell-galleriet Operations-teamet inte kan kontakta en paket ägare kan vi behöva ta bort ett paket.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="ac2fa-119">Organisationer som publicerar till PowerShell-galleriet ofta skapar ett unikt externt konto för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="ac2fa-120">Vi rekommenderar att du använder e-postvidarebefordran för att vidarebefordra meddelanden till en adress i din organisation.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="ac2fa-121">När flera ägare är associerade med ett paket skickas alla PowerShell-galleriet meddelanden till alla ägare.</span><span class="sxs-lookup"><span data-stu-id="ac2fa-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="ac2fa-122">Mer information finns i [Hantera paket ägare](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="ac2fa-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
