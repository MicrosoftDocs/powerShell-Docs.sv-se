---
title: Så här hanterar vi problem
description: Den här artikeln förklarar hur PowerShell-Docs-teamet hanterar problem.
ms.date: 12/09/2020
ms.topic: conceptual
ms.openlocfilehash: 72267137a2657f51e5f616113adf92d80647acad
ms.sourcegitcommit: 61765d08321623743dc5db5367160f6982fe7857
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/12/2020
ms.locfileid: "97352710"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="b0ff4-103">Så här hanterar vi problem</span><span class="sxs-lookup"><span data-stu-id="b0ff4-103">How we manage issues</span></span>

<span data-ttu-id="b0ff4-104">Den här artikeln dokumenterar vi hur vi hanterar problem i PowerShell-Docs lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="b0ff4-105">Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i PowerShell-Docss teamet.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="b0ff4-106">Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-106">It's published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="b0ff4-107">Problem källor</span><span class="sxs-lookup"><span data-stu-id="b0ff4-107">Sources of issues</span></span>

- <span data-ttu-id="b0ff4-108">Community-deltagare</span><span class="sxs-lookup"><span data-stu-id="b0ff4-108">Community contributors</span></span>
- <span data-ttu-id="b0ff4-109">Interna bidrags givare</span><span class="sxs-lookup"><span data-stu-id="b0ff4-109">Internal contributors</span></span>
- <span data-ttu-id="b0ff4-110">Avskrifter av kommentarer från sociala media-kanaler</span><span class="sxs-lookup"><span data-stu-id="b0ff4-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="b0ff4-111">Feedback via feedback-formuläret för dokument</span><span class="sxs-lookup"><span data-stu-id="b0ff4-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="b0ff4-112">Svars tids mål</span><span class="sxs-lookup"><span data-stu-id="b0ff4-112">Response time targets</span></span>

<span data-ttu-id="b0ff4-113">80% av de nya problemen är stängda inom tre arbets dagar.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-113">80% of new issues are closed within 3 business days.</span></span>

- <span data-ttu-id="b0ff4-114">Prioriteras – 1 arbets dagar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-114">Triaged - 1 business days</span></span>
- <span data-ttu-id="b0ff4-115">Korrigera eller ändra 10 arbets dagar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-115">Fix or change - 10 business days</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="b0ff4-116">Etikettera & mil stolpar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-116">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="b0ff4-117">Etikett typer</span><span class="sxs-lookup"><span data-stu-id="b0ff4-117">Label Types</span></span>

|   <span data-ttu-id="b0ff4-118">Typ</span><span class="sxs-lookup"><span data-stu-id="b0ff4-118">Type</span></span>   | <span data-ttu-id="b0ff4-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0ff4-119">Description</span></span>                                                         |
| -------- | ------------------------------------------------------------------- |
| <span data-ttu-id="b0ff4-120">Område</span><span class="sxs-lookup"><span data-stu-id="b0ff4-120">Area</span></span>     | <span data-ttu-id="b0ff4-121">Används för att ange vilken del av PowerShell eller dokument som problemet diskuterar.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-121">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="b0ff4-122">Användbart för funktions ägare för att hitta problem med deras funktion.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-122">Useful for feature owners to find issues for their feature.</span></span> |
| <span data-ttu-id="b0ff4-123">Problem</span><span class="sxs-lookup"><span data-stu-id="b0ff4-123">Issue</span></span>    | <span data-ttu-id="b0ff4-124">Anger typen av problem</span><span class="sxs-lookup"><span data-stu-id="b0ff4-124">Indicates the type of issue</span></span>                                         |
| <span data-ttu-id="b0ff4-125">Prioritet</span><span class="sxs-lookup"><span data-stu-id="b0ff4-125">Priority</span></span> | <span data-ttu-id="b0ff4-126">Anger prioriteten för problemet.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-126">Indicates the priority of the issue.</span></span> <span data-ttu-id="b0ff4-127">Värde intervall 0 (högt)-4 (låg)</span><span class="sxs-lookup"><span data-stu-id="b0ff4-127">Value range 0 (high) -4 (low)</span></span>  |
| <span data-ttu-id="b0ff4-128">Status</span><span class="sxs-lookup"><span data-stu-id="b0ff4-128">Status</span></span>   | <span data-ttu-id="b0ff4-129">Anger status för arbets uppgiften eller varför den stängdes</span><span class="sxs-lookup"><span data-stu-id="b0ff4-129">Indicates the status of the work item or why it was closed</span></span>          |
| <span data-ttu-id="b0ff4-130">Tagga</span><span class="sxs-lookup"><span data-stu-id="b0ff4-130">Tag</span></span>      | <span data-ttu-id="b0ff4-131">Etiketter som används för att lägga till ytterligare klassificering</span><span class="sxs-lookup"><span data-stu-id="b0ff4-131">Labels used to for additional classification</span></span>                        |
| <span data-ttu-id="b0ff4-132">Väntar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-132">Waiting</span></span>  | <span data-ttu-id="b0ff4-133">Indikerar att vi väntar på någon eller någon annan händelse</span><span class="sxs-lookup"><span data-stu-id="b0ff4-133">Indicates that we're waiting on someone or some other event</span></span>         |

#### <a name="milestones"></a><span data-ttu-id="b0ff4-134">Milstolpar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-134">Milestones</span></span>

<span data-ttu-id="b0ff4-135">Problem och pull ska taggas med lämplig mil stolpe.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-135">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="b0ff4-136">Om problemet inte gäller för en speciell version används ingen mil stolpe.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-136">If the issue doesn't apply to a specific version, then no milestone is used.</span></span> <span data-ttu-id="b0ff4-137">Pull och relaterade problem för ändringar som ännu inte har sammanfogats till PowerShell-kodbasen bör tilldelas till den **framtida** mil stolpen.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-137">PRs and related issues for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="b0ff4-138">När kod ändringen har slagits samman ändrar du mil stolpen till rätt version.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-138">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="b0ff4-139">Gränser</span><span class="sxs-lookup"><span data-stu-id="b0ff4-139">Milestone</span></span>     |                    <span data-ttu-id="b0ff4-140">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b0ff4-140">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="b0ff4-141">7.0.0</span><span class="sxs-lookup"><span data-stu-id="b0ff4-141">7.0.0</span></span>            | <span data-ttu-id="b0ff4-142">Arbets objekt som rör PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="b0ff4-142">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="b0ff4-143">7.1.0</span><span class="sxs-lookup"><span data-stu-id="b0ff4-143">7.1.0</span></span>            | <span data-ttu-id="b0ff4-144">Arbets objekt som rör PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="b0ff4-144">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="b0ff4-145">7.2.0</span><span class="sxs-lookup"><span data-stu-id="b0ff4-145">7.2.0</span></span>            | <span data-ttu-id="b0ff4-146">Arbets objekt som rör PowerShell 7,2</span><span class="sxs-lookup"><span data-stu-id="b0ff4-146">Work items related to PowerShell 7.2</span></span>               |
| <span data-ttu-id="b0ff4-147">I framtiden</span><span class="sxs-lookup"><span data-stu-id="b0ff4-147">Future</span></span>           | <span data-ttu-id="b0ff4-148">Arbets uppgifter en framtida version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="b0ff4-148">Work items a future version of PowerShell</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="b0ff4-149">Prioritering process</span><span class="sxs-lookup"><span data-stu-id="b0ff4-149">Triage process</span></span>

<span data-ttu-id="b0ff4-150">I PowerShell-dokumentets grupp medlemmar granskas problemen varje dag och prioritering nya problem när de tas emot.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-150">PowerShell docs team members review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="b0ff4-151">Teamet uppfyller vecko kraven för att diskutera problem som behöver prioritering eller vara olösta.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-151">The team meets weekly to discuss issues that need triage or remain unresolved.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="b0ff4-152">Felplacerad produkt feedback</span><span class="sxs-lookup"><span data-stu-id="b0ff4-152">Misplaced product feedback</span></span>

- <span data-ttu-id="b0ff4-153">Ange en kommentar som omdirigerar kunden till rätt feedback-kanal.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-153">Enter a comment redirecting the customer to the correct feedback channel.</span></span>
- <span data-ttu-id="b0ff4-154">Valfritt: kopiera problemet till lämplig plats för produkt feedback, Lägg till en länk till det kopierade objektet och Stäng problemet.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-154">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="b0ff4-155">Kopiera inte problem till UserVoice.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-155">DO NOT copy issues to UserVoice.</span></span>

  <span data-ttu-id="b0ff4-156">Standard platsen för PowerShell-problem är [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose) .</span><span class="sxs-lookup"><span data-stu-id="b0ff4-156">The default location for PowerShell issues is [https://github.com/PowerShell/PowerShell/issues/new/choose](https://github.com/PowerShell/PowerShell/issues/new/choose).</span></span>

  <span data-ttu-id="b0ff4-157">Följande ämnes områden har olika platser för problem:</span><span class="sxs-lookup"><span data-stu-id="b0ff4-157">The following subject areas have different locations for issues:</span></span>

  | <span data-ttu-id="b0ff4-158">Ämnen</span><span class="sxs-lookup"><span data-stu-id="b0ff4-158">Subjects</span></span> |                                                     <span data-ttu-id="b0ff4-159">URL för feedback för produkt</span><span class="sxs-lookup"><span data-stu-id="b0ff4-159">Product Feedback URL</span></span>                                                     |
  | -------- | ---------------------------------------------------------------------------------------------------------------------------- |
  | <span data-ttu-id="b0ff4-160">dsc</span><span class="sxs-lookup"><span data-stu-id="b0ff4-160">dsc</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |
  | <span data-ttu-id="b0ff4-161">galleri</span><span class="sxs-lookup"><span data-stu-id="b0ff4-161">gallery</span></span>  | [https://github.com/powershell/powershellgallery/issues/new](https://github.com/powershell/powershellgallery/issues/new)     |
  | <span data-ttu-id="b0ff4-162">Jea</span><span class="sxs-lookup"><span data-stu-id="b0ff4-162">jea</span></span>      | [https://github.com/powershell/jea/issues/new](https://github.com/powershell/jea/issues/new)                                 |
  | <span data-ttu-id="b0ff4-163">WMF</span><span class="sxs-lookup"><span data-stu-id="b0ff4-163">wmf</span></span>      | [https://windowsserver.uservoice.com/forums/301869-powershell](https://windowsserver.uservoice.com/forums/301869-powershell) |

### <a name="support-requests"></a><span data-ttu-id="b0ff4-164">Supportförfrågningar</span><span class="sxs-lookup"><span data-stu-id="b0ff4-164">Support requests</span></span>

- <span data-ttu-id="b0ff4-165">Om support frågan är enkel, kan du besvara den politely och stänga problemet.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-165">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="b0ff4-166">Om frågan är mer komplicerad eller om du svarar på fler frågor kan du omdirigera dem till forum och support kanaler.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-166">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="b0ff4-167">Föreslagen text för omdirigering till Forum:</span><span class="sxs-lookup"><span data-stu-id="b0ff4-167">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="b0ff4-168">Regler för uppförande av fel</span><span class="sxs-lookup"><span data-stu-id="b0ff4-168">Code of conduct violations</span></span>

- <span data-ttu-id="b0ff4-169">Redigera problemet om du vill ta bort stötande innehåll, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-169">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="b0ff4-170">Ange en kommentar som visar att problemet är skräp post, Stäng problemet och lås det för att förhindra ytterligare kommentarer.</span><span class="sxs-lookup"><span data-stu-id="b0ff4-170">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="b0ff4-171">Varje överträdelse bör diskuteras i varje veckas prioritering för att fastställa behovet av ytterligare åtgärd (rapportera till GitHub eller Microsoft legal).</span><span class="sxs-lookup"><span data-stu-id="b0ff4-171">Each violation should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
