---
title: Skicka pull-begäranden
description: Den här artikeln beskriver hur du skickar pull-begäranden till databasen PowerShell-dok.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 8b392a36c9469b83cf4f088c1799720a091434b4
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87782658"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="29130-103">Skicka pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="29130-103">How to submit pull requests</span></span>

<span data-ttu-id="29130-104">Skicka en pull-begäran (PR) från din förgrening om du vill göra ändringar i innehållet.</span><span class="sxs-lookup"><span data-stu-id="29130-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="29130-105">En pull-begäran måste granskas innan den kan sammanfogas.</span><span class="sxs-lookup"><span data-stu-id="29130-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="29130-106">För bästa resultat bör du läsa igenom [redaktionell check lista](editorial-checklist.md) innan du skickar din pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="29130-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="29130-107">Rikta in dig på rätt gren</span><span class="sxs-lookup"><span data-stu-id="29130-107">Target the correct branch</span></span>

<span data-ttu-id="29130-108">Alla pull-begäranden bör riktas mot `staging` grenen.</span><span class="sxs-lookup"><span data-stu-id="29130-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="29130-109">Ändringar ska aldrig skickas till `live` grenen.</span><span class="sxs-lookup"><span data-stu-id="29130-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="29130-110">Ändringar som görs i `staging` grenen sammanfogas i `live` och skriver över eventuella ändringar som gjorts i `live` .</span><span class="sxs-lookup"><span data-stu-id="29130-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="29130-111">Om du skickar en ändring som bara gäller för en version av PowerShell som är en utgåva, söker du efter en versions gren för den versionen.</span><span class="sxs-lookup"><span data-stu-id="29130-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="29130-112">Din PR ska vara riktad mot lanserings grenen.</span><span class="sxs-lookup"><span data-stu-id="29130-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="29130-113">Versionsgrenar har följande namnmönster: `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="29130-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="29130-114">Gör så att pull-begäran fungerar bättre för alla</span><span class="sxs-lookup"><span data-stu-id="29130-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="29130-115">Den enklare och mer fokuserade du kan göra din PR, desto snabbare kan du granska och slå samman.</span><span class="sxs-lookup"><span data-stu-id="29130-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="29130-116">Undvik grenar som uppdaterar ett stort antal filer eller innehåller orelaterade ändringar</span><span class="sxs-lookup"><span data-stu-id="29130-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="29130-117">Undvik att skapa pull som innehåller orelaterade ändringar.</span><span class="sxs-lookup"><span data-stu-id="29130-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="29130-118">Olika små uppdateringar i befintliga artiklar från nya artiklar eller större omskrivningar.</span><span class="sxs-lookup"><span data-stu-id="29130-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="29130-119">Arbeta på dessa ändringar i olika arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="29130-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="29130-120">Mass ändringar skapa pull med ett stort antal ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="29130-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="29130-121">Begränsa din pull-begäran till högst 50 ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="29130-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="29130-122">Stora pull-begäranden är svåra att granska och är mer benägna att innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="29130-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="29130-123">Byta namn på eller ta bort filer</span><span class="sxs-lookup"><span data-stu-id="29130-123">Renaming or deleting files</span></span>

<span data-ttu-id="29130-124">Om du byter namn på eller tar bort filer måste det finnas ett problem som är kopplat till PR.</span><span class="sxs-lookup"><span data-stu-id="29130-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="29130-125">Det här problemet måste diskutera behovet av att byta namn på eller ta bort filerna.</span><span class="sxs-lookup"><span data-stu-id="29130-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="29130-126">Undvik att blanda innehålls tillägg eller ändra med fil namn och borttagningar.</span><span class="sxs-lookup"><span data-stu-id="29130-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="29130-127">Alla filer som har bytt namn eller tas bort måste läggas till i Master-omdirigerings filen.</span><span class="sxs-lookup"><span data-stu-id="29130-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="29130-128">När det är möjligt bör du också uppdatera alla filer som länkar till innehållet som har bytt namn eller tagits bort.</span><span class="sxs-lookup"><span data-stu-id="29130-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="29130-129">Detta inkluderar alla TOC-filer.</span><span class="sxs-lookup"><span data-stu-id="29130-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="29130-130">Docs PR-valideringstjänst</span><span class="sxs-lookup"><span data-stu-id="29130-130">Docs PR validation service</span></span>

<span data-ttu-id="29130-131">Docs PR-valideringstjänsten är en GitHub-app som kör valideringsregler på filer i en PR.</span><span class="sxs-lookup"><span data-stu-id="29130-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="29130-132">Du måste åtgärda eventuella fel eller varningar (se undantag) som rapporteras av validerings tjänsten.</span><span class="sxs-lookup"><span data-stu-id="29130-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="29130-133">Följande varningar kan ignoreras:</span><span class="sxs-lookup"><span data-stu-id="29130-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="29130-134">Följande beteende kommer att visas:</span><span class="sxs-lookup"><span data-stu-id="29130-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="29130-135">Du skickar en PR.</span><span class="sxs-lookup"><span data-stu-id="29130-135">You submit a PR.</span></span>
1. <span data-ttu-id="29130-136">I GitHub-kommentaren som visar statusen för din PR ser du statusen "checkar" aktiverade på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="29130-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="29130-137">Observera att två kontroller är aktiverade i det här exemplet: "Commit Validation" och "OpenPublishing.Build":</span><span class="sxs-lookup"><span data-stu-id="29130-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![validerings status-vissa kontroller misslyckades](media/pull-requests/validation-failed.png)

   <span data-ttu-id="29130-139">Bygget kan klara även om bekräftelse valideringen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="29130-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="29130-140">Klicka på **Details** (Detaljerad information) om du vill ha mer information.</span><span class="sxs-lookup"><span data-stu-id="29130-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="29130-141">På sidan Details (Detaljerad information) visas alla valideringskontroller som har misslyckats och information om hur du åtgärdar problemen.</span><span class="sxs-lookup"><span data-stu-id="29130-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="29130-142">När verifieringen lyckas läggs följande kommentar till i pull-begäran:</span><span class="sxs-lookup"><span data-stu-id="29130-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Validerings status: lyckad](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="29130-144">Om du är en extern deltagare (inte en Microsoft-anställd) har du inte åtkomst till de detaljerade build-rapporterna eller för hands versions länkar.</span><span class="sxs-lookup"><span data-stu-id="29130-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="29130-145">När PR granskas av en medlem i gruppen PowerShell-dok, kan du bli ombedd att göra ändringar eller åtgärda problem som har flaggats i verifierings rapporten.</span><span class="sxs-lookup"><span data-stu-id="29130-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="29130-146">Gruppen PowerShell-dok kan hjälpa dig att förstå hur du kan åtgärda och undvika de här problemen för framtida bidrag.</span><span class="sxs-lookup"><span data-stu-id="29130-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="29130-147">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="29130-147">Next steps</span></span>

[<span data-ttu-id="29130-148">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="29130-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="29130-149">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="29130-149">Additional resources</span></span>

[<span data-ttu-id="29130-150">Så här hanterar vi pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="29130-150">How we manage pull requests</span></span>](managing-pull-requests.md)
