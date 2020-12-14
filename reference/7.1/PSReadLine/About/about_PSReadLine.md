---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
keywords: powershell
Locale: en-US
ms.date: 11/16/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.1&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 6d52bb04118914a9ccca5d3442a9d1915c1c2818
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94692283"
---
# <a name="psreadline"></a><span data-ttu-id="e6875-104">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e6875-104">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="e6875-105">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e6875-105">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="e6875-106">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6875-106">Short Description</span></span>

<span data-ttu-id="e6875-107">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e6875-107">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="e6875-108">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="e6875-108">Long Description</span></span>

<span data-ttu-id="e6875-109">PSReadLine 2,1 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="e6875-109">PSReadLine 2.1 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="e6875-110">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="e6875-110">It provides:</span></span>

- <span data-ttu-id="e6875-111">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="e6875-111">Syntax coloring of the command line</span></span>
- <span data-ttu-id="e6875-112">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="e6875-112">A visual indication of syntax errors</span></span>
- <span data-ttu-id="e6875-113">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="e6875-113">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="e6875-114">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="e6875-114">Customizable key bindings</span></span>
- <span data-ttu-id="e6875-115">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="e6875-115">Cmd and Emacs modes</span></span>
- <span data-ttu-id="e6875-116">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="e6875-116">Many configuration options</span></span>
- <span data-ttu-id="e6875-117">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="e6875-117">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="e6875-118">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="e6875-118">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="e6875-119">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="e6875-119">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="e6875-120">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e6875-120">Predictive IntelliSense</span></span>

<span data-ttu-id="e6875-121">PSReadLine kräver PowerShell 3,0 eller senare och konsol värden.</span><span class="sxs-lookup"><span data-stu-id="e6875-121">PSReadLine requires PowerShell 3.0, or newer, and the console host.</span></span> <span data-ttu-id="e6875-122">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="e6875-122">It does not work in PowerShell ISE.</span></span> <span data-ttu-id="e6875-123">Den fungerar i-konsolen i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="e6875-123">It does work in the console of Visual Studio Code.</span></span>

<span data-ttu-id="e6875-124">PSReadLine 2.1.0 levereras med PowerShell 7,1 och stöds i alla versioner av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="e6875-124">PSReadLine 2.1.0 ships with PowerShell 7.1 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="e6875-125">Den är tillgänglig för installation från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="e6875-125">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="e6875-126">Kör följande kommando för att installera PSReadLine-2.1.0 i en version av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="e6875-126">To install PSReadLine 2.1.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -RequiredVersion 2.1.0
```

> [!NOTE]
> <span data-ttu-id="e6875-127">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="e6875-127">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="e6875-128">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-128">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="e6875-129">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="e6875-129">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="e6875-130">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="e6875-130">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="e6875-131">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e6875-131">Predictive IntelliSense</span></span>

<span data-ttu-id="e6875-132">Förutsägelse IntelliSense är ett tillägg till begreppet TABB-slutförande som hjälper användaren att slutföra kommandon.</span><span class="sxs-lookup"><span data-stu-id="e6875-132">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="e6875-133">Det gör det möjligt för användare att upptäcka, redigera och köra fullständiga kommandon baserat på matchande förutsägelser från användarens historik och ytterligare domänanslutna plugin-program.</span><span class="sxs-lookup"><span data-stu-id="e6875-133">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="e6875-134">Aktivera förutsägelse IntelliSense</span><span class="sxs-lookup"><span data-stu-id="e6875-134">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="e6875-135">Förutsägelse IntelliSense är inaktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="e6875-135">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="e6875-136">Kör följande kommando för att aktivera förutsägelser:</span><span class="sxs-lookup"><span data-stu-id="e6875-136">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="e6875-137">Parametern **PredictionSource** kan också ta emot plugin-program för domän särskilda och anpassade krav.</span><span class="sxs-lookup"><span data-stu-id="e6875-137">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="e6875-138">För att inaktivera förutsägelse IntelliSense, kör du bara:</span><span class="sxs-lookup"><span data-stu-id="e6875-138">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="e6875-139">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="e6875-139">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="e6875-140">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-140">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="e6875-141">Avbryta</span><span class="sxs-lookup"><span data-stu-id="e6875-141">Abort</span></span>

<span data-ttu-id="e6875-142">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="e6875-142">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="e6875-143">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="e6875-143">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="e6875-144">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="e6875-144">AcceptAndGetNext</span></span>

<span data-ttu-id="e6875-145">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-145">Attempt to execute the current input.</span></span> <span data-ttu-id="e6875-146">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="e6875-146">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="e6875-147">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="e6875-147">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="e6875-148">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="e6875-148">AcceptLine</span></span>

<span data-ttu-id="e6875-149">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-149">Attempt to execute the current input.</span></span> <span data-ttu-id="e6875-150">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-150">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="e6875-151">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-151">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="e6875-152">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-152">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="e6875-153">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-153">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="e6875-154">AddLine</span><span class="sxs-lookup"><span data-stu-id="e6875-154">AddLine</span></span>

<span data-ttu-id="e6875-155">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-155">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="e6875-156">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="e6875-156">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="e6875-157">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-157">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e6875-158">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-158">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e6875-159">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-159">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="e6875-160">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-160">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="e6875-161">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="e6875-161">BackwardDeleteChar</span></span>

<span data-ttu-id="e6875-162">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-162">Delete the character before the cursor.</span></span>

- <span data-ttu-id="e6875-163">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="e6875-163">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="e6875-164">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="e6875-164">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="e6875-165">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e6875-165">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="e6875-166">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="e6875-166">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="e6875-167">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="e6875-167">BackwardDeleteLine</span></span>

<span data-ttu-id="e6875-168">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-168">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e6875-169">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-169">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="e6875-170">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-170">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="e6875-171">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="e6875-171">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="e6875-172">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="e6875-172">BackwardDeleteWord</span></span>

<span data-ttu-id="e6875-173">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-173">Deletes the previous word.</span></span>

- <span data-ttu-id="e6875-174">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="e6875-174">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="e6875-175">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="e6875-175">BackwardKillLine</span></span>

<span data-ttu-id="e6875-176">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-176">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="e6875-177">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-177">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e6875-178">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e6875-178">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="e6875-179">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="e6875-179">BackwardKillWord</span></span>

<span data-ttu-id="e6875-180">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-180">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e6875-181">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-181">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e6875-182">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e6875-183">CMD: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="e6875-183">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="e6875-184">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e6875-184">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="e6875-185">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e6875-185">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="e6875-186">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="e6875-186">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="e6875-187">CancelLine</span><span class="sxs-lookup"><span data-stu-id="e6875-187">CancelLine</span></span>

<span data-ttu-id="e6875-188">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="e6875-188">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="e6875-189">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e6875-189">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="e6875-190">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e6875-190">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="e6875-191">Kopiera</span><span class="sxs-lookup"><span data-stu-id="e6875-191">Copy</span></span>

<span data-ttu-id="e6875-192">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="e6875-192">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="e6875-193">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-193">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="e6875-194">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="e6875-194">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="e6875-195">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="e6875-195">CopyOrCancelLine</span></span>

<span data-ttu-id="e6875-196">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-196">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="e6875-197">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e6875-197">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="e6875-198">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="e6875-198">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="e6875-199">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="e6875-199">Cut</span></span>

<span data-ttu-id="e6875-200">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="e6875-200">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="e6875-201">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="e6875-201">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="e6875-202">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="e6875-202">DeleteChar</span></span>

<span data-ttu-id="e6875-203">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-203">Delete the character under the cursor.</span></span>

- <span data-ttu-id="e6875-204">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-204">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="e6875-205">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-205">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="e6875-206">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-206">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="e6875-207">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-207">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="e6875-208">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="e6875-208">DeleteCharOrExit</span></span>

<span data-ttu-id="e6875-209">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="e6875-209">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="e6875-210">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e6875-210">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="e6875-211">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="e6875-211">DeleteEndOfBuffer</span></span>

<span data-ttu-id="e6875-212">Tar bort till slutet av Multiline-bufferten.</span><span class="sxs-lookup"><span data-stu-id="e6875-212">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="e6875-213">Kommando läge för vi: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="e6875-213">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="e6875-214">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="e6875-214">DeleteEndOfWord</span></span>

<span data-ttu-id="e6875-215">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="e6875-215">Delete to the end of the word.</span></span>

- <span data-ttu-id="e6875-216">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="e6875-216">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="e6875-217">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="e6875-217">DeleteLine</span></span>

<span data-ttu-id="e6875-218">Tar bort den aktuella logiska raden för en buffert med flera rader och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="e6875-218">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="e6875-219">Kommando läge för vi: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="e6875-219">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="e6875-220">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="e6875-220">DeletePreviousLines</span></span>

<span data-ttu-id="e6875-221">Tar bort föregående begärda logiska rader och den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-221">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="e6875-222">Kommando läge för vi: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="e6875-222">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="e6875-223">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="e6875-223">DeleteRelativeLines</span></span>

<span data-ttu-id="e6875-224">Tar bort från buffertens början till den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-224">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="e6875-225">Som de flesta vi-kommandon `<d,g,g>` kan kommandot vara anpassningsprefix med ett numeriskt argument som anger ett absolut rad nummer, som tillsammans med det aktuella rad numret, utgör ett intervall med rader som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="e6875-225">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="e6875-226">Om inget värde anges är det numeriska argumentet standardvärdet 1, som refererar till den första logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-226">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="e6875-227">Det faktiska antalet rader som ska tas bort från flera rader beräknas som skillnaden mellan det aktuella logiska rad numret och det angivna numeriska argumentet, som därför kan vara negativt.</span><span class="sxs-lookup"><span data-stu-id="e6875-227">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="e6875-228">Därför är den _relativa_ delen av metod namnet.</span><span class="sxs-lookup"><span data-stu-id="e6875-228">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="e6875-229">Kommando läge för vi: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="e6875-229">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="e6875-230">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="e6875-230">DeleteNextLines</span></span>

<span data-ttu-id="e6875-231">Tar bort den aktuella logiska raden och nästa begärda logiska rader i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-231">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="e6875-232">Kommando läge för vi: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="e6875-232">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="e6875-233">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="e6875-233">DeleteLineToFirstChar</span></span>

<span data-ttu-id="e6875-234">Tar bort text från markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-234">Deletes text from the cursor to the first non-blank character of the line.</span></span>

- <span data-ttu-id="e6875-235">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="e6875-235">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="e6875-236">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="e6875-236">DeleteToEnd</span></span>

<span data-ttu-id="e6875-237">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-237">Delete to the end of the line.</span></span>

- <span data-ttu-id="e6875-238">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="e6875-238">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="e6875-239">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="e6875-239">DeleteWord</span></span>

<span data-ttu-id="e6875-240">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-240">Delete the next word.</span></span>

- <span data-ttu-id="e6875-241">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="e6875-241">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="e6875-242">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="e6875-242">ForwardDeleteLine</span></span>

<span data-ttu-id="e6875-243">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-243">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="e6875-244">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-244">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="e6875-245">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-245">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="e6875-246">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-246">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="e6875-247">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="e6875-247">InsertLineAbove</span></span>

<span data-ttu-id="e6875-248">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-248">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="e6875-249">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-249">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="e6875-250">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-250">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="e6875-251">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="e6875-251">InsertLineBelow</span></span>

<span data-ttu-id="e6875-252">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-252">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="e6875-253">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-253">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="e6875-254">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-254">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="e6875-255">InvertCase</span><span class="sxs-lookup"><span data-stu-id="e6875-255">InvertCase</span></span>

<span data-ttu-id="e6875-256">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="e6875-256">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="e6875-257">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="e6875-257">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="e6875-258">KillLine</span><span class="sxs-lookup"><span data-stu-id="e6875-258">KillLine</span></span>

<span data-ttu-id="e6875-259">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-259">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="e6875-260">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-260">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e6875-261">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="e6875-261">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="e6875-262">KillRegion</span><span class="sxs-lookup"><span data-stu-id="e6875-262">KillRegion</span></span>

<span data-ttu-id="e6875-263">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-263">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="e6875-264">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-264">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="e6875-265">KillWord</span><span class="sxs-lookup"><span data-stu-id="e6875-265">KillWord</span></span>

<span data-ttu-id="e6875-266">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="e6875-266">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="e6875-267">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-267">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="e6875-268">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-268">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e6875-269">CMD: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-269">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="e6875-270">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="e6875-270">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="e6875-271">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-271">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="e6875-272">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="e6875-272">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="e6875-273">Klistra in</span><span class="sxs-lookup"><span data-stu-id="e6875-273">Paste</span></span>

<span data-ttu-id="e6875-274">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="e6875-274">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="e6875-275">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="e6875-275">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="e6875-276">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="e6875-276">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="e6875-277">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="e6875-277">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="e6875-278">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e6875-278">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="e6875-279">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="e6875-279">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="e6875-280">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="e6875-280">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="e6875-281">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="e6875-281">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="e6875-282">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="e6875-282">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="e6875-283">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="e6875-283">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="e6875-284">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="e6875-284">PasteAfter</span></span>

<span data-ttu-id="e6875-285">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="e6875-285">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="e6875-286">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="e6875-286">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="e6875-287">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="e6875-287">PasteBefore</span></span>

<span data-ttu-id="e6875-288">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="e6875-288">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="e6875-289">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="e6875-289">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="e6875-290">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="e6875-290">PrependAndAccept</span></span>

<span data-ttu-id="e6875-291">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-291">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="e6875-292">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="e6875-292">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="e6875-293">Gör om</span><span class="sxs-lookup"><span data-stu-id="e6875-293">Redo</span></span>

<span data-ttu-id="e6875-294">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="e6875-294">Undo an undo.</span></span>

- <span data-ttu-id="e6875-295">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-295">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="e6875-296">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-296">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="e6875-297">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-297">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="e6875-298">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="e6875-298">RepeatLastCommand</span></span>

<span data-ttu-id="e6875-299">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-299">Repeat the last text modification.</span></span>

- <span data-ttu-id="e6875-300">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="e6875-300">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="e6875-301">RevertLine</span><span class="sxs-lookup"><span data-stu-id="e6875-301">RevertLine</span></span>

<span data-ttu-id="e6875-302">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="e6875-302">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="e6875-303">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="e6875-303">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="e6875-304">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="e6875-304">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="e6875-305">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="e6875-305">ShellBackwardKillWord</span></span>

<span data-ttu-id="e6875-306">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-306">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e6875-307">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-307">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e6875-308">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-308">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="e6875-309">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-309">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="e6875-310">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="e6875-310">ShellKillWord</span></span>

<span data-ttu-id="e6875-311">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="e6875-311">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="e6875-312">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-312">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="e6875-313">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-313">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="e6875-314">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-314">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="e6875-315">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="e6875-315">SwapCharacters</span></span>

<span data-ttu-id="e6875-316">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="e6875-316">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="e6875-317">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-317">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="e6875-318">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-318">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="e6875-319">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-319">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="e6875-320">Ångra</span><span class="sxs-lookup"><span data-stu-id="e6875-320">Undo</span></span>

<span data-ttu-id="e6875-321">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="e6875-321">Undo a previous edit.</span></span>

- <span data-ttu-id="e6875-322">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="e6875-322">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="e6875-323">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="e6875-323">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="e6875-324">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="e6875-324">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="e6875-325">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="e6875-325">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="e6875-326">UndoAll</span><span class="sxs-lookup"><span data-stu-id="e6875-326">UndoAll</span></span>

<span data-ttu-id="e6875-327">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-327">Undo all previous edits for line.</span></span>

- <span data-ttu-id="e6875-328">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="e6875-328">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="e6875-329">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="e6875-329">UnixWordRubout</span></span>

<span data-ttu-id="e6875-330">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-330">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="e6875-331">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-331">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="e6875-332">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-332">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="e6875-333">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="e6875-333">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="e6875-334">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="e6875-334">ValidateAndAcceptLine</span></span>

<span data-ttu-id="e6875-335">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-335">Attempt to execute the current input.</span></span> <span data-ttu-id="e6875-336">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-336">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="e6875-337">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="e6875-337">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="e6875-338">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="e6875-338">ViAcceptLine</span></span>

<span data-ttu-id="e6875-339">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="e6875-339">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="e6875-340">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="e6875-340">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="e6875-341">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="e6875-341">ViAcceptLineOrExit</span></span>

<span data-ttu-id="e6875-342">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="e6875-342">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="e6875-343">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e6875-343">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="e6875-344">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="e6875-344">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="e6875-345">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="e6875-345">ViAppendLine</span></span>

<span data-ttu-id="e6875-346">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-346">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="e6875-347">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="e6875-347">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="e6875-348">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-348">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="e6875-349">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-349">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="e6875-350">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="e6875-350">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="e6875-351">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-351">ViBackwardGlob</span></span>

<span data-ttu-id="e6875-352">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-352">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="e6875-353">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="e6875-353">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="e6875-354">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="e6875-354">ViDeleteBrace</span></span>

<span data-ttu-id="e6875-355">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="e6875-355">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="e6875-356">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="e6875-356">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="e6875-357">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-357">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="e6875-358">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="e6875-358">Delete to the end of the word.</span></span>

- <span data-ttu-id="e6875-359">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="e6875-359">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="e6875-360">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-360">ViDeleteGlob</span></span>

<span data-ttu-id="e6875-361">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="e6875-361">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="e6875-362">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="e6875-362">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="e6875-363">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="e6875-363">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="e6875-364">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="e6875-364">Deletes until given character.</span></span>

- <span data-ttu-id="e6875-365">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-365">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="e6875-366">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-366">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="e6875-367">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="e6875-367">Deletes until given character.</span></span>

- <span data-ttu-id="e6875-368">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="e6875-368">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="e6875-369">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="e6875-369">ViDeleteToChar</span></span>

<span data-ttu-id="e6875-370">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="e6875-370">Deletes until given character.</span></span>

- <span data-ttu-id="e6875-371">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="e6875-371">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="e6875-372">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-372">ViDeleteToCharBackward</span></span>

<span data-ttu-id="e6875-373">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="e6875-373">Deletes backwards until given character.</span></span>

- <span data-ttu-id="e6875-374">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="e6875-374">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="e6875-375">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="e6875-375">ViInsertAtBegining</span></span>

<span data-ttu-id="e6875-376">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-376">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="e6875-377">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="e6875-377">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="e6875-378">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="e6875-378">ViInsertAtEnd</span></span>

<span data-ttu-id="e6875-379">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-379">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="e6875-380">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="e6875-380">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="e6875-381">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="e6875-381">ViInsertLine</span></span>

<span data-ttu-id="e6875-382">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-382">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="e6875-383">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="e6875-383">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="e6875-384">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="e6875-384">ViInsertWithAppend</span></span>

<span data-ttu-id="e6875-385">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="e6875-385">Append from the current line position.</span></span>

- <span data-ttu-id="e6875-386">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="e6875-386">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="e6875-387">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="e6875-387">ViInsertWithDelete</span></span>

<span data-ttu-id="e6875-388">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="e6875-388">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="e6875-389">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="e6875-389">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="e6875-390">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="e6875-390">ViJoinLines</span></span>

<span data-ttu-id="e6875-391">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-391">Joins the current line and the next line.</span></span>

- <span data-ttu-id="e6875-392">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="e6875-392">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="e6875-393">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="e6875-393">ViReplaceLine</span></span>

<span data-ttu-id="e6875-394">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-394">Erase the entire command line.</span></span>

- <span data-ttu-id="e6875-395">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="e6875-395">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="e6875-396">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="e6875-396">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="e6875-397">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="e6875-397">Replaces until given character.</span></span>

- <span data-ttu-id="e6875-398">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-398">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="e6875-399">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-399">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="e6875-400">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="e6875-400">Replaces until given character.</span></span>

- <span data-ttu-id="e6875-401">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="e6875-401">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="e6875-402">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="e6875-402">ViReplaceToChar</span></span>

<span data-ttu-id="e6875-403">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="e6875-403">Deletes until given character.</span></span>

- <span data-ttu-id="e6875-404">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="e6875-404">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="e6875-405">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-405">ViReplaceToCharBackward</span></span>

<span data-ttu-id="e6875-406">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="e6875-406">Replaces until given character.</span></span>

- <span data-ttu-id="e6875-407">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="e6875-407">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="e6875-408">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-408">ViYankBeginningOfLine</span></span>

<span data-ttu-id="e6875-409">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-409">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="e6875-410">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="e6875-410">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="e6875-411">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-411">ViYankEndOfGlob</span></span>

<span data-ttu-id="e6875-412">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="e6875-412">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="e6875-413">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="e6875-413">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="e6875-414">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="e6875-414">ViYankEndOfWord</span></span>

<span data-ttu-id="e6875-415">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="e6875-415">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="e6875-416">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="e6875-416">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="e6875-417">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="e6875-417">ViYankLeft</span></span>

<span data-ttu-id="e6875-418">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-418">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="e6875-419">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="e6875-419">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="e6875-420">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="e6875-420">ViYankLine</span></span>

<span data-ttu-id="e6875-421">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="e6875-421">Yank the entire buffer.</span></span>

- <span data-ttu-id="e6875-422">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-422">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="e6875-423">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-423">ViYankNextGlob</span></span>

<span data-ttu-id="e6875-424">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-424">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="e6875-425">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="e6875-425">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="e6875-426">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-426">ViYankNextWord</span></span>

<span data-ttu-id="e6875-427">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-427">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="e6875-428">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="e6875-428">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="e6875-429">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="e6875-429">ViYankPercent</span></span>

<span data-ttu-id="e6875-430">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="e6875-430">Yank to/from matching brace.</span></span>

- <span data-ttu-id="e6875-431">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="e6875-431">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="e6875-432">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-432">ViYankPreviousGlob</span></span>

<span data-ttu-id="e6875-433">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-433">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="e6875-434">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="e6875-434">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="e6875-435">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="e6875-435">ViYankPreviousWord</span></span>

<span data-ttu-id="e6875-436">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-436">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="e6875-437">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="e6875-437">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="e6875-438">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="e6875-438">ViYankRight</span></span>

<span data-ttu-id="e6875-439">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-439">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="e6875-440">Kommando läge för vi: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-440">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="e6875-441">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-441">ViYankToEndOfLine</span></span>

<span data-ttu-id="e6875-442">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="e6875-442">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="e6875-443">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="e6875-443">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="e6875-444">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="e6875-444">ViYankToFirstChar</span></span>

<span data-ttu-id="e6875-445">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-445">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="e6875-446">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="e6875-446">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="e6875-447">Yank</span><span class="sxs-lookup"><span data-stu-id="e6875-447">Yank</span></span>

<span data-ttu-id="e6875-448">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-448">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="e6875-449">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-449">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="e6875-450">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="e6875-450">YankLastArg</span></span>

<span data-ttu-id="e6875-451">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-451">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="e6875-452">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="e6875-452">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="e6875-453">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="e6875-453">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="e6875-454">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="e6875-454">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="e6875-455">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="e6875-455">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="e6875-456">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="e6875-456">YankNthArg</span></span>

<span data-ttu-id="e6875-457">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-457">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="e6875-458">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="e6875-458">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="e6875-459">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-459">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="e6875-460">YankPop</span><span class="sxs-lookup"><span data-stu-id="e6875-460">YankPop</span></span>

<span data-ttu-id="e6875-461">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-461">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="e6875-462">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="e6875-462">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="e6875-463">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-463">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="e6875-464">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-464">BackwardChar</span></span>

<span data-ttu-id="e6875-465">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="e6875-465">Move the cursor one character to the left.</span></span> <span data-ttu-id="e6875-466">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-466">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="e6875-467">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-467">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="e6875-468">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="e6875-468">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="e6875-469">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-469">BackwardWord</span></span>

<span data-ttu-id="e6875-470">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-470">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e6875-471">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-471">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-472">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-472">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e6875-473">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="e6875-473">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="e6875-474">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-474">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e6875-475">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-475">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="e6875-476">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-476">BeginningOfLine</span></span>

<span data-ttu-id="e6875-477">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-477">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="e6875-478">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="e6875-478">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="e6875-479">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-479">Cmd: `<Home>`</span></span>
- <span data-ttu-id="e6875-480">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="e6875-480">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="e6875-481">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-481">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="e6875-482">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-482">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="e6875-483">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-483">EndOfLine</span></span>

<span data-ttu-id="e6875-484">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-484">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="e6875-485">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-485">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="e6875-486">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-486">Cmd: `<End>`</span></span>
- <span data-ttu-id="e6875-487">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="e6875-487">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="e6875-488">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-488">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="e6875-489">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-489">ForwardChar</span></span>

<span data-ttu-id="e6875-490">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="e6875-490">Move the cursor one character to the right.</span></span> <span data-ttu-id="e6875-491">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-491">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="e6875-492">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-492">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="e6875-493">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="e6875-493">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="e6875-494">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-494">ForwardWord</span></span>

<span data-ttu-id="e6875-495">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-495">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e6875-496">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-496">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-497">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="e6875-497">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="e6875-498">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="e6875-498">GotoBrace</span></span>

<span data-ttu-id="e6875-499">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="e6875-499">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="e6875-500">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e6875-500">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e6875-501">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e6875-501">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e6875-502">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e6875-502">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="e6875-503">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="e6875-503">GotoColumn</span></span>

<span data-ttu-id="e6875-504">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="e6875-504">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="e6875-505">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="e6875-505">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="e6875-506">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-506">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="e6875-507">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-507">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="e6875-508">Kommando läge för vi: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="e6875-508">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="e6875-509">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="e6875-509">MoveToEndOfLine</span></span>

<span data-ttu-id="e6875-510">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="e6875-510">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="e6875-511">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="e6875-511">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="e6875-512">NextLine</span><span class="sxs-lookup"><span data-stu-id="e6875-512">NextLine</span></span>

<span data-ttu-id="e6875-513">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-513">Move the cursor to the next line.</span></span>

- <span data-ttu-id="e6875-514">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-514">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="e6875-515">NextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-515">NextWord</span></span>

<span data-ttu-id="e6875-516">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-516">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e6875-517">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-517">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-518">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-518">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="e6875-519">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-519">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="e6875-520">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-520">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="e6875-521">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="e6875-521">NextWordEnd</span></span>

<span data-ttu-id="e6875-522">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-522">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e6875-523">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-523">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-524">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="e6875-524">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="e6875-525">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="e6875-525">PreviousLine</span></span>

<span data-ttu-id="e6875-526">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-526">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="e6875-527">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-527">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="e6875-528">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-528">ShellBackwardWord</span></span>

<span data-ttu-id="e6875-529">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-529">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e6875-530">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="e6875-530">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e6875-531">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-531">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="e6875-532">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-532">ShellForwardWord</span></span>

<span data-ttu-id="e6875-533">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-533">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e6875-534">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="e6875-534">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e6875-535">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-535">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="e6875-536">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-536">ShellNextWord</span></span>

<span data-ttu-id="e6875-537">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-537">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="e6875-538">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="e6875-538">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="e6875-539">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-539">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="e6875-540">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-540">ViBackwardChar</span></span>

<span data-ttu-id="e6875-541">Flytta markören ett steg till vänster i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="e6875-541">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="e6875-542">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-542">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="e6875-543">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-543">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="e6875-544">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="e6875-544">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="e6875-545">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-545">ViBackwardWord</span></span>

<span data-ttu-id="e6875-546">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-546">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="e6875-547">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-547">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-548">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="e6875-548">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="e6875-549">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-549">ViForwardChar</span></span>

<span data-ttu-id="e6875-550">Flytta markören ett steg till höger i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="e6875-550">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="e6875-551">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="e6875-551">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="e6875-552">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-552">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="e6875-553">Vi kommando läge: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="e6875-553">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="e6875-554">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-554">ViEndOfGlob</span></span>

<span data-ttu-id="e6875-555">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-555">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="e6875-556">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="e6875-556">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="e6875-557">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-557">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="e6875-558">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-558">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="e6875-559">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-559">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="e6875-560">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="e6875-560">ViGotoBrace</span></span>

<span data-ttu-id="e6875-561">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="e6875-561">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="e6875-562">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="e6875-562">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="e6875-563">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="e6875-563">ViNextGlob</span></span>

<span data-ttu-id="e6875-564">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="e6875-564">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="e6875-565">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="e6875-565">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="e6875-566">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-566">ViNextWord</span></span>

<span data-ttu-id="e6875-567">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-567">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="e6875-568">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-568">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="e6875-569">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="e6875-569">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="e6875-570">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-570">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="e6875-571">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-571">BeginningOfHistory</span></span>

<span data-ttu-id="e6875-572">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-572">Move to the first item in the history.</span></span>

- <span data-ttu-id="e6875-573">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="e6875-573">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="e6875-574">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-574">ClearHistory</span></span>

<span data-ttu-id="e6875-575">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e6875-575">Clears history in PSReadLine.</span></span> <span data-ttu-id="e6875-576">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-576">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="e6875-577">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="e6875-577">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="e6875-578">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-578">EndOfHistory</span></span>

<span data-ttu-id="e6875-579">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-579">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="e6875-580">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="e6875-580">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="e6875-581">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-581">ForwardSearchHistory</span></span>

<span data-ttu-id="e6875-582">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-582">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="e6875-583">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e6875-583">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="e6875-584">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e6875-584">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="e6875-585">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-585">HistorySearchBackward</span></span>

<span data-ttu-id="e6875-586">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-586">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="e6875-587">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="e6875-587">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="e6875-588">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="e6875-588">HistorySearchForward</span></span>

<span data-ttu-id="e6875-589">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-589">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="e6875-590">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="e6875-590">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="e6875-591">NextHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-591">NextHistory</span></span>

<span data-ttu-id="e6875-592">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-592">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="e6875-593">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-593">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="e6875-594">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="e6875-594">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="e6875-595">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-595">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="e6875-596">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="e6875-596">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="e6875-597">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-597">PreviousHistory</span></span>

<span data-ttu-id="e6875-598">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="e6875-598">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="e6875-599">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-599">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="e6875-600">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="e6875-600">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="e6875-601">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-601">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="e6875-602">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="e6875-602">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="e6875-603">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="e6875-603">ReverseSearchHistory</span></span>

<span data-ttu-id="e6875-604">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="e6875-604">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="e6875-605">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e6875-605">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="e6875-606">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e6875-606">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="e6875-607">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-607">ViSearchHistoryBackward</span></span>

<span data-ttu-id="e6875-608">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="e6875-608">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="e6875-609">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e6875-609">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="e6875-610">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="e6875-610">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="e6875-611">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="e6875-611">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="e6875-612">Klart</span><span class="sxs-lookup"><span data-stu-id="e6875-612">Complete</span></span>

<span data-ttu-id="e6875-613">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-613">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="e6875-614">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="e6875-614">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="e6875-615">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="e6875-615">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="e6875-616">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-616">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="e6875-617">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="e6875-617">MenuComplete</span></span>

<span data-ttu-id="e6875-618">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-618">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="e6875-619">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="e6875-619">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="e6875-620">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="e6875-620">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="e6875-621">CMD: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-621">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="e6875-622">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-622">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="e6875-623">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="e6875-623">PossibleCompletions</span></span>

<span data-ttu-id="e6875-624">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="e6875-624">Display the list of possible completions.</span></span>

- <span data-ttu-id="e6875-625">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="e6875-625">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="e6875-626">Vi infognings läge: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-626">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="e6875-627">Kommando läge för vi: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="e6875-627">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="e6875-628">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="e6875-628">TabCompleteNext</span></span>

<span data-ttu-id="e6875-629">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="e6875-629">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="e6875-630">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-630">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="e6875-631">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-631">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="e6875-632">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="e6875-632">TabCompletePrevious</span></span>

<span data-ttu-id="e6875-633">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="e6875-633">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="e6875-634">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-634">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="e6875-635">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-635">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="e6875-636">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="e6875-636">ViTabCompleteNext</span></span>

<span data-ttu-id="e6875-637">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="e6875-637">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="e6875-638">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-638">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="e6875-639">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="e6875-639">ViTabCompletePrevious</span></span>

<span data-ttu-id="e6875-640">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="e6875-640">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="e6875-641">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="e6875-641">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="e6875-642">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-642">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="e6875-643">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="e6875-643">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="e6875-644">Godkänn nästa ord i det infogade eller markerade förslaget.</span><span class="sxs-lookup"><span data-stu-id="e6875-644">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="e6875-645">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-645">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="e6875-646">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="e6875-646">AcceptSuggestion</span></span>

<span data-ttu-id="e6875-647">Godkänn det aktuella infogade eller valda förslaget.</span><span class="sxs-lookup"><span data-stu-id="e6875-647">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="e6875-648">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-648">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="e6875-649">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="e6875-649">CaptureScreen</span></span>

<span data-ttu-id="e6875-650">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="e6875-650">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="e6875-651">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-651">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="e6875-652">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="e6875-652">ClearScreen</span></span>

<span data-ttu-id="e6875-653">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="e6875-653">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="e6875-654">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e6875-654">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e6875-655">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e6875-655">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e6875-656">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e6875-656">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="e6875-657">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="e6875-657">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="e6875-658">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="e6875-658">DigitArgument</span></span>

<span data-ttu-id="e6875-659">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-659">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="e6875-660">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="e6875-660">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="e6875-661">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="e6875-661">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="e6875-662">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="e6875-662">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="e6875-663">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="e6875-663">InvokePrompt</span></span>

<span data-ttu-id="e6875-664">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="e6875-664">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="e6875-665">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="e6875-665">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="e6875-666">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-666">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="e6875-667">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="e6875-667">ScrollDisplayDown</span></span>

<span data-ttu-id="e6875-668">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="e6875-668">Scroll the display down one screen.</span></span>

- <span data-ttu-id="e6875-669">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e6875-669">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="e6875-670">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e6875-670">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="e6875-671">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="e6875-671">ScrollDisplayDownLine</span></span>

<span data-ttu-id="e6875-672">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="e6875-672">Scroll the display down one line.</span></span>

- <span data-ttu-id="e6875-673">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e6875-673">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="e6875-674">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="e6875-674">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="e6875-675">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="e6875-675">ScrollDisplayToCursor</span></span>

<span data-ttu-id="e6875-676">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-676">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="e6875-677">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-677">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="e6875-678">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="e6875-678">ScrollDisplayTop</span></span>

<span data-ttu-id="e6875-679">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="e6875-679">Scroll the display to the top.</span></span>

- <span data-ttu-id="e6875-680">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-680">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="e6875-681">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="e6875-681">ScrollDisplayUp</span></span>

<span data-ttu-id="e6875-682">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="e6875-682">Scroll the display up one screen.</span></span>

- <span data-ttu-id="e6875-683">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e6875-683">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="e6875-684">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e6875-684">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="e6875-685">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="e6875-685">ScrollDisplayUpLine</span></span>

<span data-ttu-id="e6875-686">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="e6875-686">Scroll the display up one line.</span></span>

- <span data-ttu-id="e6875-687">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e6875-687">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="e6875-688">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="e6875-688">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="e6875-689">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="e6875-689">SelfInsert</span></span>

<span data-ttu-id="e6875-690">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="e6875-690">Insert the key.</span></span>

- <span data-ttu-id="e6875-691">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-691">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="e6875-692">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="e6875-692">ShowKeyBindings</span></span>

<span data-ttu-id="e6875-693">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="e6875-693">Show all bound keys.</span></span>

- <span data-ttu-id="e6875-694">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e6875-694">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="e6875-695">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e6875-695">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="e6875-696">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e6875-696">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="e6875-697">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="e6875-697">ViCommandMode</span></span>

<span data-ttu-id="e6875-698">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="e6875-698">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="e6875-699">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="e6875-699">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="e6875-700">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="e6875-700">ViDigitArgumentInChord</span></span>

<span data-ttu-id="e6875-701">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="e6875-701">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="e6875-702">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-702">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="e6875-703">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="e6875-703">ViEditVisually</span></span>

<span data-ttu-id="e6875-704">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="e6875-704">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="e6875-705">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="e6875-705">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="e6875-706">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="e6875-706">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="e6875-707">ViExit</span><span class="sxs-lookup"><span data-stu-id="e6875-707">ViExit</span></span>

<span data-ttu-id="e6875-708">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="e6875-708">Exits the shell.</span></span>

- <span data-ttu-id="e6875-709">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-709">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="e6875-710">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="e6875-710">ViInsertMode</span></span>

<span data-ttu-id="e6875-711">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="e6875-711">Switch to Insert mode.</span></span>

- <span data-ttu-id="e6875-712">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="e6875-712">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="e6875-713">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="e6875-713">WhatIsKey</span></span>

<span data-ttu-id="e6875-714">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="e6875-714">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="e6875-715">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e6875-715">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="e6875-716">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="e6875-716">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="e6875-717">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-717">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="e6875-718">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="e6875-718">ExchangePointAndMark</span></span>

<span data-ttu-id="e6875-719">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-719">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="e6875-720">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="e6875-720">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="e6875-721">SelectAll</span><span class="sxs-lookup"><span data-stu-id="e6875-721">SelectAll</span></span>

<span data-ttu-id="e6875-722">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-722">Select the entire line.</span></span>

- <span data-ttu-id="e6875-723">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="e6875-723">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="e6875-724">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-724">SelectBackwardChar</span></span>

<span data-ttu-id="e6875-725">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="e6875-725">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="e6875-726">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-726">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="e6875-727">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-727">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="e6875-728">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="e6875-728">SelectBackwardsLine</span></span>

<span data-ttu-id="e6875-729">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-729">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="e6875-730">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-730">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="e6875-731">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="e6875-731">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="e6875-732">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-732">SelectBackwardWord</span></span>

<span data-ttu-id="e6875-733">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-733">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="e6875-734">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-734">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="e6875-735">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="e6875-735">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="e6875-736">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="e6875-736">SelectForwardChar</span></span>

<span data-ttu-id="e6875-737">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="e6875-737">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="e6875-738">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-738">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="e6875-739">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-739">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="e6875-740">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-740">SelectForwardWord</span></span>

<span data-ttu-id="e6875-741">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="e6875-741">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="e6875-742">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="e6875-742">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="e6875-743">SelectLine</span><span class="sxs-lookup"><span data-stu-id="e6875-743">SelectLine</span></span>

<span data-ttu-id="e6875-744">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-744">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="e6875-745">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-745">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="e6875-746">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="e6875-746">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="e6875-747">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-747">SelectNextWord</span></span>

<span data-ttu-id="e6875-748">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-748">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="e6875-749">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="e6875-749">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="e6875-750">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-750">SelectShellBackwardWord</span></span>

<span data-ttu-id="e6875-751">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="e6875-751">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="e6875-752">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-752">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="e6875-753">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="e6875-753">SelectShellForwardWord</span></span>

<span data-ttu-id="e6875-754">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="e6875-754">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="e6875-755">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-755">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="e6875-756">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="e6875-756">SelectShellNextWord</span></span>

<span data-ttu-id="e6875-757">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="e6875-757">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="e6875-758">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="e6875-758">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="e6875-759">SetMark</span><span class="sxs-lookup"><span data-stu-id="e6875-759">SetMark</span></span>

<span data-ttu-id="e6875-760">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="e6875-760">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="e6875-761">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="e6875-761">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="e6875-762">Förutsägande IntelliSense-funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-762">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="e6875-763">Förutsägelse IntelliSense måste aktive ras för att använda dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-763">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="e6875-764">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="e6875-764">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="e6875-765">Accepterar nästa ord i det infogade förslaget från förutsägande IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="e6875-765">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="e6875-766">Den här funktionen kan bindas till <kbd>CTRL</kbd> + <kbd>F</kbd> genom att köra följande kommando.</span><span class="sxs-lookup"><span data-stu-id="e6875-766">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="e6875-767">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="e6875-767">AcceptSuggestion</span></span>

<span data-ttu-id="e6875-768">Accepterar det aktuella infogade förslaget från förutsägande IntelliSense genom att trycka på <kbd>RightArrow</kbd> när markören är i slutet av den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-768">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="e6875-769">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="e6875-769">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="e6875-770">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="e6875-770">CharacterSearch</span></span>

<span data-ttu-id="e6875-771">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="e6875-771">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="e6875-772">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="e6875-772">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="e6875-773">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-773">Cmd: `<F3>`</span></span>
- <span data-ttu-id="e6875-774">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="e6875-774">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="e6875-775">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-775">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="e6875-776">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-776">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="e6875-777">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-777">CharacterSearchBackward</span></span>

<span data-ttu-id="e6875-778">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="e6875-778">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="e6875-779">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="e6875-779">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="e6875-780">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-780">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="e6875-781">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="e6875-781">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="e6875-782">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-782">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="e6875-783">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="e6875-783">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="e6875-784">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="e6875-784">RepeatLastCharSearch</span></span>

<span data-ttu-id="e6875-785">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="e6875-785">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="e6875-786">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="e6875-786">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="e6875-787">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="e6875-787">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="e6875-788">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="e6875-788">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="e6875-789">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="e6875-789">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="e6875-790">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="e6875-790">RepeatSearch</span></span>

<span data-ttu-id="e6875-791">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="e6875-791">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="e6875-792">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="e6875-792">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="e6875-793">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-793">RepeatSearchBackward</span></span>

<span data-ttu-id="e6875-794">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="e6875-794">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="e6875-795">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="e6875-795">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="e6875-796">SearchChar</span><span class="sxs-lookup"><span data-stu-id="e6875-796">SearchChar</span></span>

<span data-ttu-id="e6875-797">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-797">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="e6875-798">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-798">This is for 't' functionality.</span></span>

- <span data-ttu-id="e6875-799">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="e6875-799">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="e6875-800">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="e6875-800">SearchCharBackward</span></span>

<span data-ttu-id="e6875-801">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="e6875-801">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="e6875-802">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-802">This is for 'T' functionality.</span></span>

- <span data-ttu-id="e6875-803">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="e6875-803">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="e6875-804">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="e6875-804">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="e6875-805">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="e6875-805">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="e6875-806">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-806">This is for 'T' functionality.</span></span>

- <span data-ttu-id="e6875-807">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="e6875-807">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="e6875-808">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="e6875-808">SearchCharWithBackoff</span></span>

<span data-ttu-id="e6875-809">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="e6875-809">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="e6875-810">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="e6875-810">This is for 't' functionality.</span></span>

- <span data-ttu-id="e6875-811">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="e6875-811">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="e6875-812">SearchForward</span><span class="sxs-lookup"><span data-stu-id="e6875-812">SearchForward</span></span>

<span data-ttu-id="e6875-813">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="e6875-813">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="e6875-814">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e6875-814">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="e6875-815">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="e6875-815">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="e6875-816">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="e6875-816">Custom Key Bindings</span></span>

<span data-ttu-id="e6875-817">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="e6875-817">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="e6875-818">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="e6875-818">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="e6875-819">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="e6875-819">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="e6875-820">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="e6875-820">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="e6875-821">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="e6875-821">Some useful examples include</span></span>

- <span data-ttu-id="e6875-822">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="e6875-822">edit the command line</span></span>
- <span data-ttu-id="e6875-823">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="e6875-823">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="e6875-824">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="e6875-824">change directories without changing the command line</span></span>

<span data-ttu-id="e6875-825">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="e6875-825">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="e6875-826">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="e6875-826">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="e6875-827">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="e6875-827">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="e6875-828">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="e6875-828">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="e6875-829">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="e6875-829">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="e6875-830">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="e6875-830">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="e6875-831">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="e6875-831">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="e6875-832">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="e6875-832">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="e6875-833">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="e6875-833">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="e6875-834">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="e6875-834">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="e6875-835">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-835">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="e6875-836">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="e6875-836">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="e6875-837">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="e6875-837">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="e6875-838">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="e6875-838">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="e6875-839">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="e6875-839">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="e6875-840">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="e6875-840">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="e6875-841">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-841">Clear the kill-ring.</span></span>  <span data-ttu-id="e6875-842">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="e6875-842">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="e6875-843">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="e6875-843">Delete length characters from start.</span></span>  <span data-ttu-id="e6875-844">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="e6875-844">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="e6875-845">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="e6875-845">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="e6875-846">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="e6875-846">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="e6875-847">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="e6875-847">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="e6875-848">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="e6875-848">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="e6875-849">Dessa två funktioner används av `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="e6875-849">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="e6875-850">Den första används för att hämta alla nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="e6875-850">The first is used to get all key bindings.</span></span> <span data-ttu-id="e6875-851">Den andra används för att hämta vissa nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="e6875-851">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="e6875-852">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="e6875-852">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="e6875-853">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="e6875-853">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="e6875-854">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="e6875-854">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="e6875-855">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="e6875-855">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="e6875-856">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="e6875-856">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="e6875-857">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="e6875-857">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="e6875-858">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="e6875-858">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="e6875-859">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="e6875-859">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="e6875-860">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="e6875-860">Replace some of the input.</span></span> <span data-ttu-id="e6875-861">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="e6875-861">This operation supports undo/redo.</span></span> <span data-ttu-id="e6875-862">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="e6875-862">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="e6875-863">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="e6875-863">Move the cursor to the given offset.</span></span> <span data-ttu-id="e6875-864">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="e6875-864">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="e6875-865">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="e6875-865">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="e6875-866">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="e6875-866">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="e6875-867">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="e6875-867">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="note"></a><span data-ttu-id="e6875-868">Anteckning</span><span class="sxs-lookup"><span data-stu-id="e6875-868">Note</span></span>

### <a name="command-history"></a><span data-ttu-id="e6875-869">Kommando historik</span><span class="sxs-lookup"><span data-stu-id="e6875-869">Command History</span></span>

<span data-ttu-id="e6875-870">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="e6875-870">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="e6875-871">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="e6875-871">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="e6875-872">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="e6875-872">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="e6875-873">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="e6875-873">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="e6875-874">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="e6875-874">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="e6875-875">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="e6875-875">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="e6875-876">Feedback & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="e6875-876">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="e6875-877">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="e6875-877">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="e6875-878">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="e6875-878">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="e6875-879">Se även</span><span class="sxs-lookup"><span data-stu-id="e6875-879">See Also</span></span>

<span data-ttu-id="e6875-880">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="e6875-880">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
