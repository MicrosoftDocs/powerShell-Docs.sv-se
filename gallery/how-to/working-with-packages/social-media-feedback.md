---
ms.date: 06/12/2017
contributor: JKeithB
keywords: galleriet, powershell, cmdlet, psgallery
title: Ge Feedback via sociala medier eller kommentarer
ms.openlocfilehash: 95e5db22b94151c3974189c30f1d4e580b47eeb5
ms.sourcegitcommit: f268dce5b5e72be669be0c6634b8db11369bbae2
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/29/2019
ms.locfileid: "58623899"
---
# <a name="providing-feedback-via-social-media-or-comments"></a><span data-ttu-id="3b75d-103">Ge Feedback via sociala medier eller kommentarer</span><span class="sxs-lookup"><span data-stu-id="3b75d-103">Providing Feedback via social media or comments</span></span>

<span data-ttu-id="3b75d-104">PowerShell-galleriet stöder två metoder för användare med offentliga feedback på ett paket:</span><span class="sxs-lookup"><span data-stu-id="3b75d-104">The PowerShell Gallery supports two approaches for users to provide public feedback on a package:</span></span>

- <span data-ttu-id="3b75d-105">Använd länkarna på den vänstra kanten ”dela” ett paket i Facebook, LinkedIn och Twitter sociala webbplatser;</span><span class="sxs-lookup"><span data-stu-id="3b75d-105">Use the links on the left edge to "share" a package in Facebook, LinkedIn, or Twitter social media sites;</span></span>
- <span data-ttu-id="3b75d-106">Använd funktionen kommentaren att publicera kommentarer för ett paket, så att redigerare att se upp för kommentarer på paket som de publicerar.</span><span class="sxs-lookup"><span data-stu-id="3b75d-106">Use the Comment feature to post comments on a package, and to allow Authors to watch for comments on packages they publish.</span></span>

## <a name="social-media-feedback"></a><span data-ttu-id="3b75d-107">Sociala medier Feedback</span><span class="sxs-lookup"><span data-stu-id="3b75d-107">Social Media Feedback</span></span>

<span data-ttu-id="3b75d-108">Till vänster på sidan för varje paket i PowerShell-galleriet finns länkar till Facebook, LinkedIn och Twitter.</span><span class="sxs-lookup"><span data-stu-id="3b75d-108">On the left side of the page for each package in the PowerShell Gallery there are links for Facebook, LinkedIn, and Twitter.</span></span>
<span data-ttu-id="3b75d-109">När du klickar på länkarna öppnas webbplatsen sociala medier och Tillåt att snabbt kunna dela en länk till paketet.</span><span class="sxs-lookup"><span data-stu-id="3b75d-109">Clicking on these links will open the social media site, and allow quickly sharing a link to the package.</span></span>

<span data-ttu-id="3b75d-110">Användarna måste logga in på den plats som de har valt för att kunna dela paketets PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="3b75d-110">Users must log in to the site they have chosen in order to share the PowerShell Gallery package.</span></span>

<span data-ttu-id="3b75d-111">Användarna uppmanas att göra detta om de tycker att ett paket är något de skulle rekommendera andra.</span><span class="sxs-lookup"><span data-stu-id="3b75d-111">Users are encouraged to do this if they find that a package is something they would recommend to others.</span></span>
<span data-ttu-id="3b75d-112">PowerShell-galleriet kontrolleras varje plats för sociala medier för ”resurser” på paketet och visa hur många gånger det paketet har delats i var och en av webbplatser för sociala medier.</span><span class="sxs-lookup"><span data-stu-id="3b75d-112">The PowerShell Gallery will check each social media site for "shares" of the package, and display how many times that package has been shared in each of the social media sites.</span></span>
<span data-ttu-id="3b75d-113">Eftersom detta visar antalet gånger som något har delats blir det tolkas andra användare som ”liking” paketet.</span><span class="sxs-lookup"><span data-stu-id="3b75d-113">Since this shows only the count of times something has been shared, it will be interpreted other users as "liking" the package.</span></span>

## <a name="comments"></a><span data-ttu-id="3b75d-114">Kommentar</span><span class="sxs-lookup"><span data-stu-id="3b75d-114">Comments</span></span>

> [!IMPORTANT]
> <span data-ttu-id="3b75d-115">Livefyre-kommentarer kommer från en utomstående leverantör och längre stöds inte.</span><span class="sxs-lookup"><span data-stu-id="3b75d-115">Livefyre commenting is provided by a third-party vendor and is no longer supported.</span></span>
> <span data-ttu-id="3b75d-116">Livefyre-kommentarer är inte längre tillgänglig på PowerShell-galleriet Start 05/01/2019.</span><span class="sxs-lookup"><span data-stu-id="3b75d-116">Livefyre commenting will no longer be available on the PowerShell Gallery starting 05/01/2019.</span></span> 

<span data-ttu-id="3b75d-117">PowerShell-galleriet använder tjänsten LiveFyre så att användarna kan kommentera paket.</span><span class="sxs-lookup"><span data-stu-id="3b75d-117">The PowerShell Gallery uses the LiveFyre service to allow users to comment on packages.</span></span>
<span data-ttu-id="3b75d-118">Användare som har rekommendationer eller kommentarer kan använda den här funktionen för att ge feedback som är synlig för alla som besöker sidan package.</span><span class="sxs-lookup"><span data-stu-id="3b75d-118">Users who have recommendations or feedback can use this feature to provide feedback that is visible to anyone who visits the package page.</span></span>
<span data-ttu-id="3b75d-119">Paketet ägare kan följa denna feedback och meddelas när någon lägger upp en kommentar.</span><span class="sxs-lookup"><span data-stu-id="3b75d-119">Package owners can Follow this feedback, and be notified when someone posts a comment.</span></span>

<span data-ttu-id="3b75d-120">Kommentar systemet baseras på LiveFyre, som är en separat tjänst som inte hanteras av Microsoft och kräver unika inloggning som ska användas.</span><span class="sxs-lookup"><span data-stu-id="3b75d-120">The Comment system is based on LiveFyre, which is a separate service that is not managed by Microsoft, and requires unique login to use.</span></span>
<span data-ttu-id="3b75d-121">Första gången du väljer att lämna en kommentar eller följ kommentarer på en av dina paket, uppmanas du att skapa ett LiveFyre-konto.</span><span class="sxs-lookup"><span data-stu-id="3b75d-121">The first time you choose to leave a comment or follow comments on one of your packages, you will be prompted to create a LiveFyre account.</span></span>

<span data-ttu-id="3b75d-122">Om du har skapat ett LiveFyre-konto och loggat in kan du skapa en kommentar som ger feedback om paketet, sedan klickar du på ”Skicka kommentar...” Kommentaren visas inte direkt.</span><span class="sxs-lookup"><span data-stu-id="3b75d-122">If you have created a LiveFyre account and logged in, you can craft a comment that provides feedback on the package, then click on "Post comment..." The comment will not be visible immediately.</span></span>
<span data-ttu-id="3b75d-123">Kommentarer för gallery-paket är kontrollerade av PowerShell-galleriet-administratörer och alla inlägg granskas av moderatorerna innan den publicerade och synliga för andra.</span><span class="sxs-lookup"><span data-stu-id="3b75d-123">Comments for gallery packages are moderated by the PowerShell Gallery administrators, and all posts are reviewed by the moderators before being published and visible to others.</span></span>
<span data-ttu-id="3b75d-124">Vårt syfte i Kontrollera kommentarerna är att säkerställa att de överensstämmer med offentliga beteende som är konsekvent med PowerShell-galleriet [användningsvillkor](https://www.powershellgallery.com/policies/Terms).</span><span class="sxs-lookup"><span data-stu-id="3b75d-124">Our purpose in moderating the comments is to ensure that they align with public behavior consistent with the PowerShell Gallery [Terms of Use](https://www.powershellgallery.com/policies/Terms).</span></span>

<span data-ttu-id="3b75d-125">Paketet ägare uppmuntras att följa kommentarer som publiceras på LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="3b75d-125">Package owners are encouraged to Follow comments that are posted to LiveFyre.</span></span>
<span data-ttu-id="3b75d-126">Ett LiveFyre-konto är obligatoriskt och bör använda samma e-postadress som du använder för att publicera ditt paket i LiveFyre.</span><span class="sxs-lookup"><span data-stu-id="3b75d-126">A LiveFyre account is required, and it is recommended to use the same email address you use for publishing your package in LiveFyre.</span></span>
<span data-ttu-id="3b75d-127">Om du vill följa kommentarer, logga in på LiveFyre och navigera till alla paket som där du står som ägare.</span><span class="sxs-lookup"><span data-stu-id="3b75d-127">To Follow comments, log into LiveFyre, and navigate to any package where you are listed as an Owner.</span></span>
<span data-ttu-id="3b75d-128">Nedan i kommentarsfältet längst ned i varje paket kommer du se ”+ följer”.</span><span class="sxs-lookup"><span data-stu-id="3b75d-128">Below the Comment box at the bottom of each package you will see "+Follow".</span></span>
<span data-ttu-id="3b75d-129">När du klickar på det här skickar LiveFyre ett e-postmeddelande till den registrerade e-postadressen tid nya kommentar på förpackningen.</span><span class="sxs-lookup"><span data-stu-id="3b75d-129">Once you click on this, LiveFyre will send an email to the registered email address any time new comments made on the package.</span></span>
