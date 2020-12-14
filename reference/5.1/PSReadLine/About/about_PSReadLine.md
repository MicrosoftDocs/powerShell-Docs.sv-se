---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-5.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 25fc3a9a814728057b1ebc7e721d3fba84ae72c2
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692317"
---
# <a name="psreadline"></a><span data-ttu-id="046e3-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="046e3-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="046e3-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="046e3-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="046e3-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="046e3-106">Short Description</span></span>

<span data-ttu-id="046e3-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="046e3-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="046e3-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="046e3-108">Long Description</span></span>

<span data-ttu-id="046e3-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="046e3-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="046e3-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="046e3-110">It provides:</span></span>

- <span data-ttu-id="046e3-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="046e3-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="046e3-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="046e3-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="046e3-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="046e3-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="046e3-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="046e3-114">Customizable key bindings</span></span>
- <span data-ttu-id="046e3-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="046e3-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="046e3-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="046e3-116">Many configuration options</span></span>
- <span data-ttu-id="046e3-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="046e3-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="046e3-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="046e3-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="046e3-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="046e3-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="046e3-120">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="046e3-120">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="046e3-121">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="046e3-121">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="046e3-122">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="046e3-122">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="046e3-123">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="046e3-123">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="046e3-124">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-124">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="046e3-125">Avbryta</span><span class="sxs-lookup"><span data-stu-id="046e3-125">Abort</span></span>

<span data-ttu-id="046e3-126">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="046e3-126">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="046e3-127">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="046e3-127">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="046e3-128">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="046e3-128">AcceptAndGetNext</span></span>

<span data-ttu-id="046e3-129">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-129">Attempt to execute the current input.</span></span> <span data-ttu-id="046e3-130">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="046e3-130">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="046e3-131">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="046e3-131">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="046e3-132">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="046e3-132">AcceptLine</span></span>

<span data-ttu-id="046e3-133">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-133">Attempt to execute the current input.</span></span> <span data-ttu-id="046e3-134">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-134">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="046e3-135">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-135">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="046e3-136">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-136">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="046e3-137">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-137">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="046e3-138">AddLine</span><span class="sxs-lookup"><span data-stu-id="046e3-138">AddLine</span></span>

<span data-ttu-id="046e3-139">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-139">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="046e3-140">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="046e3-140">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="046e3-141">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-141">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="046e3-142">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-142">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="046e3-143">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-143">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="046e3-144">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-144">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="046e3-145">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="046e3-145">BackwardDeleteChar</span></span>

<span data-ttu-id="046e3-146">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-146">Delete the character before the cursor.</span></span>

- <span data-ttu-id="046e3-147">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="046e3-147">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="046e3-148">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="046e3-148">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="046e3-149">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-149">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="046e3-150">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="046e3-150">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="046e3-151">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="046e3-151">BackwardDeleteLine</span></span>

<span data-ttu-id="046e3-152">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-152">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="046e3-153">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-153">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="046e3-154">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-154">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="046e3-155">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="046e3-155">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="046e3-156">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="046e3-156">BackwardDeleteWord</span></span>

<span data-ttu-id="046e3-157">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-157">Deletes the previous word.</span></span>

- <span data-ttu-id="046e3-158">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="046e3-158">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="046e3-159">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="046e3-159">BackwardKillLine</span></span>

<span data-ttu-id="046e3-160">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-160">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="046e3-161">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-161">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="046e3-162">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-162">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="046e3-163">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="046e3-163">BackwardKillWord</span></span>

<span data-ttu-id="046e3-164">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-164">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="046e3-165">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-165">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="046e3-166">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-166">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="046e3-167">Kommandot `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-167">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="046e3-168">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-168">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="046e3-169">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-169">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="046e3-170">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="046e3-170">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="046e3-171">CancelLine</span><span class="sxs-lookup"><span data-stu-id="046e3-171">CancelLine</span></span>

<span data-ttu-id="046e3-172">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="046e3-172">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="046e3-173">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="046e3-173">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="046e3-174">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="046e3-174">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="046e3-175">Kopiera</span><span class="sxs-lookup"><span data-stu-id="046e3-175">Copy</span></span>

<span data-ttu-id="046e3-176">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="046e3-176">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="046e3-177">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-177">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="046e3-178">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="046e3-178">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="046e3-179">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="046e3-179">CopyOrCancelLine</span></span>

<span data-ttu-id="046e3-180">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-180">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="046e3-181">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="046e3-181">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="046e3-182">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="046e3-182">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="046e3-183">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="046e3-183">Cut</span></span>

<span data-ttu-id="046e3-184">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="046e3-184">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="046e3-185">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="046e3-185">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="046e3-186">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="046e3-186">DeleteChar</span></span>

<span data-ttu-id="046e3-187">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-187">Delete the character under the cursor.</span></span>

- <span data-ttu-id="046e3-188">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-188">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="046e3-189">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-189">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="046e3-190">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-190">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="046e3-191">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-191">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="046e3-192">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="046e3-192">DeleteCharOrExit</span></span>

<span data-ttu-id="046e3-193">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="046e3-193">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="046e3-194">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="046e3-194">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="046e3-195">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="046e3-195">DeleteEndOfWord</span></span>

<span data-ttu-id="046e3-196">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="046e3-196">Delete to the end of the word.</span></span>

- <span data-ttu-id="046e3-197">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="046e3-197">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="046e3-198">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="046e3-198">DeleteLine</span></span>

<span data-ttu-id="046e3-199">Tar bort den aktuella raden och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="046e3-199">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="046e3-200">Kommando läge för vi: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="046e3-200">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="046e3-201">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="046e3-201">DeleteLineToFirstChar</span></span>

<span data-ttu-id="046e3-202">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-202">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="046e3-203">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="046e3-203">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="046e3-204">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="046e3-204">DeleteToEnd</span></span>

<span data-ttu-id="046e3-205">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-205">Delete to the end of the line.</span></span>

- <span data-ttu-id="046e3-206">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="046e3-206">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="046e3-207">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="046e3-207">DeleteWord</span></span>

<span data-ttu-id="046e3-208">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-208">Delete the next word.</span></span>

- <span data-ttu-id="046e3-209">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="046e3-209">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="046e3-210">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="046e3-210">ForwardDeleteLine</span></span>

<span data-ttu-id="046e3-211">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-211">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="046e3-212">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-212">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="046e3-213">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-213">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="046e3-214">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-214">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="046e3-215">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="046e3-215">InsertLineAbove</span></span>

<span data-ttu-id="046e3-216">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-216">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="046e3-217">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-217">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="046e3-218">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-218">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="046e3-219">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="046e3-219">InsertLineBelow</span></span>

<span data-ttu-id="046e3-220">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-220">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="046e3-221">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-221">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="046e3-222">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-222">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="046e3-223">InvertCase</span><span class="sxs-lookup"><span data-stu-id="046e3-223">InvertCase</span></span>

<span data-ttu-id="046e3-224">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="046e3-224">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="046e3-225">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="046e3-225">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="046e3-226">KillLine</span><span class="sxs-lookup"><span data-stu-id="046e3-226">KillLine</span></span>

<span data-ttu-id="046e3-227">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-227">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="046e3-228">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-228">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="046e3-229">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="046e3-229">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="046e3-230">KillRegion</span><span class="sxs-lookup"><span data-stu-id="046e3-230">KillRegion</span></span>

<span data-ttu-id="046e3-231">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-231">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="046e3-232">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-232">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="046e3-233">KillWord</span><span class="sxs-lookup"><span data-stu-id="046e3-233">KillWord</span></span>

<span data-ttu-id="046e3-234">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="046e3-234">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="046e3-235">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-235">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="046e3-236">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-236">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="046e3-237">Kommandot `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-237">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="046e3-238">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="046e3-238">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="046e3-239">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-239">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="046e3-240">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="046e3-240">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="046e3-241">Klistra in</span><span class="sxs-lookup"><span data-stu-id="046e3-241">Paste</span></span>

<span data-ttu-id="046e3-242">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="046e3-242">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="046e3-243">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="046e3-243">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="046e3-244">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="046e3-244">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="046e3-245">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="046e3-245">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="046e3-246">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="046e3-246">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="046e3-247">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="046e3-247">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="046e3-248">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="046e3-248">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="046e3-249">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="046e3-249">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="046e3-250">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="046e3-250">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="046e3-251">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="046e3-251">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="046e3-252">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="046e3-252">PasteAfter</span></span>

<span data-ttu-id="046e3-253">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="046e3-253">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="046e3-254">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="046e3-254">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="046e3-255">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="046e3-255">PasteBefore</span></span>

<span data-ttu-id="046e3-256">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="046e3-256">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="046e3-257">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="046e3-257">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="046e3-258">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="046e3-258">PrependAndAccept</span></span>

<span data-ttu-id="046e3-259">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-259">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="046e3-260">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="046e3-260">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="046e3-261">Gör om</span><span class="sxs-lookup"><span data-stu-id="046e3-261">Redo</span></span>

<span data-ttu-id="046e3-262">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="046e3-262">Undo an undo.</span></span>

- <span data-ttu-id="046e3-263">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-263">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="046e3-264">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-264">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="046e3-265">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-265">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="046e3-266">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="046e3-266">RepeatLastCommand</span></span>

<span data-ttu-id="046e3-267">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-267">Repeat the last text modification.</span></span>

- <span data-ttu-id="046e3-268">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="046e3-268">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="046e3-269">RevertLine</span><span class="sxs-lookup"><span data-stu-id="046e3-269">RevertLine</span></span>

<span data-ttu-id="046e3-270">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="046e3-270">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="046e3-271">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="046e3-271">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="046e3-272">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="046e3-272">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="046e3-273">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="046e3-273">ShellBackwardKillWord</span></span>

<span data-ttu-id="046e3-274">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-274">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="046e3-275">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-275">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="046e3-276">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-276">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="046e3-277">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-277">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="046e3-278">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="046e3-278">ShellKillWord</span></span>

<span data-ttu-id="046e3-279">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="046e3-279">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="046e3-280">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-280">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="046e3-281">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-281">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="046e3-282">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-282">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="046e3-283">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="046e3-283">SwapCharacters</span></span>

<span data-ttu-id="046e3-284">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="046e3-284">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="046e3-285">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-285">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="046e3-286">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-286">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="046e3-287">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-287">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="046e3-288">Ångra</span><span class="sxs-lookup"><span data-stu-id="046e3-288">Undo</span></span>

<span data-ttu-id="046e3-289">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="046e3-289">Undo a previous edit.</span></span>

- <span data-ttu-id="046e3-290">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="046e3-290">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="046e3-291">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="046e3-291">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="046e3-292">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="046e3-292">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="046e3-293">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="046e3-293">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="046e3-294">UndoAll</span><span class="sxs-lookup"><span data-stu-id="046e3-294">UndoAll</span></span>

<span data-ttu-id="046e3-295">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-295">Undo all previous edits for line.</span></span>

- <span data-ttu-id="046e3-296">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="046e3-296">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="046e3-297">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="046e3-297">UnixWordRubout</span></span>

<span data-ttu-id="046e3-298">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-298">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="046e3-299">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-299">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="046e3-300">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-300">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="046e3-301">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="046e3-301">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="046e3-302">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="046e3-302">ValidateAndAcceptLine</span></span>

<span data-ttu-id="046e3-303">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-303">Attempt to execute the current input.</span></span> <span data-ttu-id="046e3-304">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-304">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="046e3-305">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="046e3-305">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="046e3-306">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="046e3-306">ViAcceptLine</span></span>

<span data-ttu-id="046e3-307">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="046e3-307">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="046e3-308">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="046e3-308">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="046e3-309">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="046e3-309">ViAcceptLineOrExit</span></span>

<span data-ttu-id="046e3-310">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="046e3-310">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="046e3-311">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="046e3-311">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="046e3-312">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="046e3-312">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="046e3-313">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="046e3-313">ViAppendLine</span></span>

<span data-ttu-id="046e3-314">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-314">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="046e3-315">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="046e3-315">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="046e3-316">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-316">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="046e3-317">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="046e3-317">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="046e3-318">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="046e3-318">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="046e3-319">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-319">ViBackwardGlob</span></span>

<span data-ttu-id="046e3-320">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="046e3-320">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="046e3-321">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="046e3-321">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="046e3-322">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="046e3-322">ViDeleteBrace</span></span>

<span data-ttu-id="046e3-323">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="046e3-323">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="046e3-324">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="046e3-324">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="046e3-325">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-325">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="046e3-326">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="046e3-326">Delete to the end of the word.</span></span>

- <span data-ttu-id="046e3-327">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="046e3-327">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="046e3-328">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-328">ViDeleteGlob</span></span>

<span data-ttu-id="046e3-329">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="046e3-329">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="046e3-330">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="046e3-330">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="046e3-331">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="046e3-331">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="046e3-332">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="046e3-332">Deletes until given character.</span></span>

- <span data-ttu-id="046e3-333">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-333">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="046e3-334">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-334">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="046e3-335">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="046e3-335">Deletes until given character.</span></span>

- <span data-ttu-id="046e3-336">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="046e3-336">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="046e3-337">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="046e3-337">ViDeleteToChar</span></span>

<span data-ttu-id="046e3-338">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="046e3-338">Deletes until given character.</span></span>

- <span data-ttu-id="046e3-339">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="046e3-339">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="046e3-340">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-340">ViDeleteToCharBackward</span></span>

<span data-ttu-id="046e3-341">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="046e3-341">Deletes backwards until given character.</span></span>

- <span data-ttu-id="046e3-342">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="046e3-342">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="046e3-343">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="046e3-343">ViInsertAtBegining</span></span>

<span data-ttu-id="046e3-344">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-344">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="046e3-345">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="046e3-345">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="046e3-346">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="046e3-346">ViInsertAtEnd</span></span>

<span data-ttu-id="046e3-347">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-347">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="046e3-348">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="046e3-348">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="046e3-349">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="046e3-349">ViInsertLine</span></span>

<span data-ttu-id="046e3-350">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-350">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="046e3-351">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="046e3-351">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="046e3-352">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="046e3-352">ViInsertWithAppend</span></span>

<span data-ttu-id="046e3-353">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="046e3-353">Append from the current line position.</span></span>

- <span data-ttu-id="046e3-354">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="046e3-354">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="046e3-355">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="046e3-355">ViInsertWithDelete</span></span>

<span data-ttu-id="046e3-356">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="046e3-356">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="046e3-357">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="046e3-357">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="046e3-358">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="046e3-358">ViJoinLines</span></span>

<span data-ttu-id="046e3-359">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-359">Joins the current line and the next line.</span></span>

- <span data-ttu-id="046e3-360">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="046e3-360">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="046e3-361">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="046e3-361">ViReplaceLine</span></span>

<span data-ttu-id="046e3-362">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-362">Erase the entire command line.</span></span>

- <span data-ttu-id="046e3-363">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="046e3-363">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="046e3-364">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="046e3-364">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="046e3-365">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="046e3-365">Replaces until given character.</span></span>

- <span data-ttu-id="046e3-366">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-366">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="046e3-367">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-367">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="046e3-368">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="046e3-368">Replaces until given character.</span></span>

- <span data-ttu-id="046e3-369">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="046e3-369">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="046e3-370">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="046e3-370">ViReplaceToChar</span></span>

<span data-ttu-id="046e3-371">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="046e3-371">Deletes until given character.</span></span>

- <span data-ttu-id="046e3-372">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="046e3-372">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="046e3-373">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-373">ViReplaceToCharBackward</span></span>

<span data-ttu-id="046e3-374">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="046e3-374">Replaces until given character.</span></span>

- <span data-ttu-id="046e3-375">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="046e3-375">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="046e3-376">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-376">ViYankBeginningOfLine</span></span>

<span data-ttu-id="046e3-377">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-377">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="046e3-378">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="046e3-378">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="046e3-379">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-379">ViYankEndOfGlob</span></span>

<span data-ttu-id="046e3-380">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="046e3-380">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="046e3-381">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="046e3-381">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="046e3-382">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="046e3-382">ViYankEndOfWord</span></span>

<span data-ttu-id="046e3-383">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="046e3-383">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="046e3-384">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="046e3-384">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="046e3-385">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="046e3-385">ViYankLeft</span></span>

<span data-ttu-id="046e3-386">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-386">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="046e3-387">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="046e3-387">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="046e3-388">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="046e3-388">ViYankLine</span></span>

<span data-ttu-id="046e3-389">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="046e3-389">Yank the entire buffer.</span></span>

- <span data-ttu-id="046e3-390">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-390">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="046e3-391">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-391">ViYankNextGlob</span></span>

<span data-ttu-id="046e3-392">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-392">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="046e3-393">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="046e3-393">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="046e3-394">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-394">ViYankNextWord</span></span>

<span data-ttu-id="046e3-395">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-395">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="046e3-396">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="046e3-396">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="046e3-397">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="046e3-397">ViYankPercent</span></span>

<span data-ttu-id="046e3-398">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="046e3-398">Yank to/from matching brace.</span></span>

- <span data-ttu-id="046e3-399">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="046e3-399">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="046e3-400">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-400">ViYankPreviousGlob</span></span>

<span data-ttu-id="046e3-401">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-401">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="046e3-402">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="046e3-402">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="046e3-403">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="046e3-403">ViYankPreviousWord</span></span>

<span data-ttu-id="046e3-404">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-404">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="046e3-405">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="046e3-405">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="046e3-406">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="046e3-406">ViYankRight</span></span>

<span data-ttu-id="046e3-407">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-407">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="046e3-408">Kommando läge för vi: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-408">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="046e3-409">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-409">ViYankToEndOfLine</span></span>

<span data-ttu-id="046e3-410">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="046e3-410">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="046e3-411">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="046e3-411">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="046e3-412">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="046e3-412">ViYankToFirstChar</span></span>

<span data-ttu-id="046e3-413">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-413">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="046e3-414">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="046e3-414">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="046e3-415">Yank</span><span class="sxs-lookup"><span data-stu-id="046e3-415">Yank</span></span>

<span data-ttu-id="046e3-416">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-416">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="046e3-417">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-417">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="046e3-418">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="046e3-418">YankLastArg</span></span>

<span data-ttu-id="046e3-419">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-419">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="046e3-420">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="046e3-420">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="046e3-421">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="046e3-421">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="046e3-422">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="046e3-422">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="046e3-423">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="046e3-423">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="046e3-424">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="046e3-424">YankNthArg</span></span>

<span data-ttu-id="046e3-425">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-425">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="046e3-426">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="046e3-426">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="046e3-427">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-427">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="046e3-428">YankPop</span><span class="sxs-lookup"><span data-stu-id="046e3-428">YankPop</span></span>

<span data-ttu-id="046e3-429">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-429">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="046e3-430">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="046e3-430">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="046e3-431">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-431">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="046e3-432">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="046e3-432">BackwardChar</span></span>

<span data-ttu-id="046e3-433">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="046e3-433">Move the cursor one character to the left.</span></span> <span data-ttu-id="046e3-434">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="046e3-434">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="046e3-435">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-435">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="046e3-436">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="046e3-436">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="046e3-437">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-437">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="046e3-438">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="046e3-438">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="046e3-439">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-439">BackwardWord</span></span>

<span data-ttu-id="046e3-440">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-440">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="046e3-441">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-441">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-442">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-442">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="046e3-443">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="046e3-443">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="046e3-444">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-444">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="046e3-445">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-445">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="046e3-446">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-446">BeginningOfLine</span></span>

<span data-ttu-id="046e3-447">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-447">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="046e3-448">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="046e3-448">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="046e3-449">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-449">Cmd: `<Home>`</span></span>
- <span data-ttu-id="046e3-450">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="046e3-450">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="046e3-451">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-451">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="046e3-452">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-452">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="046e3-453">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-453">EndOfLine</span></span>

<span data-ttu-id="046e3-454">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-454">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="046e3-455">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-455">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="046e3-456">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-456">Cmd: `<End>`</span></span>
- <span data-ttu-id="046e3-457">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="046e3-457">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="046e3-458">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-458">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="046e3-459">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="046e3-459">ForwardChar</span></span>

<span data-ttu-id="046e3-460">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="046e3-460">Move the cursor one character to the right.</span></span> <span data-ttu-id="046e3-461">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="046e3-461">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="046e3-462">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-462">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="046e3-463">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="046e3-463">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="046e3-464">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-464">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="046e3-465">Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="046e3-465">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="046e3-466">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-466">ForwardWord</span></span>

<span data-ttu-id="046e3-467">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-467">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="046e3-468">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-468">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-469">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="046e3-469">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="046e3-470">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="046e3-470">GotoBrace</span></span>

<span data-ttu-id="046e3-471">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="046e3-471">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="046e3-472">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="046e3-472">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="046e3-473">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="046e3-473">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="046e3-474">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="046e3-474">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="046e3-475">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="046e3-475">GotoColumn</span></span>

<span data-ttu-id="046e3-476">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="046e3-476">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="046e3-477">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="046e3-477">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="046e3-478">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-478">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="046e3-479">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-479">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="046e3-480">Kommando läge för vi: `<^>`</span><span class="sxs-lookup"><span data-stu-id="046e3-480">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="046e3-481">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="046e3-481">MoveToEndOfLine</span></span>

<span data-ttu-id="046e3-482">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="046e3-482">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="046e3-483">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="046e3-483">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="046e3-484">NextLine</span><span class="sxs-lookup"><span data-stu-id="046e3-484">NextLine</span></span>

<span data-ttu-id="046e3-485">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-485">Move the cursor to the next line.</span></span>

- <span data-ttu-id="046e3-486">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-486">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="046e3-487">NextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-487">NextWord</span></span>

<span data-ttu-id="046e3-488">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-488">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="046e3-489">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-489">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-490">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-490">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="046e3-491">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-491">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="046e3-492">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-492">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="046e3-493">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="046e3-493">NextWordEnd</span></span>

<span data-ttu-id="046e3-494">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-494">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="046e3-495">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-495">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-496">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="046e3-496">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="046e3-497">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="046e3-497">PreviousLine</span></span>

<span data-ttu-id="046e3-498">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-498">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="046e3-499">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-499">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="046e3-500">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-500">ShellBackwardWord</span></span>

<span data-ttu-id="046e3-501">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-501">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="046e3-502">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="046e3-502">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="046e3-503">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-503">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="046e3-504">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-504">ShellForwardWord</span></span>

<span data-ttu-id="046e3-505">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-505">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="046e3-506">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="046e3-506">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="046e3-507">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-507">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="046e3-508">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-508">ShellNextWord</span></span>

<span data-ttu-id="046e3-509">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-509">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="046e3-510">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="046e3-510">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="046e3-511">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-511">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="046e3-512">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-512">ViBackwardWord</span></span>

<span data-ttu-id="046e3-513">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-513">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="046e3-514">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-514">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-515">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="046e3-515">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="046e3-516">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-516">ViEndOfGlob</span></span>

<span data-ttu-id="046e3-517">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="046e3-517">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="046e3-518">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="046e3-518">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="046e3-519">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-519">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="046e3-520">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="046e3-520">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="046e3-521">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-521">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="046e3-522">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="046e3-522">ViGotoBrace</span></span>

<span data-ttu-id="046e3-523">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="046e3-523">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="046e3-524">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="046e3-524">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="046e3-525">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="046e3-525">ViNextGlob</span></span>

<span data-ttu-id="046e3-526">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="046e3-526">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="046e3-527">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="046e3-527">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="046e3-528">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-528">ViNextWord</span></span>

<span data-ttu-id="046e3-529">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-529">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="046e3-530">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-530">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="046e3-531">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="046e3-531">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="046e3-532">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-532">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="046e3-533">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-533">BeginningOfHistory</span></span>

<span data-ttu-id="046e3-534">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-534">Move to the first item in the history.</span></span>

- <span data-ttu-id="046e3-535">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="046e3-535">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="046e3-536">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-536">ClearHistory</span></span>

<span data-ttu-id="046e3-537">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="046e3-537">Clears history in PSReadLine.</span></span> <span data-ttu-id="046e3-538">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-538">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="046e3-539">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="046e3-539">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="046e3-540">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-540">EndOfHistory</span></span>

<span data-ttu-id="046e3-541">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-541">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="046e3-542">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="046e3-542">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="046e3-543">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-543">ForwardSearchHistory</span></span>

<span data-ttu-id="046e3-544">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-544">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="046e3-545">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="046e3-545">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="046e3-546">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="046e3-546">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="046e3-547">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-547">HistorySearchBackward</span></span>

<span data-ttu-id="046e3-548">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-548">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="046e3-549">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="046e3-549">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="046e3-550">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="046e3-550">HistorySearchForward</span></span>

<span data-ttu-id="046e3-551">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-551">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="046e3-552">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="046e3-552">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="046e3-553">NextHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-553">NextHistory</span></span>

<span data-ttu-id="046e3-554">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-554">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="046e3-555">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-555">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="046e3-556">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="046e3-556">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="046e3-557">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-557">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="046e3-558">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="046e3-558">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="046e3-559">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-559">PreviousHistory</span></span>

<span data-ttu-id="046e3-560">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="046e3-560">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="046e3-561">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-561">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="046e3-562">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="046e3-562">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="046e3-563">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-563">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="046e3-564">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="046e3-564">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="046e3-565">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="046e3-565">ReverseSearchHistory</span></span>

<span data-ttu-id="046e3-566">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="046e3-566">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="046e3-567">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="046e3-567">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="046e3-568">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="046e3-568">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="046e3-569">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-569">ViSearchHistoryBackward</span></span>

<span data-ttu-id="046e3-570">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="046e3-570">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="046e3-571">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="046e3-571">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="046e3-572">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="046e3-572">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="046e3-573">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="046e3-573">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="046e3-574">Klart</span><span class="sxs-lookup"><span data-stu-id="046e3-574">Complete</span></span>

<span data-ttu-id="046e3-575">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-575">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="046e3-576">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="046e3-576">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="046e3-577">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="046e3-577">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="046e3-578">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-578">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="046e3-579">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="046e3-579">MenuComplete</span></span>

<span data-ttu-id="046e3-580">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-580">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="046e3-581">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="046e3-581">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="046e3-582">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="046e3-582">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="046e3-583">Kommandot `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-583">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="046e3-584">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-584">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="046e3-585">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="046e3-585">PossibleCompletions</span></span>

<span data-ttu-id="046e3-586">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="046e3-586">Display the list of possible completions.</span></span>

- <span data-ttu-id="046e3-587">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="046e3-587">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="046e3-588">Vi infognings läge: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-588">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="046e3-589">Kommando läge för vi: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="046e3-589">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="046e3-590">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="046e3-590">TabCompleteNext</span></span>

<span data-ttu-id="046e3-591">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="046e3-591">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="046e3-592">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-592">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="046e3-593">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-593">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="046e3-594">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="046e3-594">TabCompletePrevious</span></span>

<span data-ttu-id="046e3-595">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="046e3-595">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="046e3-596">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-596">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="046e3-597">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-597">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="046e3-598">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="046e3-598">ViTabCompleteNext</span></span>

<span data-ttu-id="046e3-599">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="046e3-599">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="046e3-600">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-600">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="046e3-601">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="046e3-601">ViTabCompletePrevious</span></span>

<span data-ttu-id="046e3-602">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="046e3-602">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="046e3-603">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="046e3-603">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="046e3-604">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-604">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="046e3-605">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="046e3-605">CaptureScreen</span></span>

<span data-ttu-id="046e3-606">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="046e3-606">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="046e3-607">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-607">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="046e3-608">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="046e3-608">ClearScreen</span></span>

<span data-ttu-id="046e3-609">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="046e3-609">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="046e3-610">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="046e3-610">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="046e3-611">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="046e3-611">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="046e3-612">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="046e3-612">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="046e3-613">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="046e3-613">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="046e3-614">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="046e3-614">DigitArgument</span></span>

<span data-ttu-id="046e3-615">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="046e3-615">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="046e3-616">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="046e3-616">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="046e3-617">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="046e3-617">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="046e3-618">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="046e3-618">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="046e3-619">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="046e3-619">InvokePrompt</span></span>

<span data-ttu-id="046e3-620">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="046e3-620">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="046e3-621">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="046e3-621">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="046e3-622">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-622">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="046e3-623">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="046e3-623">ScrollDisplayDown</span></span>

<span data-ttu-id="046e3-624">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="046e3-624">Scroll the display down one screen.</span></span>

- <span data-ttu-id="046e3-625">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="046e3-625">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="046e3-626">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="046e3-626">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="046e3-627">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="046e3-627">ScrollDisplayDownLine</span></span>

<span data-ttu-id="046e3-628">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="046e3-628">Scroll the display down one line.</span></span>

- <span data-ttu-id="046e3-629">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="046e3-629">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="046e3-630">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="046e3-630">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="046e3-631">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="046e3-631">ScrollDisplayToCursor</span></span>

<span data-ttu-id="046e3-632">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-632">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="046e3-633">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-633">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="046e3-634">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="046e3-634">ScrollDisplayTop</span></span>

<span data-ttu-id="046e3-635">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="046e3-635">Scroll the display to the top.</span></span>

- <span data-ttu-id="046e3-636">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-636">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="046e3-637">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="046e3-637">ScrollDisplayUp</span></span>

<span data-ttu-id="046e3-638">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="046e3-638">Scroll the display up one screen.</span></span>

- <span data-ttu-id="046e3-639">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="046e3-639">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="046e3-640">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="046e3-640">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="046e3-641">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="046e3-641">ScrollDisplayUpLine</span></span>

<span data-ttu-id="046e3-642">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="046e3-642">Scroll the display up one line.</span></span>

- <span data-ttu-id="046e3-643">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="046e3-643">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="046e3-644">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="046e3-644">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="046e3-645">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="046e3-645">SelfInsert</span></span>

<span data-ttu-id="046e3-646">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="046e3-646">Insert the key.</span></span>

- <span data-ttu-id="046e3-647">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-647">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="046e3-648">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="046e3-648">ShowKeyBindings</span></span>

<span data-ttu-id="046e3-649">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="046e3-649">Show all bound keys.</span></span>

- <span data-ttu-id="046e3-650">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="046e3-650">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="046e3-651">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="046e3-651">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="046e3-652">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="046e3-652">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="046e3-653">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="046e3-653">ViCommandMode</span></span>

<span data-ttu-id="046e3-654">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="046e3-654">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="046e3-655">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="046e3-655">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="046e3-656">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="046e3-656">ViDigitArgumentInChord</span></span>

<span data-ttu-id="046e3-657">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="046e3-657">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="046e3-658">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-658">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="046e3-659">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="046e3-659">ViEditVisually</span></span>

<span data-ttu-id="046e3-660">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="046e3-660">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="046e3-661">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="046e3-661">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="046e3-662">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="046e3-662">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="046e3-663">ViExit</span><span class="sxs-lookup"><span data-stu-id="046e3-663">ViExit</span></span>

<span data-ttu-id="046e3-664">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="046e3-664">Exits the shell.</span></span>

- <span data-ttu-id="046e3-665">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-665">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="046e3-666">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="046e3-666">ViInsertMode</span></span>

<span data-ttu-id="046e3-667">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="046e3-667">Switch to Insert mode.</span></span>

- <span data-ttu-id="046e3-668">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="046e3-668">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="046e3-669">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="046e3-669">WhatIsKey</span></span>

<span data-ttu-id="046e3-670">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="046e3-670">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="046e3-671">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="046e3-671">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="046e3-672">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="046e3-672">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="046e3-673">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-673">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="046e3-674">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="046e3-674">ExchangePointAndMark</span></span>

<span data-ttu-id="046e3-675">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-675">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="046e3-676">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="046e3-676">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="046e3-677">SelectAll</span><span class="sxs-lookup"><span data-stu-id="046e3-677">SelectAll</span></span>

<span data-ttu-id="046e3-678">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-678">Select the entire line.</span></span>

- <span data-ttu-id="046e3-679">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="046e3-679">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="046e3-680">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="046e3-680">SelectBackwardChar</span></span>

<span data-ttu-id="046e3-681">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="046e3-681">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="046e3-682">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-682">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="046e3-683">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-683">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="046e3-684">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="046e3-684">SelectBackwardsLine</span></span>

<span data-ttu-id="046e3-685">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-685">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="046e3-686">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-686">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="046e3-687">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="046e3-687">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="046e3-688">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-688">SelectBackwardWord</span></span>

<span data-ttu-id="046e3-689">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-689">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="046e3-690">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-690">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="046e3-691">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="046e3-691">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="046e3-692">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="046e3-692">SelectForwardChar</span></span>

<span data-ttu-id="046e3-693">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="046e3-693">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="046e3-694">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-694">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="046e3-695">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-695">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="046e3-696">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-696">SelectForwardWord</span></span>

<span data-ttu-id="046e3-697">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="046e3-697">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="046e3-698">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="046e3-698">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="046e3-699">SelectLine</span><span class="sxs-lookup"><span data-stu-id="046e3-699">SelectLine</span></span>

<span data-ttu-id="046e3-700">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-700">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="046e3-701">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-701">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="046e3-702">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="046e3-702">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="046e3-703">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-703">SelectNextWord</span></span>

<span data-ttu-id="046e3-704">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-704">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="046e3-705">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="046e3-705">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="046e3-706">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-706">SelectShellBackwardWord</span></span>

<span data-ttu-id="046e3-707">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="046e3-707">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="046e3-708">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-708">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="046e3-709">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="046e3-709">SelectShellForwardWord</span></span>

<span data-ttu-id="046e3-710">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="046e3-710">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="046e3-711">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-711">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="046e3-712">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="046e3-712">SelectShellNextWord</span></span>

<span data-ttu-id="046e3-713">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="046e3-713">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="046e3-714">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="046e3-714">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="046e3-715">SetMark</span><span class="sxs-lookup"><span data-stu-id="046e3-715">SetMark</span></span>

<span data-ttu-id="046e3-716">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="046e3-716">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="046e3-717">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="046e3-717">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="046e3-718">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="046e3-718">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="046e3-719">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="046e3-719">CharacterSearch</span></span>

<span data-ttu-id="046e3-720">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="046e3-720">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="046e3-721">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="046e3-721">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="046e3-722">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-722">Cmd: `<F3>`</span></span>
- <span data-ttu-id="046e3-723">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="046e3-723">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="046e3-724">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-724">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="046e3-725">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-725">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="046e3-726">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-726">CharacterSearchBackward</span></span>

<span data-ttu-id="046e3-727">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="046e3-727">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="046e3-728">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="046e3-728">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="046e3-729">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-729">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="046e3-730">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="046e3-730">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="046e3-731">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-731">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="046e3-732">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="046e3-732">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="046e3-733">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="046e3-733">RepeatLastCharSearch</span></span>

<span data-ttu-id="046e3-734">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="046e3-734">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="046e3-735">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="046e3-735">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="046e3-736">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="046e3-736">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="046e3-737">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="046e3-737">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="046e3-738">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="046e3-738">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="046e3-739">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="046e3-739">RepeatSearch</span></span>

<span data-ttu-id="046e3-740">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="046e3-740">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="046e3-741">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="046e3-741">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="046e3-742">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-742">RepeatSearchBackward</span></span>

<span data-ttu-id="046e3-743">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="046e3-743">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="046e3-744">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="046e3-744">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="046e3-745">SearchChar</span><span class="sxs-lookup"><span data-stu-id="046e3-745">SearchChar</span></span>

<span data-ttu-id="046e3-746">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-746">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="046e3-747">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="046e3-747">This is for 't' functionality.</span></span>

- <span data-ttu-id="046e3-748">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="046e3-748">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="046e3-749">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="046e3-749">SearchCharBackward</span></span>

<span data-ttu-id="046e3-750">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="046e3-750">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="046e3-751">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="046e3-751">This is for 'T' functionality.</span></span>

- <span data-ttu-id="046e3-752">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="046e3-752">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="046e3-753">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="046e3-753">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="046e3-754">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="046e3-754">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="046e3-755">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="046e3-755">This is for 'T' functionality.</span></span>

- <span data-ttu-id="046e3-756">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="046e3-756">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="046e3-757">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="046e3-757">SearchCharWithBackoff</span></span>

<span data-ttu-id="046e3-758">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="046e3-758">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="046e3-759">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="046e3-759">This is for 't' functionality.</span></span>

- <span data-ttu-id="046e3-760">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="046e3-760">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="046e3-761">SearchForward</span><span class="sxs-lookup"><span data-stu-id="046e3-761">SearchForward</span></span>

<span data-ttu-id="046e3-762">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="046e3-762">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="046e3-763">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="046e3-763">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="046e3-764">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="046e3-764">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="046e3-765">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="046e3-765">Custom Key Bindings</span></span>

<span data-ttu-id="046e3-766">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="046e3-766">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="046e3-767">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="046e3-767">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="046e3-768">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="046e3-768">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="046e3-769">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="046e3-769">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="046e3-770">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="046e3-770">Some useful examples include</span></span>

- <span data-ttu-id="046e3-771">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="046e3-771">edit the command line</span></span>
- <span data-ttu-id="046e3-772">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="046e3-772">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="046e3-773">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="046e3-773">change directories without changing the command line</span></span>

<span data-ttu-id="046e3-774">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="046e3-774">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="046e3-775">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="046e3-775">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="046e3-776">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="046e3-776">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="046e3-777">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="046e3-777">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="046e3-778">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="046e3-778">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="046e3-779">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="046e3-779">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="046e3-780">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="046e3-780">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="046e3-781">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="046e3-781">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="046e3-782">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="046e3-782">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="046e3-783">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="046e3-783">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="046e3-784">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-784">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="046e3-785">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="046e3-785">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="046e3-786">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="046e3-786">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="046e3-787">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="046e3-787">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="046e3-788">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="046e3-788">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="046e3-789">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="046e3-789">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="046e3-790">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-790">Clear the kill-ring.</span></span>  <span data-ttu-id="046e3-791">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="046e3-791">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="046e3-792">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="046e3-792">Delete length characters from start.</span></span>  <span data-ttu-id="046e3-793">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="046e3-793">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="046e3-794">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="046e3-794">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="046e3-795">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="046e3-795">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="046e3-796">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="046e3-796">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="046e3-797">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="046e3-797">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="046e3-798">Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="046e3-798">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="046e3-799">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="046e3-799">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="046e3-800">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="046e3-800">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="046e3-801">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="046e3-801">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="046e3-802">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="046e3-802">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="046e3-803">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="046e3-803">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="046e3-804">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="046e3-804">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="046e3-805">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="046e3-805">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="046e3-806">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="046e3-806">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="046e3-807">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="046e3-807">Replace some of the input.</span></span> <span data-ttu-id="046e3-808">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="046e3-808">This operation supports undo/redo.</span></span> <span data-ttu-id="046e3-809">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="046e3-809">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="046e3-810">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="046e3-810">Move the cursor to the given offset.</span></span> <span data-ttu-id="046e3-811">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="046e3-811">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="046e3-812">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="046e3-812">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="046e3-813">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="046e3-813">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="046e3-814">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="046e3-814">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="046e3-815">Anteckning</span><span class="sxs-lookup"><span data-stu-id="046e3-815">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="046e3-816">Kommando historik</span><span class="sxs-lookup"><span data-stu-id="046e3-816">Command History</span></span>

<span data-ttu-id="046e3-817">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="046e3-817">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="046e3-818">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="046e3-818">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="046e3-819">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="046e3-819">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="046e3-820">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="046e3-820">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="046e3-821">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="046e3-821">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="046e3-822">Feedback & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="046e3-822">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="046e3-823">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="046e3-823">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="046e3-824">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="046e3-824">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="046e3-825">Se även</span><span class="sxs-lookup"><span data-stu-id="046e3-825">See Also</span></span>

<span data-ttu-id="046e3-826">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="046e3-826">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
