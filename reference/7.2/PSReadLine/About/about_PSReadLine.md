---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: ddc88dda3514e4279b6d91b023e26da88f645af7
ms.sourcegitcommit: 1dfd5554b70c7e8f4e3df19e29c384a9c0a4b227
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/03/2021
ms.locfileid: "101685218"
---
# <a name="psreadline"></a><span data-ttu-id="b2a25-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="b2a25-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="b2a25-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="b2a25-105">Short Description</span></span>

<span data-ttu-id="b2a25-106">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="b2a25-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="b2a25-107">Long Description</span></span>

<span data-ttu-id="b2a25-108">PSReadLine 2,2 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="b2a25-109">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="b2a25-109">It provides:</span></span>

- <span data-ttu-id="b2a25-110">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="b2a25-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="b2a25-111">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="b2a25-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="b2a25-112">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="b2a25-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="b2a25-113">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="b2a25-113">Customizable key bindings</span></span>
- <span data-ttu-id="b2a25-114">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="b2a25-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="b2a25-115">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="b2a25-115">Many configuration options</span></span>
- <span data-ttu-id="b2a25-116">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="b2a25-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="b2a25-117">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="b2a25-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="b2a25-118">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="b2a25-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="b2a25-119">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="b2a25-119">Predictive IntelliSense</span></span>

<span data-ttu-id="b2a25-120">PSReadLine 2.2.0 har lagt till två nya förutsägande IntelliSense-funktioner:</span><span class="sxs-lookup"><span data-stu-id="b2a25-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="b2a25-121">Parametern **PredictionViewStyle** har lagts till för att det nya ska kunna väljas `ListView` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="b2a25-122">Anslutna PSReadLine till `CommandPrediction` API: erna introducerade i PS 7,1 för att tillåta en användare att importera en förutsägbar modul som kan återge förslag från en anpassad källa.</span><span class="sxs-lookup"><span data-stu-id="b2a25-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="b2a25-123">PSReadLine kräver PowerShell 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="b2a25-124">PSReadLine fungerar med standard konsol värden, Visual Studio Code och Window Terminal.</span><span class="sxs-lookup"><span data-stu-id="b2a25-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="b2a25-125">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="b2a25-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="b2a25-126">PSReadLine 2.2.0 levereras med PowerShell 7,2 och stöds i alla versioner av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="b2a25-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="b2a25-127">Den är tillgänglig för installation från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="b2a25-128">Kör följande kommando för att installera PSReadLine-2.2.0 i en version av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="b2a25-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="b2a25-129">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="b2a25-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="b2a25-130">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="b2a25-131">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="b2a25-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="b2a25-132">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="b2a25-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="b2a25-133">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="b2a25-133">Predictive IntelliSense</span></span>

<span data-ttu-id="b2a25-134">Förutsägelse IntelliSense är ett tillägg till begreppet TABB-slutförande som hjälper användaren att slutföra kommandon.</span><span class="sxs-lookup"><span data-stu-id="b2a25-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="b2a25-135">Det gör det möjligt för användare att upptäcka, redigera och köra fullständiga kommandon baserat på matchande förutsägelser från användarens historik och ytterligare domänanslutna plugin-program.</span><span class="sxs-lookup"><span data-stu-id="b2a25-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="b2a25-136">Aktivera förutsägelse IntelliSense</span><span class="sxs-lookup"><span data-stu-id="b2a25-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="b2a25-137">Förutsägelse IntelliSense är inaktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="b2a25-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="b2a25-138">Kör följande kommando för att aktivera förutsägelser:</span><span class="sxs-lookup"><span data-stu-id="b2a25-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="b2a25-139">Parametern **PredictionSource** kan också ta emot plugin-program för domän särskilda och anpassade krav.</span><span class="sxs-lookup"><span data-stu-id="b2a25-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="b2a25-140">För att inaktivera förutsägelse IntelliSense, kör du bara:</span><span class="sxs-lookup"><span data-stu-id="b2a25-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="b2a25-141">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="b2a25-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="b2a25-142">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="b2a25-143">Avbryta</span><span class="sxs-lookup"><span data-stu-id="b2a25-143">Abort</span></span>

<span data-ttu-id="b2a25-144">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="b2a25-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="b2a25-145">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="b2a25-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="b2a25-146">AcceptAndGetNext</span></span>

<span data-ttu-id="b2a25-147">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-147">Attempt to execute the current input.</span></span> <span data-ttu-id="b2a25-148">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="b2a25-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="b2a25-149">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="b2a25-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-150">AcceptLine</span></span>

<span data-ttu-id="b2a25-151">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-151">Attempt to execute the current input.</span></span> <span data-ttu-id="b2a25-152">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b2a25-153">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="b2a25-154">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="b2a25-155">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="b2a25-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-156">AddLine</span></span>

<span data-ttu-id="b2a25-157">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="b2a25-158">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="b2a25-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="b2a25-159">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b2a25-160">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b2a25-161">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="b2a25-162">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="b2a25-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-163">BackwardDeleteChar</span></span>

<span data-ttu-id="b2a25-164">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="b2a25-165">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b2a25-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="b2a25-167">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="b2a25-168">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteinput"></a><span data-ttu-id="b2a25-169">BackwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="b2a25-169">BackwardDeleteInput</span></span>

<span data-ttu-id="b2a25-170">Som BackwardKillInput – tar bort text från punkten till början av indatamängden, men den borttagna texten tas inte med i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-170">Like BackwardKillInput - deletes text from the point to the start of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-171">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b2a25-172">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="b2a25-173">Kommando läge för vi: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="b2a25-174">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-174">BackwardDeleteLine</span></span>

<span data-ttu-id="b2a25-175">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-175">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-176">Kommando läge för vi: `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-176">Vi command mode: `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="b2a25-177">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-177">BackwardDeleteWord</span></span>

<span data-ttu-id="b2a25-178">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-178">Deletes the previous word.</span></span>

- <span data-ttu-id="b2a25-179">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-179">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillinput"></a><span data-ttu-id="b2a25-180">BackwardKillInput</span><span class="sxs-lookup"><span data-stu-id="b2a25-180">BackwardKillInput</span></span>

<span data-ttu-id="b2a25-181">Ta bort texten från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-181">Clear the text from the start of the input to the cursor.</span></span> <span data-ttu-id="b2a25-182">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-182">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-183">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-183">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="b2a25-184">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-184">BackwardKillLine</span></span>

<span data-ttu-id="b2a25-185">Ta bort texten från början av den aktuella logiska linjen till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-185">Clear the text from the start of the current logical line to the cursor.</span></span> <span data-ttu-id="b2a25-186">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-186">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-187">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-187">Function is unbound.</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="b2a25-188">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-188">BackwardKillWord</span></span>

<span data-ttu-id="b2a25-189">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-189">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b2a25-190">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-190">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b2a25-191">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-191">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-192">CMD: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-192">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="b2a25-193">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-193">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="b2a25-194">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-194">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="b2a25-195">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-195">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="b2a25-196">CancelLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-196">CancelLine</span></span>

<span data-ttu-id="b2a25-197">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-197">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="b2a25-198">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-198">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b2a25-199">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-199">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="b2a25-200">Kopiera</span><span class="sxs-lookup"><span data-stu-id="b2a25-200">Copy</span></span>

<span data-ttu-id="b2a25-201">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-201">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="b2a25-202">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-202">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="b2a25-203">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-203">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="b2a25-204">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-204">CopyOrCancelLine</span></span>

<span data-ttu-id="b2a25-205">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-205">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="b2a25-206">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-206">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="b2a25-207">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-207">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="b2a25-208">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="b2a25-208">Cut</span></span>

<span data-ttu-id="b2a25-209">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-209">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="b2a25-210">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-210">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="b2a25-211">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-211">DeleteChar</span></span>

<span data-ttu-id="b2a25-212">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-212">Delete the character under the cursor.</span></span>

- <span data-ttu-id="b2a25-213">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-213">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="b2a25-214">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-214">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="b2a25-215">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-215">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="b2a25-216">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-216">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="b2a25-217">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="b2a25-217">DeleteCharOrExit</span></span>

<span data-ttu-id="b2a25-218">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-218">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="b2a25-219">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-219">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="b2a25-220">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="b2a25-220">DeleteEndOfBuffer</span></span>

<span data-ttu-id="b2a25-221">Tar bort till slutet av Multiline-bufferten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-221">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="b2a25-222">Kommando läge för vi: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-222">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="b2a25-223">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-223">DeleteEndOfWord</span></span>

<span data-ttu-id="b2a25-224">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-224">Delete to the end of the word.</span></span>

- <span data-ttu-id="b2a25-225">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-225">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="b2a25-226">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-226">DeleteLine</span></span>

<span data-ttu-id="b2a25-227">Tar bort den aktuella logiska raden för en buffert med flera rader och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="b2a25-227">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="b2a25-228">Kommando läge för vi: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-228">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="b2a25-229">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="b2a25-229">DeletePreviousLines</span></span>

<span data-ttu-id="b2a25-230">Tar bort föregående begärda logiska rader och den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-230">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="b2a25-231">Kommando läge för vi: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-231">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="b2a25-232">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="b2a25-232">DeleteRelativeLines</span></span>

<span data-ttu-id="b2a25-233">Tar bort från buffertens början till den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-233">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="b2a25-234">Som de flesta vi-kommandon `<d,g,g>` kan kommandot vara anpassningsprefix med ett numeriskt argument som anger ett absolut rad nummer, som tillsammans med det aktuella rad numret, utgör ett intervall med rader som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="b2a25-234">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="b2a25-235">Om inget värde anges är det numeriska argumentet standardvärdet 1, som refererar till den första logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-235">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="b2a25-236">Det faktiska antalet rader som ska tas bort från flera rader beräknas som skillnaden mellan det aktuella logiska rad numret och det angivna numeriska argumentet, som därför kan vara negativt.</span><span class="sxs-lookup"><span data-stu-id="b2a25-236">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="b2a25-237">Därför är den _relativa_ delen av metod namnet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-237">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="b2a25-238">Kommando läge för vi: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-238">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="b2a25-239">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="b2a25-239">DeleteNextLines</span></span>

<span data-ttu-id="b2a25-240">Tar bort den aktuella logiska raden och nästa begärda logiska rader i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-240">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="b2a25-241">Kommando läge för vi: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-241">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="b2a25-242">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-242">DeleteLineToFirstChar</span></span>

<span data-ttu-id="b2a25-243">Tar bort från det första icke-tomma tecken i den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-243">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="b2a25-244">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-244">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="b2a25-245">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="b2a25-245">DeleteToEnd</span></span>

<span data-ttu-id="b2a25-246">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-246">Delete to the end of the line.</span></span>

- <span data-ttu-id="b2a25-247">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-247">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="b2a25-248">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-248">DeleteWord</span></span>

<span data-ttu-id="b2a25-249">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-249">Delete the next word.</span></span>

- <span data-ttu-id="b2a25-250">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-250">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteinput"></a><span data-ttu-id="b2a25-251">ForwardDeleteInput</span><span class="sxs-lookup"><span data-stu-id="b2a25-251">ForwardDeleteInput</span></span>

<span data-ttu-id="b2a25-252">Som KillLine – tar bort text från punkten till slutet av indatamängden, men den borttagna texten tas inte med i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-252">Like KillLine - deletes text from the point to the end of the input, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-253">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-253">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b2a25-254">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-254">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="b2a25-255">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-255">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="b2a25-256">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-256">ForwardDeleteLine</span></span>

<span data-ttu-id="b2a25-257">Tar bort text från punkten till slutet av den aktuella logiska linjen, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-257">Deletes text from the point to the end of the current logical line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-258">Funktionen är obunden</span><span class="sxs-lookup"><span data-stu-id="b2a25-258">Function is unbound</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="b2a25-259">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="b2a25-259">InsertLineAbove</span></span>

<span data-ttu-id="b2a25-260">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-260">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b2a25-261">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-261">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b2a25-262">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-262">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="b2a25-263">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="b2a25-263">InsertLineBelow</span></span>

<span data-ttu-id="b2a25-264">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-264">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="b2a25-265">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-265">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="b2a25-266">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-266">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="b2a25-267">InvertCase</span><span class="sxs-lookup"><span data-stu-id="b2a25-267">InvertCase</span></span>

<span data-ttu-id="b2a25-268">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="b2a25-268">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="b2a25-269">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-269">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="b2a25-270">KillLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-270">KillLine</span></span>

<span data-ttu-id="b2a25-271">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-271">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="b2a25-272">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-272">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-273">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-273">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="b2a25-274">KillRegion</span><span class="sxs-lookup"><span data-stu-id="b2a25-274">KillRegion</span></span>

<span data-ttu-id="b2a25-275">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-275">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="b2a25-276">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-276">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="b2a25-277">KillWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-277">KillWord</span></span>

<span data-ttu-id="b2a25-278">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-278">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b2a25-279">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-279">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b2a25-280">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-280">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-281">CMD: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-281">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b2a25-282">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-282">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="b2a25-283">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-283">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="b2a25-284">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-284">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="b2a25-285">Klistra in</span><span class="sxs-lookup"><span data-stu-id="b2a25-285">Paste</span></span>

<span data-ttu-id="b2a25-286">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-286">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="b2a25-287">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-287">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="b2a25-288">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-288">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="b2a25-289">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-289">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="b2a25-290">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b2a25-290">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="b2a25-291">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="b2a25-291">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="b2a25-292">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="b2a25-292">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="b2a25-293">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="b2a25-293">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="b2a25-294">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="b2a25-294">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="b2a25-295">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-295">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="b2a25-296">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="b2a25-296">PasteAfter</span></span>

<span data-ttu-id="b2a25-297">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-297">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b2a25-298">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-298">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="b2a25-299">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="b2a25-299">PasteBefore</span></span>

<span data-ttu-id="b2a25-300">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-300">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="b2a25-301">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-301">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="b2a25-302">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="b2a25-302">PrependAndAccept</span></span>

<span data-ttu-id="b2a25-303">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-303">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="b2a25-304">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-304">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="b2a25-305">Gör om</span><span class="sxs-lookup"><span data-stu-id="b2a25-305">Redo</span></span>

<span data-ttu-id="b2a25-306">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="b2a25-306">Undo an undo.</span></span>

- <span data-ttu-id="b2a25-307">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-307">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b2a25-308">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-308">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="b2a25-309">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-309">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="b2a25-310">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="b2a25-310">RepeatLastCommand</span></span>

<span data-ttu-id="b2a25-311">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-311">Repeat the last text modification.</span></span>

- <span data-ttu-id="b2a25-312">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-312">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="b2a25-313">RevertLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-313">RevertLine</span></span>

<span data-ttu-id="b2a25-314">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="b2a25-314">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="b2a25-315">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-315">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="b2a25-316">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-316">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="b2a25-317">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-317">ShellBackwardKillWord</span></span>

<span data-ttu-id="b2a25-318">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-318">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b2a25-319">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-319">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b2a25-320">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-320">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b2a25-321">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-321">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="b2a25-322">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-322">ShellKillWord</span></span>

<span data-ttu-id="b2a25-323">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-323">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="b2a25-324">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-324">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="b2a25-325">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-325">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="b2a25-326">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-326">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="b2a25-327">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="b2a25-327">SwapCharacters</span></span>

<span data-ttu-id="b2a25-328">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="b2a25-328">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="b2a25-329">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-329">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b2a25-330">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-330">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="b2a25-331">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-331">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="b2a25-332">Ångra</span><span class="sxs-lookup"><span data-stu-id="b2a25-332">Undo</span></span>

<span data-ttu-id="b2a25-333">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="b2a25-333">Undo a previous edit.</span></span>

- <span data-ttu-id="b2a25-334">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-334">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b2a25-335">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-335">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="b2a25-336">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-336">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="b2a25-337">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-337">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="b2a25-338">UndoAll</span><span class="sxs-lookup"><span data-stu-id="b2a25-338">UndoAll</span></span>

<span data-ttu-id="b2a25-339">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-339">Undo all previous edits for line.</span></span>

- <span data-ttu-id="b2a25-340">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-340">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="b2a25-341">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="b2a25-341">UnixWordRubout</span></span>

<span data-ttu-id="b2a25-342">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-342">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="b2a25-343">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-343">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="b2a25-344">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-344">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="b2a25-345">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-345">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="b2a25-346">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-346">ValidateAndAcceptLine</span></span>

<span data-ttu-id="b2a25-347">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-347">Attempt to execute the current input.</span></span> <span data-ttu-id="b2a25-348">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-348">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="b2a25-349">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-349">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="b2a25-350">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-350">ViAcceptLine</span></span>

<span data-ttu-id="b2a25-351">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="b2a25-351">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="b2a25-352">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-352">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="b2a25-353">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="b2a25-353">ViAcceptLineOrExit</span></span>

<span data-ttu-id="b2a25-354">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="b2a25-354">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="b2a25-355">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-355">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="b2a25-356">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-356">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="b2a25-357">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-357">ViAppendLine</span></span>

<span data-ttu-id="b2a25-358">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-358">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="b2a25-359">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-359">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="b2a25-360">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-360">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="b2a25-361">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-361">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="b2a25-362">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-362">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="b2a25-363">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-363">ViBackwardGlob</span></span>

<span data-ttu-id="b2a25-364">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-364">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b2a25-365">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-365">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="b2a25-366">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="b2a25-366">ViDeleteBrace</span></span>

<span data-ttu-id="b2a25-367">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-367">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="b2a25-368">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-368">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="b2a25-369">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-369">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="b2a25-370">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-370">Delete to the end of the word.</span></span>

- <span data-ttu-id="b2a25-371">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-371">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="b2a25-372">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-372">ViDeleteGlob</span></span>

<span data-ttu-id="b2a25-373">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="b2a25-373">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="b2a25-374">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-374">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="b2a25-375">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-375">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="b2a25-376">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-376">Deletes until given character.</span></span>

- <span data-ttu-id="b2a25-377">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-377">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="b2a25-378">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-378">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="b2a25-379">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-379">Deletes until given character.</span></span>

- <span data-ttu-id="b2a25-380">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-380">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="b2a25-381">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-381">ViDeleteToChar</span></span>

<span data-ttu-id="b2a25-382">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-382">Deletes until given character.</span></span>

- <span data-ttu-id="b2a25-383">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-383">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="b2a25-384">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-384">ViDeleteToCharBackward</span></span>

<span data-ttu-id="b2a25-385">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="b2a25-385">Deletes backwards until given character.</span></span>

- <span data-ttu-id="b2a25-386">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-386">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="b2a25-387">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="b2a25-387">ViInsertAtBegining</span></span>

<span data-ttu-id="b2a25-388">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-388">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="b2a25-389">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-389">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="b2a25-390">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="b2a25-390">ViInsertAtEnd</span></span>

<span data-ttu-id="b2a25-391">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-391">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="b2a25-392">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-392">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="b2a25-393">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-393">ViInsertLine</span></span>

<span data-ttu-id="b2a25-394">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-394">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="b2a25-395">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-395">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="b2a25-396">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="b2a25-396">ViInsertWithAppend</span></span>

<span data-ttu-id="b2a25-397">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-397">Append from the current line position.</span></span>

- <span data-ttu-id="b2a25-398">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-398">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="b2a25-399">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="b2a25-399">ViInsertWithDelete</span></span>

<span data-ttu-id="b2a25-400">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="b2a25-400">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="b2a25-401">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-401">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="b2a25-402">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="b2a25-402">ViJoinLines</span></span>

<span data-ttu-id="b2a25-403">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-403">Joins the current line and the next line.</span></span>

- <span data-ttu-id="b2a25-404">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-404">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="b2a25-405">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-405">ViReplaceLine</span></span>

<span data-ttu-id="b2a25-406">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-406">Erase the entire command line.</span></span>

- <span data-ttu-id="b2a25-407">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-407">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="b2a25-408">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-408">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="b2a25-409">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-409">Replaces until given character.</span></span>

- <span data-ttu-id="b2a25-410">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-410">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="b2a25-411">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-411">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="b2a25-412">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-412">Replaces until given character.</span></span>

- <span data-ttu-id="b2a25-413">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-413">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="b2a25-414">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-414">ViReplaceToChar</span></span>

<span data-ttu-id="b2a25-415">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-415">Deletes until given character.</span></span>

- <span data-ttu-id="b2a25-416">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-416">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="b2a25-417">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-417">ViReplaceToCharBackward</span></span>

<span data-ttu-id="b2a25-418">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-418">Replaces until given character.</span></span>

- <span data-ttu-id="b2a25-419">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-419">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="b2a25-420">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-420">ViYankBeginningOfLine</span></span>

<span data-ttu-id="b2a25-421">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-421">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="b2a25-422">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-422">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="b2a25-423">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-423">ViYankEndOfGlob</span></span>

<span data-ttu-id="b2a25-424">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-424">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="b2a25-425">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-425">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="b2a25-426">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-426">ViYankEndOfWord</span></span>

<span data-ttu-id="b2a25-427">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-427">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="b2a25-428">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-428">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="b2a25-429">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="b2a25-429">ViYankLeft</span></span>

<span data-ttu-id="b2a25-430">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-430">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="b2a25-431">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-431">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="b2a25-432">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-432">ViYankLine</span></span>

<span data-ttu-id="b2a25-433">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-433">Yank the entire buffer.</span></span>

- <span data-ttu-id="b2a25-434">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-434">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="b2a25-435">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-435">ViYankNextGlob</span></span>

<span data-ttu-id="b2a25-436">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-436">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="b2a25-437">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-437">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="b2a25-438">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-438">ViYankNextWord</span></span>

<span data-ttu-id="b2a25-439">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-439">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="b2a25-440">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-440">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="b2a25-441">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="b2a25-441">ViYankPercent</span></span>

<span data-ttu-id="b2a25-442">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="b2a25-442">Yank to/from matching brace.</span></span>

- <span data-ttu-id="b2a25-443">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-443">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="b2a25-444">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-444">ViYankPreviousGlob</span></span>

<span data-ttu-id="b2a25-445">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-445">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="b2a25-446">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-446">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="b2a25-447">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-447">ViYankPreviousWord</span></span>

<span data-ttu-id="b2a25-448">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-448">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="b2a25-449">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-449">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="b2a25-450">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="b2a25-450">ViYankRight</span></span>

<span data-ttu-id="b2a25-451">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-451">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="b2a25-452">Kommando läge för vi: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-452">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="b2a25-453">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-453">ViYankToEndOfLine</span></span>

<span data-ttu-id="b2a25-454">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-454">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="b2a25-455">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-455">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="b2a25-456">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-456">ViYankToFirstChar</span></span>

<span data-ttu-id="b2a25-457">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-457">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="b2a25-458">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-458">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="b2a25-459">Yank</span><span class="sxs-lookup"><span data-stu-id="b2a25-459">Yank</span></span>

<span data-ttu-id="b2a25-460">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-460">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="b2a25-461">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-461">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="b2a25-462">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="b2a25-462">YankLastArg</span></span>

<span data-ttu-id="b2a25-463">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-463">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="b2a25-464">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-464">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="b2a25-465">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="b2a25-465">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="b2a25-466">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-466">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="b2a25-467">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-467">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="b2a25-468">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="b2a25-468">YankNthArg</span></span>

<span data-ttu-id="b2a25-469">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-469">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="b2a25-470">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-470">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="b2a25-471">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-471">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="b2a25-472">YankPop</span><span class="sxs-lookup"><span data-stu-id="b2a25-472">YankPop</span></span>

<span data-ttu-id="b2a25-473">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-473">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="b2a25-474">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-474">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="b2a25-475">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-475">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="b2a25-476">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-476">BackwardChar</span></span>

<span data-ttu-id="b2a25-477">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="b2a25-477">Move the cursor one character to the left.</span></span> <span data-ttu-id="b2a25-478">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-478">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b2a25-479">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-479">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-480">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-480">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="b2a25-481">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-481">BackwardWord</span></span>

<span data-ttu-id="b2a25-482">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-482">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b2a25-483">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-483">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-484">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-484">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-485">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-485">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="b2a25-486">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-486">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-487">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-487">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="b2a25-488">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-488">BeginningOfLine</span></span>

<span data-ttu-id="b2a25-489">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-489">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="b2a25-490">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-490">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="b2a25-491">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-491">Cmd: `<Home>`</span></span>
- <span data-ttu-id="b2a25-492">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-492">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="b2a25-493">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-493">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="b2a25-494">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-494">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="b2a25-495">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-495">EndOfLine</span></span>

<span data-ttu-id="b2a25-496">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-496">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="b2a25-497">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-497">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="b2a25-498">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-498">Cmd: `<End>`</span></span>
- <span data-ttu-id="b2a25-499">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-499">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="b2a25-500">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-500">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="b2a25-501">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-501">ForwardChar</span></span>

<span data-ttu-id="b2a25-502">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="b2a25-502">Move the cursor one character to the right.</span></span> <span data-ttu-id="b2a25-503">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-503">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b2a25-504">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-504">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="b2a25-505">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-505">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="b2a25-506">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-506">ForwardWord</span></span>

<span data-ttu-id="b2a25-507">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-507">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b2a25-508">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-508">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-509">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-509">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="b2a25-510">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="b2a25-510">GotoBrace</span></span>

<span data-ttu-id="b2a25-511">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-511">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="b2a25-512">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-512">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b2a25-513">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-513">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b2a25-514">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-514">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="b2a25-515">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="b2a25-515">GotoColumn</span></span>

<span data-ttu-id="b2a25-516">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="b2a25-516">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="b2a25-517">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-517">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="b2a25-518">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-518">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="b2a25-519">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-519">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="b2a25-520">Kommando läge för vi: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-520">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="b2a25-521">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-521">MoveToEndOfLine</span></span>

<span data-ttu-id="b2a25-522">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-522">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="b2a25-523">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-523">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="b2a25-524">NextLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-524">NextLine</span></span>

<span data-ttu-id="b2a25-525">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-525">Move the cursor to the next line.</span></span>

- <span data-ttu-id="b2a25-526">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-526">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="b2a25-527">NextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-527">NextWord</span></span>

<span data-ttu-id="b2a25-528">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-528">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b2a25-529">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-529">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-530">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-530">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b2a25-531">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-531">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="b2a25-532">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-532">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="b2a25-533">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="b2a25-533">NextWordEnd</span></span>

<span data-ttu-id="b2a25-534">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-534">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b2a25-535">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-535">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-536">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-536">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="b2a25-537">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-537">PreviousLine</span></span>

<span data-ttu-id="b2a25-538">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-538">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="b2a25-539">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-539">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="b2a25-540">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-540">ShellBackwardWord</span></span>

<span data-ttu-id="b2a25-541">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-541">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b2a25-542">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="b2a25-542">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b2a25-543">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-543">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="b2a25-544">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-544">ShellForwardWord</span></span>

<span data-ttu-id="b2a25-545">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-545">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b2a25-546">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="b2a25-546">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b2a25-547">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-547">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="b2a25-548">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-548">ShellNextWord</span></span>

<span data-ttu-id="b2a25-549">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-549">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="b2a25-550">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="b2a25-550">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="b2a25-551">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-551">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="b2a25-552">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-552">ViBackwardChar</span></span>

<span data-ttu-id="b2a25-553">Flytta markören ett steg till vänster i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="b2a25-553">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="b2a25-554">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-554">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="b2a25-555">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-555">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-556">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-556">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="b2a25-557">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-557">ViBackwardWord</span></span>

<span data-ttu-id="b2a25-558">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-558">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="b2a25-559">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-559">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-560">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-560">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="b2a25-561">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-561">ViForwardChar</span></span>

<span data-ttu-id="b2a25-562">Flytta markören ett steg till höger i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="b2a25-562">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="b2a25-563">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="b2a25-563">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="b2a25-564">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-564">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="b2a25-565">Vi kommando läge: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-565">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="b2a25-566">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-566">ViEndOfGlob</span></span>

<span data-ttu-id="b2a25-567">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-567">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="b2a25-568">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-568">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="b2a25-569">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-569">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="b2a25-570">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-570">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b2a25-571">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-571">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="b2a25-572">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="b2a25-572">ViGotoBrace</span></span>

<span data-ttu-id="b2a25-573">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="b2a25-573">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="b2a25-574">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-574">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="b2a25-575">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="b2a25-575">ViNextGlob</span></span>

<span data-ttu-id="b2a25-576">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-576">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="b2a25-577">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-577">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="b2a25-578">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-578">ViNextWord</span></span>

<span data-ttu-id="b2a25-579">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-579">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="b2a25-580">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-580">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="b2a25-581">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-581">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="b2a25-582">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-582">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="b2a25-583">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-583">BeginningOfHistory</span></span>

<span data-ttu-id="b2a25-584">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-584">Move to the first item in the history.</span></span>

- <span data-ttu-id="b2a25-585">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-585">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="b2a25-586">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-586">ClearHistory</span></span>

<span data-ttu-id="b2a25-587">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b2a25-587">Clears history in PSReadLine.</span></span> <span data-ttu-id="b2a25-588">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-588">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="b2a25-589">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-589">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="b2a25-590">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-590">EndOfHistory</span></span>

<span data-ttu-id="b2a25-591">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-591">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="b2a25-592">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-592">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="b2a25-593">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-593">ForwardSearchHistory</span></span>

<span data-ttu-id="b2a25-594">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-594">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="b2a25-595">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-595">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b2a25-596">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-596">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="b2a25-597">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-597">HistorySearchBackward</span></span>

<span data-ttu-id="b2a25-598">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-598">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b2a25-599">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-599">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="b2a25-600">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="b2a25-600">HistorySearchForward</span></span>

<span data-ttu-id="b2a25-601">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-601">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="b2a25-602">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-602">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="b2a25-603">NextHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-603">NextHistory</span></span>

<span data-ttu-id="b2a25-604">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-604">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="b2a25-605">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-605">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="b2a25-606">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-606">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="b2a25-607">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-607">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="b2a25-608">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-608">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="b2a25-609">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-609">PreviousHistory</span></span>

<span data-ttu-id="b2a25-610">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="b2a25-610">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="b2a25-611">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-611">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="b2a25-612">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-612">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="b2a25-613">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-613">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="b2a25-614">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="b2a25-614">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="b2a25-615">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="b2a25-615">ReverseSearchHistory</span></span>

<span data-ttu-id="b2a25-616">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-616">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="b2a25-617">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-617">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b2a25-618">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-618">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="b2a25-619">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-619">ViSearchHistoryBackward</span></span>

<span data-ttu-id="b2a25-620">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b2a25-620">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b2a25-621">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-621">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="b2a25-622">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-622">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="b2a25-623">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="b2a25-623">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="b2a25-624">Klart</span><span class="sxs-lookup"><span data-stu-id="b2a25-624">Complete</span></span>

<span data-ttu-id="b2a25-625">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-625">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b2a25-626">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="b2a25-626">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b2a25-627">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="b2a25-627">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b2a25-628">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-628">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="b2a25-629">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="b2a25-629">MenuComplete</span></span>

<span data-ttu-id="b2a25-630">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-630">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="b2a25-631">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="b2a25-631">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="b2a25-632">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="b2a25-632">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="b2a25-633">CMD: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-633">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b2a25-634">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-634">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="b2a25-635">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="b2a25-635">PossibleCompletions</span></span>

<span data-ttu-id="b2a25-636">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="b2a25-636">Display the list of possible completions.</span></span>

- <span data-ttu-id="b2a25-637">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-637">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="b2a25-638">Vi infognings läge: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-638">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="b2a25-639">Kommando läge för vi: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-639">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="b2a25-640">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b2a25-640">TabCompleteNext</span></span>

<span data-ttu-id="b2a25-641">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="b2a25-641">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="b2a25-642">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-642">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="b2a25-643">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-643">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="b2a25-644">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b2a25-644">TabCompletePrevious</span></span>

<span data-ttu-id="b2a25-645">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="b2a25-645">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="b2a25-646">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-646">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="b2a25-647">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-647">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="b2a25-648">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="b2a25-648">ViTabCompleteNext</span></span>

<span data-ttu-id="b2a25-649">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="b2a25-649">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="b2a25-650">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-650">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="b2a25-651">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="b2a25-651">ViTabCompletePrevious</span></span>

<span data-ttu-id="b2a25-652">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="b2a25-652">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="b2a25-653">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-653">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="prediction-functions"></a><span data-ttu-id="b2a25-654">Förutsägelse funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-654">Prediction functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="b2a25-655">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-655">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="b2a25-656">När du använder `InlineView` som vyformat för förutsägelse accepterar du nästa ord för det infogade förslaget.</span><span class="sxs-lookup"><span data-stu-id="b2a25-656">When using `InlineView` as the view style for prediction, accept the next word of the inline suggestion.</span></span>

- <span data-ttu-id="b2a25-657">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-657">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="b2a25-658">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="b2a25-658">AcceptSuggestion</span></span>

<span data-ttu-id="b2a25-659">När `InlineView` du använder som vyformat för förutsägelse godkänner du det aktuella infogade förslaget.</span><span class="sxs-lookup"><span data-stu-id="b2a25-659">When using `InlineView` as the view style for prediction, accept the current inline suggestion.</span></span>

- <span data-ttu-id="b2a25-660">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-660">Function is unbound.</span></span>

### <a name="nextsuggestion"></a><span data-ttu-id="b2a25-661">NextSuggestion</span><span class="sxs-lookup"><span data-stu-id="b2a25-661">NextSuggestion</span></span>

<span data-ttu-id="b2a25-662">När du använder `ListView` som vyformat för förutsägelse navigerar du till nästa förslag i listan.</span><span class="sxs-lookup"><span data-stu-id="b2a25-662">When using `ListView` as the view style for prediction, navigate to the next suggestion in the list.</span></span>

- <span data-ttu-id="b2a25-663">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-663">Function is unbound.</span></span>

### <a name="previoussuggestion"></a><span data-ttu-id="b2a25-664">PreviousSuggestion</span><span class="sxs-lookup"><span data-stu-id="b2a25-664">PreviousSuggestion</span></span>

<span data-ttu-id="b2a25-665">När du använder `ListView` som vyformat för förutsägelse navigerar du till föregående förslag i listan.</span><span class="sxs-lookup"><span data-stu-id="b2a25-665">When using `ListView` as the view style for prediction, navigate to the previous suggestion in the list.</span></span>

- <span data-ttu-id="b2a25-666">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-666">Function is unbound.</span></span>

### <a name="switchpredictionview"></a><span data-ttu-id="b2a25-667">SwitchPredictionView</span><span class="sxs-lookup"><span data-stu-id="b2a25-667">SwitchPredictionView</span></span>

<span data-ttu-id="b2a25-668">Ändra visnings formatet för förutsägelse mellan `InlineView` och `ListView` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-668">Switch the view style for prediction between `InlineView` and `ListView`.</span></span>

- <span data-ttu-id="b2a25-669">Kommandot `<F2>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-669">Cmd: `<F2>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="b2a25-670">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-670">Miscellaneous functions</span></span>

### <a name="capturescreen"></a><span data-ttu-id="b2a25-671">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="b2a25-671">CaptureScreen</span></span>

<span data-ttu-id="b2a25-672">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="b2a25-672">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="b2a25-673">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-673">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="b2a25-674">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="b2a25-674">ClearScreen</span></span>

<span data-ttu-id="b2a25-675">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-675">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="b2a25-676">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-676">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b2a25-677">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-677">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b2a25-678">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-678">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="b2a25-679">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-679">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="b2a25-680">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="b2a25-680">DigitArgument</span></span>

<span data-ttu-id="b2a25-681">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-681">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="b2a25-682">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b2a25-682">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b2a25-683">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="b2a25-683">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="b2a25-684">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-684">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="b2a25-685">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="b2a25-685">InvokePrompt</span></span>

<span data-ttu-id="b2a25-686">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-686">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="b2a25-687">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-687">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="b2a25-688">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-688">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="b2a25-689">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="b2a25-689">ScrollDisplayDown</span></span>

<span data-ttu-id="b2a25-690">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="b2a25-690">Scroll the display down one screen.</span></span>

- <span data-ttu-id="b2a25-691">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-691">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="b2a25-692">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-692">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="b2a25-693">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-693">ScrollDisplayDownLine</span></span>

<span data-ttu-id="b2a25-694">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="b2a25-694">Scroll the display down one line.</span></span>

- <span data-ttu-id="b2a25-695">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-695">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="b2a25-696">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-696">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="b2a25-697">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="b2a25-697">ScrollDisplayToCursor</span></span>

<span data-ttu-id="b2a25-698">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-698">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="b2a25-699">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-699">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="b2a25-700">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="b2a25-700">ScrollDisplayTop</span></span>

<span data-ttu-id="b2a25-701">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="b2a25-701">Scroll the display to the top.</span></span>

- <span data-ttu-id="b2a25-702">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-702">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="b2a25-703">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="b2a25-703">ScrollDisplayUp</span></span>

<span data-ttu-id="b2a25-704">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="b2a25-704">Scroll the display up one screen.</span></span>

- <span data-ttu-id="b2a25-705">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-705">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="b2a25-706">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-706">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="b2a25-707">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-707">ScrollDisplayUpLine</span></span>

<span data-ttu-id="b2a25-708">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="b2a25-708">Scroll the display up one line.</span></span>

- <span data-ttu-id="b2a25-709">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-709">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="b2a25-710">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-710">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="b2a25-711">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="b2a25-711">SelfInsert</span></span>

<span data-ttu-id="b2a25-712">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b2a25-712">Insert the key.</span></span>

- <span data-ttu-id="b2a25-713">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-713">Function is unbound.</span></span>

### <a name="showcommandhelp"></a><span data-ttu-id="b2a25-714">ShowCommandHelp</span><span class="sxs-lookup"><span data-stu-id="b2a25-714">ShowCommandHelp</span></span>

<span data-ttu-id="b2a25-715">Innehåller en vy över fullständig cmdlet-hjälp.</span><span class="sxs-lookup"><span data-stu-id="b2a25-715">Provides a view of full cmdlet help.</span></span> <span data-ttu-id="b2a25-716">När markören är i slutet av en helt expanderad parameter, kan du trycka på `<F1>` nyckeln för att visa hjälp om den här parameterns placering.</span><span class="sxs-lookup"><span data-stu-id="b2a25-716">When the cursor is at the end of a fully-expanded parameter, hitting the `<F1>` key positions the display of help at the location of that parameter.</span></span>

<span data-ttu-id="b2a25-717">Hjälpen visas på en alternativ skärms buffert med hjälp av en pager från **Microsoft. PowerShell. pager**.</span><span class="sxs-lookup"><span data-stu-id="b2a25-717">The help is displayed on an alternate screen buffer using a Pager from **Microsoft.PowerShell.Pager**.</span></span> <span data-ttu-id="b2a25-718">När du avslutar pager-filen returneras den ursprungliga markören på den ursprungliga skärmen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-718">When you exit the pager you are returned to the original cursor position on the original screen.</span></span> <span data-ttu-id="b2a25-719">Denna pager fungerar bara i moderna Terminal-program som [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span><span class="sxs-lookup"><span data-stu-id="b2a25-719">This pager only works in modern terminal applications such as [Windows Terminal](https://www.microsoft.com/en-us/p/windows-terminal/9n0dx20hk701).</span></span>

- <span data-ttu-id="b2a25-720">Kommandot `<F1>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-720">Cmd: `<F1>`</span></span>
- <span data-ttu-id="b2a25-721">Emacs: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-721">Emacs: `<F1>`</span></span>
- <span data-ttu-id="b2a25-722">Vi infognings läge: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-722">Vi insert mode: `<F1>`</span></span>
- <span data-ttu-id="b2a25-723">Kommando läge för vi: `<F1>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-723">Vi command mode: `<F1>`</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="b2a25-724">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="b2a25-724">ShowKeyBindings</span></span>

<span data-ttu-id="b2a25-725">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="b2a25-725">Show all bound keys.</span></span>

- <span data-ttu-id="b2a25-726">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-726">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b2a25-727">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-727">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="b2a25-728">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-728">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="showparameterhelp"></a><span data-ttu-id="b2a25-729">ShowParameterHelp</span><span class="sxs-lookup"><span data-stu-id="b2a25-729">ShowParameterHelp</span></span>

<span data-ttu-id="b2a25-730">Ger dynamisk hjälp för parametrar genom att visa den under den aktuella kommando raden som `MenuComplete` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-730">Provides dynamic help for parameters by showing it below the current command line like `MenuComplete`.</span></span> <span data-ttu-id="b2a25-731">Markören måste vara i slutet av det helt utökade parameter namnet när du trycker på `<Alt+h>` nyckeln.</span><span class="sxs-lookup"><span data-stu-id="b2a25-731">The cursor must be at the end of the fully-expanded parameter name when you press the `<Alt+h>` key.</span></span>

- <span data-ttu-id="b2a25-732">Kommandot `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-732">Cmd: `<Alt+h>`</span></span>
- <span data-ttu-id="b2a25-733">Emacs: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-733">Emacs: `<Alt+h>`</span></span>
- <span data-ttu-id="b2a25-734">Vi infognings läge: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-734">Vi insert mode: `<Alt+h>`</span></span>
- <span data-ttu-id="b2a25-735">Kommando läge för vi: `<Alt+h>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-735">Vi command mode: `<Alt+h>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="b2a25-736">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="b2a25-736">ViCommandMode</span></span>

<span data-ttu-id="b2a25-737">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="b2a25-737">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="b2a25-738">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-738">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="b2a25-739">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="b2a25-739">ViDigitArgumentInChord</span></span>

<span data-ttu-id="b2a25-740">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="b2a25-740">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="b2a25-741">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-741">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="b2a25-742">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="b2a25-742">ViEditVisually</span></span>

<span data-ttu-id="b2a25-743">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="b2a25-743">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="b2a25-744">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-744">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="b2a25-745">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-745">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="b2a25-746">ViExit</span><span class="sxs-lookup"><span data-stu-id="b2a25-746">ViExit</span></span>

<span data-ttu-id="b2a25-747">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-747">Exits the shell.</span></span>

- <span data-ttu-id="b2a25-748">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-748">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="b2a25-749">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="b2a25-749">ViInsertMode</span></span>

<span data-ttu-id="b2a25-750">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="b2a25-750">Switch to Insert mode.</span></span>

- <span data-ttu-id="b2a25-751">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-751">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="b2a25-752">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="b2a25-752">WhatIsKey</span></span>

<span data-ttu-id="b2a25-753">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="b2a25-753">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="b2a25-754">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-754">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="b2a25-755">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-755">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="b2a25-756">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-756">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="b2a25-757">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="b2a25-757">ExchangePointAndMark</span></span>

<span data-ttu-id="b2a25-758">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-758">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="b2a25-759">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-759">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="b2a25-760">SelectAll</span><span class="sxs-lookup"><span data-stu-id="b2a25-760">SelectAll</span></span>

<span data-ttu-id="b2a25-761">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-761">Select the entire line.</span></span>

- <span data-ttu-id="b2a25-762">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-762">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="b2a25-763">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-763">SelectBackwardChar</span></span>

<span data-ttu-id="b2a25-764">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-764">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="b2a25-765">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-765">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-766">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-766">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="b2a25-767">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-767">SelectBackwardsLine</span></span>

<span data-ttu-id="b2a25-768">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-768">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="b2a25-769">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-769">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="b2a25-770">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-770">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="b2a25-771">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-771">SelectBackwardWord</span></span>

<span data-ttu-id="b2a25-772">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-772">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="b2a25-773">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-773">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="b2a25-774">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-774">Emacs: `<Alt+B>`</span></span>

### <a name="selectcommandargument"></a><span data-ttu-id="b2a25-775">SelectCommandArgument</span><span class="sxs-lookup"><span data-stu-id="b2a25-775">SelectCommandArgument</span></span>

<span data-ttu-id="b2a25-776">Gör visuella urval av kommando argumenten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-776">Make visual selection of the command arguments.</span></span> <span data-ttu-id="b2a25-777">Val av argument är begränsade i ett-skript block.</span><span class="sxs-lookup"><span data-stu-id="b2a25-777">Selection of arguments is scoped within a script block.</span></span> <span data-ttu-id="b2a25-778">Baserat på markörens position söker den från det innersta skript blocket till det vanligaste skript blocket och stannar när eventuella argument i ett skript Blocks område hittas.</span><span class="sxs-lookup"><span data-stu-id="b2a25-778">Based on the cursor position, it searches from the innermost script block to the outmost script block, and stops when it finds any arguments in a script block scope.</span></span>

<span data-ttu-id="b2a25-779">Den här funktionen följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b2a25-779">This function honors DigitArgument.</span></span> <span data-ttu-id="b2a25-780">Den behandlar positiva eller negativa argument värden som framåtriktade eller baklänges förskjutningar från det markerade argumentet eller från den aktuella markören när inget argument är markerat.</span><span class="sxs-lookup"><span data-stu-id="b2a25-780">It treats the positive or negative argument values as the forward or backward offsets from the currently selected argument, or from the current cursor position when no argument is selected.</span></span>

- <span data-ttu-id="b2a25-781">Kommandot `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-781">Cmd: `<Alt+a>`</span></span>
- <span data-ttu-id="b2a25-782">Emacs: `<Alt+a>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-782">Emacs: `<Alt+a>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="b2a25-783">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-783">SelectForwardChar</span></span>

<span data-ttu-id="b2a25-784">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-784">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="b2a25-785">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-785">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="b2a25-786">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-786">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="b2a25-787">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-787">SelectForwardWord</span></span>

<span data-ttu-id="b2a25-788">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-788">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="b2a25-789">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-789">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="b2a25-790">SelectLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-790">SelectLine</span></span>

<span data-ttu-id="b2a25-791">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-791">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="b2a25-792">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-792">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="b2a25-793">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-793">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="b2a25-794">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-794">SelectNextWord</span></span>

<span data-ttu-id="b2a25-795">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-795">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="b2a25-796">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-796">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="b2a25-797">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-797">SelectShellBackwardWord</span></span>

<span data-ttu-id="b2a25-798">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-798">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="b2a25-799">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-799">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="b2a25-800">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-800">SelectShellForwardWord</span></span>

<span data-ttu-id="b2a25-801">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-801">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="b2a25-802">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-802">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="b2a25-803">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="b2a25-803">SelectShellNextWord</span></span>

<span data-ttu-id="b2a25-804">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-804">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="b2a25-805">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-805">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="b2a25-806">SetMark</span><span class="sxs-lookup"><span data-stu-id="b2a25-806">SetMark</span></span>

<span data-ttu-id="b2a25-807">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="b2a25-807">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="b2a25-808">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-808">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="b2a25-809">Förutsägande IntelliSense-funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-809">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="b2a25-810">Förutsägelse IntelliSense måste aktive ras för att använda dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-810">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="b2a25-811">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="b2a25-811">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="b2a25-812">Accepterar nästa ord i det infogade förslaget från förutsägande IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="b2a25-812">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="b2a25-813">Den här funktionen kan bindas till <kbd>CTRL</kbd> + <kbd>F</kbd> genom att köra följande kommando.</span><span class="sxs-lookup"><span data-stu-id="b2a25-813">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="b2a25-814">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="b2a25-814">AcceptSuggestion</span></span>

<span data-ttu-id="b2a25-815">Accepterar det aktuella infogade förslaget från förutsägande IntelliSense genom att trycka på <kbd>RightArrow</kbd> när markören är i slutet av den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-815">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="b2a25-816">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="b2a25-816">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="b2a25-817">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="b2a25-817">CharacterSearch</span></span>

<span data-ttu-id="b2a25-818">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-818">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="b2a25-819">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-819">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b2a25-820">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-820">Cmd: `<F3>`</span></span>
- <span data-ttu-id="b2a25-821">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-821">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="b2a25-822">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-822">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="b2a25-823">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-823">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="b2a25-824">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-824">CharacterSearchBackward</span></span>

<span data-ttu-id="b2a25-825">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-825">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="b2a25-826">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-826">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="b2a25-827">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-827">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="b2a25-828">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-828">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="b2a25-829">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-829">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="b2a25-830">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-830">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="b2a25-831">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="b2a25-831">RepeatLastCharSearch</span></span>

<span data-ttu-id="b2a25-832">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-832">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="b2a25-833">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-833">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="b2a25-834">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="b2a25-834">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="b2a25-835">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-835">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="b2a25-836">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-836">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="b2a25-837">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="b2a25-837">RepeatSearch</span></span>

<span data-ttu-id="b2a25-838">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-838">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b2a25-839">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-839">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="b2a25-840">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-840">RepeatSearchBackward</span></span>

<span data-ttu-id="b2a25-841">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="b2a25-841">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="b2a25-842">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-842">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="b2a25-843">SearchChar</span><span class="sxs-lookup"><span data-stu-id="b2a25-843">SearchChar</span></span>

<span data-ttu-id="b2a25-844">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-844">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b2a25-845">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-845">This is for 't' functionality.</span></span>

- <span data-ttu-id="b2a25-846">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-846">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="b2a25-847">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="b2a25-847">SearchCharBackward</span></span>

<span data-ttu-id="b2a25-848">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-848">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b2a25-849">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-849">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b2a25-850">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-850">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="b2a25-851">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b2a25-851">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="b2a25-852">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-852">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="b2a25-853">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-853">This is for 'T' functionality.</span></span>

- <span data-ttu-id="b2a25-854">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-854">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="b2a25-855">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="b2a25-855">SearchCharWithBackoff</span></span>

<span data-ttu-id="b2a25-856">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="b2a25-856">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="b2a25-857">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="b2a25-857">This is for 't' functionality.</span></span>

- <span data-ttu-id="b2a25-858">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-858">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="b2a25-859">SearchForward</span><span class="sxs-lookup"><span data-stu-id="b2a25-859">SearchForward</span></span>

<span data-ttu-id="b2a25-860">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="b2a25-860">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="b2a25-861">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-861">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="b2a25-862">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="b2a25-862">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="b2a25-863">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="b2a25-863">Custom Key Bindings</span></span>

<span data-ttu-id="b2a25-864">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-864">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b2a25-865">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="b2a25-865">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="b2a25-866">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="b2a25-866">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="b2a25-867">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="b2a25-867">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="b2a25-868">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="b2a25-868">Some useful examples include</span></span>

- <span data-ttu-id="b2a25-869">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="b2a25-869">edit the command line</span></span>
- <span data-ttu-id="b2a25-870">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="b2a25-870">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="b2a25-871">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="b2a25-871">change directories without changing the command line</span></span>

<span data-ttu-id="b2a25-872">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="b2a25-872">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="b2a25-873">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-873">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="b2a25-874">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="b2a25-874">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="b2a25-875">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-875">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="b2a25-876">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="b2a25-876">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="b2a25-877">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b2a25-877">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="b2a25-878">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="b2a25-878">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="b2a25-879">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="b2a25-879">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="b2a25-880">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="b2a25-880">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="b2a25-881">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="b2a25-881">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="b2a25-882">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-882">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="b2a25-883">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b2a25-883">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="b2a25-884">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="b2a25-884">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="b2a25-885">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="b2a25-885">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="b2a25-886">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="b2a25-886">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="b2a25-887">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="b2a25-887">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="b2a25-888">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-888">Clear the kill-ring.</span></span>  <span data-ttu-id="b2a25-889">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-889">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="b2a25-890">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="b2a25-890">Delete length characters from start.</span></span>  <span data-ttu-id="b2a25-891">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="b2a25-891">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="b2a25-892">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="b2a25-892">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="b2a25-893">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="b2a25-893">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="b2a25-894">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="b2a25-894">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="b2a25-895">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="b2a25-895">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="b2a25-896">Dessa två funktioner används av `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-896">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="b2a25-897">Den första används för att hämta alla nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="b2a25-897">The first is used to get all key bindings.</span></span> <span data-ttu-id="b2a25-898">Den andra används för att hämta vissa nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="b2a25-898">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="b2a25-899">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-899">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="b2a25-900">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="b2a25-900">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="b2a25-901">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-901">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="b2a25-902">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="b2a25-902">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="b2a25-903">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="b2a25-903">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="b2a25-904">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="b2a25-904">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="b2a25-905">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-905">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="b2a25-906">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-906">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="b2a25-907">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="b2a25-907">Replace some of the input.</span></span> <span data-ttu-id="b2a25-908">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="b2a25-908">This operation supports undo/redo.</span></span> <span data-ttu-id="b2a25-909">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="b2a25-909">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="b2a25-910">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="b2a25-910">Move the cursor to the given offset.</span></span> <span data-ttu-id="b2a25-911">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="b2a25-911">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="b2a25-912">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="b2a25-912">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="b2a25-913">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="b2a25-913">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="b2a25-914">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="b2a25-914">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="b2a25-915">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b2a25-915">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="b2a25-916">Kommando historik</span><span class="sxs-lookup"><span data-stu-id="b2a25-916">Command History</span></span>

<span data-ttu-id="b2a25-917">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="b2a25-917">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="b2a25-918">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="b2a25-918">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="b2a25-919">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="b2a25-919">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="b2a25-920">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-920">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="b2a25-921">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-921">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="b2a25-922">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="b2a25-922">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="b2a25-923">Feedback & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="b2a25-923">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="b2a25-924">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="b2a25-924">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="b2a25-925">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="b2a25-925">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="b2a25-926">Se även</span><span class="sxs-lookup"><span data-stu-id="b2a25-926">See Also</span></span>

<span data-ttu-id="b2a25-927">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="b2a25-927">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
