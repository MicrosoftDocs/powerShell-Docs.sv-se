---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Skicka Feedback via sociala medier eller kommentarer
ms.openlocfilehash: a8e6097de4a565b504189b0b0488c45b6d78a8b6
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="c8735-103">Skicka Feedback via sociala medier eller kommentarer</span><span class="sxs-lookup"><span data-stu-id="c8735-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="c8735-104">Powershell-galleriet stöder två metoder för användare med offentliga feedback om ett objekt:</span><span class="sxs-lookup"><span data-stu-id="c8735-104">The Powershell Gallery supports two approaches for users to provide public feedback on an item:</span></span>

- <span data-ttu-id="c8735-105">Använd länkarna på den vänstra kanten ”delar” ett objekt i Facebook, LinkedIn och Twitter sociala medier platser;</span><span class="sxs-lookup"><span data-stu-id="c8735-105">Use the links on the left edge to "share" an item in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="c8735-106">Använd funktionen kommentar lämna kommentarer om ett objekt och Tillåt redigerare att bevaka för kommentarer om objekt som de publicerar.</span><span class="sxs-lookup"><span data-stu-id="c8735-106">Use the Comment feature to post comments on an item, and to allow Authors to watch for comments on items they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="c8735-107">Sociala medier Feedback</span><span class="sxs-lookup"><span data-stu-id="c8735-107">Social Media Feedback</span></span>

<span data-ttu-id="c8735-108">På vänster sida av sidan för varje objekt i PowerShell-galleriet finns länkar till Facebook, LinkedIn och Twitter.</span><span class="sxs-lookup"><span data-stu-id="c8735-108">On the left side of the page for each item in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="c8735-109">Klicka på länkarna öppnas webbplatsen sociala medier, och att snabbt dela en länk till objektet.</span><span class="sxs-lookup"><span data-stu-id="c8735-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the item.</span></span>

<span data-ttu-id="c8735-110">Användarna måste logga in till webbplatsen som de har valt för att kunna dela PowerShell galleriobjektet.</span><span class="sxs-lookup"><span data-stu-id="c8735-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery item.</span></span>

<span data-ttu-id="c8735-111">Användarna uppmanas att göra om de hitta ett objekt är något de skulle rekommendera andra.</span><span class="sxs-lookup"><span data-stu-id="c8735-111">Users are encouraged to do this if they find that an item is something they would recommend to others.</span></span>
<span data-ttu-id="c8735-112">PowerShell-galleriet kontrollerar varje plats för sociala medier för ”resurser” på objektet och visa hur många gånger som objektet har delat i var och en av platserna sociala medier.</span><span class="sxs-lookup"><span data-stu-id="c8735-112">The PowerShell Gallery will check each social media site for "shares" of the item, and display how many times that item has been shared in each of the social media sites.</span></span>
<span data-ttu-id="c8735-113">Eftersom det visar antalet gånger som något har delats blir systemkodsidan andra användare som ”liking”-objektet.</span><span class="sxs-lookup"><span data-stu-id="c8735-113">Since this shows only the count of times something has been shared, it will be intepreted other users as "liking" the item.</span></span>


## <a name="comments"></a><span data-ttu-id="c8735-114">Kommentar</span><span class="sxs-lookup"><span data-stu-id="c8735-114">Comments</span></span>

<span data-ttu-id="c8735-115">PowerShell-galleriet använder tjänsten LiveFyre så att användarna kan kommentera objekt.</span><span class="sxs-lookup"><span data-stu-id="c8735-115">The PowerShell Gallery uses the LiveFyre service to allow users to comment on items.</span></span>
<span data-ttu-id="c8735-116">Användare som har rekommendationer eller feedback kan använda den här funktionen för att ge feedback som är synliga för alla som besöker sidan artikel.</span><span class="sxs-lookup"><span data-stu-id="c8735-116">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the item page.</span></span>
<span data-ttu-id="c8735-117">Objektet ägare kan följa denna feedback och meddelas när någon publicerar en kommentar.</span><span class="sxs-lookup"><span data-stu-id="c8735-117">Item owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="c8735-118">Systemets kommentar baseras på LiveFyre, vilket är en separat tjänst som inte hanteras av Microsoft och kräver unika inloggning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c8735-118">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="c8735-119">Första gången du väljer att lämna en kommentar eller följa kommentarer på ett av objekten, uppmanas du att skapa ett LiveFyre-konto.</span><span class="sxs-lookup"><span data-stu-id="c8735-119">The first time you choose to leave a comment or Follow comments on one of your items, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="c8735-120">Om du har skapat ett konto för LiveFyre loggat in kan du skapa en kommentar som ger feedback på objektet och klicka sedan på ”... Post comment” Kommentaren visas inte direkt.</span><span class="sxs-lookup"><span data-stu-id="c8735-120">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the item, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="c8735-121">Kommentarer till galleriobjekt är kontrollerade administratörer PowerShell-galleriet och alla inlägg granskas av kontrollanten innan du publicerade och synliga för andra.</span><span class="sxs-lookup"><span data-stu-id="c8735-121">Comments for gallery items are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="c8735-122">Vår i Kontrollera kommentarerna syftar till att säkerställa att de överensstämmer med offentliga beteende som är konsekventa med PowerShell-galleriet [användningsvillkoren](https://www.powershellgallery.com/policies/Terms).</span><span class="sxs-lookup"><span data-stu-id="c8735-122">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="c8735-123">Objektet ägare uppmuntras att följa kommentarer som upp på LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="c8735-123">Item owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="c8735-124">Krävs ett LiveFyre konto och det rekommenderas att använda samma e-postadress som du använder för att publicera objektet i LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="c8735-124">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your item in LiveFyre.</span></span>
<span data-ttu-id="c8735-125">Logga in på LiveFyre om du vill följa kommentarer och navigera till ett objekt där du räknas som en ägare.</span><span class="sxs-lookup"><span data-stu-id="c8735-125">To Follow comments, log into LiveFyre, and navigate to any item where you are listed as an Owner.</span></span>
<span data-ttu-id="c8735-126">Under rutan kommentarer längst ned på varje objekt kommer du se ”+ följer”.</span><span class="sxs-lookup"><span data-stu-id="c8735-126">Below the Comment box at the bottom of each item you will see "+Follow".</span></span>
<span data-ttu-id="c8735-127">När du klickar på den här skickar LiveFyre ett e-postmeddelande till registrerade e-postadressen tid nya synpunkter på objektet.</span><span class="sxs-lookup"><span data-stu-id="c8735-127">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the item.</span></span>