---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 5b59ffcdfb35c2aa10f8e0caf3a3b365c5bcf93e
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93272294"
---
# <a name="psreadline"></a><span data-ttu-id="d8d37-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="d8d37-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="d8d37-106">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d8d37-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="d8d37-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="d8d37-108">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="d8d37-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="d8d37-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="d8d37-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="d8d37-110">It provides:</span></span>

- <span data-ttu-id="d8d37-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="d8d37-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="d8d37-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="d8d37-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="d8d37-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="d8d37-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="d8d37-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="d8d37-114">Customizable key bindings</span></span>
- <span data-ttu-id="d8d37-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="d8d37-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="d8d37-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="d8d37-116">Many configuration options</span></span>
- <span data-ttu-id="d8d37-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="d8d37-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="d8d37-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="d8d37-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="d8d37-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="d8d37-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="d8d37-120">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="d8d37-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="d8d37-121">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="d8d37-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="d8d37-122">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="d8d37-123">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="d8d37-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="d8d37-124">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="d8d37-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="d8d37-125">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="d8d37-126">Avbryta</span><span class="sxs-lookup"><span data-stu-id="d8d37-126">Abort</span></span>

<span data-ttu-id="d8d37-127">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="d8d37-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="d8d37-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="d8d37-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="d8d37-129">AcceptAndGetNext</span></span>

<span data-ttu-id="d8d37-130">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-130">Attempt to execute the current input.</span></span> <span data-ttu-id="d8d37-131">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="d8d37-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="d8d37-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="d8d37-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-133">AcceptLine</span></span>

<span data-ttu-id="d8d37-134">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-134">Attempt to execute the current input.</span></span> <span data-ttu-id="d8d37-135">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="d8d37-136">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="d8d37-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="d8d37-138">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="d8d37-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-139">AddLine</span></span>

<span data-ttu-id="d8d37-140">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="d8d37-141">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="d8d37-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="d8d37-142">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d8d37-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d8d37-144">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="d8d37-145">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="d8d37-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-146">BackwardDeleteChar</span></span>

<span data-ttu-id="d8d37-147">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="d8d37-148">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="d8d37-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="d8d37-150">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="d8d37-151">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="d8d37-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-152">BackwardDeleteLine</span></span>

<span data-ttu-id="d8d37-153">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-154">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="d8d37-155">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="d8d37-156">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="d8d37-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-157">BackwardDeleteWord</span></span>

<span data-ttu-id="d8d37-158">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-158">Deletes the previous word.</span></span>

- <span data-ttu-id="d8d37-159">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="d8d37-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-160">BackwardKillLine</span></span>

<span data-ttu-id="d8d37-161">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="d8d37-162">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="d8d37-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-164">BackwardKillWord</span></span>

<span data-ttu-id="d8d37-165">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d8d37-166">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d8d37-167">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-168">Kommandot `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="d8d37-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="d8d37-170">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="d8d37-171">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="d8d37-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-172">CancelLine</span></span>

<span data-ttu-id="d8d37-173">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="d8d37-174">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="d8d37-175">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="d8d37-176">Kopiera</span><span class="sxs-lookup"><span data-stu-id="d8d37-176">Copy</span></span>

<span data-ttu-id="d8d37-177">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="d8d37-178">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="d8d37-179">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="d8d37-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-180">CopyOrCancelLine</span></span>

<span data-ttu-id="d8d37-181">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="d8d37-182">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="d8d37-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="d8d37-184">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="d8d37-184">Cut</span></span>

<span data-ttu-id="d8d37-185">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="d8d37-186">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="d8d37-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-187">DeleteChar</span></span>

<span data-ttu-id="d8d37-188">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="d8d37-189">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="d8d37-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="d8d37-191">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="d8d37-192">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="d8d37-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="d8d37-193">DeleteCharOrExit</span></span>

<span data-ttu-id="d8d37-194">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="d8d37-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="d8d37-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-196">DeleteEndOfWord</span></span>

<span data-ttu-id="d8d37-197">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="d8d37-198">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="d8d37-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-199">DeleteLine</span></span>

<span data-ttu-id="d8d37-200">Tar bort den aktuella raden och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="d8d37-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="d8d37-201">Kommando läge för vi: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="d8d37-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="d8d37-203">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="d8d37-204">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="d8d37-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="d8d37-205">DeleteToEnd</span></span>

<span data-ttu-id="d8d37-206">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="d8d37-207">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="d8d37-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-208">DeleteWord</span></span>

<span data-ttu-id="d8d37-209">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-209">Delete the next word.</span></span>

- <span data-ttu-id="d8d37-210">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="d8d37-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-211">ForwardDeleteLine</span></span>

<span data-ttu-id="d8d37-212">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-213">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="d8d37-214">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="d8d37-215">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="d8d37-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="d8d37-216">InsertLineAbove</span></span>

<span data-ttu-id="d8d37-217">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="d8d37-218">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="d8d37-219">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="d8d37-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="d8d37-220">InsertLineBelow</span></span>

<span data-ttu-id="d8d37-221">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="d8d37-222">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="d8d37-223">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="d8d37-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="d8d37-224">InvertCase</span></span>

<span data-ttu-id="d8d37-225">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="d8d37-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="d8d37-226">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="d8d37-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-227">KillLine</span></span>

<span data-ttu-id="d8d37-228">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="d8d37-229">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-230">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="d8d37-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="d8d37-231">KillRegion</span></span>

<span data-ttu-id="d8d37-232">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="d8d37-233">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="d8d37-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-234">KillWord</span></span>

<span data-ttu-id="d8d37-235">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="d8d37-236">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="d8d37-237">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-238">Kommandot `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="d8d37-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="d8d37-240">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="d8d37-241">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="d8d37-242">Klistra in</span><span class="sxs-lookup"><span data-stu-id="d8d37-242">Paste</span></span>

<span data-ttu-id="d8d37-243">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="d8d37-244">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="d8d37-245">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="d8d37-246">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="d8d37-247">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d8d37-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="d8d37-248">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="d8d37-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="d8d37-249">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="d8d37-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="d8d37-250">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="d8d37-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="d8d37-251">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="d8d37-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="d8d37-252">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="d8d37-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="d8d37-253">PasteAfter</span></span>

<span data-ttu-id="d8d37-254">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="d8d37-255">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="d8d37-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="d8d37-256">PasteBefore</span></span>

<span data-ttu-id="d8d37-257">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="d8d37-258">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="d8d37-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="d8d37-259">PrependAndAccept</span></span>

<span data-ttu-id="d8d37-260">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="d8d37-261">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="d8d37-262">Gör om</span><span class="sxs-lookup"><span data-stu-id="d8d37-262">Redo</span></span>

<span data-ttu-id="d8d37-263">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="d8d37-263">Undo an undo.</span></span>

- <span data-ttu-id="d8d37-264">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="d8d37-265">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="d8d37-266">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="d8d37-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="d8d37-267">RepeatLastCommand</span></span>

<span data-ttu-id="d8d37-268">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="d8d37-269">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="d8d37-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-270">RevertLine</span></span>

<span data-ttu-id="d8d37-271">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="d8d37-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="d8d37-272">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="d8d37-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="d8d37-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="d8d37-275">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d8d37-276">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d8d37-277">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="d8d37-278">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="d8d37-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-279">ShellKillWord</span></span>

<span data-ttu-id="d8d37-280">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="d8d37-281">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="d8d37-282">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="d8d37-283">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="d8d37-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="d8d37-284">SwapCharacters</span></span>

<span data-ttu-id="d8d37-285">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="d8d37-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="d8d37-286">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="d8d37-287">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="d8d37-288">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="d8d37-289">Ångra</span><span class="sxs-lookup"><span data-stu-id="d8d37-289">Undo</span></span>

<span data-ttu-id="d8d37-290">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="d8d37-290">Undo a previous edit.</span></span>

- <span data-ttu-id="d8d37-291">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="d8d37-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="d8d37-293">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="d8d37-294">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="d8d37-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="d8d37-295">UndoAll</span></span>

<span data-ttu-id="d8d37-296">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="d8d37-297">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="d8d37-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="d8d37-298">UnixWordRubout</span></span>

<span data-ttu-id="d8d37-299">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="d8d37-300">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="d8d37-301">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="d8d37-302">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="d8d37-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="d8d37-304">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-304">Attempt to execute the current input.</span></span> <span data-ttu-id="d8d37-305">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="d8d37-306">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="d8d37-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-307">ViAcceptLine</span></span>

<span data-ttu-id="d8d37-308">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="d8d37-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="d8d37-309">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="d8d37-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="d8d37-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="d8d37-311">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="d8d37-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="d8d37-312">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="d8d37-313">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="d8d37-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-314">ViAppendLine</span></span>

<span data-ttu-id="d8d37-315">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="d8d37-316">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="d8d37-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="d8d37-318">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="d8d37-319">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="d8d37-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-320">ViBackwardGlob</span></span>

<span data-ttu-id="d8d37-321">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="d8d37-322">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="d8d37-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="d8d37-323">ViDeleteBrace</span></span>

<span data-ttu-id="d8d37-324">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="d8d37-325">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="d8d37-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="d8d37-327">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="d8d37-328">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="d8d37-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-329">ViDeleteGlob</span></span>

<span data-ttu-id="d8d37-330">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="d8d37-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="d8d37-331">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="d8d37-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="d8d37-333">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-333">Deletes until given character.</span></span>

- <span data-ttu-id="d8d37-334">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="d8d37-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="d8d37-336">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-336">Deletes until given character.</span></span>

- <span data-ttu-id="d8d37-337">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="d8d37-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-338">ViDeleteToChar</span></span>

<span data-ttu-id="d8d37-339">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-339">Deletes until given character.</span></span>

- <span data-ttu-id="d8d37-340">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="d8d37-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="d8d37-342">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="d8d37-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="d8d37-343">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="d8d37-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="d8d37-344">ViInsertAtBegining</span></span>

<span data-ttu-id="d8d37-345">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="d8d37-346">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="d8d37-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="d8d37-347">ViInsertAtEnd</span></span>

<span data-ttu-id="d8d37-348">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="d8d37-349">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="d8d37-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-350">ViInsertLine</span></span>

<span data-ttu-id="d8d37-351">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="d8d37-352">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="d8d37-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="d8d37-353">ViInsertWithAppend</span></span>

<span data-ttu-id="d8d37-354">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-354">Append from the current line position.</span></span>

- <span data-ttu-id="d8d37-355">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="d8d37-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="d8d37-356">ViInsertWithDelete</span></span>

<span data-ttu-id="d8d37-357">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="d8d37-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="d8d37-358">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="d8d37-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="d8d37-359">ViJoinLines</span></span>

<span data-ttu-id="d8d37-360">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="d8d37-361">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="d8d37-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-362">ViReplaceLine</span></span>

<span data-ttu-id="d8d37-363">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-363">Erase the entire command line.</span></span>

- <span data-ttu-id="d8d37-364">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="d8d37-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="d8d37-366">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-366">Replaces until given character.</span></span>

- <span data-ttu-id="d8d37-367">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="d8d37-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="d8d37-369">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-369">Replaces until given character.</span></span>

- <span data-ttu-id="d8d37-370">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="d8d37-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-371">ViReplaceToChar</span></span>

<span data-ttu-id="d8d37-372">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-372">Deletes until given character.</span></span>

- <span data-ttu-id="d8d37-373">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="d8d37-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="d8d37-375">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-375">Replaces until given character.</span></span>

- <span data-ttu-id="d8d37-376">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="d8d37-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="d8d37-378">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="d8d37-379">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="d8d37-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="d8d37-381">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="d8d37-382">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="d8d37-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-383">ViYankEndOfWord</span></span>

<span data-ttu-id="d8d37-384">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="d8d37-385">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="d8d37-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="d8d37-386">ViYankLeft</span></span>

<span data-ttu-id="d8d37-387">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="d8d37-388">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="d8d37-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-389">ViYankLine</span></span>

<span data-ttu-id="d8d37-390">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="d8d37-391">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="d8d37-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-392">ViYankNextGlob</span></span>

<span data-ttu-id="d8d37-393">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="d8d37-394">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="d8d37-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-395">ViYankNextWord</span></span>

<span data-ttu-id="d8d37-396">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="d8d37-397">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="d8d37-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="d8d37-398">ViYankPercent</span></span>

<span data-ttu-id="d8d37-399">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="d8d37-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="d8d37-400">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="d8d37-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="d8d37-402">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="d8d37-403">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="d8d37-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-404">ViYankPreviousWord</span></span>

<span data-ttu-id="d8d37-405">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="d8d37-406">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="d8d37-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="d8d37-407">ViYankRight</span></span>

<span data-ttu-id="d8d37-408">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="d8d37-409">Kommando läge för vi: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="d8d37-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="d8d37-411">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="d8d37-412">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="d8d37-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-413">ViYankToFirstChar</span></span>

<span data-ttu-id="d8d37-414">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="d8d37-415">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="d8d37-416">Yank</span><span class="sxs-lookup"><span data-stu-id="d8d37-416">Yank</span></span>

<span data-ttu-id="d8d37-417">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="d8d37-418">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="d8d37-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="d8d37-419">YankLastArg</span></span>

<span data-ttu-id="d8d37-420">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="d8d37-421">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="d8d37-422">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="d8d37-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="d8d37-423">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="d8d37-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="d8d37-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="d8d37-425">YankNthArg</span></span>

<span data-ttu-id="d8d37-426">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="d8d37-427">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="d8d37-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="d8d37-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="d8d37-429">YankPop</span></span>

<span data-ttu-id="d8d37-430">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="d8d37-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="d8d37-432">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="d8d37-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-433">BackwardChar</span></span>

<span data-ttu-id="d8d37-434">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="d8d37-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="d8d37-435">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="d8d37-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="d8d37-436">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="d8d37-438">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-439">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="d8d37-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-440">BackwardWord</span></span>

<span data-ttu-id="d8d37-441">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d8d37-442">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-443">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="d8d37-445">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-446">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="d8d37-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-447">BeginningOfLine</span></span>

<span data-ttu-id="d8d37-448">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="d8d37-449">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="d8d37-450">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="d8d37-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="d8d37-452">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="d8d37-453">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="d8d37-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-454">EndOfLine</span></span>

<span data-ttu-id="d8d37-455">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="d8d37-456">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="d8d37-457">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="d8d37-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="d8d37-459">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="d8d37-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-460">ForwardChar</span></span>

<span data-ttu-id="d8d37-461">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="d8d37-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="d8d37-462">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="d8d37-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="d8d37-463">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="d8d37-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="d8d37-465">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="d8d37-466">Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="d8d37-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-467">ForwardWord</span></span>

<span data-ttu-id="d8d37-468">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d8d37-469">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="d8d37-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="d8d37-471">GotoBrace</span></span>

<span data-ttu-id="d8d37-472">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="d8d37-473">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d8d37-474">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d8d37-475">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="d8d37-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="d8d37-476">GotoColumn</span></span>

<span data-ttu-id="d8d37-477">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="d8d37-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="d8d37-478">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="d8d37-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="d8d37-480">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="d8d37-481">Kommando läge för vi: `<^>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="d8d37-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-482">MoveToEndOfLine</span></span>

<span data-ttu-id="d8d37-483">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="d8d37-484">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="d8d37-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-485">NextLine</span></span>

<span data-ttu-id="d8d37-486">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="d8d37-487">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="d8d37-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-488">NextWord</span></span>

<span data-ttu-id="d8d37-489">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d8d37-490">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-491">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="d8d37-492">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="d8d37-493">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="d8d37-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="d8d37-494">NextWordEnd</span></span>

<span data-ttu-id="d8d37-495">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d8d37-496">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-497">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="d8d37-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-498">PreviousLine</span></span>

<span data-ttu-id="d8d37-499">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="d8d37-500">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="d8d37-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-501">ShellBackwardWord</span></span>

<span data-ttu-id="d8d37-502">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d8d37-503">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="d8d37-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d8d37-504">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="d8d37-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-505">ShellForwardWord</span></span>

<span data-ttu-id="d8d37-506">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d8d37-507">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="d8d37-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d8d37-508">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="d8d37-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-509">ShellNextWord</span></span>

<span data-ttu-id="d8d37-510">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="d8d37-511">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="d8d37-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="d8d37-512">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="d8d37-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-513">ViBackwardWord</span></span>

<span data-ttu-id="d8d37-514">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="d8d37-515">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-516">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="d8d37-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-517">ViEndOfGlob</span></span>

<span data-ttu-id="d8d37-518">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="d8d37-519">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="d8d37-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="d8d37-521">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="d8d37-522">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="d8d37-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="d8d37-523">ViGotoBrace</span></span>

<span data-ttu-id="d8d37-524">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="d8d37-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="d8d37-525">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="d8d37-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="d8d37-526">ViNextGlob</span></span>

<span data-ttu-id="d8d37-527">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="d8d37-528">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="d8d37-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-529">ViNextWord</span></span>

<span data-ttu-id="d8d37-530">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="d8d37-531">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="d8d37-532">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="d8d37-533">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="d8d37-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-534">BeginningOfHistory</span></span>

<span data-ttu-id="d8d37-535">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="d8d37-536">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="d8d37-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="d8d37-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-537">ClearHistory</span></span>

<span data-ttu-id="d8d37-538">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d8d37-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="d8d37-539">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="d8d37-540">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="d8d37-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-541">EndOfHistory</span></span>

<span data-ttu-id="d8d37-542">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="d8d37-543">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="d8d37-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-544">ForwardSearchHistory</span></span>

<span data-ttu-id="d8d37-545">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="d8d37-546">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="d8d37-547">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="d8d37-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-548">HistorySearchBackward</span></span>

<span data-ttu-id="d8d37-549">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="d8d37-550">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="d8d37-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="d8d37-551">HistorySearchForward</span></span>

<span data-ttu-id="d8d37-552">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="d8d37-553">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="d8d37-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-554">NextHistory</span></span>

<span data-ttu-id="d8d37-555">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="d8d37-556">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="d8d37-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="d8d37-558">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="d8d37-559">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="d8d37-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-560">PreviousHistory</span></span>

<span data-ttu-id="d8d37-561">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="d8d37-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="d8d37-562">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="d8d37-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="d8d37-564">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="d8d37-565">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="d8d37-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="d8d37-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="d8d37-566">ReverseSearchHistory</span></span>

<span data-ttu-id="d8d37-567">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="d8d37-568">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="d8d37-569">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="d8d37-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="d8d37-571">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="d8d37-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="d8d37-572">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="d8d37-573">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="d8d37-574">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="d8d37-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="d8d37-575">Klart</span><span class="sxs-lookup"><span data-stu-id="d8d37-575">Complete</span></span>

<span data-ttu-id="d8d37-576">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="d8d37-577">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="d8d37-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="d8d37-578">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="d8d37-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="d8d37-579">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="d8d37-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="d8d37-580">MenuComplete</span></span>

<span data-ttu-id="d8d37-581">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="d8d37-582">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="d8d37-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="d8d37-583">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="d8d37-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="d8d37-584">Kommandot `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="d8d37-585">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="d8d37-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="d8d37-586">PossibleCompletions</span></span>

<span data-ttu-id="d8d37-587">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="d8d37-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="d8d37-588">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="d8d37-589">Vi infognings läge: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="d8d37-590">Kommando läge för vi: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="d8d37-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="d8d37-591">TabCompleteNext</span></span>

<span data-ttu-id="d8d37-592">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="d8d37-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="d8d37-593">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="d8d37-594">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="d8d37-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="d8d37-595">TabCompletePrevious</span></span>

<span data-ttu-id="d8d37-596">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="d8d37-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="d8d37-597">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="d8d37-598">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="d8d37-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="d8d37-599">ViTabCompleteNext</span></span>

<span data-ttu-id="d8d37-600">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="d8d37-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="d8d37-601">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="d8d37-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="d8d37-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="d8d37-603">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="d8d37-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="d8d37-604">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="d8d37-605">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="d8d37-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="d8d37-606">CaptureScreen</span></span>

<span data-ttu-id="d8d37-607">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="d8d37-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="d8d37-608">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="d8d37-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="d8d37-609">ClearScreen</span></span>

<span data-ttu-id="d8d37-610">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="d8d37-611">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d8d37-612">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d8d37-613">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="d8d37-614">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="d8d37-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="d8d37-615">DigitArgument</span></span>

<span data-ttu-id="d8d37-616">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d37-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="d8d37-617">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="d8d37-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="d8d37-618">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="d8d37-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="d8d37-619">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="d8d37-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="d8d37-620">InvokePrompt</span></span>

<span data-ttu-id="d8d37-621">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="d8d37-622">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="d8d37-623">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="d8d37-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="d8d37-624">ScrollDisplayDown</span></span>

<span data-ttu-id="d8d37-625">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="d8d37-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="d8d37-626">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="d8d37-627">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="d8d37-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="d8d37-629">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="d8d37-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="d8d37-630">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="d8d37-631">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="d8d37-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="d8d37-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="d8d37-633">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="d8d37-634">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="d8d37-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="d8d37-635">ScrollDisplayTop</span></span>

<span data-ttu-id="d8d37-636">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="d8d37-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="d8d37-637">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="d8d37-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="d8d37-638">ScrollDisplayUp</span></span>

<span data-ttu-id="d8d37-639">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="d8d37-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="d8d37-640">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="d8d37-641">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="d8d37-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="d8d37-643">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="d8d37-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="d8d37-644">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="d8d37-645">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="d8d37-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="d8d37-646">SelfInsert</span></span>

<span data-ttu-id="d8d37-647">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="d8d37-647">Insert the key.</span></span>

- <span data-ttu-id="d8d37-648">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="d8d37-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="d8d37-649">ShowKeyBindings</span></span>

<span data-ttu-id="d8d37-650">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="d8d37-650">Show all bound keys.</span></span>

- <span data-ttu-id="d8d37-651">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="d8d37-652">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="d8d37-653">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="d8d37-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="d8d37-654">ViCommandMode</span></span>

<span data-ttu-id="d8d37-655">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="d8d37-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="d8d37-656">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="d8d37-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="d8d37-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="d8d37-658">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="d8d37-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="d8d37-659">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="d8d37-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="d8d37-660">ViEditVisually</span></span>

<span data-ttu-id="d8d37-661">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="d8d37-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="d8d37-662">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="d8d37-663">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="d8d37-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="d8d37-664">ViExit</span></span>

<span data-ttu-id="d8d37-665">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-665">Exits the shell.</span></span>

- <span data-ttu-id="d8d37-666">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="d8d37-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="d8d37-667">ViInsertMode</span></span>

<span data-ttu-id="d8d37-668">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="d8d37-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="d8d37-669">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="d8d37-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="d8d37-670">WhatIsKey</span></span>

<span data-ttu-id="d8d37-671">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="d8d37-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="d8d37-672">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="d8d37-673">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="d8d37-674">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="d8d37-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="d8d37-675">ExchangePointAndMark</span></span>

<span data-ttu-id="d8d37-676">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="d8d37-677">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="d8d37-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="d8d37-678">SelectAll</span></span>

<span data-ttu-id="d8d37-679">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-679">Select the entire line.</span></span>

- <span data-ttu-id="d8d37-680">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="d8d37-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-681">SelectBackwardChar</span></span>

<span data-ttu-id="d8d37-682">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="d8d37-683">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-684">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="d8d37-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-685">SelectBackwardsLine</span></span>

<span data-ttu-id="d8d37-686">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="d8d37-687">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="d8d37-688">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="d8d37-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-689">SelectBackwardWord</span></span>

<span data-ttu-id="d8d37-690">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="d8d37-691">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="d8d37-692">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="d8d37-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-693">SelectForwardChar</span></span>

<span data-ttu-id="d8d37-694">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="d8d37-695">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="d8d37-696">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="d8d37-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-697">SelectForwardWord</span></span>

<span data-ttu-id="d8d37-698">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="d8d37-699">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="d8d37-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-700">SelectLine</span></span>

<span data-ttu-id="d8d37-701">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="d8d37-702">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="d8d37-703">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="d8d37-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-704">SelectNextWord</span></span>

<span data-ttu-id="d8d37-705">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="d8d37-706">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="d8d37-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="d8d37-708">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="d8d37-709">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="d8d37-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-710">SelectShellForwardWord</span></span>

<span data-ttu-id="d8d37-711">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="d8d37-712">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="d8d37-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="d8d37-713">SelectShellNextWord</span></span>

<span data-ttu-id="d8d37-714">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="d8d37-715">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="d8d37-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="d8d37-716">SetMark</span></span>

<span data-ttu-id="d8d37-717">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="d8d37-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="d8d37-718">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="d8d37-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="d8d37-719">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="d8d37-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="d8d37-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="d8d37-720">CharacterSearch</span></span>

<span data-ttu-id="d8d37-721">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="d8d37-722">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="d8d37-723">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="d8d37-724">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="d8d37-725">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="d8d37-726">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="d8d37-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-727">CharacterSearchBackward</span></span>

<span data-ttu-id="d8d37-728">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="d8d37-729">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="d8d37-730">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="d8d37-731">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="d8d37-732">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="d8d37-733">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="d8d37-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="d8d37-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="d8d37-735">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="d8d37-736">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="d8d37-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="d8d37-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="d8d37-738">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="d8d37-739">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="d8d37-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="d8d37-740">RepeatSearch</span></span>

<span data-ttu-id="d8d37-741">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="d8d37-742">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="d8d37-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-743">RepeatSearchBackward</span></span>

<span data-ttu-id="d8d37-744">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="d8d37-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="d8d37-745">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="d8d37-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="d8d37-746">SearchChar</span></span>

<span data-ttu-id="d8d37-747">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="d8d37-748">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d37-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="d8d37-749">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="d8d37-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="d8d37-750">SearchCharBackward</span></span>

<span data-ttu-id="d8d37-751">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="d8d37-752">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d37-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="d8d37-753">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="d8d37-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="d8d37-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="d8d37-755">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="d8d37-756">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d37-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="d8d37-757">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="d8d37-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="d8d37-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="d8d37-759">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="d8d37-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="d8d37-760">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="d8d37-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="d8d37-761">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="d8d37-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="d8d37-762">SearchForward</span></span>

<span data-ttu-id="d8d37-763">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="d8d37-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="d8d37-764">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="d8d37-765">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="d8d37-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="d8d37-766">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="d8d37-766">Custom Key Bindings</span></span>

<span data-ttu-id="d8d37-767">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="d8d37-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="d8d37-768">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="d8d37-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="d8d37-769">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="d8d37-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="d8d37-770">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="d8d37-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="d8d37-771">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="d8d37-771">Some useful examples include</span></span>

- <span data-ttu-id="d8d37-772">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="d8d37-772">edit the command line</span></span>
- <span data-ttu-id="d8d37-773">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="d8d37-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="d8d37-774">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="d8d37-774">change directories without changing the command line</span></span>

<span data-ttu-id="d8d37-775">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="d8d37-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="d8d37-776">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="d8d37-777">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="d8d37-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="d8d37-778">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="d8d37-779">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="d8d37-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="d8d37-780">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="d8d37-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="d8d37-781">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="d8d37-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="d8d37-782">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="d8d37-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="d8d37-783">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="d8d37-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

```powershell
$parameters = @{
    Key = 'Alt+w'
    BriefDescription = 'SaveInHistory'
    LongDescription = 'Save current line in history but do not execute'
    ScriptBlock = {
      param($key, $arg)   # The arguments are ignored in this example

      # GetBufferState gives us the command line (with the cursor position)
      $line = $null
      $cursor = $null
      [Microsoft.PowerShell.PSConsoleReadLine]::GetBufferState([ref]$line,
        [ref]$cursor)

      # AddToHistory saves the line in history, but does not execute it.
      [Microsoft.PowerShell.PSConsoleReadLine]::AddToHistory($line)

      # RevertLine is like pressing Escape.
      [Microsoft.PowerShell.PSConsoleReadLine]::RevertLine()
  }
}
Set-PSReadLineKeyHandler @parameters
```

<span data-ttu-id="d8d37-784">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="d8d37-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="d8d37-785">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="d8d37-786">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="d8d37-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="d8d37-787">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="d8d37-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="d8d37-788">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="d8d37-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="d8d37-789">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="d8d37-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="d8d37-790">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="d8d37-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="d8d37-791">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-791">Clear the kill-ring.</span></span>  <span data-ttu-id="d8d37-792">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="d8d37-793">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="d8d37-793">Delete length characters from start.</span></span>  <span data-ttu-id="d8d37-794">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="d8d37-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="d8d37-795">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="d8d37-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="d8d37-796">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="d8d37-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="d8d37-797">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="d8d37-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="d8d37-798">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="d8d37-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="d8d37-799">Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="d8d37-800">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="d8d37-801">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="d8d37-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="d8d37-802">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="d8d37-803">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="d8d37-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="d8d37-804">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="d8d37-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="d8d37-805">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="d8d37-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="d8d37-806">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="d8d37-807">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="d8d37-808">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="d8d37-808">Replace some of the input.</span></span> <span data-ttu-id="d8d37-809">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="d8d37-809">This operation supports undo/redo.</span></span> <span data-ttu-id="d8d37-810">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="d8d37-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="d8d37-811">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="d8d37-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="d8d37-812">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="d8d37-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="d8d37-813">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="d8d37-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="d8d37-814">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="d8d37-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="d8d37-815">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="d8d37-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="d8d37-816">NOTE</span><span class="sxs-lookup"><span data-stu-id="d8d37-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="d8d37-817">POWERSHELL-KOMPATIBILITET</span><span class="sxs-lookup"><span data-stu-id="d8d37-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="d8d37-818">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="d8d37-819">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="d8d37-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="d8d37-820">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d8d37-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="d8d37-821">KOMMANDO HISTORIK</span><span class="sxs-lookup"><span data-stu-id="d8d37-821">COMMAND HISTORY</span></span>

<span data-ttu-id="d8d37-822">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="d8d37-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="d8d37-823">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="d8d37-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="d8d37-824">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="d8d37-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="d8d37-825">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="d8d37-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="d8d37-826">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="d8d37-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="d8d37-827">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="d8d37-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="d8d37-828">FEEDBACK & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="d8d37-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="d8d37-829">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="d8d37-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="d8d37-830">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="d8d37-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="d8d37-831">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="d8d37-831">SEE ALSO</span></span>

<span data-ttu-id="d8d37-832">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="d8d37-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
