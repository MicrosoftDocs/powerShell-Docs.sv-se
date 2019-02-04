---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa ett konto med PowerShell-galleriet
ms.openlocfilehash: e4cf73edb03267cff6bbcc0cf3b754225e45be9f
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685272"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="2d2db-103">Skapa ett konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="2d2db-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="2d2db-104">Du måste skapa ett PowerShell-galleriet-konto innan du publicerar något i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="2d2db-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="2d2db-105">PowerShell-galleriet konton måste kopplas till en e-postaktiverade inloggningskonto.</span><span class="sxs-lookup"><span data-stu-id="2d2db-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="2d2db-106">Det här kontot kan vara ett Azure Active Directory-konto eller ett Microsoft-ID, t.ex. ett e-postkonto från outlook.com eller hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="2d2db-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="2d2db-107">Om du vill skapa ett PowerShell-galleriet-konto går du till [ https://PowerShellGallery.com ](https://PowerShellGallery.com) och klicka på **logga in** enligt följande bild.</span><span class="sxs-lookup"><span data-stu-id="2d2db-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrera nytt konto](../../Images/CreateAccount-Register.png)

<span data-ttu-id="2d2db-109">Om du vill använda ett Azure Active Directory-konto, Välj **arbets- eller Skolkonto**, och logga in med ditt konto.</span><span class="sxs-lookup"><span data-stu-id="2d2db-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="2d2db-110">Om du vill använda ett Microsoft-ID, Välj **personligt konto** och logga in.</span><span class="sxs-lookup"><span data-stu-id="2d2db-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="2d2db-111">Därefter uppmanas du att skapa ett användarnamn för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="2d2db-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="2d2db-112">Granska användningsvillkor och sekretesspolicy, ange ett användarnamn och klicka sedan på **registrera**.</span><span class="sxs-lookup"><span data-stu-id="2d2db-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="2d2db-113">Namnet på kontot kan inte ändras när den har skapats.</span><span class="sxs-lookup"><span data-stu-id="2d2db-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="2d2db-114">Mer information finns i [hantera paket ägare](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="2d2db-114">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="2d2db-115">Rekommenderade metoder för konton med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="2d2db-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="2d2db-116">Det är viktigt att övervaka aktivt e-postkontot som används med ditt konto med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="2d2db-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="2d2db-117">All kommunikation med ägare av PowerShell-galleriet paket är via e-postadressen.</span><span class="sxs-lookup"><span data-stu-id="2d2db-117">All communication with owners of PowerShell Gallery packages is through this email address.</span></span> <span data-ttu-id="2d2db-118">Om PowerShell-galleriet driftsteamet kan inte kontakta en paketets ägare, kan vi behöva ta bort ett paket.</span><span class="sxs-lookup"><span data-stu-id="2d2db-118">If the PowerShell Gallery Operations team is unable to contact a package owner, we may be required to delete a package.</span></span>

<span data-ttu-id="2d2db-119">Organisationer som publicerar till PowerShell-galleriet ofta skapa en unik externt konto för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="2d2db-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="2d2db-120">Vi rekommenderar att du använder vidarebefordra e-post för att vidarebefordra meddelanden till en adress inom din organisation.</span><span class="sxs-lookup"><span data-stu-id="2d2db-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="2d2db-121">När flera ägare är associerad med ett paket, skickas meddelanden för alla PowerShell-galleriet för alla användare.</span><span class="sxs-lookup"><span data-stu-id="2d2db-121">When multiple owners are associated with a package, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="2d2db-122">Mer information finns i [hantera paket ägare](managing-package-owners.md).</span><span class="sxs-lookup"><span data-stu-id="2d2db-122">For more information, see [Managing Package Owners](managing-package-owners.md).</span></span>
