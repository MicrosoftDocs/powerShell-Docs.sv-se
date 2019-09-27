---
ms.date: 06/12/2017
contributor: JKeithB
keywords: Galleri, PowerShell, cmdlet, psgallery
title: Ge feedback via sociala medier eller kommentarer
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71328758"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="4df91-103">Ge feedback via sociala medier eller kommentarer</span><span class="sxs-lookup"><span data-stu-id="4df91-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="4df91-104">PowerShell-galleriet har stöd för två sätt för användare att tillhandahålla offentlig feedback i ett paket:</span><span class="sxs-lookup"><span data-stu-id="4df91-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="4df91-105">Använd länkarna till vänster om du vill dela ett paket på Facebook-, LinkedIn-eller Twitter-sociala medie platser.</span><span class="sxs-lookup"><span data-stu-id="4df91-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="4df91-106">Använd kommentar funktionen för att publicera kommentarer om ett paket och för att tillåta att författare tittar på kommentarer om paket som publicerats.</span><span class="sxs-lookup"><span data-stu-id="4df91-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="4df91-107">Feedback från sociala medier</span><span class="sxs-lookup"><span data-stu-id="4df91-107">Social Media Feedback</span></span>

<span data-ttu-id="4df91-108">På vänster sida av sidan för varje paket i PowerShell-galleriet finns det länkar till Facebook, LinkedIn och Twitter.</span><span class="sxs-lookup"><span data-stu-id="4df91-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="4df91-109">Om du klickar på de här länkarna öppnas webbplatsen för sociala medier och du får snabbt dela en länk till paketet.</span><span class="sxs-lookup"><span data-stu-id="4df91-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="4df91-110">Användarna måste logga in på den plats som de har valt för att kunna dela PowerShell-galleriet-paketet.</span><span class="sxs-lookup"><span data-stu-id="4df91-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="4df91-111">Användarna uppmanas att göra detta om de upptäcker att ett paket är något som de rekommenderar till andra.</span><span class="sxs-lookup"><span data-stu-id="4df91-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="4df91-112">Den PowerShell-galleriet kommer att kontrol lera om det finns "resurser" i paketet och visa hur många gånger paketet har delats på var och en av de sociala media platserna.</span><span class="sxs-lookup"><span data-stu-id="4df91-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="4df91-113">Eftersom detta bara visar hur många gånger något har delats, kommer det att tolkas som andra användare som "gilla"-paketet.</span><span class="sxs-lookup"><span data-stu-id="4df91-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="4df91-114">Kommentar</span><span class="sxs-lookup"><span data-stu-id="4df91-114">Comments</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4df91-115">Livefyre-kommentarer tillhandahålls av en tredjepartsleverantör och stöds inte längre.</span><span class="sxs-lookup"><span data-stu-id="4df91-115">Livefyre commenting is provided by a third-party vendor and is no longer supported.</span></span>
> <span data-ttu-id="4df91-116">Livefyre-kommentarer kommer inte längre vara tillgängliga på PowerShell-galleriet med start 05/01/2019.</span><span class="sxs-lookup"><span data-stu-id="4df91-116">Livefyre commenting will no longer be available on the PowerShell Gallery starting 05/01/2019.</span></span> 

<span data-ttu-id="4df91-117">PowerShell-galleriet använder LiveFyre-tjänsten för att tillåta användare att kommentera paket.</span><span class="sxs-lookup"><span data-stu-id="4df91-117">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="4df91-118">Användare som har rekommendationer eller feedback kan använda den här funktionen för att ge feedback som är synlig för alla som besöker paket sidan.</span><span class="sxs-lookup"><span data-stu-id="4df91-118">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="4df91-119">Paket ägare kan följa den här feedbacken och meddelas när någon publicerar en kommentar.</span><span class="sxs-lookup"><span data-stu-id="4df91-119">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="4df91-120">Kommentar systemet baseras på LiveFyre, som är en separat tjänst som inte hanteras av Microsoft och som kräver att unika inloggningar används.</span><span class="sxs-lookup"><span data-stu-id="4df91-120">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="4df91-121">Första gången du väljer att lämna en kommentar eller följa kommentarer om ett av dina paket, uppmanas du att skapa ett LiveFyre-konto.</span><span class="sxs-lookup"><span data-stu-id="4df91-121">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="4df91-122">Om du har skapat ett LiveFyre-konto och loggat in, kan du skapa en kommentar som ger feedback om paketet och sedan klicka på "Skicka kommentar..." Kommentaren visas inte omedelbart.</span><span class="sxs-lookup"><span data-stu-id="4df91-122">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="4df91-123">Kommentarer för Galleri paket förvaras av PowerShell-galleriet-administratörer och alla inlägg granskas av moderatorerna innan de publiceras och visas för andra.</span><span class="sxs-lookup"><span data-stu-id="4df91-123">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="4df91-124">Syftet med att kontrol lera kommentarerna är att se till att de överensstämmer med det offentliga beteendet i överensstämmelse med PowerShell-galleriet [användnings villkor](https://www.powershellgallery.com/policies/Terms).</span><span class="sxs-lookup"><span data-stu-id="4df91-124">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="4df91-125">Paket ägare uppmanas att följa kommentarer som publiceras i LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="4df91-125">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="4df91-126">Ett LiveFyre-konto krävs och vi rekommenderar att du använder samma e-postadress som du använder för att publicera ditt paket i LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="4df91-126">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="4df91-127">Om du vill följa kommentarer loggar du in på LiveFyre och navigerar till alla paket där du visas som ägare.</span><span class="sxs-lookup"><span data-stu-id="4df91-127">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="4df91-128">Under kommentars rutan längst ned i varje paket visas "+ Följ".</span><span class="sxs-lookup"><span data-stu-id="4df91-128">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="4df91-129">När du klickar på det här skickar LiveFyre ett e-postmeddelande till den registrerade e-postadressen varje gång nya kommentarer görs i paketet.</span><span class="sxs-lookup"><span data-stu-id="4df91-129">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
