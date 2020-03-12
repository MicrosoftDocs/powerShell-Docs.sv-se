---
title: Hur vi hanterar pull-begäranden
description: Den här artikeln förklarar hur PowerShell-dokument-teamet hanterar pull-begäranden.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: b9b37816dfdf38e4d8b7c2d66799164d0e97d257
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078614"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="1eb43-103">Hantera pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="1eb43-103">Managing pull requests</span></span>

<span data-ttu-id="1eb43-104">I den här artikeln beskrivs hur vi hanterar pull-begäranden i PowerShell-dok lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="1eb43-104">This article documents how we manage pull requests in the PowerShell-Docs repo.</span></span> <span data-ttu-id="1eb43-105">Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i gruppen PowerShell-dok.</span><span class="sxs-lookup"><span data-stu-id="1eb43-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="1eb43-106">Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.</span><span class="sxs-lookup"><span data-stu-id="1eb43-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="1eb43-107">Bästa praxis</span><span class="sxs-lookup"><span data-stu-id="1eb43-107">Best practices</span></span>

- <span data-ttu-id="1eb43-108">Den person som skickar in PR ska inte sammanfoga PR utan en peer-granskning.</span><span class="sxs-lookup"><span data-stu-id="1eb43-108">The person submitting the PR should not merge the PR without a peer review.</span></span>
- <span data-ttu-id="1eb43-109">Tilldela peer-granskaren när PR skickas.</span><span class="sxs-lookup"><span data-stu-id="1eb43-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="1eb43-110">Med den tidiga tilldelningen kan granskaren svara snabbare med redaktionella kommentarer.</span><span class="sxs-lookup"><span data-stu-id="1eb43-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="1eb43-111">Använd kommentarer för att beskriva vilken typ av ändring eller typ av granskning som begärs.</span><span class="sxs-lookup"><span data-stu-id="1eb43-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="1eb43-112">Se till att @mention granskaren.</span><span class="sxs-lookup"><span data-stu-id="1eb43-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="1eb43-113">Om ändringen till exempel är mindre och du inte behöver en fullständig teknisk granskning förklarar du detta i en kommentar.</span><span class="sxs-lookup"><span data-stu-id="1eb43-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="1eb43-114">Steg för PR-processen</span><span class="sxs-lookup"><span data-stu-id="1eb43-114">PR Process steps</span></span>

1. <span data-ttu-id="1eb43-115">Skribent: skapa PR</span><span class="sxs-lookup"><span data-stu-id="1eb43-115">Writer: Create PR</span></span>
   - <span data-ttu-id="1eb43-116">Länka eventuella problem som löses av PR</span><span class="sxs-lookup"><span data-stu-id="1eb43-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="1eb43-117">Stänga problemet med GitHub [-funktionen](https://help.github.com/en/articles/closing-issues-using-keywords)</span><span class="sxs-lookup"><span data-stu-id="1eb43-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="1eb43-118">Skribent: tilldela peer-granskare</span><span class="sxs-lookup"><span data-stu-id="1eb43-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="1eb43-119">Granskare: korrektur och kommentarer (om det behövs)</span><span class="sxs-lookup"><span data-stu-id="1eb43-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="1eb43-120">Skribent: införliva gransknings feedback</span><span class="sxs-lookup"><span data-stu-id="1eb43-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="1eb43-121">Båda: granska åter givning av för hands version</span><span class="sxs-lookup"><span data-stu-id="1eb43-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="1eb43-122">Båda: granska validerings rapport-korrigera varningar och fel</span><span class="sxs-lookup"><span data-stu-id="1eb43-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="1eb43-123">Skribent: Lägg till signerings kommentar (inkludera Acrolinx-information)</span><span class="sxs-lookup"><span data-stu-id="1eb43-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="1eb43-124">Granskare: markerings granskning "godkänd"</span><span class="sxs-lookup"><span data-stu-id="1eb43-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="1eb43-125">Lagrings platsen admin: slå samman PR (se nedan för villkor)</span><span class="sxs-lookup"><span data-stu-id="1eb43-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="1eb43-126">Check lista för innehålls granskare</span><span class="sxs-lookup"><span data-stu-id="1eb43-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="1eb43-127">Se [redaktionell check lista](editorial-checklist.md) för en mer omfattande lista.</span><span class="sxs-lookup"><span data-stu-id="1eb43-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="1eb43-128">Korrektur Läs för grammatik, stil, concision, teknisk precision</span><span class="sxs-lookup"><span data-stu-id="1eb43-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="1eb43-129">Se till att exempel fortfarande gäller för mål versionen</span><span class="sxs-lookup"><span data-stu-id="1eb43-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="1eb43-130">Kontrol lera för hands versions åter givning</span><span class="sxs-lookup"><span data-stu-id="1eb43-130">Check Preview rendering</span></span>
- <span data-ttu-id="1eb43-131">Kontrol lera metadata-MS. date, ta bort MS. AssetID, se till att obligatoriska fält</span><span class="sxs-lookup"><span data-stu-id="1eb43-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="1eb43-132">Verifiera markdown-korrigering</span><span class="sxs-lookup"><span data-stu-id="1eb43-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="1eb43-133">Se stil guide för formatering av speciellt innehåll</span><span class="sxs-lookup"><span data-stu-id="1eb43-133">See style guide for formatting specific content</span></span>
- <span data-ttu-id="1eb43-134">Organisera om exempel enligt följande:</span><span class="sxs-lookup"><span data-stu-id="1eb43-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="1eb43-135">Introduktions mening (er)</span><span class="sxs-lookup"><span data-stu-id="1eb43-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="1eb43-136">Kod och utdata</span><span class="sxs-lookup"><span data-stu-id="1eb43-136">Code and output</span></span>
  - <span data-ttu-id="1eb43-137">Detaljerad kod förklaring (vid behov)</span><span class="sxs-lookup"><span data-stu-id="1eb43-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="1eb43-138">Kontrol lera hyperlänkarna efter precision</span><span class="sxs-lookup"><span data-stu-id="1eb43-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="1eb43-139">Ersätta eller ta bort TechNet/MSDN-länkar</span><span class="sxs-lookup"><span data-stu-id="1eb43-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="1eb43-140">Se till att det lägsta antalet omdirigeringar är målet</span><span class="sxs-lookup"><span data-stu-id="1eb43-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="1eb43-141">Se till att HTTPS</span><span class="sxs-lookup"><span data-stu-id="1eb43-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="1eb43-142">Rätt länktyp</span><span class="sxs-lookup"><span data-stu-id="1eb43-142">Correct link type</span></span>
    - <span data-ttu-id="1eb43-143">Fil länkar för lokala filer</span><span class="sxs-lookup"><span data-stu-id="1eb43-143">File links for local files</span></span>
    - <span data-ttu-id="1eb43-144">URL-länkar för filer utanför dokument uppsättning</span><span class="sxs-lookup"><span data-stu-id="1eb43-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="1eb43-145">Ta bort språk från URL: er</span><span class="sxs-lookup"><span data-stu-id="1eb43-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="1eb43-146">Förenkla URL: er som pekar på `docs.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="1eb43-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="1eb43-147">Gren sammanfognings process</span><span class="sxs-lookup"><span data-stu-id="1eb43-147">Branch Merge Process</span></span>

<span data-ttu-id="1eb43-148">Mellanlagringsplatsen är den enda gren som någonsin ska slås samman i real tid.</span><span class="sxs-lookup"><span data-stu-id="1eb43-148">The staging branch is the only branch that should ever be merged into live.</span></span> <span data-ttu-id="1eb43-149">Sammanfogningar från förgreningar (arbets) grenar ska vara squashed.</span><span class="sxs-lookup"><span data-stu-id="1eb43-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="1eb43-150">*Sammanfoga från/till*</span><span class="sxs-lookup"><span data-stu-id="1eb43-150">*Merge from/to*</span></span>  | <span data-ttu-id="1eb43-151">*version – gren*</span><span class="sxs-lookup"><span data-stu-id="1eb43-151">*release-branch*</span></span> | <span data-ttu-id="1eb43-152">*mellanlagringsområdet*</span><span class="sxs-lookup"><span data-stu-id="1eb43-152">*staging*</span></span>        | <span data-ttu-id="1eb43-153">*realtidsinformation*</span><span class="sxs-lookup"><span data-stu-id="1eb43-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="1eb43-154">*arbets gren*</span><span class="sxs-lookup"><span data-stu-id="1eb43-154">*working-branch*</span></span> | <span data-ttu-id="1eb43-155">squash och slå samman</span><span class="sxs-lookup"><span data-stu-id="1eb43-155">squash and merge</span></span> | <span data-ttu-id="1eb43-156">squash och slå samman</span><span class="sxs-lookup"><span data-stu-id="1eb43-156">squash and merge</span></span> | <span data-ttu-id="1eb43-157">Inte tillåten</span><span class="sxs-lookup"><span data-stu-id="1eb43-157">Not allowed</span></span> |
| <span data-ttu-id="1eb43-158">*version – gren*</span><span class="sxs-lookup"><span data-stu-id="1eb43-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="1eb43-159">Katalog</span><span class="sxs-lookup"><span data-stu-id="1eb43-159">merge</span></span>            | <span data-ttu-id="1eb43-160">Inte tillåten</span><span class="sxs-lookup"><span data-stu-id="1eb43-160">Not allowed</span></span> |
| <span data-ttu-id="1eb43-161">*mellanlagringsområdet*</span><span class="sxs-lookup"><span data-stu-id="1eb43-161">*staging*</span></span>        | <span data-ttu-id="1eb43-162">basera</span><span class="sxs-lookup"><span data-stu-id="1eb43-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="1eb43-163">Katalog</span><span class="sxs-lookup"><span data-stu-id="1eb43-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="1eb43-164">Check lista för PR fusion</span><span class="sxs-lookup"><span data-stu-id="1eb43-164">PR Merger checklist</span></span>

- <span data-ttu-id="1eb43-165">Innehålls granskning slutförd</span><span class="sxs-lookup"><span data-stu-id="1eb43-165">Content review complete</span></span>
- <span data-ttu-id="1eb43-166">Korrigera mål gren för ändringen</span><span class="sxs-lookup"><span data-stu-id="1eb43-166">Correct target branch for the change</span></span>
- <span data-ttu-id="1eb43-167">Inga sammanslagnings konflikter</span><span class="sxs-lookup"><span data-stu-id="1eb43-167">No merge conflicts</span></span>
- <span data-ttu-id="1eb43-168">Alla validerings-och bygg stegs steg</span><span class="sxs-lookup"><span data-stu-id="1eb43-168">All validation and build step pass</span></span>
  - <span data-ttu-id="1eb43-169">Varningar och förslag bör åtgärdas (se [kommentarer](#notes) för undantag)</span><span class="sxs-lookup"><span data-stu-id="1eb43-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="1eb43-170">Inga brutna länkar</span><span class="sxs-lookup"><span data-stu-id="1eb43-170">No broken links</span></span>
- <span data-ttu-id="1eb43-171">Sammanfoga enligt tabell</span><span class="sxs-lookup"><span data-stu-id="1eb43-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="1eb43-172">Anteckningar</span><span class="sxs-lookup"><span data-stu-id="1eb43-172">Notes</span></span>

<span data-ttu-id="1eb43-173">Följande varningar kan ignoreras:</span><span class="sxs-lookup"><span data-stu-id="1eb43-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="1eb43-174">När en PR slås samman ändras huvud grenen i mål grenen.</span><span class="sxs-lookup"><span data-stu-id="1eb43-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="1eb43-175">Alla öppna pull som var baserade på föregående huvud är nu föråldrade.</span><span class="sxs-lookup"><span data-stu-id="1eb43-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="1eb43-176">Föråldrade PR kan slås samman med administratörs behörighet för att åsidosätta sammanslagnings varningar i GitHub.</span><span class="sxs-lookup"><span data-stu-id="1eb43-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="1eb43-177">Detta är säkert att göra om de tidigare sammanfogade PRarna inte har retuscherat samma filer.</span><span class="sxs-lookup"><span data-stu-id="1eb43-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="1eb43-178">Att klicka på knappen **Uppdatera gren** är dock det säkraste alternativet.</span><span class="sxs-lookup"><span data-stu-id="1eb43-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="1eb43-179">Du kan ha olösta konflikter som måste åtgärdas.</span><span class="sxs-lookup"><span data-stu-id="1eb43-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="1eb43-180">Publicera till Live</span><span class="sxs-lookup"><span data-stu-id="1eb43-180">Publishing to Live</span></span>

<span data-ttu-id="1eb43-181">Med jämna mellanrum måste ändringarna som har samlats in i `staging` grenen publiceras på den aktiva webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="1eb43-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span> <span data-ttu-id="1eb43-182">Detta kräver att `staging` grenen slås samman i `live` grenen.</span><span class="sxs-lookup"><span data-stu-id="1eb43-182">This require merging the `staging` branch into the `live` branch.</span></span>

- <span data-ttu-id="1eb43-183">`staging` grenen ska slås samman till `live` minst en gång per vecka.</span><span class="sxs-lookup"><span data-stu-id="1eb43-183">The `staging` branch should be merged to `live` at least once per week.</span></span>
- <span data-ttu-id="1eb43-184">`staging` grenen ska slås samman till `live` efter en betydande ändring.</span><span class="sxs-lookup"><span data-stu-id="1eb43-184">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="1eb43-185">Ändringar i 50 eller fler filer</span><span class="sxs-lookup"><span data-stu-id="1eb43-185">Changes to 50 or more files</span></span>
  - <span data-ttu-id="1eb43-186">Efter sammanslagning av en versions gren</span><span class="sxs-lookup"><span data-stu-id="1eb43-186">After merging a release branch</span></span>
  - <span data-ttu-id="1eb43-187">Ändringar av lagrings platsen-eller dokument uppsättning-konfigurationer (docfx. JSON, OPS configs, build-skript osv.)</span><span class="sxs-lookup"><span data-stu-id="1eb43-187">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="1eb43-188">Ändringar av omdirigerings filen</span><span class="sxs-lookup"><span data-stu-id="1eb43-188">Changes to the redirection file</span></span>
  - <span data-ttu-id="1eb43-189">Ändringar i innehålls förteckningen</span><span class="sxs-lookup"><span data-stu-id="1eb43-189">Changes to the TOC</span></span>
  - <span data-ttu-id="1eb43-190">Efter sammanslagning av en "Project"-gren (Content reorg, Mass uppdatering osv.)</span><span class="sxs-lookup"><span data-stu-id="1eb43-190">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
