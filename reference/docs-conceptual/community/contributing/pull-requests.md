---
title: Skicka pull-begäranden
description: Den här artikeln beskriver hur du skickar pull-begäranden till PowerShell-Docs-lagringsplatsen.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 1a21c25e19189aec4f48ad034147b02f4f804f9d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "97090217"
---
# <a name="how-to-submit-pull-requests"></a><span data-ttu-id="a1454-103">Skicka pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="a1454-103">How to submit pull requests</span></span>

<span data-ttu-id="a1454-104">Skicka en pull-begäran (PR) från din förgrening om du vill göra ändringar i innehållet.</span><span class="sxs-lookup"><span data-stu-id="a1454-104">To make changes to content, submit a pull request (PR) from your fork.</span></span> <span data-ttu-id="a1454-105">En pull-begäran måste granskas innan den kan slås samman.</span><span class="sxs-lookup"><span data-stu-id="a1454-105">A pull request must be reviewed before it can be merged.</span></span> <span data-ttu-id="a1454-106">För bästa resultat bör du läsa igenom [redaktionell check lista](editorial-checklist.md) innan du skickar din pull-begäran.</span><span class="sxs-lookup"><span data-stu-id="a1454-106">For best results, review the [editorial checklist](editorial-checklist.md) before submitting your pull request.</span></span>

## <a name="using-git-branches"></a><span data-ttu-id="a1454-107">Använda Git-grenar</span><span class="sxs-lookup"><span data-stu-id="a1454-107">Using git branches</span></span>

<span data-ttu-id="a1454-108">Standard grenen för PowerShell-Docs är `staging` grenen.</span><span class="sxs-lookup"><span data-stu-id="a1454-108">The default branch for PowerShell-Docs is the `staging` branch.</span></span> <span data-ttu-id="a1454-109">Ändringar som görs i arbets grenar sammanfogas i `staging` grenen innan de publiceras.</span><span class="sxs-lookup"><span data-stu-id="a1454-109">Changes made in working branches are merged into the `staging` branch before then being published.</span></span> <span data-ttu-id="a1454-110">`staging`Grenen slås samman i `live` grenen varje veckodag med 3:00 PM (Pacific Time).</span><span class="sxs-lookup"><span data-stu-id="a1454-110">The `staging` branch is merged into the `live` branch every weekday at 3:00 PM (Pacific Time).</span></span> <span data-ttu-id="a1454-111">`live`Grenen innehåller det innehåll som har publicerats till docs.Microsoft.com.</span><span class="sxs-lookup"><span data-stu-id="a1454-111">The `live` branch contains the content that is published to docs.microsoft.com.</span></span>

<span data-ttu-id="a1454-112">Innan du påbörjar ändringarna skapar du en arbets gren i din lokala kopia av PowerShell-Docs-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="a1454-112">Before starting any changes, create a working branch in your local copy of the PowerShell-Docs repository.</span></span> <span data-ttu-id="a1454-113">Var noga med att synkronisera din lokala lagrings plats innan du skapar din arbets gren när du arbetar lokalt.</span><span class="sxs-lookup"><span data-stu-id="a1454-113">When working locally, be sure to synchronize your local repository before creating your working branch.</span></span> <span data-ttu-id="a1454-114">Arbets grenen bör skapas från en uppdatering till dags kopia av `staging` grenen.</span><span class="sxs-lookup"><span data-stu-id="a1454-114">The working branch should be created from an update-to-date copy of the `staging` branch.</span></span>

<span data-ttu-id="a1454-115">Alla pull-begäranden bör riktas mot `staging` grenen.</span><span class="sxs-lookup"><span data-stu-id="a1454-115">All pull requests should target the `staging` branch.</span></span> <span data-ttu-id="a1454-116">Skicka inte ändringar till `live` grenen.</span><span class="sxs-lookup"><span data-stu-id="a1454-116">Don't submit change to the `live` branch.</span></span>
<span data-ttu-id="a1454-117">Ändringar som görs i `staging` grenen sammanfogas i `live` och skriver över eventuella ändringar som gjorts i `live` .</span><span class="sxs-lookup"><span data-stu-id="a1454-117">Changes made in the `staging` branch get merged into `live`, overwriting any changes made to `live`.</span></span>

## <a name="make-the-pull-request-process-work-better-for-everyone"></a><span data-ttu-id="a1454-118">Gör så att pull-begäran fungerar bättre för alla</span><span class="sxs-lookup"><span data-stu-id="a1454-118">Make the pull request process work better for everyone</span></span>

<span data-ttu-id="a1454-119">Den enklare och mer fokuserade du kan göra din PR, desto snabbare kan du granska och slå samman.</span><span class="sxs-lookup"><span data-stu-id="a1454-119">The simpler and more focused you can make your PR, the faster it can be reviewed and merged.</span></span>

### <a name="avoid-pull-requests-that-update-large-numbers-of-files-or-contain-unrelated-changes"></a><span data-ttu-id="a1454-120">Undvik pull-begäranden som uppdaterar ett stort antal filer eller innehåller orelaterade ändringar</span><span class="sxs-lookup"><span data-stu-id="a1454-120">Avoid pull requests that update large numbers of files or contain unrelated changes</span></span>

<span data-ttu-id="a1454-121">Undvik att skapa pull som innehåller orelaterade ändringar.</span><span class="sxs-lookup"><span data-stu-id="a1454-121">Avoid creating PRs that contain unrelated changes.</span></span> <span data-ttu-id="a1454-122">Olika små uppdateringar i befintliga artiklar från nya artiklar eller större omskrivningar.</span><span class="sxs-lookup"><span data-stu-id="a1454-122">Separate minor updates to existing articles from new articles or major rewrites.</span></span> <span data-ttu-id="a1454-123">Arbeta på dessa ändringar i olika arbetsflöden.</span><span class="sxs-lookup"><span data-stu-id="a1454-123">Work on these changes in separate working branches.</span></span>

<span data-ttu-id="a1454-124">Mass ändringar skapa pull med ett stort antal ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="a1454-124">Bulk changes create PRs with large numbers of changed files.</span></span> <span data-ttu-id="a1454-125">Begränsa din pull-begäran till högst 50 ändrade filer.</span><span class="sxs-lookup"><span data-stu-id="a1454-125">Limit your PRs to a maximum of 50 changed files.</span></span> <span data-ttu-id="a1454-126">Stora pull-begäranden är svåra att granska och är mer benägna att innehålla fel.</span><span class="sxs-lookup"><span data-stu-id="a1454-126">Large PRs are difficult to review and are more prone to contain errors.</span></span>

### <a name="renaming-or-deleting-files"></a><span data-ttu-id="a1454-127">Byta namn på eller ta bort filer</span><span class="sxs-lookup"><span data-stu-id="a1454-127">Renaming or deleting files</span></span>

<span data-ttu-id="a1454-128">När du byter namn på eller tar bort filer, måste det finnas ett problem som är kopplat till PR.</span><span class="sxs-lookup"><span data-stu-id="a1454-128">When renaming or deleting files, there must be an issue associated with the PR.</span></span> <span data-ttu-id="a1454-129">Det här problemet måste diskutera behovet av att byta namn på eller ta bort filerna.</span><span class="sxs-lookup"><span data-stu-id="a1454-129">That issue must discuss the need to rename or delete the files.</span></span>

<span data-ttu-id="a1454-130">Undvik att blanda innehålls tillägg eller ändra med fil namn och borttagningar.</span><span class="sxs-lookup"><span data-stu-id="a1454-130">Avoid mixing content additions or change with file renames and deletes.</span></span> <span data-ttu-id="a1454-131">Alla filer som har bytt namn eller tas bort måste läggas till i den globala omdirigerings filen.</span><span class="sxs-lookup"><span data-stu-id="a1454-131">Any file that is renamed or deleted must be added to the global redirection file.</span></span> <span data-ttu-id="a1454-132">Uppdatera eventuella filer som länkar till det omdöpta eller borttagna innehållet, inklusive eventuella TOC-filer, om det är möjligt.</span><span class="sxs-lookup"><span data-stu-id="a1454-132">When possible, update any files that link to the renamed or deleted content, including any TOC files.</span></span>

## <a name="docs-pr-validation-service"></a><span data-ttu-id="a1454-133">Docs PR-valideringstjänst</span><span class="sxs-lookup"><span data-stu-id="a1454-133">Docs PR validation service</span></span>

<span data-ttu-id="a1454-134">Verifierings tjänsten för dokument PR är en GitHub-app som kör verifierings regler på dina ändringar.</span><span class="sxs-lookup"><span data-stu-id="a1454-134">The Docs PR validation service is a GitHub app that runs validation rules on your changes.</span></span> <span data-ttu-id="a1454-135">Du måste åtgärda eventuella fel eller varningar som rapporter ATS av validerings tjänsten.</span><span class="sxs-lookup"><span data-stu-id="a1454-135">You must fix any errors or warnings reported by the validation service.</span></span>

<span data-ttu-id="a1454-136">Följande beteende kommer att visas:</span><span class="sxs-lookup"><span data-stu-id="a1454-136">You'll see the following behavior:</span></span>

1. <span data-ttu-id="a1454-137">Du skickar en PR.</span><span class="sxs-lookup"><span data-stu-id="a1454-137">You submit a PR.</span></span>
1. <span data-ttu-id="a1454-138">I GitHub-kommentaren som visar statusen för din PR ser du statusen "checkar" aktiverade på lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="a1454-138">In the GitHub comment that indicates the status of your PR, you'll see the status of "checks" enabled on the repository.</span></span> <span data-ttu-id="a1454-139">I det här exemplet finns det två kontroller aktiverade, "commit Validation" och "openpublishing. Build":</span><span class="sxs-lookup"><span data-stu-id="a1454-139">In this example, there are two checks enabled, "Commit Validation" and "OpenPublishing.Build":</span></span>

   ![validerings status-vissa kontroller misslyckades](media/pull-requests/validation-failed.png)

   <span data-ttu-id="a1454-141">Bygget kan klara även om bekräftelse valideringen Miss lyckas.</span><span class="sxs-lookup"><span data-stu-id="a1454-141">The build can pass even if commit validation fails.</span></span>

1. <span data-ttu-id="a1454-142">Klicka på **Details** (Detaljerad information) om du vill ha mer information.</span><span class="sxs-lookup"><span data-stu-id="a1454-142">Click **Details** for more information.</span></span>
1. <span data-ttu-id="a1454-143">På sidan Details (Detaljerad information) visas alla valideringskontroller som har misslyckats och information om hur du åtgärdar problemen.</span><span class="sxs-lookup"><span data-stu-id="a1454-143">On the Details page, you'll see all the validation checks that failed, with information about how to fix the issues.</span></span>
1. <span data-ttu-id="a1454-144">När verifieringen lyckas läggs följande kommentar till i pull-begäran:</span><span class="sxs-lookup"><span data-stu-id="a1454-144">When validation succeeds, the following comment is added to the PR:</span></span>

   ![Validerings status: lyckad](media/pull-requests/build-validation.png)

> [!NOTE]
> <span data-ttu-id="a1454-146">Om du är en extern deltagare (inte en Microsoft-anställd) har du inte åtkomst till de detaljerade build-rapporterna eller för hands versions länkar.</span><span class="sxs-lookup"><span data-stu-id="a1454-146">If you are an external (not a Microsoft employee) contributor you do not have access to the detailed build reports or preview links.</span></span>

<span data-ttu-id="a1454-147">När PR granskas kan du bli ombedd att göra ändringar eller åtgärda varnings meddelanden.</span><span class="sxs-lookup"><span data-stu-id="a1454-147">When the PR is reviewed, you may be asked to make changes or fix validation warning messages.</span></span> <span data-ttu-id="a1454-148">PowerShell-Docss teamet kan hjälpa dig att förstå verifierings fel och redaktionella krav.</span><span class="sxs-lookup"><span data-stu-id="a1454-148">The PowerShell-Docs team can help you understand validation errors and editorial requirements.</span></span>

## <a name="next-steps"></a><span data-ttu-id="a1454-149">Nästa steg</span><span class="sxs-lookup"><span data-stu-id="a1454-149">Next steps</span></span>

[<span data-ttu-id="a1454-150">Stilguide för PowerShell-Docs</span><span class="sxs-lookup"><span data-stu-id="a1454-150">PowerShell-Docs style guide</span></span>](powershell-style-guide.md)

## <a name="additional-resources"></a><span data-ttu-id="a1454-151">Ytterligare resurser</span><span class="sxs-lookup"><span data-stu-id="a1454-151">Additional resources</span></span>

[<span data-ttu-id="a1454-152">Så här hanterar vi pull-begäranden</span><span class="sxs-lookup"><span data-stu-id="a1454-152">How we manage pull requests</span></span>](managing-pull-requests.md)

<!--link refs-->
[fork]: /contribute/get-started-setup-local#fork-the-repository
