---
title: Så här hanterar vi pull-begäranden
description: Den här artikeln förklarar hur PowerShell-Docs-teamet hanterar pull-begäranden.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 7050db6ad30963d0a75b2a083daace494d703027
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090533"
---
# <a name="managing-pull-requests"></a><span data-ttu-id="ab078-103">Hantera pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="ab078-103">Managing pull requests</span></span>

<span data-ttu-id="ab078-104">Den här artikeln dokumenterar hur vi hanterar pull-begäranden i PowerShell-Docs-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="ab078-104">This article documents how we manage pull requests in the PowerShell-Docs repository.</span></span> <span data-ttu-id="ab078-105">Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i PowerShell-Docss teamet.</span><span class="sxs-lookup"><span data-stu-id="ab078-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="ab078-106">Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.</span><span class="sxs-lookup"><span data-stu-id="ab078-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="best-practices"></a><span data-ttu-id="ab078-107">Bästa praxis</span><span class="sxs-lookup"><span data-stu-id="ab078-107">Best practices</span></span>

- <span data-ttu-id="ab078-108">Den person som skickar PR bör inte sammanfoga PR utan en peer-granskning.</span><span class="sxs-lookup"><span data-stu-id="ab078-108">The person submitting the PR shouldn't merge the PR without a peer review.</span></span>
- <span data-ttu-id="ab078-109">Tilldela peer-granskaren när PR skickas.</span><span class="sxs-lookup"><span data-stu-id="ab078-109">Assign the peer reviewer when the PR is submitted.</span></span> <span data-ttu-id="ab078-110">Med den tidiga tilldelningen kan granskaren svara snabbare med redaktionella kommentarer.</span><span class="sxs-lookup"><span data-stu-id="ab078-110">Early assignment allows the reviewer to respond sooner with editorial remarks.</span></span>
- <span data-ttu-id="ab078-111">Använd kommentarer för att beskriva vilken typ av ändring eller typ av granskning som begärs.</span><span class="sxs-lookup"><span data-stu-id="ab078-111">Use comments to describe the nature of the change or the type of review being requested.</span></span> <span data-ttu-id="ab078-112">Se till att @mention granskaren.</span><span class="sxs-lookup"><span data-stu-id="ab078-112">Be sure to @mention the reviewer.</span></span> <span data-ttu-id="ab078-113">Om ändringen till exempel är mindre och du inte behöver en fullständig teknisk granskning förklarar du detta i en kommentar.</span><span class="sxs-lookup"><span data-stu-id="ab078-113">For example, if the change is minor and you don't need a full technical review, explain this in a comment.</span></span>

## <a name="pr-process-steps"></a><span data-ttu-id="ab078-114">Steg för PR-processen</span><span class="sxs-lookup"><span data-stu-id="ab078-114">PR Process steps</span></span>

1. <span data-ttu-id="ab078-115">Skribent: skapa PR</span><span class="sxs-lookup"><span data-stu-id="ab078-115">Writer: Create PR</span></span>
   - <span data-ttu-id="ab078-116">Länka eventuella problem som löses av PR</span><span class="sxs-lookup"><span data-stu-id="ab078-116">Link any issues resolved by the PR</span></span>
   - <span data-ttu-id="ab078-117">Stänga problemet med GitHub [-funktionen](https://help.github.com/en/articles/closing-issues-using-keywords)</span><span class="sxs-lookup"><span data-stu-id="ab078-117">Use GitHub's [autoclose](https://help.github.com/en/articles/closing-issues-using-keywords) feature to close the issue</span></span>
1. <span data-ttu-id="ab078-118">Skribent: tilldela peer-granskare</span><span class="sxs-lookup"><span data-stu-id="ab078-118">Writer: Assign peer reviewer</span></span>
1. <span data-ttu-id="ab078-119">Granskare: korrektur och kommentarer (om det behövs)</span><span class="sxs-lookup"><span data-stu-id="ab078-119">Reviewer: proofreads and comments (as necessary)</span></span>
1. <span data-ttu-id="ab078-120">Skribent: införliva gransknings feedback</span><span class="sxs-lookup"><span data-stu-id="ab078-120">Writer: Incorporate review feedback</span></span>
1. <span data-ttu-id="ab078-121">Båda: granska åter givning av för hands version</span><span class="sxs-lookup"><span data-stu-id="ab078-121">Both: Review preview rendering</span></span>
1. <span data-ttu-id="ab078-122">Båda: granska validerings rapport-korrigera varningar och fel</span><span class="sxs-lookup"><span data-stu-id="ab078-122">Both: Review validation report - fix warnings and errors</span></span>
1. <span data-ttu-id="ab078-123">Skribent: Lägg till signerings kommentar (inkludera Acrolinx-information)</span><span class="sxs-lookup"><span data-stu-id="ab078-123">Writer: Add sign-off comment (include Acrolinx info)</span></span>
1. <span data-ttu-id="ab078-124">Granskare: markerings granskning "godkänd"</span><span class="sxs-lookup"><span data-stu-id="ab078-124">Reviewer: Mark review "Approved"</span></span>
1. <span data-ttu-id="ab078-125">Lagrings platsen admin: slå samman PR (se nedan för villkor)</span><span class="sxs-lookup"><span data-stu-id="ab078-125">Repo Admin: Merge PR (see below for criteria)</span></span>

## <a name="content-reviewer-checklist"></a><span data-ttu-id="ab078-126">Check lista för innehålls granskare</span><span class="sxs-lookup"><span data-stu-id="ab078-126">Content Reviewer Checklist</span></span>

<span data-ttu-id="ab078-127">Se [redaktionell check lista](editorial-checklist.md) för en mer omfattande lista.</span><span class="sxs-lookup"><span data-stu-id="ab078-127">See the [editorial checklist](editorial-checklist.md) for a more comprehensive list.</span></span>

- <span data-ttu-id="ab078-128">Korrektur Läs för grammatik, stil, concision, teknisk precision</span><span class="sxs-lookup"><span data-stu-id="ab078-128">Proofread for grammar, style, concision, technical accuracy</span></span>
- <span data-ttu-id="ab078-129">Se till att exempel fortfarande gäller för mål versionen</span><span class="sxs-lookup"><span data-stu-id="ab078-129">Ensure examples still apply for the target version</span></span>
- <span data-ttu-id="ab078-130">Kontrol lera för hands versions åter givning</span><span class="sxs-lookup"><span data-stu-id="ab078-130">Check Preview rendering</span></span>
- <span data-ttu-id="ab078-131">Kontrol lera metadata-MS. date, ta bort MS. AssetID, se till att obligatoriska fält</span><span class="sxs-lookup"><span data-stu-id="ab078-131">Check metadata - ms.date, remove ms.assetid, ensure required fields</span></span>
- <span data-ttu-id="ab078-132">Verifiera markdown-korrigering</span><span class="sxs-lookup"><span data-stu-id="ab078-132">Validate markdown correctness</span></span>
  - <span data-ttu-id="ab078-133">Se stil guide för regler för innehålls bestämd formatering</span><span class="sxs-lookup"><span data-stu-id="ab078-133">See style guide for content-specific formatting rules</span></span>
- <span data-ttu-id="ab078-134">Organisera om exempel enligt följande:</span><span class="sxs-lookup"><span data-stu-id="ab078-134">Reorganize examples as follows:</span></span>
  - <span data-ttu-id="ab078-135">Introduktions mening (er)</span><span class="sxs-lookup"><span data-stu-id="ab078-135">Intro sentence(s)</span></span>
  - <span data-ttu-id="ab078-136">Kod och utdata</span><span class="sxs-lookup"><span data-stu-id="ab078-136">Code and output</span></span>
  - <span data-ttu-id="ab078-137">Detaljerad kod förklaring (vid behov)</span><span class="sxs-lookup"><span data-stu-id="ab078-137">Detailed explanation of code (as necessary)</span></span>
- <span data-ttu-id="ab078-138">Kontrol lera hyperlänkarna efter precision</span><span class="sxs-lookup"><span data-stu-id="ab078-138">Check hyperlinks for accuracy</span></span>
  - <span data-ttu-id="ab078-139">Ersätta eller ta bort TechNet/MSDN-länkar</span><span class="sxs-lookup"><span data-stu-id="ab078-139">Replace or remove TechNet/MSDN links</span></span>
  - <span data-ttu-id="ab078-140">Se till att det lägsta antalet omdirigeringar är målet</span><span class="sxs-lookup"><span data-stu-id="ab078-140">Ensure minimum number of redirects to target</span></span>
  - <span data-ttu-id="ab078-141">Se till att HTTPS</span><span class="sxs-lookup"><span data-stu-id="ab078-141">Ensure HTTPS</span></span>
  - <span data-ttu-id="ab078-142">Rätt länktyp</span><span class="sxs-lookup"><span data-stu-id="ab078-142">Correct link type</span></span>
    - <span data-ttu-id="ab078-143">Fil länkar för lokala filer</span><span class="sxs-lookup"><span data-stu-id="ab078-143">File links for local files</span></span>
    - <span data-ttu-id="ab078-144">URL-länkar för filer utanför dokument uppsättning</span><span class="sxs-lookup"><span data-stu-id="ab078-144">URL links for files outside of the docset</span></span>
  - <span data-ttu-id="ab078-145">Ta bort språk från URL: er</span><span class="sxs-lookup"><span data-stu-id="ab078-145">Remove locales from URLs</span></span>
  - <span data-ttu-id="ab078-146">Förenkla webb adresser som pekar på `docs.microsoft.com`</span><span class="sxs-lookup"><span data-stu-id="ab078-146">Simplify URLs pointing to `docs.microsoft.com`</span></span>

## <a name="branch-merge-process"></a><span data-ttu-id="ab078-147">Gren sammanfognings process</span><span class="sxs-lookup"><span data-stu-id="ab078-147">Branch Merge Process</span></span>

<span data-ttu-id="ab078-148">`staging`Grenen är den enda gren som sammanfogas till `live` .</span><span class="sxs-lookup"><span data-stu-id="ab078-148">The `staging` branch is the only branch that is merged into `live`.</span></span> <span data-ttu-id="ab078-149">Sammanfogningar från förgreningar (arbets) grenar ska vara squashed.</span><span class="sxs-lookup"><span data-stu-id="ab078-149">Merges from short-lived (working) branches should be squashed.</span></span>

| <span data-ttu-id="ab078-150">*Sammanfoga från/till*</span><span class="sxs-lookup"><span data-stu-id="ab078-150">*Merge from/to*</span></span>  | <span data-ttu-id="ab078-151">*version – gren*</span><span class="sxs-lookup"><span data-stu-id="ab078-151">*release-branch*</span></span> | <span data-ttu-id="ab078-152">*mellanlagringsområdet*</span><span class="sxs-lookup"><span data-stu-id="ab078-152">*staging*</span></span>        | <span data-ttu-id="ab078-153">*realtidsinformation*</span><span class="sxs-lookup"><span data-stu-id="ab078-153">*live*</span></span>      |
| ---------------- |:----------------:|:----------------:|:-----------:|
| <span data-ttu-id="ab078-154">*arbets gren*</span><span class="sxs-lookup"><span data-stu-id="ab078-154">*working-branch*</span></span> | <span data-ttu-id="ab078-155">squash och slå samman</span><span class="sxs-lookup"><span data-stu-id="ab078-155">squash and merge</span></span> | <span data-ttu-id="ab078-156">squash och slå samman</span><span class="sxs-lookup"><span data-stu-id="ab078-156">squash and merge</span></span> | <span data-ttu-id="ab078-157">Inte tillåtet</span><span class="sxs-lookup"><span data-stu-id="ab078-157">Not allowed</span></span> |
| <span data-ttu-id="ab078-158">*version – gren*</span><span class="sxs-lookup"><span data-stu-id="ab078-158">*release-branch*</span></span> | &mdash;          | <span data-ttu-id="ab078-159">merge</span><span class="sxs-lookup"><span data-stu-id="ab078-159">merge</span></span>            | <span data-ttu-id="ab078-160">Inte tillåtet</span><span class="sxs-lookup"><span data-stu-id="ab078-160">Not allowed</span></span> |
| <span data-ttu-id="ab078-161">*mellanlagringsområdet*</span><span class="sxs-lookup"><span data-stu-id="ab078-161">*staging*</span></span>        | <span data-ttu-id="ab078-162">basera</span><span class="sxs-lookup"><span data-stu-id="ab078-162">rebase</span></span>           | &mdash;          | <span data-ttu-id="ab078-163">merge</span><span class="sxs-lookup"><span data-stu-id="ab078-163">merge</span></span>       |

### <a name="pr-merger-checklist"></a><span data-ttu-id="ab078-164">Check lista för PR fusion</span><span class="sxs-lookup"><span data-stu-id="ab078-164">PR Merger checklist</span></span>

- <span data-ttu-id="ab078-165">Innehålls granskning slutförd</span><span class="sxs-lookup"><span data-stu-id="ab078-165">Content review complete</span></span>
- <span data-ttu-id="ab078-166">Korrigera mål gren för ändringen</span><span class="sxs-lookup"><span data-stu-id="ab078-166">Correct target branch for the change</span></span>
- <span data-ttu-id="ab078-167">Inga sammanslagnings konflikter</span><span class="sxs-lookup"><span data-stu-id="ab078-167">No merge conflicts</span></span>
- <span data-ttu-id="ab078-168">Alla validerings-och bygg stegs steg</span><span class="sxs-lookup"><span data-stu-id="ab078-168">All validation and build step pass</span></span>
  - <span data-ttu-id="ab078-169">Varningar och förslag bör åtgärdas (se [kommentarer](#notes) för undantag)</span><span class="sxs-lookup"><span data-stu-id="ab078-169">Warnings and suggestions should be fixed (see [Notes](#notes) for exceptions)</span></span>
  - <span data-ttu-id="ab078-170">Inga brutna länkar</span><span class="sxs-lookup"><span data-stu-id="ab078-170">No broken links</span></span>
- <span data-ttu-id="ab078-171">Sammanfoga enligt tabell</span><span class="sxs-lookup"><span data-stu-id="ab078-171">Merge according to table</span></span>

### <a name="notes"></a><span data-ttu-id="ab078-172">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ab078-172">Notes</span></span>

<span data-ttu-id="ab078-173">Följande varningar kan ignoreras:</span><span class="sxs-lookup"><span data-stu-id="ab078-173">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="ab078-174">När en PR slås samman ändras huvud grenen i mål grenen.</span><span class="sxs-lookup"><span data-stu-id="ab078-174">When a PR is merged, the HEAD of the target branch is changed.</span></span> <span data-ttu-id="ab078-175">Alla öppna pull som var baserade på föregående huvud är nu föråldrade.</span><span class="sxs-lookup"><span data-stu-id="ab078-175">Any open PRs that were based on the previous HEAD are now outdated.</span></span> <span data-ttu-id="ab078-176">Föråldrade PR kan slås samman med administratörs behörighet för att åsidosätta sammanslagnings varningar i GitHub.</span><span class="sxs-lookup"><span data-stu-id="ab078-176">The outdated PR can be merged using Admin rights to override the merge warnings in GitHub.</span></span> <span data-ttu-id="ab078-177">Detta är säkert att göra om de tidigare sammanfogade PRarna inte har retuscherat samma filer.</span><span class="sxs-lookup"><span data-stu-id="ab078-177">This is safe to do if the previously merged PR(s) have not touched the same files.</span></span> <span data-ttu-id="ab078-178">Att klicka på knappen **Uppdatera gren** är dock det säkraste alternativet.</span><span class="sxs-lookup"><span data-stu-id="ab078-178">However, clicking the **Update Branch** button is the safest option.</span></span> <span data-ttu-id="ab078-179">Du kan ha olösta konflikter som måste åtgärdas.</span><span class="sxs-lookup"><span data-stu-id="ab078-179">You may have unresolved conflicts that need to be fixed.</span></span>

## <a name="publishing-to-live"></a><span data-ttu-id="ab078-180">Publicera till Live</span><span class="sxs-lookup"><span data-stu-id="ab078-180">Publishing to Live</span></span>

<span data-ttu-id="ab078-181">Med jämna mellanrum måste ändringarna som har ackumulerats i `staging` grenen publiceras på den aktiva webbplatsen.</span><span class="sxs-lookup"><span data-stu-id="ab078-181">Periodically, the changes accumulated in the `staging` branch need to be published to the live website.</span></span>

- <span data-ttu-id="ab078-182">`staging`Grenen slås samman till `live` varje veckodag på 3pm PST.</span><span class="sxs-lookup"><span data-stu-id="ab078-182">The `staging` branch is merged to `live` each weekday at 3pm PST.</span></span>
- <span data-ttu-id="ab078-183">`staging`Grenen ska slås samman till `live` efter en betydande ändring.</span><span class="sxs-lookup"><span data-stu-id="ab078-183">The `staging` branch should be merged to `live` after any significant change.</span></span>
  - <span data-ttu-id="ab078-184">Ändringar i 50 eller fler filer</span><span class="sxs-lookup"><span data-stu-id="ab078-184">Changes to 50 or more files</span></span>
  - <span data-ttu-id="ab078-185">Efter sammanslagning av en versions gren</span><span class="sxs-lookup"><span data-stu-id="ab078-185">After merging a release branch</span></span>
  - <span data-ttu-id="ab078-186">Ändringar av lagrings platsen-eller dokument uppsättning-konfigurationer (docfx.jspå, OPS-konfiguration, bygg skript osv.)</span><span class="sxs-lookup"><span data-stu-id="ab078-186">Changes to repo or docset configurations (docfx.json, OPS configs, build scripts, etc.)</span></span>
  - <span data-ttu-id="ab078-187">Ändringar av omdirigerings filen</span><span class="sxs-lookup"><span data-stu-id="ab078-187">Changes to the redirection file</span></span>
  - <span data-ttu-id="ab078-188">Ändringar i innehålls förteckningen</span><span class="sxs-lookup"><span data-stu-id="ab078-188">Changes to the TOC</span></span>
  - <span data-ttu-id="ab078-189">Efter sammanslagning av en "Project"-gren (Content reorg, Mass uppdatering osv.)</span><span class="sxs-lookup"><span data-stu-id="ab078-189">After merging a "project" branch (content reorg, bulk update, etc.)</span></span>
