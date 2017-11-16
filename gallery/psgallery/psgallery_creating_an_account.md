---
ms.date: 2017-06-12
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Skapar ett konto med PowerShell-galleriet
ms.openlocfilehash: e21575320f220c1ba7ecd9bd464a814b3ebf49d9
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
## <a name="creating-a-powershell-gallery-account"></a><span data-ttu-id="453ce-103">Skapar ett konto med PowerShell-galleriet</span><span class="sxs-lookup"><span data-stu-id="453ce-103">Creating a PowerShell Gallery Account</span></span>

<span data-ttu-id="453ce-104">En PowerShell-galleriet måste vara konto innan du publicerar något till PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="453ce-104">A PowerShell Gallery account must be established before publishing anything to the PowerShell Gallery.</span></span> <span data-ttu-id="453ce-105">PowerShell-galleriet konton måste kopplas till ett e-postaktiverade Azure Active Directory-konto eller ett Microsoft-konto för e-post (med en domän till outlook.com, hotmail.com osv.)</span><span class="sxs-lookup"><span data-stu-id="453ce-105">The PowerShell Gallery accounts must be linked to an Azure Active Directory email-enabled account, or a Microsoft email account (with a domain of outlook.com, hotmail.com, etc.)</span></span>

<span data-ttu-id="453ce-106">Om du vill skapa ett PowerShell-galleriet-konto går du till https://PowerShellGallery.com och klicka på ”registrera” (se bilden nedan).</span><span class="sxs-lookup"><span data-stu-id="453ce-106">To create a PowerShell Gallery account, go to https://PowerShellGallery.com and click on "Register" (see the image below).</span></span> 

![Registrera nytt konto](./images/CreatingAccount-Register.png)

<span data-ttu-id="453ce-108">Välj ”arbets eller Skolkonto” om du vill använda ett Azure Active Directory-konto och logga in med ditt konto på nästa sida.</span><span class="sxs-lookup"><span data-stu-id="453ce-108">In the next page, to use an Azure Active Directory account, select "Work or School Account", and log in with your account.</span></span> <span data-ttu-id="453ce-109">Välj ”personliga konto” om du vill använda ett Microsoft-konto – till exempel en i en Hotmail.com eller Outlook.com domän - och logga in.</span><span class="sxs-lookup"><span data-stu-id="453ce-109">To use a Microsoft account - such as one in a Hotmail.com or Outlook.com domain - choose "Personal Account", and log in.</span></span> 

<span data-ttu-id="453ce-110">När du har loggat in uppmanas du att skapa ett användarnamn för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="453ce-110">Once you have logged in, you will be prompted to create a username for the PowerShell Gallery.</span></span> <span data-ttu-id="453ce-111">Granska användningsvillkoren och sekretesspolicyn för som är länkade i, ange ett användarnamn och klicka sedan på registrera.</span><span class="sxs-lookup"><span data-stu-id="453ce-111">Review the Terms of Use and Privacy Policy that are linked in, enter a username, and then click Register.</span></span>

<span data-ttu-id="453ce-112">Obs: Den här kontonamn kan inte ändras när den har skapats.</span><span class="sxs-lookup"><span data-stu-id="453ce-112">Note: This account name cannot be changed once it is created.</span></span>  
<span data-ttu-id="453ce-113">Se [hantera objekt ägare](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) för ytterligare information om det här.</span><span class="sxs-lookup"><span data-stu-id="453ce-113">See [Managing Item Owners](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) for additional details related to this.</span></span>

## <a name="recommended-practices-for-powershell-gallery-accounts"></a><span data-ttu-id="453ce-114">Rekommenderade metoder för PowerShell-galleriet konton</span><span class="sxs-lookup"><span data-stu-id="453ce-114">Recommended Practices for PowerShell Gallery Accounts</span></span>

<span data-ttu-id="453ce-115">Det är viktigt att e-postkontot som används med PowerShell-galleriet kontot övervakas aktivt.</span><span class="sxs-lookup"><span data-stu-id="453ce-115">It is important that the email account used with your PowerShell Gallery account be actively monitored.</span></span>
<span data-ttu-id="453ce-116">Alla communiction med ägare av PowerShell galleriobjekt är via e-postmeddelandet med den adress som är kopplad till ditt konto med PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="453ce-116">All communiction with owners of PowerShell Gallery items is through the email using the address associated with your PowerShell Gallery account.</span></span>
<span data-ttu-id="453ce-117">Om vi inte går att kontakta en artikel ägare, kan driftteamet behöva ta bort ett objekt i vissa fall.</span><span class="sxs-lookup"><span data-stu-id="453ce-117">If we are unable to contact an item owner, the Operations team may be required to delete an item under some circumstances.</span></span>

<span data-ttu-id="453ce-118">Organisationer som publicerar i PowerShell-galleriet ofta skapa ett unikt konto för detta ändamål i Outlook.com eller domänen med ett annat Microsoft-konto.</span><span class="sxs-lookup"><span data-stu-id="453ce-118">Organizations that publish to the PowerShell Gallery often create a unique account for that purpose in Outlook.com, or another Microsoft account domain.</span></span>
<span data-ttu-id="453ce-119">I många fall övervakas det kontot regelbundet inte.</span><span class="sxs-lookup"><span data-stu-id="453ce-119">In many cases that account is not regularly monitored.</span></span> <span data-ttu-id="453ce-120">Bästa praxis är i så fall att använda Outlook vidarebefordran för att skicka e-post till ett annat konto, vanligtvis en inom organisationen som ska övervakas av objektet ägare.</span><span class="sxs-lookup"><span data-stu-id="453ce-120">A best practice in that case is to use Outlook Forwarding to send email to another account, typically one within the organization, that will be monitored by the item owner(s).</span></span>

<span data-ttu-id="453ce-121">Om det finns flera ägare som är associerad med ett objekt, kommer all kommunikation som kommer från PowerShell-galleriet gå till alla ägare.</span><span class="sxs-lookup"><span data-stu-id="453ce-121">If there are multiple owners associated with an item, all communications that come from the PowerShell Gallery will go to all owners.</span></span>
<span data-ttu-id="453ce-122">Se [hantera objekt ägare](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) för mer information om hur du lägger till ägare till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="453ce-122">See [Managing Item Owners](https://msdn.microsoft.com/en-us/powershell/gallery/psgallery/managing-item-owners) for additional details on adding owners to an item.</span></span> 

