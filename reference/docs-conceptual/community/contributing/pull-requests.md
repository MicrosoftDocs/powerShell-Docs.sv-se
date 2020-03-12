---
title: Skicka pull-begäranden
description: Den här artikeln beskriver hur du skickar pull-begäranden till databasen PowerShell-dok.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 2600049b06da5ad4869b6ff335f00bc40c2d1c22
ms.sourcegitcommit: 18d832858a7b8ea094763afa753e0f48f01372e7
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/10/2020
ms.locfileid: "79078509"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="c16bf-103">Skicka pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="c16bf-103">How to submit pull requests</span></span>

<span data-ttu-id="c16bf-104">Skicka en pull-begäran (PR) från din förgrening om du vill göra ändringar i innehållet.</span><span class="sxs-lookup"><span data-stu-id="c16bf-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="c16bf-105">En pull-begäran måste granskas innan den kan sammanfogas.</span><span class="sxs-lookup"><span data-stu-id="c16bf-105">A pull request must be reviewed before it can merged.</span></span> <span data-ttu-id="c16bf-106">För bästa resultat bör du läsa igenom [redaktionell check lista](editorial-checklist.md) innan du skickar din pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="c16bf-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="target-the-correct-branch"></a><span data-ttu-id="c16bf-107">Rikta in dig på rätt gren</span><span class="sxs-lookup"><span data-stu-id="c16bf-107">Target the correct branch</span></span>

<span data-ttu-id="c16bf-108">Alla pull-begäranden bör vara riktade till `staging` grenen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-108">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="c16bf-109">Ändringar ska aldrig skickas till `live` grenen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-109">Changes should never be submitted to the `live` branch.</span></span> <span data-ttu-id="c16bf-110">Ändringar som görs i `staging` grenen sammanfogas i `live`och skriver över eventuella ändringar som gjorts i `live`.</span><span class="sxs-lookup"><span data-stu-id="c16bf-110">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

<span data-ttu-id="c16bf-111">Om du skickar en ändring som bara gäller för en version av PowerShell som är en utgåva, söker du efter en versions gren för den versionen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-111">If you are submitting a change that only applies to an unreleased version of PowerShell, check for a release branch for that version.</span></span> <span data-ttu-id="c16bf-112">Din PR ska vara riktad mot lanserings grenen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-112">Your PR should be targeted at the release branch.</span></span> <span data-ttu-id="c16bf-113">Versions grenar har följande namn mönster: `release-<version>`.</span><span class="sxs-lookup"><span data-stu-id="c16bf-113">Release branches have the following name pattern: `release-<version>`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="c16bf-114">Gör så att pull-begäran fungerar bättre för alla</span><span class="sxs-lookup"><span data-stu-id="c16bf-114">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="c16bf-115">Den enklare och mer fokuserade du kan göra din PR, desto snabbare kan du granska och slå samman.</span><span class="sxs-lookup"><span data-stu-id="c16bf-115">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-branches-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="c16bf-116">Undvik grenar som uppdaterar ett stort antal filer eller innehåller orelaterade ändringar</span><span class="sxs-lookup"><span data-stu-id="c16bf-116">Avoid branches that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="c16bf-117">Undvik att skapa pull som innehåller orelaterade ändringar.</span><span class="sxs-lookup"><span data-stu-id="c16bf-117">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="c16bf-118">Separata mindre uppdateringar av befintliga artiklar från nya artiklar eller större omskrivning.</span><span class="sxs-lookup"><span data-stu-id="c16bf-118">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="c16bf-119">Arbeta med dessa ändringar i separata arbets grenar.</span><span class="sxs-lookup"><span data-stu-id="c16bf-119">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="c16bf-120">Mass ändringar skapa pull med ett stort antal ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="c16bf-120">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="c16bf-121">Begränsa din pull till högst 50 ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="c16bf-121">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="c16bf-122">Stora pull är svåra att granska och är mer känsliga för att innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="c16bf-122">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="c16bf-123">Byta namn på eller ta bort filer</span><span class="sxs-lookup"><span data-stu-id="c16bf-123">Renaming or deleting files</span></span>

<span data-ttu-id="c16bf-124">Om du byter namn på eller tar bort filer måste det finnas ett problem som är kopplat till PR.</span><span class="sxs-lookup"><span data-stu-id="c16bf-124">If you are renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="c16bf-125">Det här problemet måste diskutera behovet av att byta namn på eller ta bort filerna.</span><span class="sxs-lookup"><span data-stu-id="c16bf-125">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="c16bf-126">Undvik att blanda innehålls tillägg eller ändra med fil namn och borttagningar.</span><span class="sxs-lookup"><span data-stu-id="c16bf-126">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="c16bf-127">Alla filer som har bytt namn eller tas bort måste läggas till i Master-omdirigerings filen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-127">Any file that is renamed or deleted must be added to the master redirection file.</span></span> <span data-ttu-id="c16bf-128">När det är möjligt bör du också uppdatera alla filer som länkar till innehållet som har bytt namn eller tagits bort.</span><span class="sxs-lookup"><span data-stu-id="c16bf-128">When possible, you should also update any files that link to the renamed or deleted content.</span></span> <span data-ttu-id="c16bf-129">Detta inkluderar alla TOC-filer.</span><span class="sxs-lookup"><span data-stu-id="c16bf-129">This includes any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="c16bf-130">Tjänst för dokument PR-validering</span><span class="sxs-lookup"><span data-stu-id="c16bf-130">Docs PR validation service</span></span>

<span data-ttu-id="c16bf-131">Verifierings tjänsten för dokument PR är en GitHub-app som kör verifierings regler på filerna i en PR.</span><span class="sxs-lookup"><span data-stu-id="c16bf-131">The Docs PR validation service is a GitHub app that runs validation rules on the files in a PR.</span></span> <span data-ttu-id="c16bf-132">Du måste åtgärda eventuella fel eller varningar (se undantag) som rapporteras av validerings tjänsten.</span><span class="sxs-lookup"><span data-stu-id="c16bf-132">You must fix any errors or warnings (see exceptions) reported by the validation service.</span></span>

<span data-ttu-id="c16bf-133">Följande varningar kan ignoreras:</span><span class="sxs-lookup"><span data-stu-id="c16bf-133">The following warnings can be ignored:</span></span>

```
Can't find service name for `<version>/<modulepath>/About/About.md`
```

```
Metadata with following name(s) are not allowed to be set in Yaml header, or as file level
metadata in docfx.json, or as global metadata in docfx.json: `locale`. They are generated by
Docs platform, so the values set in these 3 places will be ignored. Please remove them from all
3 places to resolve the warning.
```

<span data-ttu-id="c16bf-134">Du ser följande beteende:</span><span class="sxs-lookup"><span data-stu-id="c16bf-134">You'll see the following behavior:</span></span>

1. <span data-ttu-id="c16bf-135">Du skickar en PR.</span><span class="sxs-lookup"><span data-stu-id="c16bf-135">You submit a PR.</span></span>
1. <span data-ttu-id="c16bf-136">I GitHub-kommentaren som visar statusen för din PR ser du statusen "checkar" aktiverade på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-136">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repo.</span></span> <span data-ttu-id="c16bf-137">Observera att i det här exemplet finns det två kontroller aktiverade, "commit Validation" och "openpublishing. Build":</span><span class="sxs-lookup"><span data-stu-id="c16bf-137">Note that in this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![vissa kontroller misslyckades](media/pull-requests/validation-failed.png)

   <span data-ttu-id="c16bf-139">Bygget kan klara även om bekräftelse valideringen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="c16bf-139">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="c16bf-140">Klicka på **information** om du vill ha mer information.</span><span class="sxs-lookup"><span data-stu-id="c16bf-140">Click **Details** for more information.</span></span>
1. <span data-ttu-id="c16bf-141">På informations sidan visas alla verifierings kontroller som misslyckades, med information om hur du åtgärdar problemen.</span><span class="sxs-lookup"><span data-stu-id="c16bf-141">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="c16bf-142">När verifieringen lyckas läggs följande kommentar till i PR:</span><span class="sxs-lookup"><span data-stu-id="c16bf-142">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Bygg validering](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="c16bf-144">Om du är en extern deltagare (inte en Microsoft-anställd) har du inte åtkomst till de detaljerade build-rapporterna eller för hands versions länkar.</span><span class="sxs-lookup"><span data-stu-id="c16bf-144">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="c16bf-145">När PR granskas av en medlem i gruppen PowerShell-dok, kan du bli ombedd att göra ändringar eller åtgärda problem som har flaggats i verifierings rapporten.</span><span class="sxs-lookup"><span data-stu-id="c16bf-145">When the PR is reviewed by a member of the PowerShell-Docs team, you may be asked to make changes or fix problems flagged by the validation report.</span></span> <span data-ttu-id="c16bf-146">Gruppen PowerShell-dok kan hjälpa dig att förstå hur du kan åtgärda och undvika de här problemen för framtida bidrag.</span><span class="sxs-lookup"><span data-stu-id="c16bf-146">The PowerShell-Docs team can help you understand how to fix and avoid these problems for future submissions.</span></span>

## <a name="next-steps"></a><span data-ttu-id="c16bf-147">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="c16bf-147">Next steps</span></span>

[<span data-ttu-id="c16bf-148">PowerShell – format guide för dokument</span><span class="sxs-lookup"><span data-stu-id="c16bf-148">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="c16bf-149">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="c16bf-149">Additional resources</span></span>

[<span data-ttu-id="c16bf-150">Hur vi hanterar pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="c16bf-150">How we manage pull requests</span></span>](managing-pull-requests.md)
