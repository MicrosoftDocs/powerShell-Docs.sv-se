---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera paket ägare
ms.openlocfilehash: 5cf26a7195ac446177cbb7f3a055e8e0a78569cc
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685979"
---
# <a name="managing-package-owners"></a><span data-ttu-id="3b3c1-103">Hantera paket ägare</span><span class="sxs-lookup"><span data-stu-id="3b3c1-103">Managing package owners</span></span>

<span data-ttu-id="3b3c1-104">Ägarskap för ett paket i PowerShell-galleriet definieras av vem som publicerade paketet i galleriet.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-104">Ownership of a package in the PowerShell Gallery is defined by who published the package to the gallery.</span></span>
<span data-ttu-id="3b3c1-105">Ibland måste dessa metadata hanteras utöver publicering initialt paket, vilket innebär att metadata som ägare måste vara föränderliga själva paketet är inte.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-105">Sometimes this metadata needs to be managed beyond the initial package publishing, which means the owner metadata needs to be mutable while the package itself is not.</span></span>

<span data-ttu-id="3b3c1-106">Alla paket ägare är peer-datorer.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-106">All package owners are peers.</span></span>
<span data-ttu-id="3b3c1-107">Det innebär att alla paket-ägare kan publicera en ny version av ett paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-107">This means any package owner can publish a new version of an package.</span></span> <span data-ttu-id="3b3c1-108">Det innebär också att alla paket-ägare kan ta bort paketets ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-108">It also means that any package owner can remove any other package owner.</span></span>
<span data-ttu-id="3b3c1-109">Ingen ägare har mer behörighet än andra ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-109">No owner has more authority than other owners.</span></span>

## <a name="setting-a-packages-initial-owner"></a><span data-ttu-id="3b3c1-110">Ange ett paket ursprunglig ägare</span><span class="sxs-lookup"><span data-stu-id="3b3c1-110">Setting a Package's Initial Owner</span></span>

<span data-ttu-id="3b3c1-111">När ett nytt paket har publicerats i PowerShell-galleriet, har ursprunglig ägare definierats av användaren som publicerade paketet.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-111">When a new package is published to PowerShell Gallery, the initial owner is defined by the user that published the package.</span></span> <span data-ttu-id="3b3c1-112">Detta bestäms av vars API: et nyckel har använts i cmdlet Publish-Module.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="3b3c1-113">Att lägga till ägare</span><span class="sxs-lookup"><span data-stu-id="3b3c1-113">Adding Owners</span></span>

<span data-ttu-id="3b3c1-114">När ett paket har publicerats i PowerShell-galleriet, är det enkelt att bjuda in fler användare att bli ägare till ett paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-114">Once a package has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of a package.</span></span>

1. <span data-ttu-id="3b3c1-115">[Logga in](https://powershellgallery.com/users/account/LogOn) PowerShell-galleriet med det konto som är den nuvarande ägaren av ett paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of a package.</span></span>
2. <span data-ttu-id="3b3c1-116">Inloggningsinformationen för ett paket med hjälp av fliken ”Items”, söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina paket**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-116">Navigate to a package page using the 'Items' tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="3b3c1-117">När du loggat in som ägare för ett paket, finns det en hantera ägare-länk på vänster sida för att klicka på.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-117">When logged on as an package's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="3b3c1-118">Ange användarnamnet för personen att lägga till som ägare och klicka på ”Lägg till”.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="3b3c1-119">Ett e-postmeddelande skickas sedan till den nya Medägare som en inbjudan att bli ägare till ett paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-119">An email is then sent to the new co-owner, as an invitation to become an owner of a package.</span></span>
6. <span data-ttu-id="3b3c1-120">När användaren klickar på länken, är de fullständiga Medägare med fullständig kontroll över ett paket, inklusive möjligheten att ta bort andra användare som ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-120">Once that user clicks the link, they are a full co-owner with full control over a package, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="3b3c1-121">**OBS**: Tills den nya ägaren bekräftar ägarskapet, de *inte* anges som ägare av ett paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of a package.</span></span>
<span data-ttu-id="3b3c1-122">När du visar den **hantera ägare** sidan visas en ”väntar på godkännande”-post i aktuell ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="3b3c1-123">Den inbjudan kan tas bort; precis som andra ägare kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="3b3c1-124">Processen att inbjudningar förhindrar användare från att lägga till andra användare som ägare till sina paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-124">This process of invitations prevents users from falsely adding other users as owners of their packages.</span></span>

<span data-ttu-id="3b3c1-125">Observera att ”författarna” metadata är helt och hållet Friform text. endast ”ägare” styrs.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="3b3c1-126">Ta bort ägare</span><span class="sxs-lookup"><span data-stu-id="3b3c1-126">Removing Owners</span></span>

<span data-ttu-id="3b3c1-127">När ett paket har flera ägare och en måste tas bort, är processen enkel:</span><span class="sxs-lookup"><span data-stu-id="3b3c1-127">When a package has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="3b3c1-128">[Logga in](https://powershellgallery.com/users/account/LogOn) PowerShell-galleriet med det konto som är den nuvarande ägaren av ett paket;</span><span class="sxs-lookup"><span data-stu-id="3b3c1-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of a package;</span></span>
2. <span data-ttu-id="3b3c1-129">Inloggningsinformationen för ett paket med paket-fliken, söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina paket**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="3b3c1-129">Navigate to a package page using the Packages tab, searching, or clicking your username and then [**Manage My Packages**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="3b3c1-130">När du loggat in som ägare för ett paket, finns det en länk för hantera ägare på vänster sida för att klicka på;</span><span class="sxs-lookup"><span data-stu-id="3b3c1-130">When logged on as a package's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="3b3c1-131">Klicka på länken ”ta bort' bredvid ägare som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-package-ownership"></a><span data-ttu-id="3b3c1-132">Överföra ägarskapet för paketet</span><span class="sxs-lookup"><span data-stu-id="3b3c1-132">Transferring Package Ownership</span></span>

<span data-ttu-id="3b3c1-133">Vi kommer ibland supportärenden att överföra äganderätten för paket från en användare till en annan, men du kan nästan alltid göra det själv.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-133">We sometimes get support requests to transfer package ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="3b3c1-134">Överföra ägarskapet från en användare till en annan är helt enkelt en kombination av de två funktionerna som ovan.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="3b3c1-135">Den nuvarande ägaren bjuder in den nya användaren att bli en Medägare och den nya användaren accepterar inbjudan;</span><span class="sxs-lookup"><span data-stu-id="3b3c1-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="3b3c1-136">Den nya användaren tar bort den gamla användaren från listan över ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="3b3c1-137">Den här begäran har aktiverats under ett par formulär, men processen fungerar på samma.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-137">This request has come in under a couple forms but the process works the same.</span></span>

- <span data-ttu-id="3b3c1-138">Paketet ägarskap ändras från en utvecklare till en annan</span><span class="sxs-lookup"><span data-stu-id="3b3c1-138">The package ownership is changing from one developer to another</span></span>
- <span data-ttu-id="3b3c1-139">Paketet publicerades av misstag använda fel konto</span><span class="sxs-lookup"><span data-stu-id="3b3c1-139">The package was accidentally published using the wrong account</span></span>


## <a name="orphaned-packages"></a><span data-ttu-id="3b3c1-140">Överblivna paket</span><span class="sxs-lookup"><span data-stu-id="3b3c1-140">Orphaned Packages</span></span>

<span data-ttu-id="3b3c1-141">Ett senaste scenario har inträffat, men inte många gånger.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="3b3c1-142">Paket har blivit överblivna och det enda kontot för paketet ägare kan inte användas för att lägga till nya ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-142">Packages have become orphans and the only package owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="3b3c1-143">Här följer några exempel på det här scenariot:</span><span class="sxs-lookup"><span data-stu-id="3b3c1-143">Here are some examples of this scenario:</span></span>

- <span data-ttu-id="3b3c1-144">Ägarens konto är kopplat till en e-postadress som inte längre finns och att användaren har glömt sitt lösenord</span><span class="sxs-lookup"><span data-stu-id="3b3c1-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
- <span data-ttu-id="3b3c1-145">Registrerad ägare har lämnat företaget som tillverkar paketet och går inte att nå för att uppdatera paketet ägarskap</span><span class="sxs-lookup"><span data-stu-id="3b3c1-145">The registered owner has left the company that produces the package and cannot be reached to update the package ownership</span></span>
- <span data-ttu-id="3b3c1-146">På grund av ett fel som påverkar endast en handfull paket finns paketet på något sätt ownerless i galleriet</span><span class="sxs-lookup"><span data-stu-id="3b3c1-146">Due to a bug that has only affected a handful of packages, the package is somehow ownerless on the gallery</span></span>

<span data-ttu-id="3b3c1-147">PowerShell-galleriet administratörer kan använda länken hantera ägare för valfritt paket.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any package.</span></span>
<span data-ttu-id="3b3c1-148">Om du är berättigat ägaren av ett paket och inte går att nå den nuvarande ägaren för att få ägarskap behörigheter, använder du länken ”Rapportera missbruk' i galleriet för att nå administratörer för PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-148">If you are the rightful owner of a package and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="3b3c1-149">Vi sedan följer en process för att verifiera ditt ägarskap för paketet.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-149">We will then follow a process to verify your ownership of the package.</span></span>
<span data-ttu-id="3b3c1-150">Om vi fastställer bör du vara ägare till paketet, vi använder länken hantera ägare för paketet skapar och skickar inbjudan att bli ägare.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-150">If we determine you should be an owner of the package, we will use the 'Manage Owners' link for the package ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="3b3c1-151">Vi kommer endast göra detta när du har verifierat att du ska vara ägare och processen för detta varierar beroende på omständigheter.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="3b3c1-152">Ofta vi använder paketets projekt-URL för att hitta ett sätt att kontakta Projektägaren, men vi kan också använda Twitter, e-post, eller på annat sätt för att kontakta Projektägaren.</span><span class="sxs-lookup"><span data-stu-id="3b3c1-152">Often times, we will use the package's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>
