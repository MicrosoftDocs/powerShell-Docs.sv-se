---
ms.date: 09/11/2018
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapa ett konto med PowerShell-galleriet
ms.openlocfilehash: 08d18310d9e18b00bd9e22efcc552dfd29f8982c
ms.sourcegitcommit: e46b868f56f359909ff7c8230b1d1770935cce0e
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/13/2018
ms.locfileid: "45522851"
---
# <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="aef2d-103">Skapa ett konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="aef2d-103">Creating a PowerShell Gallery account</span></span>

<span data-ttu-id="aef2d-104">Du måste skapa ett PowerShell-galleriet-konto innan du publicerar något i PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="aef2d-104">You must create a PowerShell Gallery account before publishing anything to the PowerShell Gallery.</span></span>
<span data-ttu-id="aef2d-105">PowerShell-galleriet konton måste kopplas till en e-postaktiverade inloggningskonto.</span><span class="sxs-lookup"><span data-stu-id="aef2d-105">PowerShell Gallery accounts must be linked to an email-enabled login account.</span></span> <span data-ttu-id="aef2d-106">Det här kontot kan vara ett Azure Active Directory-konto eller ett Microsoft-ID, t.ex. ett e-postkonto från outlook.com eller hotmail.com.</span><span class="sxs-lookup"><span data-stu-id="aef2d-106">This account can be an Azure Active Directory account or a Microsoft ID, like an email account from outlook.com or hotmail.com.</span></span>

<span data-ttu-id="aef2d-107">Om du vill skapa ett PowerShell-galleriet-konto går du till [ https://PowerShellGallery.com ](https://PowerShellGallery.com) och klicka på **logga in** enligt följande bild.</span><span class="sxs-lookup"><span data-stu-id="aef2d-107">To create a PowerShell Gallery account, go to [https://PowerShellGallery.com](https://PowerShellGallery.com) and click on **Sign in** as shown in the following image.</span></span>

![Registrera nytt konto](../../Images/CreateAccount-Register.png)

<span data-ttu-id="aef2d-109">Om du vill använda ett Azure Active Directory-konto, Välj **arbets- eller Skolkonto**, och logga in med ditt konto.</span><span class="sxs-lookup"><span data-stu-id="aef2d-109">To use an Azure Active Directory account, select **Work or School Account**, and sign in with your account.</span></span> <span data-ttu-id="aef2d-110">Om du vill använda ett Microsoft-ID, Välj **personligt konto** och logga in.</span><span class="sxs-lookup"><span data-stu-id="aef2d-110">To use a Microsoft ID, choose **Personal Account** and sign in.</span></span>

<span data-ttu-id="aef2d-111">Därefter uppmanas du att skapa ett användarnamn för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="aef2d-111">Next, you are prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="aef2d-112">Granska användningsvillkor och sekretesspolicy, ange ett användarnamn och klicka sedan på **registrera**.</span><span class="sxs-lookup"><span data-stu-id="aef2d-112">Review the Terms of Use and Privacy Policy, enter a username, and then click **Register**.</span></span>

> [!NOTE]
> <span data-ttu-id="aef2d-113">Namnet på kontot kan inte ändras när den har skapats.</span><span class="sxs-lookup"><span data-stu-id="aef2d-113">The account name cannot be changed once it is created.</span></span> <span data-ttu-id="aef2d-114">Mer information finns i [hantera objektägare](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="aef2d-114">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="aef2d-115">Rekommenderade metoder för konton med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="aef2d-115">Recommended practices for PowerShell Gallery accounts</span></span>

<span data-ttu-id="aef2d-116">Det är viktigt att övervaka aktivt e-postkontot som används med ditt konto med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="aef2d-116">It's important to actively monitor the email account used with your PowerShell Gallery account.</span></span> <span data-ttu-id="aef2d-117">All kommunikation med ägare av objekt PowerShell-galleriet är via e-postadressen.</span><span class="sxs-lookup"><span data-stu-id="aef2d-117">All communication with owners of PowerShell Gallery items is through this email address.</span></span> <span data-ttu-id="aef2d-118">Om PowerShell-galleriet driftsteamet kan inte kontakta ägare objekt, kan vi behöva ta bort ett objekt.</span><span class="sxs-lookup"><span data-stu-id="aef2d-118">If the PowerShell Gallery Operations team is unable to contact an item owner, we may be required to delete an item.</span></span>

<span data-ttu-id="aef2d-119">Organisationer som publicerar till PowerShell-galleriet ofta skapa en unik externt konto för detta ändamål.</span><span class="sxs-lookup"><span data-stu-id="aef2d-119">Organizations that publish to the PowerShell Gallery often create a unique external account for that purpose.</span></span> <span data-ttu-id="aef2d-120">Vi rekommenderar att du använder vidarebefordra e-post för att vidarebefordra meddelanden till en adress inom din organisation.</span><span class="sxs-lookup"><span data-stu-id="aef2d-120">We recommend you use email forwarding to forward notifications to an address within your organization.</span></span>

<span data-ttu-id="aef2d-121">När flera ägare är associerad med ett objekt, skickas meddelanden för alla PowerShell-galleriet för alla användare.</span><span class="sxs-lookup"><span data-stu-id="aef2d-121">When multiple owners are associated with an item, all PowerShell Gallery notifications are sent to all owners.</span></span> <span data-ttu-id="aef2d-122">Mer information finns i [hantera objektägare](managing-item-owners.md).</span><span class="sxs-lookup"><span data-stu-id="aef2d-122">For more information, see [Managing Item Owners](managing-item-owners.md).</span></span>
