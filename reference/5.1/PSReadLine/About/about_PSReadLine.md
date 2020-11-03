---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: ad6e85a30f866cb332c89a4c36f42231f511f5ae
ms.sourcegitcommit: ae8b89e12c6fa2108075888dd6da92788d6c2888
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/21/2020
ms.locfileid: "93273213"
---
# <a name="psreadline"></a><span data-ttu-id="ff820-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ff820-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="ff820-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ff820-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="ff820-106">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff820-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="ff820-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ff820-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="ff820-108">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="ff820-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="ff820-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="ff820-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="ff820-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="ff820-110">It provides:</span></span>

- <span data-ttu-id="ff820-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="ff820-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="ff820-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="ff820-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="ff820-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="ff820-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="ff820-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="ff820-114">Customizable key bindings</span></span>
- <span data-ttu-id="ff820-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="ff820-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="ff820-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="ff820-116">Many configuration options</span></span>
- <span data-ttu-id="ff820-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="ff820-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="ff820-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="ff820-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="ff820-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="ff820-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="ff820-120">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="ff820-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="ff820-121">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-121">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="ff820-122">Avbryta</span><span class="sxs-lookup"><span data-stu-id="ff820-122">Abort</span></span>

<span data-ttu-id="ff820-123">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="ff820-123">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="ff820-124">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="ff820-124">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="ff820-125">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="ff820-125">AcceptAndGetNext</span></span>

<span data-ttu-id="ff820-126">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-126">Attempt to execute the current input.</span></span> <span data-ttu-id="ff820-127">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="ff820-127">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="ff820-128">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="ff820-128">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="ff820-129">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="ff820-129">AcceptLine</span></span>

<span data-ttu-id="ff820-130">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-130">Attempt to execute the current input.</span></span> <span data-ttu-id="ff820-131">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-131">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ff820-132">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-132">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="ff820-133">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-133">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="ff820-134">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-134">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="ff820-135">AddLine</span><span class="sxs-lookup"><span data-stu-id="ff820-135">AddLine</span></span>

<span data-ttu-id="ff820-136">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-136">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="ff820-137">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="ff820-137">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="ff820-138">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-138">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ff820-139">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-139">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ff820-140">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-140">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="ff820-141">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-141">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="ff820-142">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="ff820-142">BackwardDeleteChar</span></span>

<span data-ttu-id="ff820-143">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-143">Delete the character before the cursor.</span></span>

- <span data-ttu-id="ff820-144">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ff820-144">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ff820-145">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="ff820-145">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="ff820-146">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-146">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="ff820-147">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="ff820-147">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="ff820-148">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ff820-148">BackwardDeleteLine</span></span>

<span data-ttu-id="ff820-149">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-149">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ff820-150">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-150">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ff820-151">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-151">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="ff820-152">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="ff820-152">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="ff820-153">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="ff820-153">BackwardDeleteWord</span></span>

<span data-ttu-id="ff820-154">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-154">Deletes the previous word.</span></span>

- <span data-ttu-id="ff820-155">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="ff820-155">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="ff820-156">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="ff820-156">BackwardKillLine</span></span>

<span data-ttu-id="ff820-157">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-157">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="ff820-158">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-158">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ff820-159">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-159">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="ff820-160">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ff820-160">BackwardKillWord</span></span>

<span data-ttu-id="ff820-161">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-161">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ff820-162">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-162">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ff820-163">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-163">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ff820-164">Kommandot `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-164">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="ff820-165">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-165">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="ff820-166">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-166">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="ff820-167">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="ff820-167">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="ff820-168">CancelLine</span><span class="sxs-lookup"><span data-stu-id="ff820-168">CancelLine</span></span>

<span data-ttu-id="ff820-169">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="ff820-169">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="ff820-170">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ff820-170">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ff820-171">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ff820-171">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="ff820-172">Kopiera</span><span class="sxs-lookup"><span data-stu-id="ff820-172">Copy</span></span>

<span data-ttu-id="ff820-173">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="ff820-173">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="ff820-174">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-174">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="ff820-175">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="ff820-175">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="ff820-176">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="ff820-176">CopyOrCancelLine</span></span>

<span data-ttu-id="ff820-177">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-177">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="ff820-178">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ff820-178">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="ff820-179">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="ff820-179">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="ff820-180">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="ff820-180">Cut</span></span>

<span data-ttu-id="ff820-181">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="ff820-181">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="ff820-182">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ff820-182">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="ff820-183">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="ff820-183">DeleteChar</span></span>

<span data-ttu-id="ff820-184">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-184">Delete the character under the cursor.</span></span>

- <span data-ttu-id="ff820-185">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-185">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="ff820-186">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-186">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="ff820-187">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-187">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="ff820-188">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-188">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="ff820-189">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="ff820-189">DeleteCharOrExit</span></span>

<span data-ttu-id="ff820-190">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="ff820-190">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="ff820-191">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ff820-191">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="ff820-192">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ff820-192">DeleteEndOfWord</span></span>

<span data-ttu-id="ff820-193">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="ff820-193">Delete to the end of the word.</span></span>

- <span data-ttu-id="ff820-194">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="ff820-194">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="ff820-195">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="ff820-195">DeleteLine</span></span>

<span data-ttu-id="ff820-196">Tar bort den aktuella raden och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="ff820-196">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="ff820-197">Kommando läge för vi: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="ff820-197">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="ff820-198">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ff820-198">DeleteLineToFirstChar</span></span>

<span data-ttu-id="ff820-199">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-199">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="ff820-200">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="ff820-200">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="ff820-201">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="ff820-201">DeleteToEnd</span></span>

<span data-ttu-id="ff820-202">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-202">Delete to the end of the line.</span></span>

- <span data-ttu-id="ff820-203">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="ff820-203">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="ff820-204">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="ff820-204">DeleteWord</span></span>

<span data-ttu-id="ff820-205">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-205">Delete the next word.</span></span>

- <span data-ttu-id="ff820-206">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="ff820-206">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="ff820-207">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="ff820-207">ForwardDeleteLine</span></span>

<span data-ttu-id="ff820-208">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-208">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="ff820-209">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-209">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ff820-210">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-210">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="ff820-211">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-211">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="ff820-212">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="ff820-212">InsertLineAbove</span></span>

<span data-ttu-id="ff820-213">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-213">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ff820-214">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-214">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ff820-215">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-215">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="ff820-216">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="ff820-216">InsertLineBelow</span></span>

<span data-ttu-id="ff820-217">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-217">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="ff820-218">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="ff820-219">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-219">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="ff820-220">InvertCase</span><span class="sxs-lookup"><span data-stu-id="ff820-220">InvertCase</span></span>

<span data-ttu-id="ff820-221">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="ff820-221">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="ff820-222">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="ff820-222">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="ff820-223">KillLine</span><span class="sxs-lookup"><span data-stu-id="ff820-223">KillLine</span></span>

<span data-ttu-id="ff820-224">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-224">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="ff820-225">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-225">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ff820-226">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="ff820-226">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="ff820-227">KillRegion</span><span class="sxs-lookup"><span data-stu-id="ff820-227">KillRegion</span></span>

<span data-ttu-id="ff820-228">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-228">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="ff820-229">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-229">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="ff820-230">KillWord</span><span class="sxs-lookup"><span data-stu-id="ff820-230">KillWord</span></span>

<span data-ttu-id="ff820-231">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="ff820-231">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ff820-232">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-232">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ff820-233">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-233">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ff820-234">Kommandot `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-234">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ff820-235">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="ff820-235">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="ff820-236">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-236">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="ff820-237">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="ff820-237">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="ff820-238">Klistra in</span><span class="sxs-lookup"><span data-stu-id="ff820-238">Paste</span></span>

<span data-ttu-id="ff820-239">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="ff820-239">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="ff820-240">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="ff820-240">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="ff820-241">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ff820-241">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="ff820-242">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="ff820-242">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="ff820-243">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ff820-243">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="ff820-244">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="ff820-244">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="ff820-245">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="ff820-245">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="ff820-246">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="ff820-246">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="ff820-247">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="ff820-247">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="ff820-248">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="ff820-248">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="ff820-249">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="ff820-249">PasteAfter</span></span>

<span data-ttu-id="ff820-250">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="ff820-250">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ff820-251">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="ff820-251">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="ff820-252">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="ff820-252">PasteBefore</span></span>

<span data-ttu-id="ff820-253">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="ff820-253">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="ff820-254">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="ff820-254">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="ff820-255">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="ff820-255">PrependAndAccept</span></span>

<span data-ttu-id="ff820-256">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-256">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="ff820-257">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="ff820-257">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="ff820-258">Gör om</span><span class="sxs-lookup"><span data-stu-id="ff820-258">Redo</span></span>

<span data-ttu-id="ff820-259">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="ff820-259">Undo an undo.</span></span>

- <span data-ttu-id="ff820-260">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-260">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ff820-261">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-261">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="ff820-262">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-262">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="ff820-263">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="ff820-263">RepeatLastCommand</span></span>

<span data-ttu-id="ff820-264">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-264">Repeat the last text modification.</span></span>

- <span data-ttu-id="ff820-265">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="ff820-265">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="ff820-266">RevertLine</span><span class="sxs-lookup"><span data-stu-id="ff820-266">RevertLine</span></span>

<span data-ttu-id="ff820-267">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="ff820-267">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="ff820-268">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ff820-268">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="ff820-269">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="ff820-269">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="ff820-270">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="ff820-270">ShellBackwardKillWord</span></span>

<span data-ttu-id="ff820-271">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-271">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ff820-272">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-272">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ff820-273">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-273">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ff820-274">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-274">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="ff820-275">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="ff820-275">ShellKillWord</span></span>

<span data-ttu-id="ff820-276">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="ff820-276">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="ff820-277">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-277">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="ff820-278">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-278">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="ff820-279">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-279">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="ff820-280">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="ff820-280">SwapCharacters</span></span>

<span data-ttu-id="ff820-281">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="ff820-281">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="ff820-282">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-282">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ff820-283">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-283">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="ff820-284">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-284">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="ff820-285">Ångra</span><span class="sxs-lookup"><span data-stu-id="ff820-285">Undo</span></span>

<span data-ttu-id="ff820-286">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="ff820-286">Undo a previous edit.</span></span>

- <span data-ttu-id="ff820-287">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ff820-287">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ff820-288">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="ff820-288">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="ff820-289">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="ff820-289">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="ff820-290">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="ff820-290">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="ff820-291">UndoAll</span><span class="sxs-lookup"><span data-stu-id="ff820-291">UndoAll</span></span>

<span data-ttu-id="ff820-292">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-292">Undo all previous edits for line.</span></span>

- <span data-ttu-id="ff820-293">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="ff820-293">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="ff820-294">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="ff820-294">UnixWordRubout</span></span>

<span data-ttu-id="ff820-295">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-295">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="ff820-296">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-296">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="ff820-297">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-297">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="ff820-298">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="ff820-298">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="ff820-299">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ff820-299">ValidateAndAcceptLine</span></span>

<span data-ttu-id="ff820-300">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-300">Attempt to execute the current input.</span></span> <span data-ttu-id="ff820-301">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-301">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="ff820-302">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="ff820-302">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="ff820-303">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="ff820-303">ViAcceptLine</span></span>

<span data-ttu-id="ff820-304">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="ff820-304">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="ff820-305">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="ff820-305">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="ff820-306">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="ff820-306">ViAcceptLineOrExit</span></span>

<span data-ttu-id="ff820-307">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="ff820-307">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="ff820-308">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ff820-308">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="ff820-309">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="ff820-309">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="ff820-310">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="ff820-310">ViAppendLine</span></span>

<span data-ttu-id="ff820-311">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-311">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="ff820-312">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="ff820-312">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="ff820-313">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-313">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="ff820-314">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ff820-314">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="ff820-315">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="ff820-315">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="ff820-316">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-316">ViBackwardGlob</span></span>

<span data-ttu-id="ff820-317">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ff820-317">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ff820-318">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="ff820-318">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="ff820-319">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="ff820-319">ViDeleteBrace</span></span>

<span data-ttu-id="ff820-320">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="ff820-320">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="ff820-321">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="ff820-321">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="ff820-322">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-322">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="ff820-323">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="ff820-323">Delete to the end of the word.</span></span>

- <span data-ttu-id="ff820-324">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="ff820-324">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="ff820-325">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-325">ViDeleteGlob</span></span>

<span data-ttu-id="ff820-326">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="ff820-326">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="ff820-327">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="ff820-327">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="ff820-328">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ff820-328">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="ff820-329">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="ff820-329">Deletes until given character.</span></span>

- <span data-ttu-id="ff820-330">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-330">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="ff820-331">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-331">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="ff820-332">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="ff820-332">Deletes until given character.</span></span>

- <span data-ttu-id="ff820-333">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="ff820-333">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="ff820-334">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="ff820-334">ViDeleteToChar</span></span>

<span data-ttu-id="ff820-335">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="ff820-335">Deletes until given character.</span></span>

- <span data-ttu-id="ff820-336">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="ff820-336">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="ff820-337">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-337">ViDeleteToCharBackward</span></span>

<span data-ttu-id="ff820-338">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="ff820-338">Deletes backwards until given character.</span></span>

- <span data-ttu-id="ff820-339">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="ff820-339">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="ff820-340">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="ff820-340">ViInsertAtBegining</span></span>

<span data-ttu-id="ff820-341">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-341">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="ff820-342">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="ff820-342">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="ff820-343">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="ff820-343">ViInsertAtEnd</span></span>

<span data-ttu-id="ff820-344">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-344">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="ff820-345">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="ff820-345">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="ff820-346">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="ff820-346">ViInsertLine</span></span>

<span data-ttu-id="ff820-347">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-347">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="ff820-348">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="ff820-348">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="ff820-349">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="ff820-349">ViInsertWithAppend</span></span>

<span data-ttu-id="ff820-350">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="ff820-350">Append from the current line position.</span></span>

- <span data-ttu-id="ff820-351">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="ff820-351">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="ff820-352">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="ff820-352">ViInsertWithDelete</span></span>

<span data-ttu-id="ff820-353">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="ff820-353">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="ff820-354">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="ff820-354">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="ff820-355">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="ff820-355">ViJoinLines</span></span>

<span data-ttu-id="ff820-356">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-356">Joins the current line and the next line.</span></span>

- <span data-ttu-id="ff820-357">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="ff820-357">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="ff820-358">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="ff820-358">ViReplaceLine</span></span>

<span data-ttu-id="ff820-359">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-359">Erase the entire command line.</span></span>

- <span data-ttu-id="ff820-360">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="ff820-360">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="ff820-361">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="ff820-361">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="ff820-362">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="ff820-362">Replaces until given character.</span></span>

- <span data-ttu-id="ff820-363">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-363">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="ff820-364">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-364">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="ff820-365">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="ff820-365">Replaces until given character.</span></span>

- <span data-ttu-id="ff820-366">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="ff820-366">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="ff820-367">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="ff820-367">ViReplaceToChar</span></span>

<span data-ttu-id="ff820-368">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="ff820-368">Deletes until given character.</span></span>

- <span data-ttu-id="ff820-369">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="ff820-369">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="ff820-370">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-370">ViReplaceToCharBackward</span></span>

<span data-ttu-id="ff820-371">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="ff820-371">Replaces until given character.</span></span>

- <span data-ttu-id="ff820-372">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="ff820-372">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="ff820-373">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-373">ViYankBeginningOfLine</span></span>

<span data-ttu-id="ff820-374">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-374">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="ff820-375">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="ff820-375">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="ff820-376">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-376">ViYankEndOfGlob</span></span>

<span data-ttu-id="ff820-377">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="ff820-377">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="ff820-378">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="ff820-378">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="ff820-379">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="ff820-379">ViYankEndOfWord</span></span>

<span data-ttu-id="ff820-380">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="ff820-380">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="ff820-381">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="ff820-381">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="ff820-382">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="ff820-382">ViYankLeft</span></span>

<span data-ttu-id="ff820-383">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-383">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="ff820-384">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="ff820-384">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="ff820-385">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="ff820-385">ViYankLine</span></span>

<span data-ttu-id="ff820-386">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="ff820-386">Yank the entire buffer.</span></span>

- <span data-ttu-id="ff820-387">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-387">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="ff820-388">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-388">ViYankNextGlob</span></span>

<span data-ttu-id="ff820-389">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-389">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="ff820-390">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="ff820-390">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="ff820-391">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-391">ViYankNextWord</span></span>

<span data-ttu-id="ff820-392">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-392">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="ff820-393">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="ff820-393">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="ff820-394">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="ff820-394">ViYankPercent</span></span>

<span data-ttu-id="ff820-395">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="ff820-395">Yank to/from matching brace.</span></span>

- <span data-ttu-id="ff820-396">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="ff820-396">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="ff820-397">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-397">ViYankPreviousGlob</span></span>

<span data-ttu-id="ff820-398">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-398">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="ff820-399">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="ff820-399">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="ff820-400">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="ff820-400">ViYankPreviousWord</span></span>

<span data-ttu-id="ff820-401">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-401">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="ff820-402">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="ff820-402">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="ff820-403">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="ff820-403">ViYankRight</span></span>

<span data-ttu-id="ff820-404">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-404">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="ff820-405">Kommando läge för vi: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-405">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="ff820-406">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-406">ViYankToEndOfLine</span></span>

<span data-ttu-id="ff820-407">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="ff820-407">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="ff820-408">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="ff820-408">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="ff820-409">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="ff820-409">ViYankToFirstChar</span></span>

<span data-ttu-id="ff820-410">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-410">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="ff820-411">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="ff820-411">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="ff820-412">Yank</span><span class="sxs-lookup"><span data-stu-id="ff820-412">Yank</span></span>

<span data-ttu-id="ff820-413">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-413">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="ff820-414">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-414">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="ff820-415">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="ff820-415">YankLastArg</span></span>

<span data-ttu-id="ff820-416">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-416">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="ff820-417">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="ff820-417">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="ff820-418">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="ff820-418">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="ff820-419">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="ff820-419">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="ff820-420">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="ff820-420">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="ff820-421">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="ff820-421">YankNthArg</span></span>

<span data-ttu-id="ff820-422">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-422">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="ff820-423">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="ff820-423">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="ff820-424">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-424">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="ff820-425">YankPop</span><span class="sxs-lookup"><span data-stu-id="ff820-425">YankPop</span></span>

<span data-ttu-id="ff820-426">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-426">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="ff820-427">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="ff820-427">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="ff820-428">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-428">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="ff820-429">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="ff820-429">BackwardChar</span></span>

<span data-ttu-id="ff820-430">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="ff820-430">Move the cursor one character to the left.</span></span> <span data-ttu-id="ff820-431">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="ff820-431">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="ff820-432">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-432">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="ff820-433">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="ff820-433">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="ff820-434">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-434">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="ff820-435">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="ff820-435">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="ff820-436">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-436">BackwardWord</span></span>

<span data-ttu-id="ff820-437">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-437">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ff820-438">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-438">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-439">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-439">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ff820-440">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="ff820-440">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="ff820-441">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-441">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ff820-442">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-442">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="ff820-443">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-443">BeginningOfLine</span></span>

<span data-ttu-id="ff820-444">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-444">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="ff820-445">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="ff820-445">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="ff820-446">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-446">Cmd: `<Home>`</span></span>
- <span data-ttu-id="ff820-447">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ff820-447">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="ff820-448">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-448">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="ff820-449">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-449">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="ff820-450">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-450">EndOfLine</span></span>

<span data-ttu-id="ff820-451">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-451">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="ff820-452">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-452">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="ff820-453">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-453">Cmd: `<End>`</span></span>
- <span data-ttu-id="ff820-454">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ff820-454">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="ff820-455">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-455">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="ff820-456">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="ff820-456">ForwardChar</span></span>

<span data-ttu-id="ff820-457">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="ff820-457">Move the cursor one character to the right.</span></span> <span data-ttu-id="ff820-458">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="ff820-458">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="ff820-459">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-459">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="ff820-460">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="ff820-460">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="ff820-461">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-461">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="ff820-462">Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="ff820-462">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="ff820-463">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-463">ForwardWord</span></span>

<span data-ttu-id="ff820-464">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-464">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ff820-465">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-465">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-466">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="ff820-466">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="ff820-467">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="ff820-467">GotoBrace</span></span>

<span data-ttu-id="ff820-468">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="ff820-468">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="ff820-469">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ff820-469">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ff820-470">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ff820-470">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ff820-471">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ff820-471">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="ff820-472">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="ff820-472">GotoColumn</span></span>

<span data-ttu-id="ff820-473">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="ff820-473">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="ff820-474">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="ff820-474">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="ff820-475">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-475">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="ff820-476">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-476">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="ff820-477">Kommando läge för vi: `<^>`</span><span class="sxs-lookup"><span data-stu-id="ff820-477">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="ff820-478">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="ff820-478">MoveToEndOfLine</span></span>

<span data-ttu-id="ff820-479">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="ff820-479">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="ff820-480">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="ff820-480">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="ff820-481">NextLine</span><span class="sxs-lookup"><span data-stu-id="ff820-481">NextLine</span></span>

<span data-ttu-id="ff820-482">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-482">Move the cursor to the next line.</span></span>

- <span data-ttu-id="ff820-483">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-483">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="ff820-484">NextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-484">NextWord</span></span>

<span data-ttu-id="ff820-485">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-485">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ff820-486">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-486">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-487">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-487">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ff820-488">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-488">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="ff820-489">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-489">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="ff820-490">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="ff820-490">NextWordEnd</span></span>

<span data-ttu-id="ff820-491">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-491">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ff820-492">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-492">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-493">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="ff820-493">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="ff820-494">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="ff820-494">PreviousLine</span></span>

<span data-ttu-id="ff820-495">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-495">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="ff820-496">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-496">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="ff820-497">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-497">ShellBackwardWord</span></span>

<span data-ttu-id="ff820-498">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-498">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ff820-499">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="ff820-499">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ff820-500">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-500">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="ff820-501">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-501">ShellForwardWord</span></span>

<span data-ttu-id="ff820-502">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-502">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ff820-503">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="ff820-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ff820-504">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-504">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="ff820-505">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-505">ShellNextWord</span></span>

<span data-ttu-id="ff820-506">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-506">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="ff820-507">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="ff820-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="ff820-508">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-508">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="ff820-509">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-509">ViBackwardWord</span></span>

<span data-ttu-id="ff820-510">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-510">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="ff820-511">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-511">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-512">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="ff820-512">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="ff820-513">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-513">ViEndOfGlob</span></span>

<span data-ttu-id="ff820-514">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ff820-514">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="ff820-515">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="ff820-515">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="ff820-516">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-516">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="ff820-517">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ff820-517">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ff820-518">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-518">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="ff820-519">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="ff820-519">ViGotoBrace</span></span>

<span data-ttu-id="ff820-520">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="ff820-520">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="ff820-521">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="ff820-521">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="ff820-522">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="ff820-522">ViNextGlob</span></span>

<span data-ttu-id="ff820-523">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="ff820-523">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="ff820-524">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="ff820-524">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="ff820-525">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-525">ViNextWord</span></span>

<span data-ttu-id="ff820-526">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-526">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="ff820-527">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-527">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="ff820-528">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="ff820-528">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="ff820-529">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-529">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="ff820-530">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-530">BeginningOfHistory</span></span>

<span data-ttu-id="ff820-531">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-531">Move to the first item in the history.</span></span>

- <span data-ttu-id="ff820-532">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="ff820-532">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="ff820-533">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-533">ClearHistory</span></span>

<span data-ttu-id="ff820-534">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ff820-534">Clears history in PSReadLine.</span></span> <span data-ttu-id="ff820-535">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-535">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="ff820-536">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="ff820-536">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="ff820-537">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-537">EndOfHistory</span></span>

<span data-ttu-id="ff820-538">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-538">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="ff820-539">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="ff820-539">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="ff820-540">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-540">ForwardSearchHistory</span></span>

<span data-ttu-id="ff820-541">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-541">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="ff820-542">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ff820-542">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ff820-543">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ff820-543">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="ff820-544">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-544">HistorySearchBackward</span></span>

<span data-ttu-id="ff820-545">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-545">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ff820-546">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="ff820-546">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="ff820-547">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="ff820-547">HistorySearchForward</span></span>

<span data-ttu-id="ff820-548">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-548">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="ff820-549">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="ff820-549">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="ff820-550">NextHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-550">NextHistory</span></span>

<span data-ttu-id="ff820-551">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-551">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="ff820-552">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-552">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="ff820-553">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="ff820-553">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="ff820-554">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-554">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="ff820-555">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="ff820-555">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="ff820-556">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-556">PreviousHistory</span></span>

<span data-ttu-id="ff820-557">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="ff820-557">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="ff820-558">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-558">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="ff820-559">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="ff820-559">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="ff820-560">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-560">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="ff820-561">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="ff820-561">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="ff820-562">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="ff820-562">ReverseSearchHistory</span></span>

<span data-ttu-id="ff820-563">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="ff820-563">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="ff820-564">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ff820-564">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ff820-565">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ff820-565">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="ff820-566">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-566">ViSearchHistoryBackward</span></span>

<span data-ttu-id="ff820-567">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ff820-567">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ff820-568">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ff820-568">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="ff820-569">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="ff820-569">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="ff820-570">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="ff820-570">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="ff820-571">Klart</span><span class="sxs-lookup"><span data-stu-id="ff820-571">Complete</span></span>

<span data-ttu-id="ff820-572">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-572">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ff820-573">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="ff820-573">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ff820-574">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="ff820-574">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ff820-575">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-575">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="ff820-576">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="ff820-576">MenuComplete</span></span>

<span data-ttu-id="ff820-577">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-577">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="ff820-578">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="ff820-578">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="ff820-579">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="ff820-579">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="ff820-580">Kommandot `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-580">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="ff820-581">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-581">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="ff820-582">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="ff820-582">PossibleCompletions</span></span>

<span data-ttu-id="ff820-583">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="ff820-583">Display the list of possible completions.</span></span>

- <span data-ttu-id="ff820-584">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="ff820-584">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="ff820-585">Vi infognings läge: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-585">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="ff820-586">Kommando läge för vi: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="ff820-586">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="ff820-587">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ff820-587">TabCompleteNext</span></span>

<span data-ttu-id="ff820-588">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="ff820-588">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="ff820-589">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-589">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="ff820-590">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-590">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="ff820-591">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ff820-591">TabCompletePrevious</span></span>

<span data-ttu-id="ff820-592">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="ff820-592">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="ff820-593">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-593">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="ff820-594">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-594">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="ff820-595">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="ff820-595">ViTabCompleteNext</span></span>

<span data-ttu-id="ff820-596">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="ff820-596">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="ff820-597">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-597">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="ff820-598">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="ff820-598">ViTabCompletePrevious</span></span>

<span data-ttu-id="ff820-599">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="ff820-599">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="ff820-600">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="ff820-600">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="ff820-601">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-601">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="ff820-602">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="ff820-602">CaptureScreen</span></span>

<span data-ttu-id="ff820-603">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="ff820-603">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="ff820-604">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-604">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="ff820-605">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="ff820-605">ClearScreen</span></span>

<span data-ttu-id="ff820-606">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="ff820-606">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="ff820-607">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ff820-607">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ff820-608">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ff820-608">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ff820-609">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ff820-609">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="ff820-610">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="ff820-610">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="ff820-611">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="ff820-611">DigitArgument</span></span>

<span data-ttu-id="ff820-612">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="ff820-612">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="ff820-613">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ff820-613">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ff820-614">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="ff820-614">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="ff820-615">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="ff820-615">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="ff820-616">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="ff820-616">InvokePrompt</span></span>

<span data-ttu-id="ff820-617">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="ff820-617">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="ff820-618">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="ff820-618">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="ff820-619">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-619">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="ff820-620">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="ff820-620">ScrollDisplayDown</span></span>

<span data-ttu-id="ff820-621">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="ff820-621">Scroll the display down one screen.</span></span>

- <span data-ttu-id="ff820-622">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ff820-622">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="ff820-623">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ff820-623">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="ff820-624">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="ff820-624">ScrollDisplayDownLine</span></span>

<span data-ttu-id="ff820-625">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="ff820-625">Scroll the display down one line.</span></span>

- <span data-ttu-id="ff820-626">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ff820-626">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="ff820-627">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="ff820-627">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="ff820-628">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="ff820-628">ScrollDisplayToCursor</span></span>

<span data-ttu-id="ff820-629">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-629">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="ff820-630">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-630">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="ff820-631">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="ff820-631">ScrollDisplayTop</span></span>

<span data-ttu-id="ff820-632">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="ff820-632">Scroll the display to the top.</span></span>

- <span data-ttu-id="ff820-633">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-633">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="ff820-634">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="ff820-634">ScrollDisplayUp</span></span>

<span data-ttu-id="ff820-635">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="ff820-635">Scroll the display up one screen.</span></span>

- <span data-ttu-id="ff820-636">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ff820-636">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="ff820-637">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ff820-637">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="ff820-638">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="ff820-638">ScrollDisplayUpLine</span></span>

<span data-ttu-id="ff820-639">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="ff820-639">Scroll the display up one line.</span></span>

- <span data-ttu-id="ff820-640">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ff820-640">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="ff820-641">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="ff820-641">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="ff820-642">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="ff820-642">SelfInsert</span></span>

<span data-ttu-id="ff820-643">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="ff820-643">Insert the key.</span></span>

- <span data-ttu-id="ff820-644">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-644">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="ff820-645">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="ff820-645">ShowKeyBindings</span></span>

<span data-ttu-id="ff820-646">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="ff820-646">Show all bound keys.</span></span>

- <span data-ttu-id="ff820-647">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ff820-647">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ff820-648">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ff820-648">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="ff820-649">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ff820-649">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="ff820-650">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="ff820-650">ViCommandMode</span></span>

<span data-ttu-id="ff820-651">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="ff820-651">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="ff820-652">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="ff820-652">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="ff820-653">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="ff820-653">ViDigitArgumentInChord</span></span>

<span data-ttu-id="ff820-654">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="ff820-654">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="ff820-655">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-655">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="ff820-656">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="ff820-656">ViEditVisually</span></span>

<span data-ttu-id="ff820-657">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="ff820-657">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="ff820-658">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="ff820-658">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="ff820-659">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="ff820-659">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="ff820-660">ViExit</span><span class="sxs-lookup"><span data-stu-id="ff820-660">ViExit</span></span>

<span data-ttu-id="ff820-661">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="ff820-661">Exits the shell.</span></span>

- <span data-ttu-id="ff820-662">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-662">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="ff820-663">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="ff820-663">ViInsertMode</span></span>

<span data-ttu-id="ff820-664">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="ff820-664">Switch to Insert mode.</span></span>

- <span data-ttu-id="ff820-665">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="ff820-665">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="ff820-666">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="ff820-666">WhatIsKey</span></span>

<span data-ttu-id="ff820-667">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="ff820-667">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="ff820-668">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ff820-668">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="ff820-669">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="ff820-669">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="ff820-670">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-670">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="ff820-671">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="ff820-671">ExchangePointAndMark</span></span>

<span data-ttu-id="ff820-672">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-672">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="ff820-673">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="ff820-673">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="ff820-674">SelectAll</span><span class="sxs-lookup"><span data-stu-id="ff820-674">SelectAll</span></span>

<span data-ttu-id="ff820-675">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-675">Select the entire line.</span></span>

- <span data-ttu-id="ff820-676">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="ff820-676">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="ff820-677">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="ff820-677">SelectBackwardChar</span></span>

<span data-ttu-id="ff820-678">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="ff820-678">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="ff820-679">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-679">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="ff820-680">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-680">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="ff820-681">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="ff820-681">SelectBackwardsLine</span></span>

<span data-ttu-id="ff820-682">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-682">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="ff820-683">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-683">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="ff820-684">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="ff820-684">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="ff820-685">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-685">SelectBackwardWord</span></span>

<span data-ttu-id="ff820-686">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-686">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="ff820-687">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-687">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="ff820-688">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="ff820-688">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="ff820-689">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="ff820-689">SelectForwardChar</span></span>

<span data-ttu-id="ff820-690">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="ff820-690">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="ff820-691">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-691">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="ff820-692">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-692">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="ff820-693">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-693">SelectForwardWord</span></span>

<span data-ttu-id="ff820-694">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ff820-694">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="ff820-695">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="ff820-695">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="ff820-696">SelectLine</span><span class="sxs-lookup"><span data-stu-id="ff820-696">SelectLine</span></span>

<span data-ttu-id="ff820-697">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-697">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="ff820-698">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-698">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="ff820-699">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="ff820-699">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="ff820-700">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-700">SelectNextWord</span></span>

<span data-ttu-id="ff820-701">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-701">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="ff820-702">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="ff820-702">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="ff820-703">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-703">SelectShellBackwardWord</span></span>

<span data-ttu-id="ff820-704">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="ff820-704">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="ff820-705">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-705">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="ff820-706">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="ff820-706">SelectShellForwardWord</span></span>

<span data-ttu-id="ff820-707">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="ff820-707">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="ff820-708">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-708">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="ff820-709">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="ff820-709">SelectShellNextWord</span></span>

<span data-ttu-id="ff820-710">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="ff820-710">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="ff820-711">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="ff820-711">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="ff820-712">SetMark</span><span class="sxs-lookup"><span data-stu-id="ff820-712">SetMark</span></span>

<span data-ttu-id="ff820-713">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="ff820-713">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="ff820-714">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="ff820-714">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="ff820-715">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="ff820-715">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="ff820-716">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="ff820-716">CharacterSearch</span></span>

<span data-ttu-id="ff820-717">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="ff820-717">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="ff820-718">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="ff820-718">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ff820-719">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-719">Cmd: `<F3>`</span></span>
- <span data-ttu-id="ff820-720">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="ff820-720">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="ff820-721">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-721">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="ff820-722">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-722">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="ff820-723">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-723">CharacterSearchBackward</span></span>

<span data-ttu-id="ff820-724">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="ff820-724">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="ff820-725">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="ff820-725">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="ff820-726">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-726">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="ff820-727">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="ff820-727">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="ff820-728">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-728">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="ff820-729">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="ff820-729">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="ff820-730">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="ff820-730">RepeatLastCharSearch</span></span>

<span data-ttu-id="ff820-731">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="ff820-731">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="ff820-732">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="ff820-732">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="ff820-733">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="ff820-733">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="ff820-734">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="ff820-734">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="ff820-735">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="ff820-735">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="ff820-736">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="ff820-736">RepeatSearch</span></span>

<span data-ttu-id="ff820-737">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="ff820-737">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ff820-738">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="ff820-738">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="ff820-739">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-739">RepeatSearchBackward</span></span>

<span data-ttu-id="ff820-740">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="ff820-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="ff820-741">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="ff820-741">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="ff820-742">SearchChar</span><span class="sxs-lookup"><span data-stu-id="ff820-742">SearchChar</span></span>

<span data-ttu-id="ff820-743">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-743">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ff820-744">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="ff820-744">This is for 't' functionality.</span></span>

- <span data-ttu-id="ff820-745">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="ff820-745">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="ff820-746">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="ff820-746">SearchCharBackward</span></span>

<span data-ttu-id="ff820-747">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="ff820-747">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ff820-748">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="ff820-748">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ff820-749">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="ff820-749">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="ff820-750">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ff820-750">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="ff820-751">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="ff820-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="ff820-752">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="ff820-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="ff820-753">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="ff820-753">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="ff820-754">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="ff820-754">SearchCharWithBackoff</span></span>

<span data-ttu-id="ff820-755">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="ff820-755">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="ff820-756">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="ff820-756">This is for 't' functionality.</span></span>

- <span data-ttu-id="ff820-757">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="ff820-757">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="ff820-758">SearchForward</span><span class="sxs-lookup"><span data-stu-id="ff820-758">SearchForward</span></span>

<span data-ttu-id="ff820-759">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="ff820-759">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="ff820-760">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ff820-760">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="ff820-761">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="ff820-761">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="ff820-762">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="ff820-762">Custom Key Bindings</span></span>

<span data-ttu-id="ff820-763">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="ff820-763">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="ff820-764">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="ff820-764">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="ff820-765">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="ff820-765">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="ff820-766">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="ff820-766">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="ff820-767">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="ff820-767">Some useful examples include</span></span>

- <span data-ttu-id="ff820-768">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="ff820-768">edit the command line</span></span>
- <span data-ttu-id="ff820-769">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="ff820-769">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="ff820-770">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="ff820-770">change directories without changing the command line</span></span>

<span data-ttu-id="ff820-771">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="ff820-771">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="ff820-772">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="ff820-772">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="ff820-773">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="ff820-773">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="ff820-774">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="ff820-774">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="ff820-775">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="ff820-775">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="ff820-776">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ff820-776">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="ff820-777">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="ff820-777">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="ff820-778">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="ff820-778">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="ff820-779">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="ff820-779">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="ff820-780">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="ff820-780">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="ff820-781">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-781">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="ff820-782">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="ff820-782">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="ff820-783">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="ff820-783">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="ff820-784">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="ff820-784">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="ff820-785">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="ff820-785">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="ff820-786">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="ff820-786">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="ff820-787">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-787">Clear the kill-ring.</span></span>  <span data-ttu-id="ff820-788">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="ff820-788">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="ff820-789">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="ff820-789">Delete length characters from start.</span></span>  <span data-ttu-id="ff820-790">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="ff820-790">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="ff820-791">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="ff820-791">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="ff820-792">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="ff820-792">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="ff820-793">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="ff820-793">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="ff820-794">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="ff820-794">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="ff820-795">Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="ff820-795">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="ff820-796">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="ff820-796">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="ff820-797">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="ff820-797">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="ff820-798">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="ff820-798">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="ff820-799">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="ff820-799">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="ff820-800">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="ff820-800">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="ff820-801">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="ff820-801">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="ff820-802">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="ff820-802">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="ff820-803">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="ff820-803">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="ff820-804">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="ff820-804">Replace some of the input.</span></span> <span data-ttu-id="ff820-805">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="ff820-805">This operation supports undo/redo.</span></span> <span data-ttu-id="ff820-806">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="ff820-806">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="ff820-807">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="ff820-807">Move the cursor to the given offset.</span></span> <span data-ttu-id="ff820-808">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="ff820-808">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="ff820-809">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="ff820-809">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="ff820-810">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="ff820-810">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="ff820-811">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="ff820-811">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="ff820-812">NOTE</span><span class="sxs-lookup"><span data-stu-id="ff820-812">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="ff820-813">POWERSHELL-KOMPATIBILITET</span><span class="sxs-lookup"><span data-stu-id="ff820-813">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="ff820-814">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="ff820-814">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="ff820-815">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="ff820-815">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="ff820-816">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="ff820-816">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="ff820-817">KOMMANDO HISTORIK</span><span class="sxs-lookup"><span data-stu-id="ff820-817">COMMAND HISTORY</span></span>

<span data-ttu-id="ff820-818">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="ff820-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="ff820-819">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="ff820-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="ff820-820">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="ff820-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="ff820-821">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="ff820-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="ff820-822">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="ff820-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="ff820-823">FEEDBACK & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="ff820-823">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="ff820-824">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="ff820-824">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="ff820-825">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="ff820-825">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="ff820-826">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="ff820-826">SEE ALSO</span></span>

<span data-ttu-id="ff820-827">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="ff820-827">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
