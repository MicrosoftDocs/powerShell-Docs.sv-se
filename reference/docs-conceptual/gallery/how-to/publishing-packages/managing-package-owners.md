---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Hantera paket ägare
ms.openlocfilehash: 72a3ff72818c5461c74d46de5689e2d6c59b19bf
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564677"
---
# <a name="managing-package-owners"></a><span data-ttu-id="0c1f9-103">Hantera paket ägare</span><span class="sxs-lookup"><span data-stu-id="0c1f9-103">Managing package owners</span></span>

<span data-ttu-id="0c1f9-104">Ägarskapet av ett paket i PowerShell-galleriet definieras av vem som publicerade paketet i galleriet.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="0c1f9-105">Ibland måste dessa metadata hanteras bortom den inledande paket publiceringen, vilket innebär att föränderligt måste vara medan själva paketet inte är det.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="0c1f9-106">Alla paket ägare är peer-datorer.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-106">All package owners are peers.</span></span>
<span data-ttu-id="0c1f9-107">Det innebär att alla paket ägare kan publicera en ny version av ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="0c1f9-108">Det innebär också att alla paket ägare kan ta bort alla andra paket ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="0c1f9-109">Ingen ägare har fler utfärdare än andra ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="0c1f9-110">Ange ett pakets initiala ägare</span><span class="sxs-lookup"><span data-stu-id="0c1f9-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="0c1f9-111">När ett nytt paket publiceras till PowerShell-galleriet definieras den ursprungliga ägaren av den användare som publicerade paketet.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="0c1f9-112">Detta bestäms av vars API-nyckel användes i Publishing-module-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="0c1f9-113">Lägga till ägare</span><span class="sxs-lookup"><span data-stu-id="0c1f9-113">Adding Owners</span></span>

<span data-ttu-id="0c1f9-114">När ett paket har publicerats till PowerShell-galleriet är det enkelt att bjuda in fler användare att bli ägare till ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="0c1f9-115">[Logga](https://powershellgallery.com/users/account/LogOn) in på PowerShell-galleriet med det konto som är den aktuella ägaren till ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="0c1f9-116">Gå till sidan paket genom att använda fliken objekt, söka eller klicka på ditt användar namn och sedan [**hantera mina paket**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="0c1f9-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="0c1f9-117">När du är inloggad som ett pakets ägare finns länken "Hantera ägare" på vänster sida för att klicka.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="0c1f9-118">Ange användar namnet för den person som ska läggas till som ägare och klicka på Lägg till.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="0c1f9-119">Ett e-postmeddelande skickas sedan till den nya medägaren som en inbjudan att bli ägare till ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="0c1f9-120">När användaren klickar på länken är de en fullständig samägare med fullständig kontroll över ett paket, inklusive möjligheten att ta bort andra användare som ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="0c1f9-121">**Obs!** tills den nya ägaren bekräftar ägarskapet visas de *inte* som ägare till ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="0c1f9-122">När du visar sidan **Hantera ägare** visas posten "väntar på godkännande" i aktuella ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="0c1f9-123">Den inbjudan kan tas bort. precis som andra ägare kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="0c1f9-124">Den här processen av inbjudningar förhindrar att användare lägger till andra användare felaktigt som ägare till sina paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="0c1f9-125">Observera att metadata för "författare" är en helt fri hands text. endast "ägare" kontrol leras.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>

## <a name="removing-owners"></a><span data-ttu-id="0c1f9-126">Ta bort ägare</span><span class="sxs-lookup"><span data-stu-id="0c1f9-126">Removing Owners</span></span>

<span data-ttu-id="0c1f9-127">När ett paket har flera ägare och en måste tas bort är processen enkel:</span><span class="sxs-lookup"><span data-stu-id="0c1f9-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="0c1f9-128">[Logga in](https://powershellgallery.com/users/account/LogOn) på PowerShell-galleriet med det konto som är den aktuella ägaren till ett paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="0c1f9-129">Gå till sidan paket på fliken paket, Sök eller klicka på ditt användar namn och [**hantera mina paket**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="0c1f9-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="0c1f9-130">När du är inloggad som ett pakets ägare finns länken "Hantera ägare" på vänster sida för att klicka.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="0c1f9-131">Klicka på länken Ta bort bredvid den ägare som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-131">Click the 'remove' link next to the owner to be removed.</span></span>

## <a name="transferring-package-ownership"></a><span data-ttu-id="0c1f9-132">Överför paket ägarskap</span><span class="sxs-lookup"><span data-stu-id="0c1f9-132">Transferring Package Ownership</span></span>

<span data-ttu-id="0c1f9-133">Vi får ibland support förfrågningar om att överföra paket ägarskap från en användare till en annan, men du kan nästan alltid göra detta själv.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="0c1f9-134">Överföring av ägarskap från en användare till en annan är bara en kombination av de två funktionerna ovan.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="0c1f9-135">Den aktuella ägaren bjuder in den nya användaren att bli en medägare och den nya användaren godkänner inbjudan.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="0c1f9-136">Den nya användaren tar bort den gamla användaren från listan över ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="0c1f9-137">Den här begäran har kommit under ett par formulär, men processen fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="0c1f9-138">Paketets ägarskap ändras från en utvecklare till en annan</span><span class="sxs-lookup"><span data-stu-id="0c1f9-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="0c1f9-139">Paketet publicerades av misstag med fel konto</span><span class="sxs-lookup"><span data-stu-id="0c1f9-139">The package was accidentally published using the wrong account</span></span>

## <a name="orphaned-packages"></a><span data-ttu-id="0c1f9-140">Överblivna paket</span><span class="sxs-lookup"><span data-stu-id="0c1f9-140">Orphaned Packages</span></span>

<span data-ttu-id="0c1f9-141">Ett sista scenario har inträffat, men inte många gånger.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="0c1f9-142">Paketen har blivit överblivna och det enda paket ägar kontot kan inte användas för att lägga till nya ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="0c1f9-143">Här följer några exempel på det här scenariot:</span><span class="sxs-lookup"><span data-stu-id="0c1f9-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="0c1f9-144">Ägarens konto är associerat med en e-postadress som inte längre finns och användaren har glömt sitt lösen ord</span><span class="sxs-lookup"><span data-stu-id="0c1f9-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="0c1f9-145">Den registrerade ägaren har lämnat företaget som tillverkar paketet och kan inte nås för att uppdatera paket ägarskapet</span><span class="sxs-lookup"><span data-stu-id="0c1f9-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="0c1f9-146">På grund av ett fel som endast har påverkat en fåtal av paket, är paketet insamlat på ett inaktivt sätt i galleriet</span><span class="sxs-lookup"><span data-stu-id="0c1f9-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="0c1f9-147">PowerShell-galleriet-administratörer kan komma åt länken "Hantera ägare" för alla paket.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="0c1f9-148">Om du är Rightful-ägare till ett paket och inte kan nå den aktuella ägaren för att få ägande behörighet, använder du länken "rapportera missbruk" i galleriet för att nå PowerShell-galleriet-administratörer.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="0c1f9-149">Vi följer sedan en process för att verifiera din ägande av paketet.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="0c1f9-150">Om vi fastställer att du ska vara ägare till paketet använder vi länken "Hantera ägare" för paketets skapar och skickar dig inbjudan att bli ägare.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="0c1f9-151">Vi kommer bara att göra detta när du har verifierat att du bör vara en ägare och processen för detta beror på omständigheter.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="0c1f9-152">Ofta kommer vi att använda paketets projekt-URL för att hitta ett sätt att kontakta projekt ägaren, men vi kan också använda Twitter, e-post eller andra sätt för att kontakta projekt ägaren.</span><span class="sxs-lookup"><span data-stu-id="0c1f9-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
