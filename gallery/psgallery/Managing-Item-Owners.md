---
ms.date: 06/12/2017
contributor: JKeithB
ms.topic: conceptual
keywords: galleriet, powershell, cmdlet, psgallery
title: Hantera objekt ägare
ms.openlocfilehash: e550b74ebde00cfbb154dbf4fb1fa4ae0582e029
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="managing-item-owners"></a><span data-ttu-id="51e07-103">Hantera objekt ägare</span><span class="sxs-lookup"><span data-stu-id="51e07-103">Managing Item Owners</span></span>

<span data-ttu-id="51e07-104">Ägare till ett objekt i PowerShell-galleriet definieras av vem som publicerade artikeln i galleriet.</span><span class="sxs-lookup"><span data-stu-id="51e07-104">Ownership of an item in the PowerShell Gallery is defined by who published the item to the gallery.</span></span>
<span data-ttu-id="51e07-105">Ibland behöver dessa metadata hanteras utöver publicering inledande objektet, vilket innebär att metadata för ägare måste vara föränderliga själva objektet är inte.</span><span class="sxs-lookup"><span data-stu-id="51e07-105">Sometimes this metadata needs to be managed beyond the initial item publishing, which means the owner metadata needs to be mutable while the item itself is not.</span></span>

<span data-ttu-id="51e07-106">Alla användare som har objekt är likvärdiga.</span><span class="sxs-lookup"><span data-stu-id="51e07-106">All item owners are peers.</span></span>
<span data-ttu-id="51e07-107">Det innebär att alla objekt ägare kan publicera en ny version av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-107">This means any item owner can publish a new version of an item.</span></span> <span data-ttu-id="51e07-108">Det innebär också att alla objekt ägaren kan ta bort andra element-ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-108">It also means that any item owner can remove any other item owner.</span></span>
<span data-ttu-id="51e07-109">Ingen ägare har flera utfärdare än andra ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-109">No owner has more authority than other owners.</span></span>

## <a name="setting-an-items-initial-owner"></a><span data-ttu-id="51e07-110">Ange ett objekt inledande ägare</span><span class="sxs-lookup"><span data-stu-id="51e07-110">Setting an Item's Initial Owner</span></span>

<span data-ttu-id="51e07-111">När ett nytt objekt publiceras till PowerShell-galleriet, definieras den ursprungliga ägaren av användaren som publicerade artikeln.</span><span class="sxs-lookup"><span data-stu-id="51e07-111">When a new item is published to PowerShell Gallery, the initial owner is defined by the user that published the item.</span></span> <span data-ttu-id="51e07-112">Detta bestäms genom vars API nyckel användes i Publicera modul-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="51e07-112">This is determined by whose API key was used in the Publish-Module cmdlet.</span></span>

## <a name="adding-owners"></a><span data-ttu-id="51e07-113">Lägga till ägare</span><span class="sxs-lookup"><span data-stu-id="51e07-113">Adding Owners</span></span>

<span data-ttu-id="51e07-114">När ett objekt har publicerats till PowerShell-galleriet, är det enkelt att bjuda in ytterligare användare att bli ägare till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-114">Once an item has been published to the PowerShell Gallery, it's easy to invite additional users to become owners of an item.</span></span>

1. <span data-ttu-id="51e07-115">[Logga in](https://powershellgallery.com/users/account/LogOn) i PowerShell-galleriet med det konto som är den nuvarande ägaren av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-115">[Log on](https://powershellgallery.com/users/account/LogOn) to the PowerShell Gallery with the account that is the current owner of an item.</span></span>
2. <span data-ttu-id="51e07-116">Navigera till ett objekt-sida på fliken 'Element', söka eller klicka på ditt användarnamn och sedan [ **Hantera Mina objekt**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="51e07-116">Navigate to an item page using the 'Items' tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="51e07-117">När inloggad som en artikel ägare, finns en hantera ägare länk till vänster på.</span><span class="sxs-lookup"><span data-stu-id="51e07-117">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click.</span></span>
4. <span data-ttu-id="51e07-118">Ange användarnamnet för personen att lägga till som ägare och klicka på ”Lägg till'.</span><span class="sxs-lookup"><span data-stu-id="51e07-118">Enter the username of the person to add as an owner and click 'Add'.</span></span>
5. <span data-ttu-id="51e07-119">Ett e-postmeddelande skickas sedan till den nya Medägare som en inbjudan ska bli ägare till ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-119">An email is then sent to the new co-owner, as an invitation to become an owner of an item.</span></span>
6. <span data-ttu-id="51e07-120">När användaren klickar på länken, är de en fullständig Medägare med fullständig kontroll över ett objekt, inklusive möjligheten att ta bort andra användare som ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-120">Once that user clicks the link, they are a full co-owner with full control over an item, including the ability to remove other users as owners.</span></span>

<span data-ttu-id="51e07-121">**Obs**: tills den nya ägaren bekräftar ägarskapet, de *inte* visas som en ägare av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-121">**NOTE**: Until the new owner confirms ownership, they *will not* be listed as an owner of an item.</span></span>
<span data-ttu-id="51e07-122">När du visar den **hantera ägare** sidan visas en ”väntar på godkännande” post i de aktuella ägarna.</span><span class="sxs-lookup"><span data-stu-id="51e07-122">When viewing the **Manage Owners** page, you will see a "pending approval" entry in the current owners.</span></span>
<span data-ttu-id="51e07-123">Den inbjudan som kan tas bort; precis som andra ägare kan tas bort.</span><span class="sxs-lookup"><span data-stu-id="51e07-123">That invitation can be removed; just as other owners can be removed.</span></span>
<span data-ttu-id="51e07-124">Den här processen att inbjudningar hindrar användare från att lägga till andra användare som ägare till sina objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-124">This process of invitations prevents users from falsely adding other users as owners of their items.</span></span>

<span data-ttu-id="51e07-125">Observera att ”författarna” metadata är rent frihandsfigurer text. endast ”ägare” kontrolleras.</span><span class="sxs-lookup"><span data-stu-id="51e07-125">Note that the "Authors" metadata is purely freeform text; only "Owners" are controlled.</span></span>


## <a name="removing-owners"></a><span data-ttu-id="51e07-126">Ta bort ägare</span><span class="sxs-lookup"><span data-stu-id="51e07-126">Removing Owners</span></span>
<span data-ttu-id="51e07-127">När ett objekt har flera ägare och en måste tas bort, är processen enkel:</span><span class="sxs-lookup"><span data-stu-id="51e07-127">When an item has multiple owners and one needs to be removed, the process is simple:</span></span>

1. <span data-ttu-id="51e07-128">[Logga in](https://powershellgallery.com/users/account/LogOn) till PowerShell-galleriet med det konto som är den nuvarande ägaren av ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-128">[Log on](https://powershellgallery.com/users/account/LogOn) to PowerShell Gallery with the account that is the current owner of an item;</span></span>
2. <span data-ttu-id="51e07-129">Navigera till ett objekt-sida på fliken objekt, söker eller klicka på ditt användarnamn och sedan [ **Hantera Mina objekt**](https://www.powershellgallery.com/account/Packages).</span><span class="sxs-lookup"><span data-stu-id="51e07-129">Navigate to an item page using the Items tab, searching, or clicking your username and then [**Manage My Items**](https://www.powershellgallery.com/account/Packages).</span></span>
3. <span data-ttu-id="51e07-130">När inloggad som en artikel ägare, finns det en länk för hantera ägare till vänster på;</span><span class="sxs-lookup"><span data-stu-id="51e07-130">When logged on as an item's owner, there is a 'Manage Owners' link on the left side to click;</span></span>
4. <span data-ttu-id="51e07-131">Klicka på länken ”ta bort' bredvid ägaren som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="51e07-131">Click the 'remove' link next to the owner to be removed.</span></span>



## <a name="transferring-item-ownership"></a><span data-ttu-id="51e07-132">Överföra ägarskap för objektet</span><span class="sxs-lookup"><span data-stu-id="51e07-132">Transferring Item Ownership</span></span>
<span data-ttu-id="51e07-133">Vi hämta ibland supportärenden att överföra objektet ägarskap från en användare till en annan, men du kan nästan alltid utföra den själv.</span><span class="sxs-lookup"><span data-stu-id="51e07-133">We sometimes get support requests to transfer item ownership from one user to another, but you can almost always accomplish this yourself.</span></span>
<span data-ttu-id="51e07-134">Överföra ägarskap från en användare till en annan är helt enkelt en kombination av de två funktionerna som ovan.</span><span class="sxs-lookup"><span data-stu-id="51e07-134">Transferring ownership from one user to another is simply a combination of the two features above.</span></span>

1. <span data-ttu-id="51e07-135">Den nuvarande ägaren inbjuder den nya användaren ska bli en Medägare och den nya användaren accepterar inbjudan;</span><span class="sxs-lookup"><span data-stu-id="51e07-135">The current owner invites the new user to become a co-owner and the new user accepts the invite;</span></span>
2. <span data-ttu-id="51e07-136">Den nya användaren tar bort den gamla användaren från listan över ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-136">The new user removes the old user from the list of owners.</span></span>

<span data-ttu-id="51e07-137">Denna begäran har kommit i under några formulär, men processen fungerar på samma sätt.</span><span class="sxs-lookup"><span data-stu-id="51e07-137">This request has come in under a couple forms but the process works the same.</span></span>

* <span data-ttu-id="51e07-138">Objektet ägarskap ändras från en utvecklare till en annan</span><span class="sxs-lookup"><span data-stu-id="51e07-138">The item ownership is changing from one developer to another</span></span>
* <span data-ttu-id="51e07-139">Artikeln publicerades av misstag med fel konto</span><span class="sxs-lookup"><span data-stu-id="51e07-139">The item was accidentally published using the wrong account</span></span>


## <a name="orphaned-items"></a><span data-ttu-id="51e07-140">Överblivna objekt</span><span class="sxs-lookup"><span data-stu-id="51e07-140">Orphaned Items</span></span>
<span data-ttu-id="51e07-141">En sista scenariot har inträffat, men inte många gånger.</span><span class="sxs-lookup"><span data-stu-id="51e07-141">One last scenario has occurred, but not many times.</span></span>
<span data-ttu-id="51e07-142">Objekt har blivit överblivna och det enda objekt ägare kontot kan inte användas för att lägga till nya ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-142">Items have become orphans and the only item owner account cannot be used to add new owners.</span></span>
<span data-ttu-id="51e07-143">Här följer några exempel på det här scenariot:</span><span class="sxs-lookup"><span data-stu-id="51e07-143">Here are some examples of this scenario:</span></span>

* <span data-ttu-id="51e07-144">Ägarens konto är kopplat till en e-postadress som inte längre finns och att användaren har glömt sitt lösenord</span><span class="sxs-lookup"><span data-stu-id="51e07-144">The owner's account is associated with an email address that no longer exists and the user has forgotten their password</span></span>
* <span data-ttu-id="51e07-145">Registrerad ägare har lämnat företaget som producerar objektet och går inte att nå för att uppdatera objektet ägarskap</span><span class="sxs-lookup"><span data-stu-id="51e07-145">The registered owner has left the company that produces the item and cannot be reached to update the item ownership</span></span>
* <span data-ttu-id="51e07-146">På grund av ett fel som påverkar bara ett fåtal objekt finns objektet på något sätt ownerless på galleriet</span><span class="sxs-lookup"><span data-stu-id="51e07-146">Due to a bug that has only affected a handful of items, the item is somehow ownerless on the gallery</span></span>

<span data-ttu-id="51e07-147">PowerShell-galleriet administratörer har åtkomst till länken hantera ägare för ett objekt.</span><span class="sxs-lookup"><span data-stu-id="51e07-147">The PowerShell Gallery Administrators can access the 'Manage Owners' link for any item.</span></span>
<span data-ttu-id="51e07-148">Om du är berättigat ägaren till ett objekt och kan inte nå den nuvarande ägaren för att få ägarskap behörigheter Använd länken Rapportera missbruk på galleriet för att nå PowerShell-galleriet administratörer.</span><span class="sxs-lookup"><span data-stu-id="51e07-148">If you are the rightful owner of a item and cannot reach the current owner to gain ownership permissions, then use the 'Report Abuse' link on the gallery to reach the PowerShell Gallery Administrators.</span></span>
<span data-ttu-id="51e07-149">Vi sedan följer en process för att verifiera ditt ägarskap för objektet.</span><span class="sxs-lookup"><span data-stu-id="51e07-149">We will then follow a process to verify your ownership of the item.</span></span>
<span data-ttu-id="51e07-150">Om vi anser att du ska vara ägare till objektet kommer att använda länken hantera ägare för objektet oss själva och skicka inbjudan ska bli ägare.</span><span class="sxs-lookup"><span data-stu-id="51e07-150">If we determine you should be an owner of the item, we will use the 'Manage Owners' link for the item ourselves and send you the invite to become an owner.</span></span>
<span data-ttu-id="51e07-151">Vi kommer bara göra det när du har verifierat att du ska vara en ägare och processen för detta varierar beroende på omständigheter.</span><span class="sxs-lookup"><span data-stu-id="51e07-151">We will only do this after verifying that you should be an owner and the process for this varies by circumstances.</span></span>
<span data-ttu-id="51e07-152">Ofta URL för objektet ska användas för att hitta ett sätt att kontakta Projektägaren, men vi kan också använda Twitter, e-post, eller på annat sätt för att kontakta Projektägaren.</span><span class="sxs-lookup"><span data-stu-id="51e07-152">Often times, we will use the item's Project URL to find a way to contact the project owner, but we may also use Twitter, Email, or other means for contacting the project owner.</span></span>