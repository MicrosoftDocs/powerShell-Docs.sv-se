---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 02/10/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 1188b8dc0b4099a7c1dcc472e3b02c2d4fa908bc
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270129"
---
# <a name="psreadline"></a><span data-ttu-id="1200a-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1200a-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="1200a-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1200a-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="1200a-106">KORT BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1200a-106">SHORT DESCRIPTION</span></span>

<span data-ttu-id="1200a-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1200a-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="1200a-108">LÅNG BESKRIVNING</span><span class="sxs-lookup"><span data-stu-id="1200a-108">LONG DESCRIPTION</span></span>

<span data-ttu-id="1200a-109">PSReadLine 2,0 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1200a-109">PSReadLine 2.0 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="1200a-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="1200a-110">It provides:</span></span>

- <span data-ttu-id="1200a-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="1200a-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="1200a-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="1200a-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="1200a-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="1200a-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="1200a-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="1200a-114">Customizable key bindings</span></span>
- <span data-ttu-id="1200a-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="1200a-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="1200a-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="1200a-116">Many configuration options</span></span>
- <span data-ttu-id="1200a-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="1200a-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="1200a-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="1200a-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="1200a-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="1200a-119">PowerShell token based "word" movement and kill</span></span>

<span data-ttu-id="1200a-120">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="1200a-120">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

> [!NOTE]
> <span data-ttu-id="1200a-121">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="1200a-121">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="1200a-122">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-122">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="1200a-123">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="1200a-123">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="1200a-124">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="1200a-124">You can manually load the module if necessary.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="1200a-125">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-125">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="1200a-126">Avbryta</span><span class="sxs-lookup"><span data-stu-id="1200a-126">Abort</span></span>

<span data-ttu-id="1200a-127">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="1200a-127">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="1200a-128">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="1200a-128">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="1200a-129">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="1200a-129">AcceptAndGetNext</span></span>

<span data-ttu-id="1200a-130">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-130">Attempt to execute the current input.</span></span> <span data-ttu-id="1200a-131">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="1200a-131">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="1200a-132">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="1200a-132">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="1200a-133">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="1200a-133">AcceptLine</span></span>

<span data-ttu-id="1200a-134">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-134">Attempt to execute the current input.</span></span> <span data-ttu-id="1200a-135">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-135">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="1200a-136">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-136">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="1200a-137">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-137">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="1200a-138">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-138">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="1200a-139">AddLine</span><span class="sxs-lookup"><span data-stu-id="1200a-139">AddLine</span></span>

<span data-ttu-id="1200a-140">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-140">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="1200a-141">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="1200a-141">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="1200a-142">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-142">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1200a-143">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-143">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1200a-144">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-144">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1200a-145">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-145">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="1200a-146">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="1200a-146">BackwardDeleteChar</span></span>

<span data-ttu-id="1200a-147">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-147">Delete the character before the cursor.</span></span>

- <span data-ttu-id="1200a-148">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="1200a-148">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="1200a-149">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="1200a-149">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="1200a-150">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1200a-150">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="1200a-151">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="1200a-151">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="1200a-152">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="1200a-152">BackwardDeleteLine</span></span>

<span data-ttu-id="1200a-153">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-153">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="1200a-154">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-154">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="1200a-155">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-155">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="1200a-156">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="1200a-156">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="1200a-157">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="1200a-157">BackwardDeleteWord</span></span>

<span data-ttu-id="1200a-158">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-158">Deletes the previous word.</span></span>

- <span data-ttu-id="1200a-159">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="1200a-159">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="1200a-160">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="1200a-160">BackwardKillLine</span></span>

<span data-ttu-id="1200a-161">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-161">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="1200a-162">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-162">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1200a-163">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1200a-163">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="1200a-164">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="1200a-164">BackwardKillWord</span></span>

<span data-ttu-id="1200a-165">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-165">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1200a-166">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-166">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1200a-167">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-167">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1200a-168">CMD: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="1200a-168">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="1200a-169">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1200a-169">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="1200a-170">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1200a-170">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="1200a-171">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1200a-171">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="1200a-172">CancelLine</span><span class="sxs-lookup"><span data-stu-id="1200a-172">CancelLine</span></span>

<span data-ttu-id="1200a-173">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="1200a-173">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="1200a-174">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1200a-174">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="1200a-175">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1200a-175">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="1200a-176">Kopiera</span><span class="sxs-lookup"><span data-stu-id="1200a-176">Copy</span></span>

<span data-ttu-id="1200a-177">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1200a-177">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="1200a-178">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-178">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="1200a-179">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="1200a-179">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="1200a-180">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="1200a-180">CopyOrCancelLine</span></span>

<span data-ttu-id="1200a-181">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-181">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="1200a-182">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1200a-182">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="1200a-183">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1200a-183">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="1200a-184">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="1200a-184">Cut</span></span>

<span data-ttu-id="1200a-185">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1200a-185">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="1200a-186">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="1200a-186">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="1200a-187">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="1200a-187">DeleteChar</span></span>

<span data-ttu-id="1200a-188">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-188">Delete the character under the cursor.</span></span>

- <span data-ttu-id="1200a-189">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-189">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="1200a-190">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-190">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="1200a-191">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-191">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="1200a-192">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-192">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="1200a-193">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="1200a-193">DeleteCharOrExit</span></span>

<span data-ttu-id="1200a-194">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="1200a-194">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="1200a-195">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1200a-195">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="1200a-196">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="1200a-196">DeleteEndOfBuffer</span></span>

<span data-ttu-id="1200a-197">Tar bort till slutet av Multiline-bufferten.</span><span class="sxs-lookup"><span data-stu-id="1200a-197">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="1200a-198">Kommando läge för vi: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="1200a-198">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="1200a-199">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="1200a-199">DeleteEndOfWord</span></span>

<span data-ttu-id="1200a-200">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="1200a-200">Delete to the end of the word.</span></span>

- <span data-ttu-id="1200a-201">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="1200a-201">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="1200a-202">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="1200a-202">DeleteLine</span></span>

<span data-ttu-id="1200a-203">Tar bort den aktuella logiska raden för en buffert med flera rader och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="1200a-203">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="1200a-204">Kommando läge för vi: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="1200a-204">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="1200a-205">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="1200a-205">DeletePreviousLines</span></span>

<span data-ttu-id="1200a-206">Tar bort föregående begärda logiska rader och den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-206">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="1200a-207">Kommando läge för vi: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="1200a-207">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="1200a-208">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="1200a-208">DeleteRelativeLines</span></span>

<span data-ttu-id="1200a-209">Tar bort från buffertens början till den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-209">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="1200a-210">Som de flesta vi-kommandon `<d,g,g>` kan kommandot vara anpassningsprefix med ett numeriskt argument som anger ett absolut rad nummer, som tillsammans med det aktuella rad numret, utgör ett intervall med rader som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="1200a-210">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="1200a-211">Om inget värde anges är det numeriska argumentet standardvärdet 1, som refererar till den första logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-211">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="1200a-212">Det faktiska antalet rader som ska tas bort från flera rader beräknas som skillnaden mellan det aktuella logiska rad numret och det angivna numeriska argumentet, som därför kan vara negativt.</span><span class="sxs-lookup"><span data-stu-id="1200a-212">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="1200a-213">Därför är den _relativa_ delen av metod namnet.</span><span class="sxs-lookup"><span data-stu-id="1200a-213">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="1200a-214">Kommando läge för vi: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="1200a-214">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="1200a-215">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="1200a-215">DeleteNextLines</span></span>

<span data-ttu-id="1200a-216">Tar bort den aktuella logiska raden och nästa begärda logiska rader i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-216">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="1200a-217">Kommando läge för vi: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="1200a-217">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="1200a-218">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="1200a-218">DeleteLineToFirstChar</span></span>

<span data-ttu-id="1200a-219">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-219">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="1200a-220">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="1200a-220">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="1200a-221">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="1200a-221">DeleteToEnd</span></span>

<span data-ttu-id="1200a-222">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-222">Delete to the end of the line.</span></span>

- <span data-ttu-id="1200a-223">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="1200a-223">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="1200a-224">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="1200a-224">DeleteWord</span></span>

<span data-ttu-id="1200a-225">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-225">Delete the next word.</span></span>

- <span data-ttu-id="1200a-226">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="1200a-226">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="1200a-227">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="1200a-227">ForwardDeleteLine</span></span>

<span data-ttu-id="1200a-228">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-228">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="1200a-229">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-229">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="1200a-230">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-230">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="1200a-231">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-231">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="1200a-232">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="1200a-232">InsertLineAbove</span></span>

<span data-ttu-id="1200a-233">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-233">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="1200a-234">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-234">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="1200a-235">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-235">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="1200a-236">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="1200a-236">InsertLineBelow</span></span>

<span data-ttu-id="1200a-237">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-237">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="1200a-238">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-238">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="1200a-239">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-239">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="1200a-240">InvertCase</span><span class="sxs-lookup"><span data-stu-id="1200a-240">InvertCase</span></span>

<span data-ttu-id="1200a-241">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="1200a-241">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="1200a-242">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="1200a-242">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="1200a-243">KillLine</span><span class="sxs-lookup"><span data-stu-id="1200a-243">KillLine</span></span>

<span data-ttu-id="1200a-244">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-244">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="1200a-245">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-245">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1200a-246">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="1200a-246">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="1200a-247">KillRegion</span><span class="sxs-lookup"><span data-stu-id="1200a-247">KillRegion</span></span>

<span data-ttu-id="1200a-248">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-248">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="1200a-249">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-249">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="1200a-250">KillWord</span><span class="sxs-lookup"><span data-stu-id="1200a-250">KillWord</span></span>

<span data-ttu-id="1200a-251">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="1200a-251">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="1200a-252">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-252">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="1200a-253">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-253">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1200a-254">CMD: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-254">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="1200a-255">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="1200a-255">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="1200a-256">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-256">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="1200a-257">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1200a-257">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="1200a-258">Klistra in</span><span class="sxs-lookup"><span data-stu-id="1200a-258">Paste</span></span>

<span data-ttu-id="1200a-259">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1200a-259">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="1200a-260">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="1200a-260">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="1200a-261">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="1200a-261">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="1200a-262">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="1200a-262">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1200a-263">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1200a-263">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="1200a-264">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="1200a-264">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="1200a-265">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="1200a-265">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="1200a-266">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="1200a-266">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="1200a-267">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="1200a-267">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="1200a-268">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="1200a-268">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="1200a-269">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="1200a-269">PasteAfter</span></span>

<span data-ttu-id="1200a-270">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="1200a-270">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="1200a-271">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="1200a-271">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="1200a-272">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="1200a-272">PasteBefore</span></span>

<span data-ttu-id="1200a-273">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="1200a-273">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="1200a-274">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="1200a-274">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="1200a-275">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="1200a-275">PrependAndAccept</span></span>

<span data-ttu-id="1200a-276">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-276">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="1200a-277">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="1200a-277">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="1200a-278">Gör om</span><span class="sxs-lookup"><span data-stu-id="1200a-278">Redo</span></span>

<span data-ttu-id="1200a-279">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="1200a-279">Undo an undo.</span></span>

- <span data-ttu-id="1200a-280">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-280">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="1200a-281">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-281">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="1200a-282">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-282">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="1200a-283">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="1200a-283">RepeatLastCommand</span></span>

<span data-ttu-id="1200a-284">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-284">Repeat the last text modification.</span></span>

- <span data-ttu-id="1200a-285">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="1200a-285">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="1200a-286">RevertLine</span><span class="sxs-lookup"><span data-stu-id="1200a-286">RevertLine</span></span>

<span data-ttu-id="1200a-287">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="1200a-287">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="1200a-288">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="1200a-288">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="1200a-289">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="1200a-289">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="1200a-290">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="1200a-290">ShellBackwardKillWord</span></span>

<span data-ttu-id="1200a-291">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-291">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1200a-292">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-292">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1200a-293">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-293">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="1200a-294">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-294">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="1200a-295">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="1200a-295">ShellKillWord</span></span>

<span data-ttu-id="1200a-296">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="1200a-296">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="1200a-297">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-297">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="1200a-298">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-298">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="1200a-299">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-299">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="1200a-300">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="1200a-300">SwapCharacters</span></span>

<span data-ttu-id="1200a-301">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="1200a-301">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="1200a-302">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-302">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="1200a-303">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-303">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="1200a-304">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-304">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="1200a-305">Ångra</span><span class="sxs-lookup"><span data-stu-id="1200a-305">Undo</span></span>

<span data-ttu-id="1200a-306">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="1200a-306">Undo a previous edit.</span></span>

- <span data-ttu-id="1200a-307">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="1200a-307">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="1200a-308">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="1200a-308">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="1200a-309">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="1200a-309">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="1200a-310">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="1200a-310">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="1200a-311">UndoAll</span><span class="sxs-lookup"><span data-stu-id="1200a-311">UndoAll</span></span>

<span data-ttu-id="1200a-312">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-312">Undo all previous edits for line.</span></span>

- <span data-ttu-id="1200a-313">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="1200a-313">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="1200a-314">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="1200a-314">UnixWordRubout</span></span>

<span data-ttu-id="1200a-315">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-315">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1200a-316">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-316">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1200a-317">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-317">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1200a-318">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="1200a-318">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="1200a-319">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="1200a-319">ValidateAndAcceptLine</span></span>

<span data-ttu-id="1200a-320">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-320">Attempt to execute the current input.</span></span> <span data-ttu-id="1200a-321">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-321">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="1200a-322">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="1200a-322">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="1200a-323">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="1200a-323">ViAcceptLine</span></span>

<span data-ttu-id="1200a-324">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1200a-324">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="1200a-325">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1200a-325">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="1200a-326">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="1200a-326">ViAcceptLineOrExit</span></span>

<span data-ttu-id="1200a-327">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="1200a-327">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="1200a-328">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1200a-328">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="1200a-329">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1200a-329">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="1200a-330">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="1200a-330">ViAppendLine</span></span>

<span data-ttu-id="1200a-331">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-331">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="1200a-332">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="1200a-332">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="1200a-333">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-333">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="1200a-334">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-334">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="1200a-335">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="1200a-335">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="1200a-336">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-336">ViBackwardGlob</span></span>

<span data-ttu-id="1200a-337">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-337">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="1200a-338">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="1200a-338">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="1200a-339">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="1200a-339">ViDeleteBrace</span></span>

<span data-ttu-id="1200a-340">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="1200a-340">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="1200a-341">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="1200a-341">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="1200a-342">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-342">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="1200a-343">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="1200a-343">Delete to the end of the word.</span></span>

- <span data-ttu-id="1200a-344">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="1200a-344">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="1200a-345">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-345">ViDeleteGlob</span></span>

<span data-ttu-id="1200a-346">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="1200a-346">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="1200a-347">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="1200a-347">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="1200a-348">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="1200a-348">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="1200a-349">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1200a-349">Deletes until given character.</span></span>

- <span data-ttu-id="1200a-350">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-350">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="1200a-351">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-351">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="1200a-352">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1200a-352">Deletes until given character.</span></span>

- <span data-ttu-id="1200a-353">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="1200a-353">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="1200a-354">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="1200a-354">ViDeleteToChar</span></span>

<span data-ttu-id="1200a-355">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1200a-355">Deletes until given character.</span></span>

- <span data-ttu-id="1200a-356">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="1200a-356">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="1200a-357">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-357">ViDeleteToCharBackward</span></span>

<span data-ttu-id="1200a-358">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="1200a-358">Deletes backwards until given character.</span></span>

- <span data-ttu-id="1200a-359">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="1200a-359">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="1200a-360">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="1200a-360">ViInsertAtBegining</span></span>

<span data-ttu-id="1200a-361">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-361">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="1200a-362">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="1200a-362">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="1200a-363">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="1200a-363">ViInsertAtEnd</span></span>

<span data-ttu-id="1200a-364">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-364">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="1200a-365">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="1200a-365">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="1200a-366">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="1200a-366">ViInsertLine</span></span>

<span data-ttu-id="1200a-367">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-367">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="1200a-368">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="1200a-368">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="1200a-369">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="1200a-369">ViInsertWithAppend</span></span>

<span data-ttu-id="1200a-370">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="1200a-370">Append from the current line position.</span></span>

- <span data-ttu-id="1200a-371">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="1200a-371">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="1200a-372">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="1200a-372">ViInsertWithDelete</span></span>

<span data-ttu-id="1200a-373">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1200a-373">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="1200a-374">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="1200a-374">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="1200a-375">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="1200a-375">ViJoinLines</span></span>

<span data-ttu-id="1200a-376">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-376">Joins the current line and the next line.</span></span>

- <span data-ttu-id="1200a-377">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="1200a-377">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="1200a-378">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="1200a-378">ViReplaceLine</span></span>

<span data-ttu-id="1200a-379">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-379">Erase the entire command line.</span></span>

- <span data-ttu-id="1200a-380">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="1200a-380">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="1200a-381">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="1200a-381">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="1200a-382">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1200a-382">Replaces until given character.</span></span>

- <span data-ttu-id="1200a-383">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-383">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="1200a-384">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-384">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="1200a-385">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1200a-385">Replaces until given character.</span></span>

- <span data-ttu-id="1200a-386">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="1200a-386">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="1200a-387">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="1200a-387">ViReplaceToChar</span></span>

<span data-ttu-id="1200a-388">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1200a-388">Deletes until given character.</span></span>

- <span data-ttu-id="1200a-389">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="1200a-389">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="1200a-390">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-390">ViReplaceToCharBackward</span></span>

<span data-ttu-id="1200a-391">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1200a-391">Replaces until given character.</span></span>

- <span data-ttu-id="1200a-392">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="1200a-392">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="1200a-393">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-393">ViYankBeginningOfLine</span></span>

<span data-ttu-id="1200a-394">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-394">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="1200a-395">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="1200a-395">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="1200a-396">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-396">ViYankEndOfGlob</span></span>

<span data-ttu-id="1200a-397">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="1200a-397">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="1200a-398">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="1200a-398">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="1200a-399">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="1200a-399">ViYankEndOfWord</span></span>

<span data-ttu-id="1200a-400">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="1200a-400">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="1200a-401">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="1200a-401">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="1200a-402">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="1200a-402">ViYankLeft</span></span>

<span data-ttu-id="1200a-403">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-403">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="1200a-404">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="1200a-404">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="1200a-405">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="1200a-405">ViYankLine</span></span>

<span data-ttu-id="1200a-406">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="1200a-406">Yank the entire buffer.</span></span>

- <span data-ttu-id="1200a-407">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-407">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="1200a-408">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-408">ViYankNextGlob</span></span>

<span data-ttu-id="1200a-409">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-409">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="1200a-410">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="1200a-410">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="1200a-411">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-411">ViYankNextWord</span></span>

<span data-ttu-id="1200a-412">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-412">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="1200a-413">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="1200a-413">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="1200a-414">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="1200a-414">ViYankPercent</span></span>

<span data-ttu-id="1200a-415">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="1200a-415">Yank to/from matching brace.</span></span>

- <span data-ttu-id="1200a-416">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="1200a-416">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="1200a-417">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-417">ViYankPreviousGlob</span></span>

<span data-ttu-id="1200a-418">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-418">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="1200a-419">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="1200a-419">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="1200a-420">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="1200a-420">ViYankPreviousWord</span></span>

<span data-ttu-id="1200a-421">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-421">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="1200a-422">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="1200a-422">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="1200a-423">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="1200a-423">ViYankRight</span></span>

<span data-ttu-id="1200a-424">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-424">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="1200a-425">Kommando läge för vi: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-425">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="1200a-426">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-426">ViYankToEndOfLine</span></span>

<span data-ttu-id="1200a-427">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="1200a-427">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="1200a-428">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="1200a-428">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="1200a-429">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="1200a-429">ViYankToFirstChar</span></span>

<span data-ttu-id="1200a-430">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-430">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="1200a-431">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="1200a-431">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="1200a-432">Yank</span><span class="sxs-lookup"><span data-stu-id="1200a-432">Yank</span></span>

<span data-ttu-id="1200a-433">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-433">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="1200a-434">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-434">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="1200a-435">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="1200a-435">YankLastArg</span></span>

<span data-ttu-id="1200a-436">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-436">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="1200a-437">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="1200a-437">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="1200a-438">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="1200a-438">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="1200a-439">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="1200a-439">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="1200a-440">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="1200a-440">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="1200a-441">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="1200a-441">YankNthArg</span></span>

<span data-ttu-id="1200a-442">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-442">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="1200a-443">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="1200a-443">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="1200a-444">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-444">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="1200a-445">YankPop</span><span class="sxs-lookup"><span data-stu-id="1200a-445">YankPop</span></span>

<span data-ttu-id="1200a-446">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-446">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="1200a-447">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="1200a-447">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="1200a-448">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-448">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="1200a-449">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-449">BackwardChar</span></span>

<span data-ttu-id="1200a-450">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="1200a-450">Move the cursor one character to the left.</span></span> <span data-ttu-id="1200a-451">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-451">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="1200a-452">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-452">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="1200a-453">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="1200a-453">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="1200a-454">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-454">BackwardWord</span></span>

<span data-ttu-id="1200a-455">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-455">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1200a-456">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-456">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-457">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-457">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1200a-458">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="1200a-458">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="1200a-459">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-459">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1200a-460">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-460">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="1200a-461">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-461">BeginningOfLine</span></span>

<span data-ttu-id="1200a-462">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-462">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="1200a-463">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="1200a-463">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="1200a-464">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-464">Cmd: `<Home>`</span></span>
- <span data-ttu-id="1200a-465">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="1200a-465">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="1200a-466">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-466">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="1200a-467">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-467">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="1200a-468">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-468">EndOfLine</span></span>

<span data-ttu-id="1200a-469">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-469">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="1200a-470">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-470">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="1200a-471">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-471">Cmd: `<End>`</span></span>
- <span data-ttu-id="1200a-472">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="1200a-472">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="1200a-473">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-473">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="1200a-474">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-474">ForwardChar</span></span>

<span data-ttu-id="1200a-475">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="1200a-475">Move the cursor one character to the right.</span></span> <span data-ttu-id="1200a-476">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-476">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="1200a-477">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-477">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="1200a-478">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="1200a-478">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="1200a-479">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-479">ForwardWord</span></span>

<span data-ttu-id="1200a-480">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-480">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1200a-481">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-481">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-482">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="1200a-482">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="1200a-483">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="1200a-483">GotoBrace</span></span>

<span data-ttu-id="1200a-484">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="1200a-484">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="1200a-485">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1200a-485">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1200a-486">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1200a-486">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1200a-487">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1200a-487">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="1200a-488">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="1200a-488">GotoColumn</span></span>

<span data-ttu-id="1200a-489">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="1200a-489">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="1200a-490">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="1200a-490">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="1200a-491">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-491">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="1200a-492">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-492">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="1200a-493">Kommando läge för vi: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="1200a-493">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="1200a-494">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="1200a-494">MoveToEndOfLine</span></span>

<span data-ttu-id="1200a-495">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1200a-495">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="1200a-496">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="1200a-496">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="1200a-497">NextLine</span><span class="sxs-lookup"><span data-stu-id="1200a-497">NextLine</span></span>

<span data-ttu-id="1200a-498">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-498">Move the cursor to the next line.</span></span>

- <span data-ttu-id="1200a-499">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-499">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="1200a-500">NextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-500">NextWord</span></span>

<span data-ttu-id="1200a-501">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-501">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1200a-502">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-502">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-503">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-503">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="1200a-504">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-504">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="1200a-505">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-505">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="1200a-506">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="1200a-506">NextWordEnd</span></span>

<span data-ttu-id="1200a-507">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1200a-508">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-509">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="1200a-509">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="1200a-510">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="1200a-510">PreviousLine</span></span>

<span data-ttu-id="1200a-511">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-511">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="1200a-512">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-512">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="1200a-513">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-513">ShellBackwardWord</span></span>

<span data-ttu-id="1200a-514">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-514">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1200a-515">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1200a-515">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1200a-516">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-516">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="1200a-517">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-517">ShellForwardWord</span></span>

<span data-ttu-id="1200a-518">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1200a-519">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1200a-519">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1200a-520">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-520">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="1200a-521">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-521">ShellNextWord</span></span>

<span data-ttu-id="1200a-522">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1200a-523">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1200a-523">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1200a-524">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-524">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="1200a-525">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-525">ViBackwardChar</span></span>

<span data-ttu-id="1200a-526">Flytta markören ett steg till vänster i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="1200a-526">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="1200a-527">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-527">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="1200a-528">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-528">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="1200a-529">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="1200a-529">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="1200a-530">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-530">ViBackwardWord</span></span>

<span data-ttu-id="1200a-531">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1200a-532">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-532">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-533">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="1200a-533">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="1200a-534">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-534">ViForwardChar</span></span>

<span data-ttu-id="1200a-535">Flytta markören ett steg till höger i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="1200a-535">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="1200a-536">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1200a-536">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="1200a-537">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-537">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="1200a-538">Vi kommando läge: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="1200a-538">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="1200a-539">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-539">ViEndOfGlob</span></span>

<span data-ttu-id="1200a-540">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-540">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="1200a-541">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="1200a-541">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="1200a-542">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-542">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="1200a-543">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-543">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="1200a-544">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-544">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="1200a-545">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="1200a-545">ViGotoBrace</span></span>

<span data-ttu-id="1200a-546">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="1200a-546">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="1200a-547">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="1200a-547">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="1200a-548">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="1200a-548">ViNextGlob</span></span>

<span data-ttu-id="1200a-549">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1200a-549">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="1200a-550">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="1200a-550">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="1200a-551">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-551">ViNextWord</span></span>

<span data-ttu-id="1200a-552">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-552">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1200a-553">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-553">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1200a-554">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="1200a-554">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="1200a-555">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-555">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="1200a-556">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-556">BeginningOfHistory</span></span>

<span data-ttu-id="1200a-557">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-557">Move to the first item in the history.</span></span>

- <span data-ttu-id="1200a-558">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="1200a-558">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="1200a-559">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-559">ClearHistory</span></span>

<span data-ttu-id="1200a-560">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1200a-560">Clears history in PSReadLine.</span></span> <span data-ttu-id="1200a-561">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-561">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="1200a-562">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="1200a-562">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="1200a-563">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-563">EndOfHistory</span></span>

<span data-ttu-id="1200a-564">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-564">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="1200a-565">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="1200a-565">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="1200a-566">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-566">ForwardSearchHistory</span></span>

<span data-ttu-id="1200a-567">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-567">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="1200a-568">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1200a-568">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="1200a-569">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1200a-569">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="1200a-570">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-570">HistorySearchBackward</span></span>

<span data-ttu-id="1200a-571">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-571">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="1200a-572">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="1200a-572">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="1200a-573">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="1200a-573">HistorySearchForward</span></span>

<span data-ttu-id="1200a-574">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-574">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="1200a-575">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="1200a-575">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="1200a-576">NextHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-576">NextHistory</span></span>

<span data-ttu-id="1200a-577">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-577">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="1200a-578">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-578">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="1200a-579">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="1200a-579">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="1200a-580">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-580">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="1200a-581">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="1200a-581">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="1200a-582">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-582">PreviousHistory</span></span>

<span data-ttu-id="1200a-583">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="1200a-583">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="1200a-584">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-584">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="1200a-585">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="1200a-585">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="1200a-586">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-586">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="1200a-587">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="1200a-587">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="1200a-588">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="1200a-588">ReverseSearchHistory</span></span>

<span data-ttu-id="1200a-589">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="1200a-589">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="1200a-590">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1200a-590">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="1200a-591">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1200a-591">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="1200a-592">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-592">ViSearchHistoryBackward</span></span>

<span data-ttu-id="1200a-593">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="1200a-593">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="1200a-594">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1200a-594">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="1200a-595">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1200a-595">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="1200a-596">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="1200a-596">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="1200a-597">Klart</span><span class="sxs-lookup"><span data-stu-id="1200a-597">Complete</span></span>

<span data-ttu-id="1200a-598">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-598">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="1200a-599">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1200a-599">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="1200a-600">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1200a-600">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="1200a-601">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-601">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="1200a-602">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="1200a-602">MenuComplete</span></span>

<span data-ttu-id="1200a-603">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-603">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="1200a-604">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1200a-604">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="1200a-605">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1200a-605">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="1200a-606">CMD: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-606">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="1200a-607">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-607">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="1200a-608">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="1200a-608">PossibleCompletions</span></span>

<span data-ttu-id="1200a-609">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1200a-609">Display the list of possible completions.</span></span>

- <span data-ttu-id="1200a-610">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="1200a-610">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="1200a-611">Vi infognings läge: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-611">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="1200a-612">Kommando läge för vi: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1200a-612">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="1200a-613">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="1200a-613">TabCompleteNext</span></span>

<span data-ttu-id="1200a-614">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="1200a-614">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="1200a-615">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-615">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="1200a-616">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-616">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="1200a-617">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="1200a-617">TabCompletePrevious</span></span>

<span data-ttu-id="1200a-618">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="1200a-618">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="1200a-619">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-619">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="1200a-620">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-620">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="1200a-621">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="1200a-621">ViTabCompleteNext</span></span>

<span data-ttu-id="1200a-622">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="1200a-622">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="1200a-623">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-623">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="1200a-624">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="1200a-624">ViTabCompletePrevious</span></span>

<span data-ttu-id="1200a-625">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="1200a-625">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="1200a-626">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1200a-626">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="1200a-627">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-627">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="1200a-628">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="1200a-628">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="1200a-629">Godkänn nästa ord i det infogade eller markerade förslaget.</span><span class="sxs-lookup"><span data-stu-id="1200a-629">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="1200a-630">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-630">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="1200a-631">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="1200a-631">AcceptSuggestion</span></span>

<span data-ttu-id="1200a-632">Godkänn det aktuella infogade eller valda förslaget.</span><span class="sxs-lookup"><span data-stu-id="1200a-632">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="1200a-633">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-633">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="1200a-634">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="1200a-634">CaptureScreen</span></span>

<span data-ttu-id="1200a-635">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="1200a-635">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="1200a-636">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-636">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="1200a-637">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="1200a-637">ClearScreen</span></span>

<span data-ttu-id="1200a-638">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="1200a-638">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="1200a-639">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1200a-639">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1200a-640">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1200a-640">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1200a-641">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1200a-641">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1200a-642">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1200a-642">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="1200a-643">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="1200a-643">DigitArgument</span></span>

<span data-ttu-id="1200a-644">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="1200a-644">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="1200a-645">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="1200a-645">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="1200a-646">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="1200a-646">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="1200a-647">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="1200a-647">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="1200a-648">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="1200a-648">InvokePrompt</span></span>

<span data-ttu-id="1200a-649">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="1200a-649">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="1200a-650">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1200a-650">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="1200a-651">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-651">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="1200a-652">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="1200a-652">ScrollDisplayDown</span></span>

<span data-ttu-id="1200a-653">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="1200a-653">Scroll the display down one screen.</span></span>

- <span data-ttu-id="1200a-654">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1200a-654">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="1200a-655">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1200a-655">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="1200a-656">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="1200a-656">ScrollDisplayDownLine</span></span>

<span data-ttu-id="1200a-657">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="1200a-657">Scroll the display down one line.</span></span>

- <span data-ttu-id="1200a-658">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1200a-658">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="1200a-659">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1200a-659">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="1200a-660">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="1200a-660">ScrollDisplayToCursor</span></span>

<span data-ttu-id="1200a-661">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-661">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="1200a-662">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-662">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="1200a-663">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="1200a-663">ScrollDisplayTop</span></span>

<span data-ttu-id="1200a-664">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="1200a-664">Scroll the display to the top.</span></span>

- <span data-ttu-id="1200a-665">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-665">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="1200a-666">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="1200a-666">ScrollDisplayUp</span></span>

<span data-ttu-id="1200a-667">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="1200a-667">Scroll the display up one screen.</span></span>

- <span data-ttu-id="1200a-668">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1200a-668">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="1200a-669">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1200a-669">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="1200a-670">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="1200a-670">ScrollDisplayUpLine</span></span>

<span data-ttu-id="1200a-671">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="1200a-671">Scroll the display up one line.</span></span>

- <span data-ttu-id="1200a-672">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1200a-672">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="1200a-673">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1200a-673">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="1200a-674">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="1200a-674">SelfInsert</span></span>

<span data-ttu-id="1200a-675">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="1200a-675">Insert the key.</span></span>

- <span data-ttu-id="1200a-676">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-676">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="1200a-677">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="1200a-677">ShowKeyBindings</span></span>

<span data-ttu-id="1200a-678">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="1200a-678">Show all bound keys.</span></span>

- <span data-ttu-id="1200a-679">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1200a-679">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="1200a-680">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1200a-680">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="1200a-681">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1200a-681">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="1200a-682">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="1200a-682">ViCommandMode</span></span>

<span data-ttu-id="1200a-683">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="1200a-683">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="1200a-684">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="1200a-684">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="1200a-685">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="1200a-685">ViDigitArgumentInChord</span></span>

<span data-ttu-id="1200a-686">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="1200a-686">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="1200a-687">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-687">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="1200a-688">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="1200a-688">ViEditVisually</span></span>

<span data-ttu-id="1200a-689">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="1200a-689">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="1200a-690">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="1200a-690">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="1200a-691">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="1200a-691">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="1200a-692">ViExit</span><span class="sxs-lookup"><span data-stu-id="1200a-692">ViExit</span></span>

<span data-ttu-id="1200a-693">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1200a-693">Exits the shell.</span></span>

- <span data-ttu-id="1200a-694">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-694">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="1200a-695">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="1200a-695">ViInsertMode</span></span>

<span data-ttu-id="1200a-696">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1200a-696">Switch to Insert mode.</span></span>

- <span data-ttu-id="1200a-697">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="1200a-697">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="1200a-698">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="1200a-698">WhatIsKey</span></span>

<span data-ttu-id="1200a-699">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="1200a-699">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="1200a-700">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1200a-700">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="1200a-701">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1200a-701">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="1200a-702">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-702">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="1200a-703">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="1200a-703">ExchangePointAndMark</span></span>

<span data-ttu-id="1200a-704">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-704">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="1200a-705">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="1200a-705">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="1200a-706">SelectAll</span><span class="sxs-lookup"><span data-stu-id="1200a-706">SelectAll</span></span>

<span data-ttu-id="1200a-707">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-707">Select the entire line.</span></span>

- <span data-ttu-id="1200a-708">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="1200a-708">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="1200a-709">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-709">SelectBackwardChar</span></span>

<span data-ttu-id="1200a-710">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="1200a-710">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="1200a-711">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-711">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="1200a-712">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-712">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="1200a-713">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="1200a-713">SelectBackwardsLine</span></span>

<span data-ttu-id="1200a-714">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-714">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="1200a-715">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-715">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="1200a-716">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="1200a-716">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="1200a-717">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-717">SelectBackwardWord</span></span>

<span data-ttu-id="1200a-718">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-718">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="1200a-719">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-719">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1200a-720">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="1200a-720">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="1200a-721">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="1200a-721">SelectForwardChar</span></span>

<span data-ttu-id="1200a-722">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="1200a-722">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="1200a-723">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-723">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="1200a-724">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-724">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="1200a-725">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-725">SelectForwardWord</span></span>

<span data-ttu-id="1200a-726">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="1200a-726">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="1200a-727">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="1200a-727">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="1200a-728">SelectLine</span><span class="sxs-lookup"><span data-stu-id="1200a-728">SelectLine</span></span>

<span data-ttu-id="1200a-729">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-729">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="1200a-730">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-730">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="1200a-731">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="1200a-731">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="1200a-732">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-732">SelectNextWord</span></span>

<span data-ttu-id="1200a-733">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-733">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="1200a-734">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1200a-734">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="1200a-735">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-735">SelectShellBackwardWord</span></span>

<span data-ttu-id="1200a-736">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="1200a-736">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="1200a-737">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-737">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="1200a-738">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="1200a-738">SelectShellForwardWord</span></span>

<span data-ttu-id="1200a-739">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="1200a-739">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="1200a-740">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-740">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="1200a-741">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="1200a-741">SelectShellNextWord</span></span>

<span data-ttu-id="1200a-742">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="1200a-742">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="1200a-743">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1200a-743">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="1200a-744">SetMark</span><span class="sxs-lookup"><span data-stu-id="1200a-744">SetMark</span></span>

<span data-ttu-id="1200a-745">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="1200a-745">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="1200a-746">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="1200a-746">Emacs: `<Ctrl+@>`</span></span>

## <a name="search-functions"></a><span data-ttu-id="1200a-747">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="1200a-747">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="1200a-748">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="1200a-748">CharacterSearch</span></span>

<span data-ttu-id="1200a-749">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1200a-749">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="1200a-750">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="1200a-750">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="1200a-751">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-751">Cmd: `<F3>`</span></span>
- <span data-ttu-id="1200a-752">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1200a-752">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1200a-753">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-753">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="1200a-754">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-754">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="1200a-755">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-755">CharacterSearchBackward</span></span>

<span data-ttu-id="1200a-756">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1200a-756">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="1200a-757">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="1200a-757">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="1200a-758">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-758">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="1200a-759">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="1200a-759">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="1200a-760">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-760">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="1200a-761">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1200a-761">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="1200a-762">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="1200a-762">RepeatLastCharSearch</span></span>

<span data-ttu-id="1200a-763">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="1200a-763">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="1200a-764">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="1200a-764">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="1200a-765">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="1200a-765">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="1200a-766">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="1200a-766">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="1200a-767">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="1200a-767">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="1200a-768">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="1200a-768">RepeatSearch</span></span>

<span data-ttu-id="1200a-769">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="1200a-769">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="1200a-770">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="1200a-770">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="1200a-771">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-771">RepeatSearchBackward</span></span>

<span data-ttu-id="1200a-772">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="1200a-772">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="1200a-773">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="1200a-773">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="1200a-774">SearchChar</span><span class="sxs-lookup"><span data-stu-id="1200a-774">SearchChar</span></span>

<span data-ttu-id="1200a-775">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-775">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="1200a-776">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1200a-776">This is for 't' functionality.</span></span>

- <span data-ttu-id="1200a-777">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="1200a-777">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="1200a-778">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="1200a-778">SearchCharBackward</span></span>

<span data-ttu-id="1200a-779">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="1200a-779">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="1200a-780">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1200a-780">This is for 'T' functionality.</span></span>

- <span data-ttu-id="1200a-781">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="1200a-781">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="1200a-782">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="1200a-782">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="1200a-783">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="1200a-783">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="1200a-784">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1200a-784">This is for 'T' functionality.</span></span>

- <span data-ttu-id="1200a-785">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="1200a-785">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="1200a-786">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="1200a-786">SearchCharWithBackoff</span></span>

<span data-ttu-id="1200a-787">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1200a-787">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="1200a-788">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1200a-788">This is for 't' functionality.</span></span>

- <span data-ttu-id="1200a-789">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="1200a-789">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="1200a-790">SearchForward</span><span class="sxs-lookup"><span data-stu-id="1200a-790">SearchForward</span></span>

<span data-ttu-id="1200a-791">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="1200a-791">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="1200a-792">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1200a-792">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="1200a-793">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1200a-793">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="1200a-794">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="1200a-794">Custom Key Bindings</span></span>

<span data-ttu-id="1200a-795">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="1200a-795">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="1200a-796">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="1200a-796">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="1200a-797">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="1200a-797">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="1200a-798">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="1200a-798">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="1200a-799">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="1200a-799">Some useful examples include</span></span>

- <span data-ttu-id="1200a-800">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="1200a-800">edit the command line</span></span>
- <span data-ttu-id="1200a-801">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="1200a-801">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="1200a-802">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="1200a-802">change directories without changing the command line</span></span>

<span data-ttu-id="1200a-803">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="1200a-803">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="1200a-804">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="1200a-804">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="1200a-805">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="1200a-805">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="1200a-806">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="1200a-806">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="1200a-807">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="1200a-807">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="1200a-808">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="1200a-808">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="1200a-809">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="1200a-809">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="1200a-810">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="1200a-810">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="1200a-811">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="1200a-811">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="1200a-812">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="1200a-812">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="1200a-813">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-813">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="1200a-814">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="1200a-814">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="1200a-815">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="1200a-815">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="1200a-816">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="1200a-816">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="1200a-817">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1200a-817">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="1200a-818">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="1200a-818">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="1200a-819">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-819">Clear the kill-ring.</span></span>  <span data-ttu-id="1200a-820">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="1200a-820">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="1200a-821">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="1200a-821">Delete length characters from start.</span></span>  <span data-ttu-id="1200a-822">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1200a-822">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="1200a-823">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="1200a-823">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="1200a-824">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="1200a-824">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="1200a-825">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="1200a-825">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="1200a-826">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="1200a-826">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="1200a-827">Dessa två funktioner används av `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="1200a-827">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="1200a-828">Den första används för att hämta alla nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1200a-828">The first is used to get all key bindings.</span></span> <span data-ttu-id="1200a-829">Den andra används för att hämta vissa nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1200a-829">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="1200a-830">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1200a-830">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="1200a-831">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="1200a-831">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="1200a-832">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="1200a-832">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="1200a-833">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="1200a-833">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="1200a-834">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1200a-834">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="1200a-835">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1200a-835">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="1200a-836">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1200a-836">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="1200a-837">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1200a-837">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="1200a-838">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="1200a-838">Replace some of the input.</span></span> <span data-ttu-id="1200a-839">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1200a-839">This operation supports undo/redo.</span></span> <span data-ttu-id="1200a-840">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="1200a-840">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="1200a-841">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="1200a-841">Move the cursor to the given offset.</span></span> <span data-ttu-id="1200a-842">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="1200a-842">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="1200a-843">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="1200a-843">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="1200a-844">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="1200a-844">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="1200a-845">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="1200a-845">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="1200a-846">NOTE</span><span class="sxs-lookup"><span data-stu-id="1200a-846">NOTE</span></span>

### <a name="powershell-compatibility"></a><span data-ttu-id="1200a-847">POWERSHELL-KOMPATIBILITET</span><span class="sxs-lookup"><span data-stu-id="1200a-847">POWERSHELL COMPATIBILITY</span></span>

<span data-ttu-id="1200a-848">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="1200a-848">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="1200a-849">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1200a-849">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="1200a-850">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="1200a-850">It does work in the console of Visual Studio Code.</span></span>

### <a name="command-history"></a><span data-ttu-id="1200a-851">KOMMANDO HISTORIK</span><span class="sxs-lookup"><span data-stu-id="1200a-851">COMMAND HISTORY</span></span>

<span data-ttu-id="1200a-852">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1200a-852">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="1200a-853">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1200a-853">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="1200a-854">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="1200a-854">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="1200a-855">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="1200a-855">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="1200a-856">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="1200a-856">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="1200a-857">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="1200a-857">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="1200a-858">FEEDBACK & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1200a-858">FEEDBACK & CONTRIBUTING TO PSReadLine</span></span>

[<span data-ttu-id="1200a-859">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="1200a-859">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="1200a-860">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="1200a-860">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1200a-861">SE ÄVEN</span><span class="sxs-lookup"><span data-stu-id="1200a-861">SEE ALSO</span></span>

<span data-ttu-id="1200a-862">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="1200a-862">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>

