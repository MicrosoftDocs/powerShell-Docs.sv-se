---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 890f8e92172f2d492b6b817b558d4f25c70e8949
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93269936"
---
# <a name="psreadline"></a><span data-ttu-id="7c410-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="7c410-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="7c410-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="7c410-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="7c410-106">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7c410-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="7c410-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7c410-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="7c410-108">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="7c410-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="7c410-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="7c410-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="7c410-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="7c410-110">It provides:</span></span>

- <span data-ttu-id="7c410-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="7c410-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="7c410-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="7c410-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="7c410-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="7c410-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="7c410-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="7c410-114">Customizable key bindings</span></span>
- <span data-ttu-id="7c410-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="7c410-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="7c410-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="7c410-116">Many configuration options</span></span>
- <span data-ttu-id="7c410-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="7c410-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="7c410-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="7c410-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="7c410-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="7c410-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="7c410-120">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="7c410-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="7c410-121">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="7c410-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="7c410-122">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="7c410-123">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="7c410-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="7c410-124">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="7c410-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="7c410-125">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="7c410-126">Avbryta</span><span class="sxs-lookup"><span data-stu-id="7c410-126">Abort</span></span>

<span data-ttu-id="7c410-127">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="7c410-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="7c410-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="7c410-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="7c410-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="7c410-129">AcceptAndGetNext</span></span>

<span data-ttu-id="7c410-130">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-130">Attempt to execute the current input.</span></span> <span data-ttu-id="7c410-131">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="7c410-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="7c410-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="7c410-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="7c410-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="7c410-133">AcceptLine</span></span>

<span data-ttu-id="7c410-134">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-134">Attempt to execute the current input.</span></span> <span data-ttu-id="7c410-135">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="7c410-136">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="7c410-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="7c410-138">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="7c410-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="7c410-139">AddLine</span></span>

<span data-ttu-id="7c410-140">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="7c410-141">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="7c410-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="7c410-142">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="7c410-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="7c410-144">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="7c410-145">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="7c410-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="7c410-146">BackwardDeleteChar</span></span>

<span data-ttu-id="7c410-147">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="7c410-148">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="7c410-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="7c410-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="7c410-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="7c410-150">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="7c410-151">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="7c410-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="7c410-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="7c410-152">BackwardDeleteLine</span></span>

<span data-ttu-id="7c410-153">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="7c410-154">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="7c410-155">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="7c410-156">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="7c410-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="7c410-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="7c410-157">BackwardDeleteWord</span></span>

<span data-ttu-id="7c410-158">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-158">Deletes the previous word.</span></span>

- <span data-ttu-id="7c410-159">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="7c410-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="7c410-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="7c410-160">BackwardKillLine</span></span>

<span data-ttu-id="7c410-161">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="7c410-162">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="7c410-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="7c410-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="7c410-164">BackwardKillWord</span></span>

<span data-ttu-id="7c410-165">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="7c410-166">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="7c410-167">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="7c410-168">Kommandot `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="7c410-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="7c410-170">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="7c410-171">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="7c410-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="7c410-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="7c410-172">CancelLine</span></span>

<span data-ttu-id="7c410-173">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="7c410-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="7c410-174">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="7c410-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="7c410-175">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="7c410-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="7c410-176">Kopiera</span><span class="sxs-lookup"><span data-stu-id="7c410-176">Copy</span></span>

<span data-ttu-id="7c410-177">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="7c410-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="7c410-178">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="7c410-179">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="7c410-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="7c410-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="7c410-180">CopyOrCancelLine</span></span>

<span data-ttu-id="7c410-181">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="7c410-182">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="7c410-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="7c410-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="7c410-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="7c410-184">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="7c410-184">Cut</span></span>

<span data-ttu-id="7c410-185">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="7c410-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="7c410-186">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="7c410-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="7c410-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="7c410-187">DeleteChar</span></span>

<span data-ttu-id="7c410-188">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="7c410-189">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="7c410-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="7c410-191">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="7c410-192">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="7c410-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="7c410-193">DeleteCharOrExit</span></span>

<span data-ttu-id="7c410-194">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="7c410-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="7c410-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="7c410-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="7c410-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="7c410-196">DeleteEndOfWord</span></span>

<span data-ttu-id="7c410-197">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="7c410-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="7c410-198">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="7c410-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="7c410-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="7c410-199">DeleteLine</span></span>

<span data-ttu-id="7c410-200">Tar bort den aktuella raden och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="7c410-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="7c410-201">Kommando läge för vi: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="7c410-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="7c410-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="7c410-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="7c410-203">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="7c410-204">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="7c410-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="7c410-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="7c410-205">DeleteToEnd</span></span>

<span data-ttu-id="7c410-206">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="7c410-207">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="7c410-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="7c410-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="7c410-208">DeleteWord</span></span>

<span data-ttu-id="7c410-209">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-209">Delete the next word.</span></span>

- <span data-ttu-id="7c410-210">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="7c410-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="7c410-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="7c410-211">ForwardDeleteLine</span></span>

<span data-ttu-id="7c410-212">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="7c410-213">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="7c410-214">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="7c410-215">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="7c410-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="7c410-216">InsertLineAbove</span></span>

<span data-ttu-id="7c410-217">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="7c410-218">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="7c410-219">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="7c410-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="7c410-220">InsertLineBelow</span></span>

<span data-ttu-id="7c410-221">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="7c410-222">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="7c410-223">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="7c410-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="7c410-224">InvertCase</span></span>

<span data-ttu-id="7c410-225">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="7c410-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="7c410-226">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="7c410-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="7c410-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="7c410-227">KillLine</span></span>

<span data-ttu-id="7c410-228">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="7c410-229">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="7c410-230">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="7c410-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="7c410-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="7c410-231">KillRegion</span></span>

<span data-ttu-id="7c410-232">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="7c410-233">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="7c410-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="7c410-234">KillWord</span></span>

<span data-ttu-id="7c410-235">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="7c410-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="7c410-236">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="7c410-237">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="7c410-238">Kommandot `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="7c410-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="7c410-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="7c410-240">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="7c410-241">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="7c410-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="7c410-242">Klistra in</span><span class="sxs-lookup"><span data-stu-id="7c410-242">Paste</span></span>

<span data-ttu-id="7c410-243">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="7c410-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="7c410-244">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="7c410-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="7c410-245">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="7c410-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="7c410-246">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="7c410-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="7c410-247">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7c410-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="7c410-248">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="7c410-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="7c410-249">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="7c410-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="7c410-250">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="7c410-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="7c410-251">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="7c410-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="7c410-252">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="7c410-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="7c410-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="7c410-253">PasteAfter</span></span>

<span data-ttu-id="7c410-254">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="7c410-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="7c410-255">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="7c410-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="7c410-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="7c410-256">PasteBefore</span></span>

<span data-ttu-id="7c410-257">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="7c410-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="7c410-258">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="7c410-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="7c410-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="7c410-259">PrependAndAccept</span></span>

<span data-ttu-id="7c410-260">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="7c410-261">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="7c410-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="7c410-262">Gör om</span><span class="sxs-lookup"><span data-stu-id="7c410-262">Redo</span></span>

<span data-ttu-id="7c410-263">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="7c410-263">Undo an undo.</span></span>

- <span data-ttu-id="7c410-264">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="7c410-265">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="7c410-266">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="7c410-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="7c410-267">RepeatLastCommand</span></span>

<span data-ttu-id="7c410-268">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="7c410-269">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="7c410-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="7c410-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="7c410-270">RevertLine</span></span>

<span data-ttu-id="7c410-271">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="7c410-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="7c410-272">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="7c410-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="7c410-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="7c410-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="7c410-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="7c410-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="7c410-275">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="7c410-276">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="7c410-277">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="7c410-278">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="7c410-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="7c410-279">ShellKillWord</span></span>

<span data-ttu-id="7c410-280">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="7c410-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="7c410-281">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="7c410-282">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="7c410-283">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="7c410-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="7c410-284">SwapCharacters</span></span>

<span data-ttu-id="7c410-285">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="7c410-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="7c410-286">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="7c410-287">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="7c410-288">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="7c410-289">Ångra</span><span class="sxs-lookup"><span data-stu-id="7c410-289">Undo</span></span>

<span data-ttu-id="7c410-290">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="7c410-290">Undo a previous edit.</span></span>

- <span data-ttu-id="7c410-291">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="7c410-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="7c410-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="7c410-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="7c410-293">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="7c410-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="7c410-294">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="7c410-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="7c410-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="7c410-295">UndoAll</span></span>

<span data-ttu-id="7c410-296">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="7c410-297">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="7c410-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="7c410-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="7c410-298">UnixWordRubout</span></span>

<span data-ttu-id="7c410-299">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="7c410-300">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="7c410-301">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="7c410-302">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="7c410-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="7c410-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="7c410-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="7c410-304">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-304">Attempt to execute the current input.</span></span> <span data-ttu-id="7c410-305">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="7c410-306">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="7c410-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="7c410-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="7c410-307">ViAcceptLine</span></span>

<span data-ttu-id="7c410-308">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="7c410-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="7c410-309">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="7c410-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="7c410-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="7c410-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="7c410-311">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="7c410-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="7c410-312">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="7c410-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="7c410-313">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="7c410-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="7c410-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="7c410-314">ViAppendLine</span></span>

<span data-ttu-id="7c410-315">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="7c410-316">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="7c410-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="7c410-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="7c410-318">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="7c410-319">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="7c410-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="7c410-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-320">ViBackwardGlob</span></span>

<span data-ttu-id="7c410-321">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="7c410-322">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="7c410-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="7c410-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="7c410-323">ViDeleteBrace</span></span>

<span data-ttu-id="7c410-324">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="7c410-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="7c410-325">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="7c410-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="7c410-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="7c410-327">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="7c410-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="7c410-328">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="7c410-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="7c410-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-329">ViDeleteGlob</span></span>

<span data-ttu-id="7c410-330">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="7c410-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="7c410-331">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="7c410-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="7c410-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="7c410-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="7c410-333">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="7c410-333">Deletes until given character.</span></span>

- <span data-ttu-id="7c410-334">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="7c410-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="7c410-336">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="7c410-336">Deletes until given character.</span></span>

- <span data-ttu-id="7c410-337">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="7c410-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="7c410-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="7c410-338">ViDeleteToChar</span></span>

<span data-ttu-id="7c410-339">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="7c410-339">Deletes until given character.</span></span>

- <span data-ttu-id="7c410-340">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="7c410-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="7c410-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="7c410-342">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="7c410-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="7c410-343">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="7c410-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="7c410-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="7c410-344">ViInsertAtBegining</span></span>

<span data-ttu-id="7c410-345">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="7c410-346">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="7c410-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="7c410-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="7c410-347">ViInsertAtEnd</span></span>

<span data-ttu-id="7c410-348">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="7c410-349">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="7c410-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="7c410-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="7c410-350">ViInsertLine</span></span>

<span data-ttu-id="7c410-351">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="7c410-352">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="7c410-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="7c410-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="7c410-353">ViInsertWithAppend</span></span>

<span data-ttu-id="7c410-354">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="7c410-354">Append from the current line position.</span></span>

- <span data-ttu-id="7c410-355">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="7c410-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="7c410-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="7c410-356">ViInsertWithDelete</span></span>

<span data-ttu-id="7c410-357">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="7c410-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="7c410-358">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="7c410-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="7c410-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="7c410-359">ViJoinLines</span></span>

<span data-ttu-id="7c410-360">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="7c410-361">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="7c410-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="7c410-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="7c410-362">ViReplaceLine</span></span>

<span data-ttu-id="7c410-363">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-363">Erase the entire command line.</span></span>

- <span data-ttu-id="7c410-364">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="7c410-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="7c410-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="7c410-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="7c410-366">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="7c410-366">Replaces until given character.</span></span>

- <span data-ttu-id="7c410-367">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="7c410-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="7c410-369">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="7c410-369">Replaces until given character.</span></span>

- <span data-ttu-id="7c410-370">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="7c410-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="7c410-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="7c410-371">ViReplaceToChar</span></span>

<span data-ttu-id="7c410-372">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="7c410-372">Deletes until given character.</span></span>

- <span data-ttu-id="7c410-373">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="7c410-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="7c410-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="7c410-375">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="7c410-375">Replaces until given character.</span></span>

- <span data-ttu-id="7c410-376">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="7c410-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="7c410-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="7c410-378">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="7c410-379">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="7c410-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="7c410-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="7c410-381">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="7c410-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="7c410-382">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="7c410-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="7c410-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="7c410-383">ViYankEndOfWord</span></span>

<span data-ttu-id="7c410-384">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="7c410-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="7c410-385">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="7c410-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="7c410-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="7c410-386">ViYankLeft</span></span>

<span data-ttu-id="7c410-387">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="7c410-388">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="7c410-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="7c410-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="7c410-389">ViYankLine</span></span>

<span data-ttu-id="7c410-390">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="7c410-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="7c410-391">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="7c410-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-392">ViYankNextGlob</span></span>

<span data-ttu-id="7c410-393">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="7c410-394">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="7c410-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="7c410-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-395">ViYankNextWord</span></span>

<span data-ttu-id="7c410-396">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="7c410-397">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="7c410-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="7c410-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="7c410-398">ViYankPercent</span></span>

<span data-ttu-id="7c410-399">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="7c410-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="7c410-400">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="7c410-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="7c410-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="7c410-402">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="7c410-403">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="7c410-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="7c410-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="7c410-404">ViYankPreviousWord</span></span>

<span data-ttu-id="7c410-405">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="7c410-406">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="7c410-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="7c410-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="7c410-407">ViYankRight</span></span>

<span data-ttu-id="7c410-408">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="7c410-409">Kommando läge för vi: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="7c410-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="7c410-411">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="7c410-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="7c410-412">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="7c410-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="7c410-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="7c410-413">ViYankToFirstChar</span></span>

<span data-ttu-id="7c410-414">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="7c410-415">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="7c410-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="7c410-416">Yank</span><span class="sxs-lookup"><span data-stu-id="7c410-416">Yank</span></span>

<span data-ttu-id="7c410-417">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="7c410-418">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="7c410-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="7c410-419">YankLastArg</span></span>

<span data-ttu-id="7c410-420">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="7c410-421">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="7c410-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="7c410-422">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="7c410-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="7c410-423">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="7c410-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="7c410-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="7c410-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="7c410-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="7c410-425">YankNthArg</span></span>

<span data-ttu-id="7c410-426">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="7c410-427">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="7c410-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="7c410-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="7c410-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="7c410-429">YankPop</span></span>

<span data-ttu-id="7c410-430">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="7c410-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="7c410-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="7c410-432">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="7c410-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="7c410-433">BackwardChar</span></span>

<span data-ttu-id="7c410-434">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="7c410-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="7c410-435">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="7c410-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="7c410-436">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="7c410-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="7c410-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="7c410-438">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="7c410-439">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="7c410-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="7c410-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-440">BackwardWord</span></span>

<span data-ttu-id="7c410-441">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="7c410-442">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-443">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="7c410-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="7c410-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="7c410-445">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="7c410-446">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="7c410-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-447">BeginningOfLine</span></span>

<span data-ttu-id="7c410-448">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="7c410-449">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="7c410-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="7c410-450">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="7c410-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="7c410-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="7c410-452">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="7c410-453">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="7c410-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-454">EndOfLine</span></span>

<span data-ttu-id="7c410-455">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="7c410-456">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="7c410-457">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="7c410-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="7c410-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="7c410-459">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="7c410-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="7c410-460">ForwardChar</span></span>

<span data-ttu-id="7c410-461">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="7c410-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="7c410-462">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="7c410-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="7c410-463">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="7c410-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="7c410-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="7c410-465">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="7c410-466">Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="7c410-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="7c410-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-467">ForwardWord</span></span>

<span data-ttu-id="7c410-468">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="7c410-469">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="7c410-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="7c410-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="7c410-471">GotoBrace</span></span>

<span data-ttu-id="7c410-472">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="7c410-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="7c410-473">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="7c410-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="7c410-474">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="7c410-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="7c410-475">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="7c410-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="7c410-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="7c410-476">GotoColumn</span></span>

<span data-ttu-id="7c410-477">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="7c410-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="7c410-478">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="7c410-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="7c410-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="7c410-480">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="7c410-481">Kommando läge för vi: `<^>`</span><span class="sxs-lookup"><span data-stu-id="7c410-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="7c410-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="7c410-482">MoveToEndOfLine</span></span>

<span data-ttu-id="7c410-483">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="7c410-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="7c410-484">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="7c410-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="7c410-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="7c410-485">NextLine</span></span>

<span data-ttu-id="7c410-486">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="7c410-487">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="7c410-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-488">NextWord</span></span>

<span data-ttu-id="7c410-489">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="7c410-490">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-491">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="7c410-492">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="7c410-493">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="7c410-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="7c410-494">NextWordEnd</span></span>

<span data-ttu-id="7c410-495">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="7c410-496">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-497">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="7c410-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="7c410-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="7c410-498">PreviousLine</span></span>

<span data-ttu-id="7c410-499">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="7c410-500">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="7c410-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-501">ShellBackwardWord</span></span>

<span data-ttu-id="7c410-502">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="7c410-503">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="7c410-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="7c410-504">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="7c410-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-505">ShellForwardWord</span></span>

<span data-ttu-id="7c410-506">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="7c410-507">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="7c410-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="7c410-508">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="7c410-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-509">ShellNextWord</span></span>

<span data-ttu-id="7c410-510">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="7c410-511">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="7c410-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="7c410-512">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="7c410-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-513">ViBackwardWord</span></span>

<span data-ttu-id="7c410-514">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="7c410-515">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-516">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="7c410-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="7c410-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-517">ViEndOfGlob</span></span>

<span data-ttu-id="7c410-518">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="7c410-519">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="7c410-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="7c410-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="7c410-521">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="7c410-522">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="7c410-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="7c410-523">ViGotoBrace</span></span>

<span data-ttu-id="7c410-524">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="7c410-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="7c410-525">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="7c410-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="7c410-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="7c410-526">ViNextGlob</span></span>

<span data-ttu-id="7c410-527">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="7c410-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="7c410-528">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="7c410-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="7c410-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-529">ViNextWord</span></span>

<span data-ttu-id="7c410-530">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="7c410-531">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="7c410-532">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="7c410-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="7c410-533">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="7c410-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-534">BeginningOfHistory</span></span>

<span data-ttu-id="7c410-535">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="7c410-536">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="7c410-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="7c410-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-537">ClearHistory</span></span>

<span data-ttu-id="7c410-538">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7c410-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="7c410-539">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="7c410-540">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="7c410-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="7c410-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-541">EndOfHistory</span></span>

<span data-ttu-id="7c410-542">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="7c410-543">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="7c410-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="7c410-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-544">ForwardSearchHistory</span></span>

<span data-ttu-id="7c410-545">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="7c410-546">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="7c410-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="7c410-547">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="7c410-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="7c410-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-548">HistorySearchBackward</span></span>

<span data-ttu-id="7c410-549">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="7c410-550">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="7c410-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="7c410-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="7c410-551">HistorySearchForward</span></span>

<span data-ttu-id="7c410-552">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="7c410-553">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="7c410-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="7c410-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-554">NextHistory</span></span>

<span data-ttu-id="7c410-555">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="7c410-556">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="7c410-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="7c410-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="7c410-558">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="7c410-559">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="7c410-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="7c410-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-560">PreviousHistory</span></span>

<span data-ttu-id="7c410-561">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="7c410-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="7c410-562">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="7c410-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="7c410-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="7c410-564">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="7c410-565">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="7c410-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="7c410-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="7c410-566">ReverseSearchHistory</span></span>

<span data-ttu-id="7c410-567">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="7c410-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="7c410-568">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="7c410-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="7c410-569">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="7c410-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="7c410-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="7c410-571">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="7c410-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="7c410-572">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="7c410-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="7c410-573">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="7c410-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="7c410-574">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="7c410-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="7c410-575">Klart</span><span class="sxs-lookup"><span data-stu-id="7c410-575">Complete</span></span>

<span data-ttu-id="7c410-576">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="7c410-577">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="7c410-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="7c410-578">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="7c410-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="7c410-579">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="7c410-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="7c410-580">MenuComplete</span></span>

<span data-ttu-id="7c410-581">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="7c410-582">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="7c410-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="7c410-583">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="7c410-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="7c410-584">Kommandot `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="7c410-585">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="7c410-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="7c410-586">PossibleCompletions</span></span>

<span data-ttu-id="7c410-587">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="7c410-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="7c410-588">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="7c410-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="7c410-589">Vi infognings läge: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="7c410-590">Kommando läge för vi: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="7c410-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="7c410-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="7c410-591">TabCompleteNext</span></span>

<span data-ttu-id="7c410-592">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="7c410-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="7c410-593">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="7c410-594">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="7c410-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="7c410-595">TabCompletePrevious</span></span>

<span data-ttu-id="7c410-596">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="7c410-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="7c410-597">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="7c410-598">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="7c410-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="7c410-599">ViTabCompleteNext</span></span>

<span data-ttu-id="7c410-600">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="7c410-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="7c410-601">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="7c410-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="7c410-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="7c410-603">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="7c410-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="7c410-604">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="7c410-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="7c410-605">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="7c410-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="7c410-606">CaptureScreen</span></span>

<span data-ttu-id="7c410-607">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="7c410-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="7c410-608">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="7c410-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="7c410-609">ClearScreen</span></span>

<span data-ttu-id="7c410-610">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="7c410-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="7c410-611">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="7c410-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="7c410-612">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="7c410-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="7c410-613">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="7c410-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="7c410-614">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="7c410-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="7c410-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="7c410-615">DigitArgument</span></span>

<span data-ttu-id="7c410-616">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="7c410-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="7c410-617">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="7c410-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="7c410-618">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="7c410-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="7c410-619">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="7c410-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="7c410-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="7c410-620">InvokePrompt</span></span>

<span data-ttu-id="7c410-621">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="7c410-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="7c410-622">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="7c410-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="7c410-623">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="7c410-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="7c410-624">ScrollDisplayDown</span></span>

<span data-ttu-id="7c410-625">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="7c410-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="7c410-626">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="7c410-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="7c410-627">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="7c410-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="7c410-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="7c410-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="7c410-629">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="7c410-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="7c410-630">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="7c410-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="7c410-631">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="7c410-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="7c410-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="7c410-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="7c410-633">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="7c410-634">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="7c410-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="7c410-635">ScrollDisplayTop</span></span>

<span data-ttu-id="7c410-636">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="7c410-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="7c410-637">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="7c410-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="7c410-638">ScrollDisplayUp</span></span>

<span data-ttu-id="7c410-639">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="7c410-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="7c410-640">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="7c410-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="7c410-641">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="7c410-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="7c410-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="7c410-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="7c410-643">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="7c410-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="7c410-644">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="7c410-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="7c410-645">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="7c410-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="7c410-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="7c410-646">SelfInsert</span></span>

<span data-ttu-id="7c410-647">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="7c410-647">Insert the key.</span></span>

- <span data-ttu-id="7c410-648">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="7c410-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="7c410-649">ShowKeyBindings</span></span>

<span data-ttu-id="7c410-650">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="7c410-650">Show all bound keys.</span></span>

- <span data-ttu-id="7c410-651">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="7c410-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="7c410-652">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="7c410-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="7c410-653">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="7c410-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="7c410-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="7c410-654">ViCommandMode</span></span>

<span data-ttu-id="7c410-655">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="7c410-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="7c410-656">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="7c410-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="7c410-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="7c410-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="7c410-658">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="7c410-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="7c410-659">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="7c410-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="7c410-660">ViEditVisually</span></span>

<span data-ttu-id="7c410-661">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="7c410-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="7c410-662">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="7c410-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="7c410-663">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="7c410-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="7c410-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="7c410-664">ViExit</span></span>

<span data-ttu-id="7c410-665">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="7c410-665">Exits the shell.</span></span>

- <span data-ttu-id="7c410-666">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="7c410-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="7c410-667">ViInsertMode</span></span>

<span data-ttu-id="7c410-668">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="7c410-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="7c410-669">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="7c410-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="7c410-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="7c410-670">WhatIsKey</span></span>

<span data-ttu-id="7c410-671">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="7c410-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="7c410-672">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="7c410-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="7c410-673">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="7c410-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="7c410-674">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="7c410-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="7c410-675">ExchangePointAndMark</span></span>

<span data-ttu-id="7c410-676">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="7c410-677">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="7c410-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="7c410-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="7c410-678">SelectAll</span></span>

<span data-ttu-id="7c410-679">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-679">Select the entire line.</span></span>

- <span data-ttu-id="7c410-680">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="7c410-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="7c410-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="7c410-681">SelectBackwardChar</span></span>

<span data-ttu-id="7c410-682">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="7c410-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="7c410-683">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="7c410-684">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="7c410-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="7c410-685">SelectBackwardsLine</span></span>

<span data-ttu-id="7c410-686">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="7c410-687">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="7c410-688">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="7c410-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="7c410-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-689">SelectBackwardWord</span></span>

<span data-ttu-id="7c410-690">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="7c410-691">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="7c410-692">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="7c410-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="7c410-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="7c410-693">SelectForwardChar</span></span>

<span data-ttu-id="7c410-694">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="7c410-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="7c410-695">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="7c410-696">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="7c410-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-697">SelectForwardWord</span></span>

<span data-ttu-id="7c410-698">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="7c410-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="7c410-699">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="7c410-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="7c410-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="7c410-700">SelectLine</span></span>

<span data-ttu-id="7c410-701">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="7c410-702">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="7c410-703">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="7c410-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="7c410-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-704">SelectNextWord</span></span>

<span data-ttu-id="7c410-705">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="7c410-706">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="7c410-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="7c410-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="7c410-708">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="7c410-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="7c410-709">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="7c410-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="7c410-710">SelectShellForwardWord</span></span>

<span data-ttu-id="7c410-711">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="7c410-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="7c410-712">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="7c410-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="7c410-713">SelectShellNextWord</span></span>

<span data-ttu-id="7c410-714">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="7c410-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="7c410-715">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="7c410-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="7c410-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="7c410-716">SetMark</span></span>

<span data-ttu-id="7c410-717">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="7c410-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="7c410-718">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="7c410-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="7c410-719">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="7c410-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="7c410-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="7c410-720">CharacterSearch</span></span>

<span data-ttu-id="7c410-721">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="7c410-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="7c410-722">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="7c410-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="7c410-723">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="7c410-724">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="7c410-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="7c410-725">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="7c410-726">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="7c410-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-727">CharacterSearchBackward</span></span>

<span data-ttu-id="7c410-728">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="7c410-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="7c410-729">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="7c410-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="7c410-730">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="7c410-731">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="7c410-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="7c410-732">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="7c410-733">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="7c410-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="7c410-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="7c410-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="7c410-735">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="7c410-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="7c410-736">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="7c410-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="7c410-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="7c410-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="7c410-738">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="7c410-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="7c410-739">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="7c410-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="7c410-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="7c410-740">RepeatSearch</span></span>

<span data-ttu-id="7c410-741">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="7c410-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="7c410-742">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="7c410-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="7c410-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-743">RepeatSearchBackward</span></span>

<span data-ttu-id="7c410-744">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="7c410-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="7c410-745">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="7c410-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="7c410-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="7c410-746">SearchChar</span></span>

<span data-ttu-id="7c410-747">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="7c410-748">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="7c410-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="7c410-749">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="7c410-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="7c410-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="7c410-750">SearchCharBackward</span></span>

<span data-ttu-id="7c410-751">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="7c410-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="7c410-752">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="7c410-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="7c410-753">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="7c410-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="7c410-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="7c410-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="7c410-755">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="7c410-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="7c410-756">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="7c410-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="7c410-757">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="7c410-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="7c410-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="7c410-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="7c410-759">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="7c410-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="7c410-760">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="7c410-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="7c410-761">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="7c410-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="7c410-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="7c410-762">SearchForward</span></span>

<span data-ttu-id="7c410-763">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="7c410-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="7c410-764">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="7c410-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="7c410-765">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="7c410-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="7c410-766">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="7c410-766">Custom Key Bindings</span></span>

<span data-ttu-id="7c410-767">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="7c410-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="7c410-768">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="7c410-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="7c410-769">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="7c410-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="7c410-770">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="7c410-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="7c410-771">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="7c410-771">Some useful examples include</span></span>

- <span data-ttu-id="7c410-772">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="7c410-772">edit the command line</span></span>
- <span data-ttu-id="7c410-773">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="7c410-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="7c410-774">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="7c410-774">change directories without changing the command line</span></span>

<span data-ttu-id="7c410-775">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="7c410-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="7c410-776">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="7c410-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="7c410-777">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="7c410-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="7c410-778">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="7c410-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="7c410-779">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="7c410-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="7c410-780">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="7c410-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="7c410-781">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="7c410-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="7c410-782">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="7c410-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="7c410-783">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="7c410-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="7c410-784">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="7c410-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="7c410-785">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="7c410-786">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="7c410-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="7c410-787">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="7c410-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="7c410-788">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="7c410-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="7c410-789">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="7c410-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="7c410-790">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="7c410-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="7c410-791">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-791">Clear the kill-ring.</span></span>  <span data-ttu-id="7c410-792">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="7c410-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="7c410-793">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="7c410-793">Delete length characters from start.</span></span>  <span data-ttu-id="7c410-794">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="7c410-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="7c410-795">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="7c410-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="7c410-796">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="7c410-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="7c410-797">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="7c410-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="7c410-798">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="7c410-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="7c410-799">Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="7c410-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="7c410-800">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="7c410-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="7c410-801">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="7c410-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="7c410-802">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="7c410-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="7c410-803">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="7c410-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="7c410-804">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="7c410-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="7c410-805">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="7c410-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="7c410-806">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="7c410-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="7c410-807">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="7c410-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="7c410-808">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="7c410-808">Replace some of the input.</span></span> <span data-ttu-id="7c410-809">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="7c410-809">This operation supports undo/redo.</span></span> <span data-ttu-id="7c410-810">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="7c410-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="7c410-811">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="7c410-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="7c410-812">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="7c410-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="7c410-813">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="7c410-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="7c410-814">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="7c410-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="7c410-815">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="7c410-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="7c410-816">NOTE</span><span class="sxs-lookup"><span data-stu-id="7c410-816">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="7c410-817">POWERSHELL-KOMPATIBILITET</span><span class="sxs-lookup"><span data-stu-id="7c410-817">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="7c410-818">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="7c410-818">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="7c410-819">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="7c410-819">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="7c410-820">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="7c410-820">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="7c410-821">KOMMANDO HISTORIK</span><span class="sxs-lookup"><span data-stu-id="7c410-821">COMMAND HISTORY</span></span>

<span data-ttu-id="7c410-822">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="7c410-822">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="7c410-823">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="7c410-823">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="7c410-824">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="7c410-824">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="7c410-825">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="7c410-825">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="7c410-826">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="7c410-826">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="7c410-827">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="7c410-827">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="7c410-828">FEEDBACK & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="7c410-828">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="7c410-829">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="7c410-829">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="7c410-830">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="7c410-830">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="7c410-831">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="7c410-831">SEE ALSO</span></span>

<span data-ttu-id="7c410-832">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="7c410-832">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
