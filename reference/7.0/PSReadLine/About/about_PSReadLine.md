---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: f5ae99a7c8bdae82372423a3e4d8261d95ab83d5
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692215"
---
# <a name="psreadline"></a><span data-ttu-id="6ee20-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="6ee20-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="6ee20-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="6ee20-106">Short Description</span></span>

<span data-ttu-id="6ee20-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="6ee20-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="6ee20-108">Long Description</span></span>

<span data-ttu-id="6ee20-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="6ee20-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="6ee20-110">It provides:</span></span>

- <span data-ttu-id="6ee20-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="6ee20-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="6ee20-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="6ee20-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="6ee20-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="6ee20-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="6ee20-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="6ee20-114">Customizable key bindings</span></span>
- <span data-ttu-id="6ee20-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="6ee20-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="6ee20-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="6ee20-116">Many configuration options</span></span>
- <span data-ttu-id="6ee20-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="6ee20-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="6ee20-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="6ee20-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="6ee20-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="6ee20-119">PowerShell token based "word" movement and kill</span></span>

> [!NOTE]
> <span data-ttu-id="6ee20-120">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="6ee20-120">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="6ee20-121">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-121">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="6ee20-122">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="6ee20-122">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="6ee20-123">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="6ee20-123">You can manually load the module if necessary.</span></span>

<span data-ttu-id="6ee20-124">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="6ee20-124">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="6ee20-125">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="6ee20-126">Avbryta</span><span class="sxs-lookup"><span data-stu-id="6ee20-126">Abort</span></span>

<span data-ttu-id="6ee20-127">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="6ee20-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="6ee20-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="6ee20-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="6ee20-129">AcceptAndGetNext</span></span>

<span data-ttu-id="6ee20-130">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-130">Attempt to execute the current input.</span></span> <span data-ttu-id="6ee20-131">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="6ee20-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="6ee20-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="6ee20-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-133">AcceptLine</span></span>

<span data-ttu-id="6ee20-134">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-134">Attempt to execute the current input.</span></span> <span data-ttu-id="6ee20-135">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="6ee20-136">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="6ee20-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="6ee20-138">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="6ee20-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-139">AddLine</span></span>

<span data-ttu-id="6ee20-140">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="6ee20-141">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="6ee20-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="6ee20-142">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="6ee20-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="6ee20-144">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="6ee20-145">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="6ee20-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-146">BackwardDeleteChar</span></span>

<span data-ttu-id="6ee20-147">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="6ee20-148">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="6ee20-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="6ee20-150">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="6ee20-151">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="6ee20-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-152">BackwardDeleteLine</span></span>

<span data-ttu-id="6ee20-153">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-154">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="6ee20-155">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="6ee20-156">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="6ee20-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-157">BackwardDeleteWord</span></span>

<span data-ttu-id="6ee20-158">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-158">Deletes the previous word.</span></span>

- <span data-ttu-id="6ee20-159">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="6ee20-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-160">BackwardKillLine</span></span>

<span data-ttu-id="6ee20-161">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="6ee20-162">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="6ee20-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-164">BackwardKillWord</span></span>

<span data-ttu-id="6ee20-165">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="6ee20-166">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="6ee20-167">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-168">Kommandot `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-168">Cmd: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="6ee20-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="6ee20-170">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="6ee20-171">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="6ee20-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-172">CancelLine</span></span>

<span data-ttu-id="6ee20-173">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="6ee20-174">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="6ee20-175">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="6ee20-176">Kopiera</span><span class="sxs-lookup"><span data-stu-id="6ee20-176">Copy</span></span>

<span data-ttu-id="6ee20-177">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="6ee20-178">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="6ee20-179">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="6ee20-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-180">CopyOrCancelLine</span></span>

<span data-ttu-id="6ee20-181">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="6ee20-182">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="6ee20-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="6ee20-184">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="6ee20-184">Cut</span></span>

<span data-ttu-id="6ee20-185">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="6ee20-186">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="6ee20-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-187">DeleteChar</span></span>

<span data-ttu-id="6ee20-188">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="6ee20-189">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="6ee20-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="6ee20-191">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="6ee20-192">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Space>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="6ee20-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="6ee20-193">DeleteCharOrExit</span></span>

<span data-ttu-id="6ee20-194">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="6ee20-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="6ee20-196">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-196">DeleteEndOfWord</span></span>

<span data-ttu-id="6ee20-197">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-197">Delete to the end of the word.</span></span>

- <span data-ttu-id="6ee20-198">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-198">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="6ee20-199">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-199">DeleteLine</span></span>

<span data-ttu-id="6ee20-200">Tar bort den aktuella raden och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="6ee20-200">Deletes the current line, enabling undo.</span></span>

- <span data-ttu-id="6ee20-201">Kommando läge för vi: `<d,d>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-201">Vi command mode: `<d,d>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="6ee20-202">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-202">DeleteLineToFirstChar</span></span>

<span data-ttu-id="6ee20-203">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-203">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="6ee20-204">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-204">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="6ee20-205">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="6ee20-205">DeleteToEnd</span></span>

<span data-ttu-id="6ee20-206">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-206">Delete to the end of the line.</span></span>

- <span data-ttu-id="6ee20-207">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-207">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="6ee20-208">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-208">DeleteWord</span></span>

<span data-ttu-id="6ee20-209">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-209">Delete the next word.</span></span>

- <span data-ttu-id="6ee20-210">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-210">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="6ee20-211">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-211">ForwardDeleteLine</span></span>

<span data-ttu-id="6ee20-212">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-212">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-213">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-213">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="6ee20-214">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-214">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="6ee20-215">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-215">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="6ee20-216">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="6ee20-216">InsertLineAbove</span></span>

<span data-ttu-id="6ee20-217">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-217">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="6ee20-218">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-218">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="6ee20-219">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-219">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="6ee20-220">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="6ee20-220">InsertLineBelow</span></span>

<span data-ttu-id="6ee20-221">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-221">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="6ee20-222">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-222">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="6ee20-223">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-223">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="6ee20-224">InvertCase</span><span class="sxs-lookup"><span data-stu-id="6ee20-224">InvertCase</span></span>

<span data-ttu-id="6ee20-225">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="6ee20-225">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="6ee20-226">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-226">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="6ee20-227">KillLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-227">KillLine</span></span>

<span data-ttu-id="6ee20-228">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-228">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="6ee20-229">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-229">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-230">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-230">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="6ee20-231">KillRegion</span><span class="sxs-lookup"><span data-stu-id="6ee20-231">KillRegion</span></span>

<span data-ttu-id="6ee20-232">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-232">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="6ee20-233">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-233">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="6ee20-234">KillWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-234">KillWord</span></span>

<span data-ttu-id="6ee20-235">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-235">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="6ee20-236">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-236">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="6ee20-237">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-237">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-238">Kommandot `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-238">Cmd: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="6ee20-239">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-239">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="6ee20-240">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-240">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="6ee20-241">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-241">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="6ee20-242">Klistra in</span><span class="sxs-lookup"><span data-stu-id="6ee20-242">Paste</span></span>

<span data-ttu-id="6ee20-243">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-243">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="6ee20-244">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-244">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="6ee20-245">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-245">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="6ee20-246">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-246">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="6ee20-247">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="6ee20-247">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="6ee20-248">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="6ee20-248">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="6ee20-249">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="6ee20-249">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="6ee20-250">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="6ee20-250">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="6ee20-251">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="6ee20-251">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="6ee20-252">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-252">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="6ee20-253">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="6ee20-253">PasteAfter</span></span>

<span data-ttu-id="6ee20-254">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-254">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="6ee20-255">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-255">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="6ee20-256">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="6ee20-256">PasteBefore</span></span>

<span data-ttu-id="6ee20-257">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-257">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="6ee20-258">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-258">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="6ee20-259">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="6ee20-259">PrependAndAccept</span></span>

<span data-ttu-id="6ee20-260">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-260">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="6ee20-261">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-261">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="6ee20-262">Gör om</span><span class="sxs-lookup"><span data-stu-id="6ee20-262">Redo</span></span>

<span data-ttu-id="6ee20-263">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="6ee20-263">Undo an undo.</span></span>

- <span data-ttu-id="6ee20-264">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-264">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="6ee20-265">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-265">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="6ee20-266">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-266">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="6ee20-267">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="6ee20-267">RepeatLastCommand</span></span>

<span data-ttu-id="6ee20-268">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-268">Repeat the last text modification.</span></span>

- <span data-ttu-id="6ee20-269">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-269">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="6ee20-270">RevertLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-270">RevertLine</span></span>

<span data-ttu-id="6ee20-271">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="6ee20-271">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="6ee20-272">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-272">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="6ee20-273">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-273">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="6ee20-274">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-274">ShellBackwardKillWord</span></span>

<span data-ttu-id="6ee20-275">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-275">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="6ee20-276">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-276">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="6ee20-277">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-277">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="6ee20-278">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-278">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="6ee20-279">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-279">ShellKillWord</span></span>

<span data-ttu-id="6ee20-280">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-280">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="6ee20-281">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-281">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="6ee20-282">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-282">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="6ee20-283">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-283">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="6ee20-284">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="6ee20-284">SwapCharacters</span></span>

<span data-ttu-id="6ee20-285">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="6ee20-285">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="6ee20-286">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-286">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="6ee20-287">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-287">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="6ee20-288">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-288">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="6ee20-289">Ångra</span><span class="sxs-lookup"><span data-stu-id="6ee20-289">Undo</span></span>

<span data-ttu-id="6ee20-290">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="6ee20-290">Undo a previous edit.</span></span>

- <span data-ttu-id="6ee20-291">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-291">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="6ee20-292">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-292">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="6ee20-293">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-293">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="6ee20-294">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-294">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="6ee20-295">UndoAll</span><span class="sxs-lookup"><span data-stu-id="6ee20-295">UndoAll</span></span>

<span data-ttu-id="6ee20-296">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-296">Undo all previous edits for line.</span></span>

- <span data-ttu-id="6ee20-297">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-297">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="6ee20-298">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="6ee20-298">UnixWordRubout</span></span>

<span data-ttu-id="6ee20-299">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-299">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="6ee20-300">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-300">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="6ee20-301">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-301">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="6ee20-302">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-302">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="6ee20-303">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-303">ValidateAndAcceptLine</span></span>

<span data-ttu-id="6ee20-304">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-304">Attempt to execute the current input.</span></span> <span data-ttu-id="6ee20-305">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-305">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="6ee20-306">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-306">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="6ee20-307">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-307">ViAcceptLine</span></span>

<span data-ttu-id="6ee20-308">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="6ee20-308">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="6ee20-309">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-309">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="6ee20-310">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="6ee20-310">ViAcceptLineOrExit</span></span>

<span data-ttu-id="6ee20-311">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="6ee20-311">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="6ee20-312">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-312">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="6ee20-313">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-313">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="6ee20-314">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-314">ViAppendLine</span></span>

<span data-ttu-id="6ee20-315">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-315">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="6ee20-316">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-316">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="6ee20-317">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-317">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="6ee20-318">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-318">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="6ee20-319">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-319">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="6ee20-320">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-320">ViBackwardGlob</span></span>

<span data-ttu-id="6ee20-321">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-321">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="6ee20-322">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-322">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="6ee20-323">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="6ee20-323">ViDeleteBrace</span></span>

<span data-ttu-id="6ee20-324">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-324">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="6ee20-325">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-325">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="6ee20-326">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-326">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="6ee20-327">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-327">Delete to the end of the word.</span></span>

- <span data-ttu-id="6ee20-328">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-328">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="6ee20-329">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-329">ViDeleteGlob</span></span>

<span data-ttu-id="6ee20-330">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="6ee20-330">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="6ee20-331">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-331">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="6ee20-332">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-332">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="6ee20-333">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-333">Deletes until given character.</span></span>

- <span data-ttu-id="6ee20-334">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-334">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="6ee20-335">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-335">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="6ee20-336">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-336">Deletes until given character.</span></span>

- <span data-ttu-id="6ee20-337">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-337">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="6ee20-338">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-338">ViDeleteToChar</span></span>

<span data-ttu-id="6ee20-339">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-339">Deletes until given character.</span></span>

- <span data-ttu-id="6ee20-340">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-340">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="6ee20-341">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-341">ViDeleteToCharBackward</span></span>

<span data-ttu-id="6ee20-342">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="6ee20-342">Deletes backwards until given character.</span></span>

- <span data-ttu-id="6ee20-343">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-343">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="6ee20-344">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="6ee20-344">ViInsertAtBegining</span></span>

<span data-ttu-id="6ee20-345">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-345">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="6ee20-346">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-346">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="6ee20-347">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="6ee20-347">ViInsertAtEnd</span></span>

<span data-ttu-id="6ee20-348">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-348">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="6ee20-349">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-349">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="6ee20-350">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-350">ViInsertLine</span></span>

<span data-ttu-id="6ee20-351">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-351">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="6ee20-352">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-352">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="6ee20-353">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="6ee20-353">ViInsertWithAppend</span></span>

<span data-ttu-id="6ee20-354">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-354">Append from the current line position.</span></span>

- <span data-ttu-id="6ee20-355">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-355">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="6ee20-356">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="6ee20-356">ViInsertWithDelete</span></span>

<span data-ttu-id="6ee20-357">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="6ee20-357">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="6ee20-358">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-358">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="6ee20-359">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="6ee20-359">ViJoinLines</span></span>

<span data-ttu-id="6ee20-360">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-360">Joins the current line and the next line.</span></span>

- <span data-ttu-id="6ee20-361">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-361">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="6ee20-362">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-362">ViReplaceLine</span></span>

<span data-ttu-id="6ee20-363">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-363">Erase the entire command line.</span></span>

- <span data-ttu-id="6ee20-364">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-364">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="6ee20-365">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-365">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="6ee20-366">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-366">Replaces until given character.</span></span>

- <span data-ttu-id="6ee20-367">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-367">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="6ee20-368">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-368">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="6ee20-369">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-369">Replaces until given character.</span></span>

- <span data-ttu-id="6ee20-370">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-370">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="6ee20-371">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-371">ViReplaceToChar</span></span>

<span data-ttu-id="6ee20-372">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-372">Deletes until given character.</span></span>

- <span data-ttu-id="6ee20-373">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-373">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="6ee20-374">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-374">ViReplaceToCharBackward</span></span>

<span data-ttu-id="6ee20-375">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-375">Replaces until given character.</span></span>

- <span data-ttu-id="6ee20-376">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-376">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="6ee20-377">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-377">ViYankBeginningOfLine</span></span>

<span data-ttu-id="6ee20-378">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-378">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="6ee20-379">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-379">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="6ee20-380">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-380">ViYankEndOfGlob</span></span>

<span data-ttu-id="6ee20-381">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-381">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="6ee20-382">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-382">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="6ee20-383">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-383">ViYankEndOfWord</span></span>

<span data-ttu-id="6ee20-384">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-384">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="6ee20-385">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-385">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="6ee20-386">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="6ee20-386">ViYankLeft</span></span>

<span data-ttu-id="6ee20-387">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-387">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="6ee20-388">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-388">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="6ee20-389">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-389">ViYankLine</span></span>

<span data-ttu-id="6ee20-390">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-390">Yank the entire buffer.</span></span>

- <span data-ttu-id="6ee20-391">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-391">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="6ee20-392">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-392">ViYankNextGlob</span></span>

<span data-ttu-id="6ee20-393">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-393">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="6ee20-394">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-394">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="6ee20-395">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-395">ViYankNextWord</span></span>

<span data-ttu-id="6ee20-396">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-396">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="6ee20-397">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-397">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="6ee20-398">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="6ee20-398">ViYankPercent</span></span>

<span data-ttu-id="6ee20-399">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="6ee20-399">Yank to/from matching brace.</span></span>

- <span data-ttu-id="6ee20-400">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-400">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="6ee20-401">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-401">ViYankPreviousGlob</span></span>

<span data-ttu-id="6ee20-402">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-402">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="6ee20-403">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-403">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="6ee20-404">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-404">ViYankPreviousWord</span></span>

<span data-ttu-id="6ee20-405">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-405">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="6ee20-406">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-406">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="6ee20-407">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="6ee20-407">ViYankRight</span></span>

<span data-ttu-id="6ee20-408">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-408">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="6ee20-409">Kommando läge för vi: `<y,l>` , `<y,Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-409">Vi command mode: `<y,l>`, `<y,Space>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="6ee20-410">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-410">ViYankToEndOfLine</span></span>

<span data-ttu-id="6ee20-411">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-411">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="6ee20-412">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-412">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="6ee20-413">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-413">ViYankToFirstChar</span></span>

<span data-ttu-id="6ee20-414">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-414">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="6ee20-415">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-415">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="6ee20-416">Yank</span><span class="sxs-lookup"><span data-stu-id="6ee20-416">Yank</span></span>

<span data-ttu-id="6ee20-417">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-417">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="6ee20-418">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-418">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="6ee20-419">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="6ee20-419">YankLastArg</span></span>

<span data-ttu-id="6ee20-420">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-420">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="6ee20-421">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-421">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="6ee20-422">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="6ee20-422">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="6ee20-423">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-423">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="6ee20-424">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-424">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="6ee20-425">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="6ee20-425">YankNthArg</span></span>

<span data-ttu-id="6ee20-426">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-426">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="6ee20-427">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-427">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="6ee20-428">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-428">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="6ee20-429">YankPop</span><span class="sxs-lookup"><span data-stu-id="6ee20-429">YankPop</span></span>

<span data-ttu-id="6ee20-430">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-430">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="6ee20-431">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-431">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="6ee20-432">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-432">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="6ee20-433">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-433">BackwardChar</span></span>

<span data-ttu-id="6ee20-434">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="6ee20-434">Move the cursor one character to the left.</span></span> <span data-ttu-id="6ee20-435">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="6ee20-435">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="6ee20-436">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-436">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-437">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-437">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>
- <span data-ttu-id="6ee20-438">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-438">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-439">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-439">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="6ee20-440">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-440">BackwardWord</span></span>

<span data-ttu-id="6ee20-441">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-441">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="6ee20-442">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-442">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-443">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-443">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-444">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-444">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="6ee20-445">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-445">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-446">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-446">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="6ee20-447">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-447">BeginningOfLine</span></span>

<span data-ttu-id="6ee20-448">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-448">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="6ee20-449">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-449">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="6ee20-450">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-450">Cmd: `<Home>`</span></span>
- <span data-ttu-id="6ee20-451">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-451">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="6ee20-452">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-452">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="6ee20-453">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-453">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="6ee20-454">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-454">EndOfLine</span></span>

<span data-ttu-id="6ee20-455">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-455">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="6ee20-456">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-456">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="6ee20-457">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-457">Cmd: `<End>`</span></span>
- <span data-ttu-id="6ee20-458">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-458">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="6ee20-459">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-459">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="6ee20-460">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-460">ForwardChar</span></span>

<span data-ttu-id="6ee20-461">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="6ee20-461">Move the cursor one character to the right.</span></span> <span data-ttu-id="6ee20-462">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="6ee20-462">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="6ee20-463">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-463">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="6ee20-464">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-464">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>
- <span data-ttu-id="6ee20-465">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-465">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="6ee20-466">Vi kommando läge: `<RightArrow>` , `<Space>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-466">Vi command mode: `<RightArrow>`, `<Space>`, `<l>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="6ee20-467">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-467">ForwardWord</span></span>

<span data-ttu-id="6ee20-468">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-468">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="6ee20-469">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-469">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-470">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-470">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="6ee20-471">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="6ee20-471">GotoBrace</span></span>

<span data-ttu-id="6ee20-472">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-472">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="6ee20-473">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-473">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="6ee20-474">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-474">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="6ee20-475">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-475">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="6ee20-476">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="6ee20-476">GotoColumn</span></span>

<span data-ttu-id="6ee20-477">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="6ee20-477">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="6ee20-478">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-478">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="6ee20-479">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-479">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="6ee20-480">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-480">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="6ee20-481">Kommando läge för vi: `<^>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-481">Vi command mode: `<^>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="6ee20-482">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-482">MoveToEndOfLine</span></span>

<span data-ttu-id="6ee20-483">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-483">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="6ee20-484">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-484">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="6ee20-485">NextLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-485">NextLine</span></span>

<span data-ttu-id="6ee20-486">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-486">Move the cursor to the next line.</span></span>

- <span data-ttu-id="6ee20-487">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-487">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="6ee20-488">NextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-488">NextWord</span></span>

<span data-ttu-id="6ee20-489">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-489">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="6ee20-490">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-490">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-491">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-491">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="6ee20-492">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-492">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="6ee20-493">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-493">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="6ee20-494">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="6ee20-494">NextWordEnd</span></span>

<span data-ttu-id="6ee20-495">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="6ee20-496">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-497">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-497">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="6ee20-498">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-498">PreviousLine</span></span>

<span data-ttu-id="6ee20-499">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-499">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="6ee20-500">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-500">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="6ee20-501">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-501">ShellBackwardWord</span></span>

<span data-ttu-id="6ee20-502">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-502">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="6ee20-503">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="6ee20-503">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="6ee20-504">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-504">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="6ee20-505">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-505">ShellForwardWord</span></span>

<span data-ttu-id="6ee20-506">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-506">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="6ee20-507">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="6ee20-507">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="6ee20-508">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-508">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="6ee20-509">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-509">ShellNextWord</span></span>

<span data-ttu-id="6ee20-510">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-510">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="6ee20-511">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="6ee20-511">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="6ee20-512">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-512">Function is unbound.</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="6ee20-513">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-513">ViBackwardWord</span></span>

<span data-ttu-id="6ee20-514">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="6ee20-515">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-515">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-516">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-516">Vi command mode: `<b>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="6ee20-517">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-517">ViEndOfGlob</span></span>

<span data-ttu-id="6ee20-518">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-518">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="6ee20-519">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-519">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="6ee20-520">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-520">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="6ee20-521">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-521">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="6ee20-522">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-522">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="6ee20-523">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="6ee20-523">ViGotoBrace</span></span>

<span data-ttu-id="6ee20-524">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="6ee20-524">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="6ee20-525">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-525">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="6ee20-526">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="6ee20-526">ViNextGlob</span></span>

<span data-ttu-id="6ee20-527">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-527">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="6ee20-528">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-528">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="6ee20-529">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-529">ViNextWord</span></span>

<span data-ttu-id="6ee20-530">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-530">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="6ee20-531">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-531">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="6ee20-532">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-532">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="6ee20-533">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-533">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="6ee20-534">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-534">BeginningOfHistory</span></span>

<span data-ttu-id="6ee20-535">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-535">Move to the first item in the history.</span></span>

- <span data-ttu-id="6ee20-536">Emacs: `<Alt+`<>\`</span><span class="sxs-lookup"><span data-stu-id="6ee20-536">Emacs: `<Alt+`<>\`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="6ee20-537">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-537">ClearHistory</span></span>

<span data-ttu-id="6ee20-538">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="6ee20-538">Clears history in PSReadLine.</span></span> <span data-ttu-id="6ee20-539">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-539">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="6ee20-540">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-540">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="6ee20-541">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-541">EndOfHistory</span></span>

<span data-ttu-id="6ee20-542">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-542">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="6ee20-543">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-543">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="6ee20-544">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-544">ForwardSearchHistory</span></span>

<span data-ttu-id="6ee20-545">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-545">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="6ee20-546">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-546">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="6ee20-547">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-547">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="6ee20-548">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-548">HistorySearchBackward</span></span>

<span data-ttu-id="6ee20-549">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-549">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="6ee20-550">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-550">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="6ee20-551">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="6ee20-551">HistorySearchForward</span></span>

<span data-ttu-id="6ee20-552">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-552">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="6ee20-553">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-553">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="6ee20-554">NextHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-554">NextHistory</span></span>

<span data-ttu-id="6ee20-555">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-555">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="6ee20-556">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-556">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="6ee20-557">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-557">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="6ee20-558">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-558">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="6ee20-559">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-559">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="6ee20-560">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-560">PreviousHistory</span></span>

<span data-ttu-id="6ee20-561">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="6ee20-561">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="6ee20-562">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-562">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="6ee20-563">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-563">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="6ee20-564">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-564">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="6ee20-565">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="6ee20-565">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="6ee20-566">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="6ee20-566">ReverseSearchHistory</span></span>

<span data-ttu-id="6ee20-567">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-567">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="6ee20-568">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-568">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="6ee20-569">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-569">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="6ee20-570">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-570">ViSearchHistoryBackward</span></span>

<span data-ttu-id="6ee20-571">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="6ee20-571">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="6ee20-572">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-572">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="6ee20-573">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-573">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="6ee20-574">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="6ee20-574">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="6ee20-575">Klart</span><span class="sxs-lookup"><span data-stu-id="6ee20-575">Complete</span></span>

<span data-ttu-id="6ee20-576">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-576">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="6ee20-577">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="6ee20-577">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="6ee20-578">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="6ee20-578">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="6ee20-579">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-579">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="6ee20-580">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="6ee20-580">MenuComplete</span></span>

<span data-ttu-id="6ee20-581">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-581">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="6ee20-582">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="6ee20-582">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="6ee20-583">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="6ee20-583">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="6ee20-584">Kommandot `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-584">Cmd: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="6ee20-585">Emacs: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-585">Emacs: `<Ctrl+Space>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="6ee20-586">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="6ee20-586">PossibleCompletions</span></span>

<span data-ttu-id="6ee20-587">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="6ee20-587">Display the list of possible completions.</span></span>

- <span data-ttu-id="6ee20-588">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-588">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="6ee20-589">Vi infognings läge: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-589">Vi insert mode: `<Ctrl+Space>`</span></span>
- <span data-ttu-id="6ee20-590">Kommando läge för vi: `<Ctrl+Space>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-590">Vi command mode: `<Ctrl+Space>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="6ee20-591">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="6ee20-591">TabCompleteNext</span></span>

<span data-ttu-id="6ee20-592">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="6ee20-592">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="6ee20-593">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-593">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="6ee20-594">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-594">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="6ee20-595">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="6ee20-595">TabCompletePrevious</span></span>

<span data-ttu-id="6ee20-596">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="6ee20-596">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="6ee20-597">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-597">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="6ee20-598">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-598">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="6ee20-599">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="6ee20-599">ViTabCompleteNext</span></span>

<span data-ttu-id="6ee20-600">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="6ee20-600">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="6ee20-601">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-601">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="6ee20-602">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="6ee20-602">ViTabCompletePrevious</span></span>

<span data-ttu-id="6ee20-603">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="6ee20-603">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="6ee20-604">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-604">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="6ee20-605">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-605">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="6ee20-606">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="6ee20-606">CaptureScreen</span></span>

<span data-ttu-id="6ee20-607">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="6ee20-607">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="6ee20-608">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-608">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="6ee20-609">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="6ee20-609">ClearScreen</span></span>

<span data-ttu-id="6ee20-610">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-610">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="6ee20-611">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-611">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="6ee20-612">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-612">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="6ee20-613">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-613">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="6ee20-614">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-614">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="6ee20-615">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="6ee20-615">DigitArgument</span></span>

<span data-ttu-id="6ee20-616">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ee20-616">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="6ee20-617">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="6ee20-617">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="6ee20-618">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="6ee20-618">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="6ee20-619">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-619">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="6ee20-620">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="6ee20-620">InvokePrompt</span></span>

<span data-ttu-id="6ee20-621">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-621">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="6ee20-622">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-622">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="6ee20-623">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-623">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="6ee20-624">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="6ee20-624">ScrollDisplayDown</span></span>

<span data-ttu-id="6ee20-625">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="6ee20-625">Scroll the display down one screen.</span></span>

- <span data-ttu-id="6ee20-626">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-626">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="6ee20-627">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-627">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="6ee20-628">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-628">ScrollDisplayDownLine</span></span>

<span data-ttu-id="6ee20-629">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="6ee20-629">Scroll the display down one line.</span></span>

- <span data-ttu-id="6ee20-630">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-630">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="6ee20-631">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-631">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="6ee20-632">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="6ee20-632">ScrollDisplayToCursor</span></span>

<span data-ttu-id="6ee20-633">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-633">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="6ee20-634">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-634">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="6ee20-635">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="6ee20-635">ScrollDisplayTop</span></span>

<span data-ttu-id="6ee20-636">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="6ee20-636">Scroll the display to the top.</span></span>

- <span data-ttu-id="6ee20-637">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-637">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="6ee20-638">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="6ee20-638">ScrollDisplayUp</span></span>

<span data-ttu-id="6ee20-639">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="6ee20-639">Scroll the display up one screen.</span></span>

- <span data-ttu-id="6ee20-640">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-640">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="6ee20-641">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-641">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="6ee20-642">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-642">ScrollDisplayUpLine</span></span>

<span data-ttu-id="6ee20-643">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="6ee20-643">Scroll the display up one line.</span></span>

- <span data-ttu-id="6ee20-644">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-644">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="6ee20-645">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-645">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="6ee20-646">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="6ee20-646">SelfInsert</span></span>

<span data-ttu-id="6ee20-647">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="6ee20-647">Insert the key.</span></span>

- <span data-ttu-id="6ee20-648">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-648">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="6ee20-649">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="6ee20-649">ShowKeyBindings</span></span>

<span data-ttu-id="6ee20-650">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="6ee20-650">Show all bound keys.</span></span>

- <span data-ttu-id="6ee20-651">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-651">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="6ee20-652">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-652">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="6ee20-653">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-653">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="6ee20-654">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="6ee20-654">ViCommandMode</span></span>

<span data-ttu-id="6ee20-655">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="6ee20-655">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="6ee20-656">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-656">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="6ee20-657">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="6ee20-657">ViDigitArgumentInChord</span></span>

<span data-ttu-id="6ee20-658">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="6ee20-658">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="6ee20-659">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-659">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="6ee20-660">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="6ee20-660">ViEditVisually</span></span>

<span data-ttu-id="6ee20-661">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="6ee20-661">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="6ee20-662">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-662">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="6ee20-663">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-663">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="6ee20-664">ViExit</span><span class="sxs-lookup"><span data-stu-id="6ee20-664">ViExit</span></span>

<span data-ttu-id="6ee20-665">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-665">Exits the shell.</span></span>

- <span data-ttu-id="6ee20-666">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-666">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="6ee20-667">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="6ee20-667">ViInsertMode</span></span>

<span data-ttu-id="6ee20-668">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="6ee20-668">Switch to Insert mode.</span></span>

- <span data-ttu-id="6ee20-669">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-669">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="6ee20-670">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="6ee20-670">WhatIsKey</span></span>

<span data-ttu-id="6ee20-671">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="6ee20-671">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="6ee20-672">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-672">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="6ee20-673">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-673">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="6ee20-674">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-674">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="6ee20-675">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="6ee20-675">ExchangePointAndMark</span></span>

<span data-ttu-id="6ee20-676">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-676">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="6ee20-677">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-677">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="6ee20-678">SelectAll</span><span class="sxs-lookup"><span data-stu-id="6ee20-678">SelectAll</span></span>

<span data-ttu-id="6ee20-679">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-679">Select the entire line.</span></span>

- <span data-ttu-id="6ee20-680">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-680">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="6ee20-681">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-681">SelectBackwardChar</span></span>

<span data-ttu-id="6ee20-682">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-682">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="6ee20-683">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-683">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-684">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-684">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="6ee20-685">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-685">SelectBackwardsLine</span></span>

<span data-ttu-id="6ee20-686">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-686">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="6ee20-687">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-687">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="6ee20-688">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-688">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="6ee20-689">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-689">SelectBackwardWord</span></span>

<span data-ttu-id="6ee20-690">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-690">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="6ee20-691">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-691">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="6ee20-692">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-692">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="6ee20-693">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-693">SelectForwardChar</span></span>

<span data-ttu-id="6ee20-694">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-694">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="6ee20-695">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-695">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="6ee20-696">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-696">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="6ee20-697">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-697">SelectForwardWord</span></span>

<span data-ttu-id="6ee20-698">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-698">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="6ee20-699">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-699">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="6ee20-700">SelectLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-700">SelectLine</span></span>

<span data-ttu-id="6ee20-701">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-701">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="6ee20-702">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-702">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="6ee20-703">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-703">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="6ee20-704">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-704">SelectNextWord</span></span>

<span data-ttu-id="6ee20-705">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-705">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="6ee20-706">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-706">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="6ee20-707">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-707">SelectShellBackwardWord</span></span>

<span data-ttu-id="6ee20-708">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-708">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="6ee20-709">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-709">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="6ee20-710">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-710">SelectShellForwardWord</span></span>

<span data-ttu-id="6ee20-711">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-711">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="6ee20-712">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-712">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="6ee20-713">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="6ee20-713">SelectShellNextWord</span></span>

<span data-ttu-id="6ee20-714">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-714">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="6ee20-715">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-715">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="6ee20-716">SetMark</span><span class="sxs-lookup"><span data-stu-id="6ee20-716">SetMark</span></span>

<span data-ttu-id="6ee20-717">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="6ee20-717">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="6ee20-718">Emacs: `<Ctrl+`>\`</span><span class="sxs-lookup"><span data-stu-id="6ee20-718">Emacs: `<Ctrl+`>\`</span></span>

## <a name="search-functions"></a><span data-ttu-id="6ee20-719">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="6ee20-719">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="6ee20-720">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="6ee20-720">CharacterSearch</span></span>

<span data-ttu-id="6ee20-721">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-721">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="6ee20-722">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-722">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="6ee20-723">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-723">Cmd: `<F3>`</span></span>
- <span data-ttu-id="6ee20-724">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-724">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="6ee20-725">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-725">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="6ee20-726">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-726">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="6ee20-727">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-727">CharacterSearchBackward</span></span>

<span data-ttu-id="6ee20-728">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-728">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="6ee20-729">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-729">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="6ee20-730">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-730">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="6ee20-731">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-731">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="6ee20-732">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-732">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="6ee20-733">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-733">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="6ee20-734">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="6ee20-734">RepeatLastCharSearch</span></span>

<span data-ttu-id="6ee20-735">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-735">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="6ee20-736">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-736">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="6ee20-737">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="6ee20-737">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="6ee20-738">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-738">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="6ee20-739">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-739">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="6ee20-740">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="6ee20-740">RepeatSearch</span></span>

<span data-ttu-id="6ee20-741">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-741">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="6ee20-742">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-742">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="6ee20-743">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-743">RepeatSearchBackward</span></span>

<span data-ttu-id="6ee20-744">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="6ee20-744">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="6ee20-745">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-745">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="6ee20-746">SearchChar</span><span class="sxs-lookup"><span data-stu-id="6ee20-746">SearchChar</span></span>

<span data-ttu-id="6ee20-747">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-747">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="6ee20-748">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ee20-748">This is for 't' functionality.</span></span>

- <span data-ttu-id="6ee20-749">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-749">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="6ee20-750">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="6ee20-750">SearchCharBackward</span></span>

<span data-ttu-id="6ee20-751">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-751">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="6ee20-752">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ee20-752">This is for 'T' functionality.</span></span>

- <span data-ttu-id="6ee20-753">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-753">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="6ee20-754">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="6ee20-754">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="6ee20-755">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-755">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="6ee20-756">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ee20-756">This is for 'T' functionality.</span></span>

- <span data-ttu-id="6ee20-757">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-757">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="6ee20-758">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="6ee20-758">SearchCharWithBackoff</span></span>

<span data-ttu-id="6ee20-759">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="6ee20-759">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="6ee20-760">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="6ee20-760">This is for 't' functionality.</span></span>

- <span data-ttu-id="6ee20-761">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-761">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="6ee20-762">SearchForward</span><span class="sxs-lookup"><span data-stu-id="6ee20-762">SearchForward</span></span>

<span data-ttu-id="6ee20-763">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="6ee20-763">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="6ee20-764">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-764">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="6ee20-765">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="6ee20-765">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="6ee20-766">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="6ee20-766">Custom Key Bindings</span></span>

<span data-ttu-id="6ee20-767">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="6ee20-767">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="6ee20-768">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="6ee20-768">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="6ee20-769">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="6ee20-769">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="6ee20-770">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="6ee20-770">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="6ee20-771">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="6ee20-771">Some useful examples include</span></span>

- <span data-ttu-id="6ee20-772">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="6ee20-772">edit the command line</span></span>
- <span data-ttu-id="6ee20-773">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="6ee20-773">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="6ee20-774">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="6ee20-774">change directories without changing the command line</span></span>

<span data-ttu-id="6ee20-775">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="6ee20-775">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="6ee20-776">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-776">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="6ee20-777">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="6ee20-777">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="6ee20-778">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-778">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="6ee20-779">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="6ee20-779">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="6ee20-780">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="6ee20-780">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="6ee20-781">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="6ee20-781">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="6ee20-782">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="6ee20-782">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="6ee20-783">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="6ee20-783">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="6ee20-784">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="6ee20-784">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="6ee20-785">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-785">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="6ee20-786">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="6ee20-786">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="6ee20-787">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="6ee20-787">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="6ee20-788">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="6ee20-788">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="6ee20-789">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="6ee20-789">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="6ee20-790">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="6ee20-790">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="6ee20-791">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-791">Clear the kill-ring.</span></span>  <span data-ttu-id="6ee20-792">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-792">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="6ee20-793">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="6ee20-793">Delete length characters from start.</span></span>  <span data-ttu-id="6ee20-794">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="6ee20-794">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="6ee20-795">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="6ee20-795">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="6ee20-796">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="6ee20-796">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="6ee20-797">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="6ee20-797">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="6ee20-798">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="6ee20-798">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

```

<span data-ttu-id="6ee20-799">Den här funktionen används av Get-PSReadLineKeyHandler och är förmodligen inte användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-799">This function is used by Get-PSReadLineKeyHandler and probably isn't useful in a custom key binding.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="6ee20-800">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-800">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="6ee20-801">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="6ee20-801">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="6ee20-802">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-802">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="6ee20-803">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="6ee20-803">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="6ee20-804">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="6ee20-804">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="6ee20-805">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="6ee20-805">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="6ee20-806">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-806">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="6ee20-807">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-807">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="6ee20-808">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="6ee20-808">Replace some of the input.</span></span> <span data-ttu-id="6ee20-809">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="6ee20-809">This operation supports undo/redo.</span></span> <span data-ttu-id="6ee20-810">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="6ee20-810">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="6ee20-811">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="6ee20-811">Move the cursor to the given offset.</span></span> <span data-ttu-id="6ee20-812">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="6ee20-812">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="6ee20-813">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="6ee20-813">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="6ee20-814">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="6ee20-814">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="6ee20-815">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="6ee20-815">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="6ee20-816">Anteckning</span><span class="sxs-lookup"><span data-stu-id="6ee20-816">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="6ee20-817">Kommando historik</span><span class="sxs-lookup"><span data-stu-id="6ee20-817">Command History</span></span>

<span data-ttu-id="6ee20-818">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="6ee20-818">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="6ee20-819">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="6ee20-819">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="6ee20-820">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="6ee20-820">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="6ee20-821">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="6ee20-821">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="6ee20-822">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="6ee20-822">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="6ee20-823">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="6ee20-823">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="6ee20-824">Feedback & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="6ee20-824">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="6ee20-825">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="6ee20-825">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="6ee20-826">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="6ee20-826">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="6ee20-827">Se även</span><span class="sxs-lookup"><span data-stu-id="6ee20-827">See Also</span></span>

<span data-ttu-id="6ee20-828">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="6ee20-828">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
