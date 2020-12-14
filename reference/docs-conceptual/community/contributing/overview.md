---
title: Bidra till PowerShell-dokumentation
description: Den här artikeln beskriver de steg som krävs för att bidra till PowerShell-dokumentationen.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 9fbdafa023eac80340437f30d2d6925a1a4ed3cb
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97076457"
---
# <a name="contributing-to-powershell-documentation"></a><span data-ttu-id="a4edc-103">Bidra till PowerShell-dokumentation</span><span class="sxs-lookup"><span data-stu-id="a4edc-103">Contributing to PowerShell documentation</span></span>

<span data-ttu-id="a4edc-104">Tack för ditt stöd för PowerShell!</span><span class="sxs-lookup"><span data-stu-id="a4edc-104">Thank you for your support of PowerShell!</span></span>

<span data-ttu-id="a4edc-105">Bidrags guidens guide är en samling artiklar som beskriver de verktyg och processer som vi använder för att skapa dokumentation på Microsoft.</span><span class="sxs-lookup"><span data-stu-id="a4edc-105">The Contributor's Guide is a collection of articles that describe the tools and processes we use to create documentation at Microsoft.</span></span> <span data-ttu-id="a4edc-106">Några av de här vägledningarna beskriver information som är gemensam för alla dokumentations uppsättningar som publicerats på [docs.Microsoft.com][docs].</span><span class="sxs-lookup"><span data-stu-id="a4edc-106">Some of these guides cover information that is common to any documentation set published to [docs.microsoft.com][docs].</span></span> <span data-ttu-id="a4edc-107">Vissa av vägledningarna är specifika för hur vi skriver dokumentation för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="a4edc-107">Some of the guides are specific to how we write documentation for PowerShell.</span></span>

<span data-ttu-id="a4edc-108">De vanliga artiklarna är tillgängliga i vårt centraliserade [bidrags guide][contribute].</span><span class="sxs-lookup"><span data-stu-id="a4edc-108">The common articles are available in our centralized [Contributor's Guide][contribute].</span></span> <span data-ttu-id="a4edc-109">PowerShell-/regionsspecifika guider finns här.</span><span class="sxs-lookup"><span data-stu-id="a4edc-109">The PowerShell-specific guides are available here.</span></span>

## <a name="ways-to-contribute"></a><span data-ttu-id="a4edc-110">Sätt att bidra</span><span class="sxs-lookup"><span data-stu-id="a4edc-110">Ways to contribute</span></span>

<span data-ttu-id="a4edc-111">Det finns två sätt att bidra.</span><span class="sxs-lookup"><span data-stu-id="a4edc-111">There are two ways to contribute.</span></span> <span data-ttu-id="a4edc-112">Båda bidragen är värdefulla för oss.</span><span class="sxs-lookup"><span data-stu-id="a4edc-112">Both contributions are valuable to us.</span></span>

- <span data-ttu-id="a4edc-113">Genom att [arkivera problem][file-an-issue] kan vi identifiera problem och luckor i vår dokumentation.</span><span class="sxs-lookup"><span data-stu-id="a4edc-113">[Filing issues][file-an-issue] helps us identify problems and gaps in our documentation.</span></span> <span data-ttu-id="a4edc-114">Ibland är problemen svåra att lösa, vilket kräver mer undersökningar och forskning.</span><span class="sxs-lookup"><span data-stu-id="a4edc-114">Sometimes the issues are difficult to resolve, requiring more investigation and research.</span></span> <span data-ttu-id="a4edc-115">Med ärende processen kan vi få en konversation om problemet och utveckla en tillfredsställande lösning.</span><span class="sxs-lookup"><span data-stu-id="a4edc-115">The issue process allows us to have a conversation about the problem and develop a satisfactory resolution.</span></span>

- <span data-ttu-id="a4edc-116">Att [skicka en pull-begäran](pull-requests.md) om att lägga till eller ändra innehåll är en mer engagerad process.</span><span class="sxs-lookup"><span data-stu-id="a4edc-116">[Submitting a pull request](pull-requests.md) to add or change content is a more involved process.</span></span>
  <span data-ttu-id="a4edc-117">Följande information beskriver verktyg, processer och standarder för att skicka innehåll till dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="a4edc-117">The following information outlines the tools, processes, and standards for submitting content to the documentation.</span></span>

## <a name="prepare-to-make-a-contribution"></a><span data-ttu-id="a4edc-118">Förbered för att göra ett bidrag</span><span class="sxs-lookup"><span data-stu-id="a4edc-118">Prepare to make a contribution</span></span>

<span data-ttu-id="a4edc-119">Du behöver ett GitHub-konto för att bidra till dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="a4edc-119">Contributing to the documentation requires a GitHub account.</span></span> <span data-ttu-id="a4edc-120">Använd följande check lista för att installera och konfigurera de verktyg du behöver för att göra bidrag.</span><span class="sxs-lookup"><span data-stu-id="a4edc-120">Use the following checklist to install and configure the tools you need to make contributions.</span></span>

1. [<span data-ttu-id="a4edc-121">Registrera dig för GitHub</span><span class="sxs-lookup"><span data-stu-id="a4edc-121">Sign up for GitHub</span></span>](/contribute/get-started-setup-github)
1. [<span data-ttu-id="a4edc-122">Installera Git- och Markdown-verktyg</span><span class="sxs-lookup"><span data-stu-id="a4edc-122">Install Git and Markdown tools</span></span>](/contribute/get-started-setup-tools)
1. [<span data-ttu-id="a4edc-123">Installera redigerings paketet för dokument</span><span class="sxs-lookup"><span data-stu-id="a4edc-123">Install the Docs Authoring Pack</span></span>](/contribute/how-to-write-docs-auth-pack)
1. <span data-ttu-id="a4edc-124">[Installera posh-git][posh-git] – inte obligatoriskt, men rekommenderas</span><span class="sxs-lookup"><span data-stu-id="a4edc-124">[Install Posh-Git][posh-git] - not required but recommended</span></span>
1. [<span data-ttu-id="a4edc-125">Konfigurera en lokal Git-lagringsplats</span><span class="sxs-lookup"><span data-stu-id="a4edc-125">Set up a local Git repository</span></span>](/contribute/get-started-setup-local)
1. [<span data-ttu-id="a4edc-126">Granska git och GitHub fundament ALS</span><span class="sxs-lookup"><span data-stu-id="a4edc-126">Review Git and GitHub fundamentals</span></span>](/contribute/git-github-fundamentals)

## <a name="get-started-writing-docs"></a><span data-ttu-id="a4edc-127">Komma igång med att skriva dokument</span><span class="sxs-lookup"><span data-stu-id="a4edc-127">Get started writing docs</span></span>

<span data-ttu-id="a4edc-128">Det finns två sätt att bidra till ändringar i dokumentationen:</span><span class="sxs-lookup"><span data-stu-id="a4edc-128">There are two ways to contribute changes to the documentation:</span></span>

1. [<span data-ttu-id="a4edc-129">Snabb redigering av befintliga dokument</span><span class="sxs-lookup"><span data-stu-id="a4edc-129">Quick edits to existing docs</span></span>](/contribute/#quick-edits-to-existing-documents)
   - <span data-ttu-id="a4edc-130">Mindre korrigeringar, korrigering av skrivfel eller små tillägg</span><span class="sxs-lookup"><span data-stu-id="a4edc-130">Minor corrections, fixing typos, or small additions</span></span>
1. [<span data-ttu-id="a4edc-131">Fullständigt GitHub-arbetsflöde för dokument</span><span class="sxs-lookup"><span data-stu-id="a4edc-131">Full GitHub workflow for docs</span></span>](/contribute/how-to-write-workflows-major)
   - <span data-ttu-id="a4edc-132">stora ändringar, flera versioner, lägga till eller ändra bilder eller bidra med nya artiklar</span><span class="sxs-lookup"><span data-stu-id="a4edc-132">large changes, multiple versions, adding or changing images, or contributing new articles</span></span>

<span data-ttu-id="a4edc-133">Läs även avsnittet [Skriv Essentials](/contribute/style-quick-start) i den centrala deltagarens guide.</span><span class="sxs-lookup"><span data-stu-id="a4edc-133">Also, read the [Writing essentials](/contribute/style-quick-start) section of the centralized Contributor's Guide.</span></span> <span data-ttu-id="a4edc-134">En annan utmärkt resurs är [Microsofts Skriv stils guide][style-guide].</span><span class="sxs-lookup"><span data-stu-id="a4edc-134">Another excellent resource is the [Microsoft Writing Style Guide][style-guide].</span></span> <span data-ttu-id="a4edc-135">Målet med Microsoft writing Style Guide är att hjälpa redigerare, tekniska skrivare, utvecklare, marknads förare och andra i IT att skriva bättre innehåll.</span><span class="sxs-lookup"><span data-stu-id="a4edc-135">The goal of the Microsoft Writing Style Guide is to help editors, technical writers, developers, marketers, and anyone else in IT write better content.</span></span>

<span data-ttu-id="a4edc-136">Mindre korrigeringar eller klargöranden av dokumentation och kod exempel i offentliga databaser omfattas av docs.microsoft.com användnings [villkor][terms-of-use].</span><span class="sxs-lookup"><span data-stu-id="a4edc-136">Minor corrections or clarifications to documentation and code examples in public repositories are covered by the docs.microsoft.com [Terms of Use][terms-of-use].</span></span>

<span data-ttu-id="a4edc-137">Använd det fullständiga GitHub-arbetsflödet när du gör betydande ändringar.</span><span class="sxs-lookup"><span data-stu-id="a4edc-137">Use the full GitHub workflow when you're making significant changes.</span></span> <span data-ttu-id="a4edc-138">Om du inte är anställd hos Microsoft genererar betydande ändringar en kommentar i pull-begäran som ber dig att skicka ett [licens avtal för CLA (online bidrag)][cla].</span><span class="sxs-lookup"><span data-stu-id="a4edc-138">If you're not an employee of Microsoft, significant changes generate a comment in the pull request that asks you to submit an online [Contribution Licensing Agreement (CLA)][cla].</span></span> <span data-ttu-id="a4edc-139">Du måste fylla i hela online-formuläret innan vi kan granska eller acceptera din pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="a4edc-139">We need you to complete the online form before we can review or accept your pull request.</span></span>

## <a name="code-of-conduct"></a><span data-ttu-id="a4edc-140">Uppförandekod</span><span class="sxs-lookup"><span data-stu-id="a4edc-140">Code of conduct</span></span>

<span data-ttu-id="a4edc-141">Alla informationslager som publicerar till docs.microsoft.com har antagit [Microsoft Open Source-uppförandekoden](https://opensource.microsoft.com/codeofconduct/) eller [.NET Foundation-uppförandekoden](https://dotnetfoundation.org/code-of-conduct).</span><span class="sxs-lookup"><span data-stu-id="a4edc-141">All repositories that publish to docs.microsoft.com have adopted the [Microsoft Open Source Code of Conduct](https://opensource.microsoft.com/codeofconduct/) or the [.NET Foundation Code of Conduct](https://dotnetfoundation.org/code-of-conduct).</span></span> <span data-ttu-id="a4edc-142">Mer information finns i [vanliga frågor och svar om uppförandekoden](https://opensource.microsoft.com/codeofconduct/faq/).</span><span class="sxs-lookup"><span data-stu-id="a4edc-142">For more information, see the [Code of Conduct FAQ](https://opensource.microsoft.com/codeofconduct/faq/).</span></span>

## <a name="next-steps"></a><span data-ttu-id="a4edc-143">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="a4edc-143">Next steps</span></span>

<span data-ttu-id="a4edc-144">Följande artiklar beskriver information som är unik för PowerShell-dokumentationen.</span><span class="sxs-lookup"><span data-stu-id="a4edc-144">The following articles cover information specific to PowerShell documentation.</span></span> <span data-ttu-id="a4edc-145">Om det finns överlappande vägledning i den centraliserade deltagar guiden, så kallar vi hur reglerna skiljer sig åt för PowerShell-innehållet.</span><span class="sxs-lookup"><span data-stu-id="a4edc-145">Where there's overlap with the guidance in the centralized Contributor's Guide, we call out how those rules differ for the PowerShell content.</span></span>

<span data-ttu-id="a4edc-146">Läs följande dokument:</span><span class="sxs-lookup"><span data-stu-id="a4edc-146">Review the following documents:</span></span>

- [<span data-ttu-id="a4edc-147">Så här arkiverar du ett problem</span><span class="sxs-lookup"><span data-stu-id="a4edc-147">How to file an issue</span></span>](file-an-issue.md)
- [<span data-ttu-id="a4edc-148">Komma igång med att skriva dokument</span><span class="sxs-lookup"><span data-stu-id="a4edc-148">Get started writing docs</span></span>](get-started-writing.md)
- [<span data-ttu-id="a4edc-149">Skicka en pull-begäran</span><span class="sxs-lookup"><span data-stu-id="a4edc-149">Submitting a pull request</span></span>](pull-requests.md)
- [<span data-ttu-id="a4edc-150">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="a4edc-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

<span data-ttu-id="a4edc-151">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="a4edc-151">Additional resources</span></span>

- [<span data-ttu-id="a4edc-152">Checklista för redigering</span><span class="sxs-lookup"><span data-stu-id="a4edc-152">Editorial checklist</span></span>](editorial-checklist.md)
- [<span data-ttu-id="a4edc-153">Så här hanterar vi problem</span><span class="sxs-lookup"><span data-stu-id="a4edc-153">How we manage issues</span></span>](managing-issues.md)
- [<span data-ttu-id="a4edc-154">Så här hanterar vi pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="a4edc-154">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[cla]: https://cla.microsoft.com/
[contribute]: /contribute/
[docs]: https://docs.microsoft.com/
[file-an-issue]: file-an-issue.md
[posh-git]: https://www.powershellgallery.com/packages/posh-git
[psdocs]: /powershell
[style-guide]: /style-guide/welcome/
[terms-of-use]: /legal/termsofuse
