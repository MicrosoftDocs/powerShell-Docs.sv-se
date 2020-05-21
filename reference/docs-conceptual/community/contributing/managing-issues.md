---
title: Så här hanterar vi problem
description: Den här artikeln förklarar hur PowerShell-dokument-teamet hanterar pull-begäranden.
ms.date: 03/05/2020
ms.topic: conceptual
ms.openlocfilehash: 018200f1a9384f1ea956c9b27a7605db21f2da9e
ms.sourcegitcommit: 17d798a041851382b406ed789097843faf37692d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/20/2020
ms.locfileid: "83692524"
---
# <a name="how-we-manage-issues"></a><span data-ttu-id="efbe3-103">Så här hanterar vi problem</span><span class="sxs-lookup"><span data-stu-id="efbe3-103">How we manage issues</span></span>

<span data-ttu-id="efbe3-104">Den här artikeln dokumenterar vi hur vi hanterar problem i PowerShell-dok lagrings platsen.</span><span class="sxs-lookup"><span data-stu-id="efbe3-104">This article documents how we manage issues in the PowerShell-Docs repo.</span></span> <span data-ttu-id="efbe3-105">Den här artikeln är utformad för att vara ett jobb stöd för medlemmar i gruppen PowerShell-dok.</span><span class="sxs-lookup"><span data-stu-id="efbe3-105">This article is designed to be a job aid for members of the PowerShell-Docs team.</span></span> <span data-ttu-id="efbe3-106">Den publiceras här för att tillhandahålla process genomskinlighet för våra offentliga deltagare.</span><span class="sxs-lookup"><span data-stu-id="efbe3-106">It is published here to provide process transparency for our public contributors.</span></span>

## <a name="sources-of-issues"></a><span data-ttu-id="efbe3-107">Problem källor</span><span class="sxs-lookup"><span data-stu-id="efbe3-107">Sources of issues</span></span>

- <span data-ttu-id="efbe3-108">Community-deltagare</span><span class="sxs-lookup"><span data-stu-id="efbe3-108">Community contributors</span></span>
- <span data-ttu-id="efbe3-109">Interna bidrags givare</span><span class="sxs-lookup"><span data-stu-id="efbe3-109">Internal contributors</span></span>
- <span data-ttu-id="efbe3-110">Avskrifter av kommentarer från sociala media-kanaler</span><span class="sxs-lookup"><span data-stu-id="efbe3-110">Transcriptions of comments from social media channels</span></span>
- <span data-ttu-id="efbe3-111">Feedback via feedback-formuläret för dokument</span><span class="sxs-lookup"><span data-stu-id="efbe3-111">Feedback via the Docs feedback form</span></span>

## <a name="response-time-targets"></a><span data-ttu-id="efbe3-112">Svars tids mål</span><span class="sxs-lookup"><span data-stu-id="efbe3-112">Response time targets</span></span>

- <span data-ttu-id="efbe3-113">Prioriteras – 5 arbets dagar</span><span class="sxs-lookup"><span data-stu-id="efbe3-113">Triaged - 5 business days</span></span>
- <span data-ttu-id="efbe3-114">Åtgärda eller ändra inga specifika mål – bästa möjliga ansträngning</span><span class="sxs-lookup"><span data-stu-id="efbe3-114">Fix or change - no specific target - best effort only</span></span>

### <a name="labeling--milestones"></a><span data-ttu-id="efbe3-115">Etikettera & mil stolpar</span><span class="sxs-lookup"><span data-stu-id="efbe3-115">Labeling & Milestones</span></span>

#### <a name="label-types"></a><span data-ttu-id="efbe3-116">Etikett typer</span><span class="sxs-lookup"><span data-stu-id="efbe3-116">Label Types</span></span>

|<span data-ttu-id="efbe3-117">Prefix</span><span class="sxs-lookup"><span data-stu-id="efbe3-117">Prefix</span></span>  | <span data-ttu-id="efbe3-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="efbe3-118">Description</span></span>                                                         |
|------- | --------------------------------------------------------------------|
|<span data-ttu-id="efbe3-119">Område</span><span class="sxs-lookup"><span data-stu-id="efbe3-119">Area</span></span>    | <span data-ttu-id="efbe3-120">Används för att ange vilken del av PowerShell eller dokument som problemet diskuterar.</span><span class="sxs-lookup"><span data-stu-id="efbe3-120">Used to indicate what part of PowerShell or the docs that the issue is discussing.</span></span><br><span data-ttu-id="efbe3-121">Användbart för funktions ägare för att hitta problem med deras funktion.</span><span class="sxs-lookup"><span data-stu-id="efbe3-121">Useful for feature owners to find issues for their feature.</span></span>|
|<span data-ttu-id="efbe3-122">Pri</span><span class="sxs-lookup"><span data-stu-id="efbe3-122">Pri</span></span>     | <span data-ttu-id="efbe3-123">Används för att ange prioriteten för problemet.</span><span class="sxs-lookup"><span data-stu-id="efbe3-123">Used to indicate the priority of the issue.</span></span> <span data-ttu-id="efbe3-124">Värde intervall 0-4.</span><span class="sxs-lookup"><span data-stu-id="efbe3-124">Value range 0-4.</span></span>        |
|<span data-ttu-id="efbe3-125">Problem</span><span class="sxs-lookup"><span data-stu-id="efbe3-125">Issue</span></span>   | <span data-ttu-id="efbe3-126">Används för att klassificera typen av feedback för problem</span><span class="sxs-lookup"><span data-stu-id="efbe3-126">Used to classify the type of feedback for issue</span></span>                     |
|<span data-ttu-id="efbe3-127">Granska</span><span class="sxs-lookup"><span data-stu-id="efbe3-127">Review</span></span>  | <span data-ttu-id="efbe3-128">Används för problem som kräver ytterligare granskning av teamet</span><span class="sxs-lookup"><span data-stu-id="efbe3-128">Used for issue that require further review by the team</span></span>              |
|<span data-ttu-id="efbe3-129">Status</span><span class="sxs-lookup"><span data-stu-id="efbe3-129">Status</span></span>  | <span data-ttu-id="efbe3-130">Används för att ange arbets objektets status</span><span class="sxs-lookup"><span data-stu-id="efbe3-130">Used to indicate the status of the work item</span></span>                        |
|<span data-ttu-id="efbe3-131">Väntar</span><span class="sxs-lookup"><span data-stu-id="efbe3-131">Waiting</span></span> | <span data-ttu-id="efbe3-132">Används för att indikera att vi väntar på något</span><span class="sxs-lookup"><span data-stu-id="efbe3-132">Used to indicate that we are waiting on something</span></span>                   |

#### <a name="milestones"></a><span data-ttu-id="efbe3-133">Milstolpar</span><span class="sxs-lookup"><span data-stu-id="efbe3-133">Milestones</span></span>

<span data-ttu-id="efbe3-134">Problem och pull ska taggas med lämplig mil stolpe.</span><span class="sxs-lookup"><span data-stu-id="efbe3-134">Issues and PRs should be tagged with the appropriate milestone.</span></span> <span data-ttu-id="efbe3-135">Om problemet inte är avsett för en viss version, används ingen mil stolpe.</span><span class="sxs-lookup"><span data-stu-id="efbe3-135">If the issue is not targeted for a specific version then no milestone is used.</span></span> <span data-ttu-id="efbe3-136">Problem med dokument pull för ändringar som ännu inte har slagits samman i PowerShell-kodbasen bör tilldelas till den **framtida** mil stolpen.</span><span class="sxs-lookup"><span data-stu-id="efbe3-136">Issues for Docs PRs for changes that have yet to be merged into the PowerShell code base should be assigned to the **Future** milestone.</span></span> <span data-ttu-id="efbe3-137">När kod ändringen har slagits samman ändrar du mil stolpen till rätt version.</span><span class="sxs-lookup"><span data-stu-id="efbe3-137">After the code change has been merged, change the milestone to the appropriate version.</span></span>

|    <span data-ttu-id="efbe3-138">Gränser</span><span class="sxs-lookup"><span data-stu-id="efbe3-138">Milestone</span></span>     |                    <span data-ttu-id="efbe3-139">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="efbe3-139">Description</span></span>                     |
| ---------------- | -------------------------------------------------- |
| <span data-ttu-id="efbe3-140">6.x</span><span class="sxs-lookup"><span data-stu-id="efbe3-140">6.x</span></span>              | <span data-ttu-id="efbe3-141">Arbets objekt som rör PowerShell 6,0 till och med 6.2. x</span><span class="sxs-lookup"><span data-stu-id="efbe3-141">Work items related to PowerShell 6.0 through 6.2.x</span></span> |
| <span data-ttu-id="efbe3-142">7.0.0</span><span class="sxs-lookup"><span data-stu-id="efbe3-142">7.0.0</span></span>            | <span data-ttu-id="efbe3-143">Arbets objekt som rör PowerShell 7,0</span><span class="sxs-lookup"><span data-stu-id="efbe3-143">Work items related to PowerShell 7.0</span></span>               |
| <span data-ttu-id="efbe3-144">7.1.0</span><span class="sxs-lookup"><span data-stu-id="efbe3-144">7.1.0</span></span>            | <span data-ttu-id="efbe3-145">Arbets objekt som rör PowerShell 7,1</span><span class="sxs-lookup"><span data-stu-id="efbe3-145">Work items related to PowerShell 7.1</span></span>               |
| <span data-ttu-id="efbe3-146">I framtiden</span><span class="sxs-lookup"><span data-stu-id="efbe3-146">Future</span></span>           | <span data-ttu-id="efbe3-147">Arbets uppgifter en framtida version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="efbe3-147">Work items a future version of PowerShell</span></span>          |
| <span data-ttu-id="efbe3-148">PSReadline – vNext</span><span class="sxs-lookup"><span data-stu-id="efbe3-148">PSReadline-vNext</span></span> | <span data-ttu-id="efbe3-149">Arbets objekt en framtida version av PSReadline</span><span class="sxs-lookup"><span data-stu-id="efbe3-149">Work items a future version of PSReadline</span></span>          |

## <a name="triage-process"></a><span data-ttu-id="efbe3-150">Prioritering process</span><span class="sxs-lookup"><span data-stu-id="efbe3-150">Triage process</span></span>

<span data-ttu-id="efbe3-151">Gruppen PowerShell-dokument uppfyller en gång per vecka för att diskutera eventuella problem som har lagts till sedan förra mötet.</span><span class="sxs-lookup"><span data-stu-id="efbe3-151">The PowerShell docs team meets once per week to discuss any issues added since last meeting.</span></span> <span data-ttu-id="efbe3-152">Ett problem anses ha prioriteras när etiketter har tilldelats eller en ägare har tilldelats.</span><span class="sxs-lookup"><span data-stu-id="efbe3-152">An issue is considered to have been triaged when labels have been assigned or an owner has been assigned.</span></span> <span data-ttu-id="efbe3-153">Grupp medlemmar i PowerShell-teamet uppmanas att granska problemen varje dag och prioritering nya problem när de tas emot.</span><span class="sxs-lookup"><span data-stu-id="efbe3-153">PowerShell docs team members are encouraged to review the issues daily and triage new issues as they arrive.</span></span> <span data-ttu-id="efbe3-154">Det veckovis prioritering mötet kan sedan användas för att diskutera de nya problemen mer detaljerat efter behov.</span><span class="sxs-lookup"><span data-stu-id="efbe3-154">The weekly triage meeting can then be used to discuss the new issues in more detail, as needed.</span></span>

### <a name="misplaced-product-feedback"></a><span data-ttu-id="efbe3-155">Felplacerad produkt feedback</span><span class="sxs-lookup"><span data-stu-id="efbe3-155">Misplaced product feedback</span></span>

- <span data-ttu-id="efbe3-156">Ange en kommentar för kunden som visar att den är produkt kommentarer och ange en länk till lämplig feedback-kanal.</span><span class="sxs-lookup"><span data-stu-id="efbe3-156">Enter a comment for the customer indicating it is product feedback and provide a link to the appropriate feedback channel.</span></span>
- <span data-ttu-id="efbe3-157">Valfritt: kopiera problemet till lämplig plats för produkt feedback, Lägg till en länk till det kopierade objektet och Stäng problemet.</span><span class="sxs-lookup"><span data-stu-id="efbe3-157">Optional: Copy the issue to the appropriate product feedback location, add a link to the copied item, and close the issue.</span></span> <span data-ttu-id="efbe3-158">Kopiera inte problem till UserVoice.</span><span class="sxs-lookup"><span data-stu-id="efbe3-158">DO NOT copy issues to UserVoice.</span></span>

  | <span data-ttu-id="efbe3-159">Dokument uppsättning</span><span class="sxs-lookup"><span data-stu-id="efbe3-159">DocSet</span></span>    | <span data-ttu-id="efbe3-160">URL för feedback för produkt</span><span class="sxs-lookup"><span data-stu-id="efbe3-160">Product Feedback URL</span></span>                                           |
  | --------- | -------------------------------------------------------------- |
  | <span data-ttu-id="efbe3-161">utvecklare</span><span class="sxs-lookup"><span data-stu-id="efbe3-161">developer</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="efbe3-162">DSC</span><span class="sxs-lookup"><span data-stu-id="efbe3-162">dsc</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |
  | <span data-ttu-id="efbe3-163">galleri</span><span class="sxs-lookup"><span data-stu-id="efbe3-163">gallery</span></span>   | `https://github.com/powershell/powershellgallery/issues/new`   |
  | <span data-ttu-id="efbe3-164">Jea</span><span class="sxs-lookup"><span data-stu-id="efbe3-164">jea</span></span>       | `https://github.com/powershell/jea/issues/new`                 |
  | <span data-ttu-id="efbe3-165">förhållande</span><span class="sxs-lookup"><span data-stu-id="efbe3-165">reference</span></span> | `https://github.com/PowerShell/PowerShell/issues/new/choose`   |
  | <span data-ttu-id="efbe3-166">WMF</span><span class="sxs-lookup"><span data-stu-id="efbe3-166">wmf</span></span>       | `https://windowsserver.uservoice.com/forums/301869-powershell` |

### <a name="support-requests"></a><span data-ttu-id="efbe3-167">Supportförfrågningar</span><span class="sxs-lookup"><span data-stu-id="efbe3-167">Support requests</span></span>

- <span data-ttu-id="efbe3-168">Om support frågan är enkel, kan du besvara den politely och stänga problemet.</span><span class="sxs-lookup"><span data-stu-id="efbe3-168">If the support question is simple, answer it politely and close the issue.</span></span>
- <span data-ttu-id="efbe3-169">Om frågan är mer komplicerad eller om du svarar på fler frågor kan du omdirigera dem till forum och support kanaler.</span><span class="sxs-lookup"><span data-stu-id="efbe3-169">If the question is more complicated, or the submitter replies with more questions, redirect them to forums and support channels.</span></span> <span data-ttu-id="efbe3-170">Föreslagen text för omdirigering till Forum:</span><span class="sxs-lookup"><span data-stu-id="efbe3-170">Suggested text for redirecting to forums:</span></span>

  ```Markdown
  > This is not the right forum for these kinds of questions. Try posting your question in a
  > community support forum. For a list of community forums see:
  > https://docs.microsoft.com/powershell/scripting/community/community-support
  ```

### <a name="code-of-conduct-violations"></a><span data-ttu-id="efbe3-171">Regler för uppförande av fel</span><span class="sxs-lookup"><span data-stu-id="efbe3-171">Code of conduct violations</span></span>

- <span data-ttu-id="efbe3-172">Redigera problemet om du vill ta bort stötande innehåll, om det behövs.</span><span class="sxs-lookup"><span data-stu-id="efbe3-172">Edit the issue to remove any offensive content, if necessary.</span></span>
- <span data-ttu-id="efbe3-173">Ange en kommentar som visar att problemet är skräp post, Stäng problemet och lås det för att förhindra ytterligare kommentarer.</span><span class="sxs-lookup"><span data-stu-id="efbe3-173">Enter a comment indicating the issue is spam, close the issue, and then lock it to prevent further comments.</span></span>
- <span data-ttu-id="efbe3-174">Varje förekomst av detta bör diskuteras i varje veckas prioritering för att fastställa behovet av ytterligare åtgärd (rapportera till GitHub eller Microsoft legal).</span><span class="sxs-lookup"><span data-stu-id="efbe3-174">Each occurrence of this should be discussed in the weekly triage to determine the need for further action (report to GitHub or Microsoft Legal).</span></span>
