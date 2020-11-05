---
title: Bidra till PowerShell-dokumentation
description: Den här artikeln beskriver de steg som krävs för att bidra till PowerShell-dokumentationen.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 255b74a75b8412ed509f6da930eb722d54233711
ms.sourcegitcommit: 39c2a697228276d5dae39e540995fa479c2b5f39
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/05/2020
ms.locfileid: "93354413"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="26c32-103">Bidra till PowerShell-dokumentation</span><span class="sxs-lookup"><span data-stu-id="26c32-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="26c32-104">Tack för ditt stöd för PowerShell!</span><span class="sxs-lookup"><span data-stu-id="26c32-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="26c32-105">Deltagarguiden är en samling artiklar som beskriver de verktyg och processer som vi använder för att skapa dokumentation på Microsoft.</span><span class="sxs-lookup"><span data-stu-id="26c32-105">The Contributor's Guide is a collection of articles that explain the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="26c32-106">Några av de här vägledningarna beskriver information som är gemensam för alla dokumentations uppsättningar som publicerats på [docs.Microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="26c32-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="26c32-107">Vissa av vägledningarna är specifika för hur vi skriver dokumentation för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="26c32-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="26c32-108">De vanliga artiklarna är tillgängliga i vårt centraliserade [bidrags guide][contribute].</span><span class="sxs-lookup"><span data-stu-id="26c32-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="26c32-109">PowerShell-/regionsspecifika guider finns här.</span><span class="sxs-lookup"><span data-stu-id="26c32-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="26c32-110">Sätt att bidra</span><span class="sxs-lookup"><span data-stu-id="26c32-110">Ways to contribute</span></span>

<span data-ttu-id="26c32-111">Det finns två sätt att bidra.</span><span class="sxs-lookup"><span data-stu-id="26c32-111">There are two ways to contribute.</span></span> <span data-ttu-id="26c32-112">Båda bidragen är värdefulla för oss.</span><span class="sxs-lookup"><span data-stu-id="26c32-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="26c32-113">Genom att [arkivera problem][file-an-issue] kan vi identifiera problem och luckor i vår dokumentation.</span><span class="sxs-lookup"><span data-stu-id="26c32-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="26c32-114">Ibland är problemen svåra att lösa, vilket kräver mer undersökningar och forskning.</span><span class="sxs-lookup"><span data-stu-id="26c32-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="26c32-115">Med ärende processen kan vi få en konversation om problemet och utveckla en tillfredsställande lösning.</span><span class="sxs-lookup"><span data-stu-id="26c32-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="26c32-116">Att skicka nytt innehåll eller ändringar i befintliga artiklar är en mer engagerad process.</span><span class="sxs-lookup"><span data-stu-id="26c32-116">Submitting new content or changes to existing articles is a more involved process.</span></span> <span data-ttu-id="26c32-117">Följande information beskriver verktyg, processer och standarder för att skicka innehåll till dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="26c32-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="26c32-118">Förbered för att göra ett bidrag</span><span class="sxs-lookup"><span data-stu-id="26c32-118">Prepare to make a contribution</span></span>

<span data-ttu-id="26c32-119">Du behöver ett GitHub-konto för att bidra till dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="26c32-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="26c32-120">Använd följande check lista för att hämta verktyg och förstå de processer som vi använder för att göra bidrag.</span><span class="sxs-lookup"><span data-stu-id="26c32-120">Use the following checklist to get the tools and understand the processes we use for making contributions.</span></span>

1. [<span data-ttu-id="26c32-121">Registrera dig för GitHub</span><span class="sxs-lookup"><span data-stu-id="26c32-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="26c32-122">Installera Git- och Markdown-verktyg</span><span class="sxs-lookup"><span data-stu-id="26c32-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="26c32-123">Installera redigerings paketet för dokument</span><span class="sxs-lookup"><span data-stu-id="26c32-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="26c32-124">[Installera posh-git][posh-git] – inte obligatoriskt, men rekommenderas</span><span class="sxs-lookup"><span data-stu-id="26c32-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="26c32-125">Konfigurera en lokal Git-lagringsplats</span><span class="sxs-lookup"><span data-stu-id="26c32-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="26c32-126">Granska git och GitHub fundament ALS</span><span class="sxs-lookup"><span data-stu-id="26c32-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="26c32-127">Komma igång med att skriva dokument</span><span class="sxs-lookup"><span data-stu-id="26c32-127">Get started writing docs</span></span>

<span data-ttu-id="26c32-128">Det finns två sätt att bidra till ändringar i dokumentationen:</span><span class="sxs-lookup"><span data-stu-id="26c32-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="26c32-129">Snabb redigering av befintliga dokument</span><span class="sxs-lookup"><span data-stu-id="26c32-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="26c32-130">Mindre korrigeringar, korrigering av skrivfel eller små tillägg</span><span class="sxs-lookup"><span data-stu-id="26c32-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="26c32-131">Fullständigt GitHub-arbetsflöde för dokument</span><span class="sxs-lookup"><span data-stu-id="26c32-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="26c32-132">stora ändringar, flera versioner, lägga till eller ändra bilder eller bidra med nya artiklar</span><span class="sxs-lookup"><span data-stu-id="26c32-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="26c32-133">Läs även avsnittet [Skriv Essentials](/contribute/style-quick-start) i den centrala deltagarens guide.</span><span class="sxs-lookup"><span data-stu-id="26c32-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="26c32-134">En annan utmärkt resurs är [Microsofts Skriv stils guide][style-guide].</span><span class="sxs-lookup"><span data-stu-id="26c32-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="26c32-135">Målet med Microsoft writing Style Guide är att hjälpa redigerare, tekniska skrivare, utvecklare, marknads förare och andra i IT att skriva bättre innehåll.</span><span class="sxs-lookup"><span data-stu-id="26c32-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="26c32-136">Mindre korrigeringar eller klargöranden av dokumentation och kod exempel i offentliga databaser omfattas av docs.microsoft.com användnings [villkor][terms-of-use].</span><span class="sxs-lookup"><span data-stu-id="26c32-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="26c32-137">Använd det fullständiga GitHub-arbetsflödet när du gör betydande ändringar.</span><span class="sxs-lookup"><span data-stu-id="26c32-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="26c32-138">Om du inte är anställd hos Microsoft genererar betydande ändringar en kommentar i pull-begäran som ber dig att skicka ett [licens avtal för CLA (online bidrag)][cla].</span><span class="sxs-lookup"><span data-stu-id="26c32-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="26c32-139">Du måste fylla i hela online-formuläret innan vi kan granska eller acceptera din pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="26c32-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="26c32-140">Uppförandekod</span><span class="sxs-lookup"><span data-stu-id="26c32-140">Code of conduct</span></span>

<span data-ttu-id="26c32-141">Alla informationslager som publicerar till docs.microsoft.com har antagit [Microsoft Open Source-uppförandekoden](https://opensource.microsoft.com/codeofconduct/) eller [.NET Foundation-uppförandekoden](https://dotnetfoundation.org/code-of-conduct).</span><span class="sxs-lookup"><span data-stu-id="26c32-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="26c32-142">Mer information finns i [vanliga frågor och svar om uppförandekoden](https://opensource.microsoft.com/codeofconduct/faq/).</span><span class="sxs-lookup"><span data-stu-id="26c32-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="26c32-143">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="26c32-143">Next steps</span></span>

<span data-ttu-id="26c32-144">Följande artiklar beskriver information som är unik för PowerShell-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="26c32-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="26c32-145">Om det finns överlappande vägledning i den centraliserade deltagar guiden, så kallar vi hur reglerna skiljer sig åt för PowerShell-innehållet.</span><span class="sxs-lookup"><span data-stu-id="26c32-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="26c32-146">Läs följande dokument:</span><span class="sxs-lookup"><span data-stu-id="26c32-146">Review the following documents:</span></span>

- [<span data-ttu-id="26c32-147">Så här arkiverar du ett problem</span><span class="sxs-lookup"><span data-stu-id="26c32-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="26c32-148">Komma igång med att skriva dokument</span><span class="sxs-lookup"><span data-stu-id="26c32-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="26c32-149">Skicka en pull-begäran</span><span class="sxs-lookup"><span data-stu-id="26c32-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="26c32-150">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="26c32-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)
- [<span data-ttu-id="26c32-151">Redigera cmdlet-referens</span><span class="sxs-lookup"><span data-stu-id="26c32-151">Editing cmdlet reference</span></span>](editing-cmdlet-ref.md)

<span data-ttu-id="26c32-152">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="26c32-152">Additional resources</span></span>

- [<span data-ttu-id="26c32-153">Checklista för redigering</span><span class="sxs-lookup"><span data-stu-id="26c32-153">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="26c32-154">Så här hanterar vi problem</span><span class="sxs-lookup"><span data-stu-id="26c32-154">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="26c32-155">Så här hanterar vi pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="26c32-155">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
