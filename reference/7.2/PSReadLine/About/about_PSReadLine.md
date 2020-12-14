---
description: PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.
Locale: en-US
ms.date: 11/23/2020
online version: https://docs.microsoft.com/powershell/module/psreadline/about/about_psreadline?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: Om PSReadLine
ms.openlocfilehash: 4836abfec465ba7cdfb6800c1e60104fba19ce08
ms.sourcegitcommit: 560a9f3c3148acab4655e91e8b07745ab74d5d26
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/09/2020
ms.locfileid: "96913309"
---
# <a name="psreadline"></a><span data-ttu-id="1d3bc-103">PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-103">PSReadLine</span></span>

## <a name="about_psreadline"></a><span data-ttu-id="1d3bc-104">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-104">about_PSReadLine</span></span>

## <a name="short-description"></a><span data-ttu-id="1d3bc-105">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d3bc-105">Short Description</span></span>

<span data-ttu-id="1d3bc-106">PSReadLine ger en förbättrad kommando rads redigerings upplevelse i PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-106">PSReadLine provides an improved command-line editing experience in the PowerShell console.</span></span>

## <a name="long-description"></a><span data-ttu-id="1d3bc-107">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="1d3bc-107">Long Description</span></span>

<span data-ttu-id="1d3bc-108">PSReadLine 2,2 ger en kraftfull redigerings upplevelse för kommando tolken för PowerShell-konsolen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-108">PSReadLine 2.2 provides a powerful command-line editing experience for the PowerShell console.</span></span> <span data-ttu-id="1d3bc-109">Den tillhandahåller:</span><span class="sxs-lookup"><span data-stu-id="1d3bc-109">It provides:</span></span>

- <span data-ttu-id="1d3bc-110">Syntax för kommando rads färg</span><span class="sxs-lookup"><span data-stu-id="1d3bc-110">Syntax coloring of the command line</span></span>
- <span data-ttu-id="1d3bc-111">En visuell indikation på syntaxfel</span><span class="sxs-lookup"><span data-stu-id="1d3bc-111">A visual indication of syntax errors</span></span>
- <span data-ttu-id="1d3bc-112">En bättre multi-line-upplevelse (både redigering och historik)</span><span class="sxs-lookup"><span data-stu-id="1d3bc-112">A better multi-line experience (both editing and history)</span></span>
- <span data-ttu-id="1d3bc-113">Anpassningsbara nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-113">Customizable key bindings</span></span>
- <span data-ttu-id="1d3bc-114">Cmd-och emacs-lägen</span><span class="sxs-lookup"><span data-stu-id="1d3bc-114">Cmd and Emacs modes</span></span>
- <span data-ttu-id="1d3bc-115">Många konfigurations alternativ</span><span class="sxs-lookup"><span data-stu-id="1d3bc-115">Many configuration options</span></span>
- <span data-ttu-id="1d3bc-116">Slut för ande av bash-format (valfritt i cmd-läge, standard i emacs-läge)</span><span class="sxs-lookup"><span data-stu-id="1d3bc-116">Bash style completion (optional in Cmd mode, default in Emacs mode)</span></span>
- <span data-ttu-id="1d3bc-117">Emacs YANK/Kill-ring</span><span class="sxs-lookup"><span data-stu-id="1d3bc-117">Emacs yank/kill-ring</span></span>
- <span data-ttu-id="1d3bc-118">PowerShell-token-baserad "Word"-förflyttning och stopp</span><span class="sxs-lookup"><span data-stu-id="1d3bc-118">PowerShell token based "word" movement and kill</span></span>
- <span data-ttu-id="1d3bc-119">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="1d3bc-119">Predictive IntelliSense</span></span>

<span data-ttu-id="1d3bc-120">PSReadLine 2.2.0 har lagt till två nya förutsägande IntelliSense-funktioner:</span><span class="sxs-lookup"><span data-stu-id="1d3bc-120">PSReadLine 2.2.0 added two new predictive IntelliSense features:</span></span>

- <span data-ttu-id="1d3bc-121">Parametern **PredictionViewStyle** har lagts till för att det nya ska kunna väljas `ListView` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-121">Added the **PredictionViewStyle** parameter to allow for the selection of the new `ListView`.</span></span>
- <span data-ttu-id="1d3bc-122">Anslutna PSReadLine till `CommandPrediction` API: erna introducerade i PS 7,1 för att tillåta en användare att importera en förutsägbar modul som kan återge förslag från en anpassad källa.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-122">Connected PSReadLine to the `CommandPrediction` APIs introduced in PS 7.1 to allow a user can import a predictor module that can render the suggestions from a custom source.</span></span>

<span data-ttu-id="1d3bc-123">PSReadLine kräver PowerShell 3,0 eller senare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-123">PSReadLine requires PowerShell 3.0, or newer.</span></span> <span data-ttu-id="1d3bc-124">PSReadLine fungerar med standard konsol värden, Visual Studio Code och Window Terminal.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-124">PSReadLine works with default console host, Visual Studio Code, and Window Terminal.</span></span> <span data-ttu-id="1d3bc-125">Den fungerar inte i PowerShell ISE.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-125">It does not work in PowerShell ISE.</span></span>

<span data-ttu-id="1d3bc-126">PSReadLine 2.2.0 levereras med PowerShell 7,2 och stöds i alla versioner av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-126">PSReadLine 2.2.0 ships with PowerShell 7.2 and is supported in all supported versions of PowerShell.</span></span> <span data-ttu-id="1d3bc-127">Den är tillgänglig för installation från PowerShell-galleriet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-127">It is available to install from the PowerShell Gallery.</span></span>
<span data-ttu-id="1d3bc-128">Kör följande kommando för att installera PSReadLine-2.2.0 i en version av PowerShell som stöds.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-128">To install PSReadLine 2.2.0 in a supported version of PowerShell run the following command.</span></span>

```powershell
Install-Module -Name PSReadLine -AllowPrerelease
```

> [!NOTE]
> <span data-ttu-id="1d3bc-129">Från och med PowerShell 7,0 hoppar PowerShell över automatisk inläsning av PSReadLine i Windows om ett skärm läsar program har identifierats.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-129">Beginning with PowerShell 7.0, PowerShell skips auto-loading PSReadLine on Windows if a screen reader program is detected.</span></span> <span data-ttu-id="1d3bc-130">PSReadLine fungerar för närvarande inte bra med skärm läsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-130">Currently, PSReadLine doesn't work well with the screen readers.</span></span> <span data-ttu-id="1d3bc-131">Standard åter givningen och formateringen av PowerShell 7,0 i Windows fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-131">The default rendering and formatting of PowerShell 7.0 on Windows works properly.</span></span> <span data-ttu-id="1d3bc-132">Du kan läsa in modulen manuellt om det behövs.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-132">You can manually load the module if necessary.</span></span>

## <a name="predictive-intellisense"></a><span data-ttu-id="1d3bc-133">Förutsäga IntelliSense</span><span class="sxs-lookup"><span data-stu-id="1d3bc-133">Predictive IntelliSense</span></span>

<span data-ttu-id="1d3bc-134">Förutsägelse IntelliSense är ett tillägg till begreppet TABB-slutförande som hjälper användaren att slutföra kommandon.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-134">Predictive IntelliSense is an addition to the concept of tab completion that assists the user in successfully completing commands.</span></span> <span data-ttu-id="1d3bc-135">Det gör det möjligt för användare att upptäcka, redigera och köra fullständiga kommandon baserat på matchande förutsägelser från användarens historik och ytterligare domänanslutna plugin-program.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-135">It enables users to discover, edit, and execute full commands based on matching predictions from the user's history and additional domain specific plugins.</span></span>

### <a name="enable-predictive-intellisense"></a><span data-ttu-id="1d3bc-136">Aktivera förutsägelse IntelliSense</span><span class="sxs-lookup"><span data-stu-id="1d3bc-136">Enable Predictive IntelliSense</span></span>

<span data-ttu-id="1d3bc-137">Förutsägelse IntelliSense är inaktiverat som standard.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-137">Predictive IntelliSense is disabled by default.</span></span> <span data-ttu-id="1d3bc-138">Kör följande kommando för att aktivera förutsägelser:</span><span class="sxs-lookup"><span data-stu-id="1d3bc-138">To enable predictions, just run the following command:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource History
```

<span data-ttu-id="1d3bc-139">Parametern **PredictionSource** kan också ta emot plugin-program för domän särskilda och anpassade krav.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-139">The **PredictionSource** parameter can also accept plugins for domain specific and custom requirements.</span></span>

<span data-ttu-id="1d3bc-140">För att inaktivera förutsägelse IntelliSense, kör du bara:</span><span class="sxs-lookup"><span data-stu-id="1d3bc-140">To disable Predictive IntelliSense, just run:</span></span>

```powershell
Set-PSReadLineOption -PredictionSource None
```

<span data-ttu-id="1d3bc-141">Följande funktioner är tillgängliga i klassen **[Microsoft. PowerShell. PSConsoleReadLine]**.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-141">The following functions are available in the class **[Microsoft.PowerShell.PSConsoleReadLine]**.</span></span>

## <a name="basic-editing-functions"></a><span data-ttu-id="1d3bc-142">Grundläggande redigerings funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-142">Basic editing functions</span></span>

### <a name="abort"></a><span data-ttu-id="1d3bc-143">Avbryta</span><span class="sxs-lookup"><span data-stu-id="1d3bc-143">Abort</span></span>

<span data-ttu-id="1d3bc-144">Avbryt den aktuella åtgärden, t. ex. stegvis Sök historik.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-144">Abort current action, e.g. incremental history search.</span></span>

- <span data-ttu-id="1d3bc-145">Emacs: `<Ctrl+g>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-145">Emacs: `<Ctrl+g>`</span></span>

### <a name="acceptandgetnext"></a><span data-ttu-id="1d3bc-146">AcceptAndGetNext</span><span class="sxs-lookup"><span data-stu-id="1d3bc-146">AcceptAndGetNext</span></span>

<span data-ttu-id="1d3bc-147">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-147">Attempt to execute the current input.</span></span> <span data-ttu-id="1d3bc-148">Om den kan köras (t. ex. AcceptLine) kan du återkalla nästa objekt från historik nästa gången ReadLine anropas.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-148">If it can be executed (like AcceptLine), then recall the next item from history the next time ReadLine is called.</span></span>

- <span data-ttu-id="1d3bc-149">Emacs: `<Ctrl+o>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-149">Emacs: `<Ctrl+o>`</span></span>

### <a name="acceptline"></a><span data-ttu-id="1d3bc-150">AcceptLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-150">AcceptLine</span></span>

<span data-ttu-id="1d3bc-151">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-151">Attempt to execute the current input.</span></span> <span data-ttu-id="1d3bc-152">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-152">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="1d3bc-153">Kommandot `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-153">Cmd: `<Enter>`</span></span>
- <span data-ttu-id="1d3bc-154">Emacs: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-154">Emacs: `<Enter>`</span></span>
- <span data-ttu-id="1d3bc-155">Vi infognings läge: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-155">Vi insert mode: `<Enter>`</span></span>

### <a name="addline"></a><span data-ttu-id="1d3bc-156">AddLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-156">AddLine</span></span>

<span data-ttu-id="1d3bc-157">Fortsättnings meddelandet visas på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-157">The continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span> <span data-ttu-id="1d3bc-158">Detta är användbart för att ange flera rader som ett enda kommando, även när en enskild rad är fullständig indata.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-158">This is useful to enter multi-line input as a single command even when a single line is complete input by itself.</span></span>

- <span data-ttu-id="1d3bc-159">Kommandot `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-159">Cmd: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1d3bc-160">Emacs: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-160">Emacs: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1d3bc-161">Vi infognings läge: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-161">Vi insert mode: `<Shift+Enter>`</span></span>
- <span data-ttu-id="1d3bc-162">Kommando läge för vi: `<Shift+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-162">Vi command mode: `<Shift+Enter>`</span></span>

### <a name="backwarddeletechar"></a><span data-ttu-id="1d3bc-163">BackwardDeleteChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-163">BackwardDeleteChar</span></span>

<span data-ttu-id="1d3bc-164">Ta bort det före markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-164">Delete the character before the cursor.</span></span>

- <span data-ttu-id="1d3bc-165">CMD: `<Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-165">Cmd: `<Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="1d3bc-166">Emacs: `<Backspace>` , `<Ctrl+Backspace>` , `<Ctrl+h>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-166">Emacs: `<Backspace>`, `<Ctrl+Backspace>`, `<Ctrl+h>`</span></span>
- <span data-ttu-id="1d3bc-167">Vi infognings läge: `<Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-167">Vi insert mode: `<Backspace>`</span></span>
- <span data-ttu-id="1d3bc-168">Kommando läge för vi: `<X>` , `<d,h>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-168">Vi command mode: `<X>`, `<d,h>`</span></span>

### <a name="backwarddeleteline"></a><span data-ttu-id="1d3bc-169">BackwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-169">BackwardDeleteLine</span></span>

<span data-ttu-id="1d3bc-170">Som BackwardKillLine – tar bort text från punkten till början av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-170">Like BackwardKillLine - deletes text from the point to the start of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-171">Kommandot `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-171">Cmd: `<Ctrl+Home>`</span></span>
- <span data-ttu-id="1d3bc-172">Vi infognings läge: `<Ctrl+u>` , `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-172">Vi insert mode: `<Ctrl+u>`, `<Ctrl+Home>`</span></span>
- <span data-ttu-id="1d3bc-173">Vi kommando läge: `<Ctrl+u>` , `<Ctrl+Home>` , `<d,0>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-173">Vi command mode: `<Ctrl+u>`, `<Ctrl+Home>`, `<d,0>`</span></span>

### <a name="backwarddeleteword"></a><span data-ttu-id="1d3bc-174">BackwardDeleteWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-174">BackwardDeleteWord</span></span>

<span data-ttu-id="1d3bc-175">Tar bort föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-175">Deletes the previous word.</span></span>

- <span data-ttu-id="1d3bc-176">Kommando läge för vi: `<Ctrl+w>` , `<d,b>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-176">Vi command mode: `<Ctrl+w>`, `<d,b>`</span></span>

### <a name="backwardkillline"></a><span data-ttu-id="1d3bc-177">BackwardKillLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-177">BackwardKillLine</span></span>

<span data-ttu-id="1d3bc-178">Ta bort indatamängden från början av inmatarna till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-178">Clear the input from the start of the input to the cursor.</span></span> <span data-ttu-id="1d3bc-179">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-179">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-180">Emacs: `<Ctrl+u>` , `<Ctrl+x,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-180">Emacs: `<Ctrl+u>`, `<Ctrl+x,Backspace>`</span></span>

### <a name="backwardkillword"></a><span data-ttu-id="1d3bc-181">BackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-181">BackwardKillWord</span></span>

<span data-ttu-id="1d3bc-182">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-182">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1d3bc-183">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-183">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1d3bc-184">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-184">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-185">CMD: `<Ctrl+Backspace>` , `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-185">Cmd: `<Ctrl+Backspace>`, `<Ctrl+w>`</span></span>
- <span data-ttu-id="1d3bc-186">Emacs: `<Alt+Backspace>` , `<Escape,Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-186">Emacs: `<Alt+Backspace>`, `<Escape,Backspace>`</span></span>
- <span data-ttu-id="1d3bc-187">Vi infognings läge: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-187">Vi insert mode: `<Ctrl+Backspace>`</span></span>
- <span data-ttu-id="1d3bc-188">Kommando läge för vi: `<Ctrl+Backspace>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-188">Vi command mode: `<Ctrl+Backspace>`</span></span>

### <a name="cancelline"></a><span data-ttu-id="1d3bc-189">CancelLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-189">CancelLine</span></span>

<span data-ttu-id="1d3bc-190">Avbryt inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inaktuella inmatade åtgärder, men återgår till värden så att frågan utvärderas igen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-190">Cancel the current input, leaving the input on the screen, but returns back to the host so the prompt is evaluated again.</span></span>

- <span data-ttu-id="1d3bc-191">Vi infognings läge: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-191">Vi insert mode: `<Ctrl+c>`</span></span>
- <span data-ttu-id="1d3bc-192">Kommando läge för vi: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-192">Vi command mode: `<Ctrl+c>`</span></span>

### <a name="copy"></a><span data-ttu-id="1d3bc-193">Kopiera</span><span class="sxs-lookup"><span data-stu-id="1d3bc-193">Copy</span></span>

<span data-ttu-id="1d3bc-194">Kopiera vald region till Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-194">Copy selected region to the system clipboard.</span></span> <span data-ttu-id="1d3bc-195">Om ingen region har valts kopierar du hela raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-195">If no region is selected, copy the whole line.</span></span>

- <span data-ttu-id="1d3bc-196">Kommandot `<Ctrl+C>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-196">Cmd: `<Ctrl+C>`</span></span>

### <a name="copyorcancelline"></a><span data-ttu-id="1d3bc-197">CopyOrCancelLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-197">CopyOrCancelLine</span></span>

<span data-ttu-id="1d3bc-198">Om text är markerad kopierar du till Urklipp, annars avbryter du raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-198">If text is selected, copy to the clipboard, otherwise cancel the line.</span></span>

- <span data-ttu-id="1d3bc-199">Kommandot `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-199">Cmd: `<Ctrl+c>`</span></span>
- <span data-ttu-id="1d3bc-200">Emacs: `<Ctrl+c>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-200">Emacs: `<Ctrl+c>`</span></span>

### <a name="cut"></a><span data-ttu-id="1d3bc-201">Klipp ut</span><span class="sxs-lookup"><span data-stu-id="1d3bc-201">Cut</span></span>

<span data-ttu-id="1d3bc-202">Ta bort markerad region som placerar borttagen text i Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-202">Delete selected region placing deleted text in the system clipboard.</span></span>

- <span data-ttu-id="1d3bc-203">Kommandot `<Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-203">Cmd: `<Ctrl+x>`</span></span>

### <a name="deletechar"></a><span data-ttu-id="1d3bc-204">DeleteChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-204">DeleteChar</span></span>

<span data-ttu-id="1d3bc-205">Ta bort specialtecknet under markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-205">Delete the character under the cursor.</span></span>

- <span data-ttu-id="1d3bc-206">Kommandot `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-206">Cmd: `<Delete>`</span></span>
- <span data-ttu-id="1d3bc-207">Emacs: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-207">Emacs: `<Delete>`</span></span>
- <span data-ttu-id="1d3bc-208">Vi infognings läge: `<Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-208">Vi insert mode: `<Delete>`</span></span>
- <span data-ttu-id="1d3bc-209">Vi kommando läge: `<Delete>` , `<x>` , `<d,l>` , `<d,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-209">Vi command mode: `<Delete>`, `<x>`, `<d,l>`, `<d,Spacebar>`</span></span>

### <a name="deletecharorexit"></a><span data-ttu-id="1d3bc-210">DeleteCharOrExit</span><span class="sxs-lookup"><span data-stu-id="1d3bc-210">DeleteCharOrExit</span></span>

<span data-ttu-id="1d3bc-211">Ta bort tecknen under markören, eller om raden är tom, avslutar du processen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-211">Delete the character under the cursor, or if the line is empty, exit the process.</span></span>

- <span data-ttu-id="1d3bc-212">Emacs: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-212">Emacs: `<Ctrl+d>`</span></span>

### <a name="deleteendofbuffer"></a><span data-ttu-id="1d3bc-213">DeleteEndOfBuffer</span><span class="sxs-lookup"><span data-stu-id="1d3bc-213">DeleteEndOfBuffer</span></span>

<span data-ttu-id="1d3bc-214">Tar bort till slutet av Multiline-bufferten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-214">Deletes to the end of the multiline buffer.</span></span>

- <span data-ttu-id="1d3bc-215">Kommando läge för vi: `<d,G>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-215">Vi command mode: `<d,G>`</span></span>

### <a name="deleteendofword"></a><span data-ttu-id="1d3bc-216">DeleteEndOfWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-216">DeleteEndOfWord</span></span>

<span data-ttu-id="1d3bc-217">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-217">Delete to the end of the word.</span></span>

- <span data-ttu-id="1d3bc-218">Kommando läge för vi: `<d,e>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-218">Vi command mode: `<d,e>`</span></span>

### <a name="deleteline"></a><span data-ttu-id="1d3bc-219">DeleteLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-219">DeleteLine</span></span>

<span data-ttu-id="1d3bc-220">Tar bort den aktuella logiska raden för en buffert med flera rader och aktiverar ångra.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-220">Deletes the current logical line of a multiline buffer, enabling undo.</span></span>

- <span data-ttu-id="1d3bc-221">Kommando läge för vi: `<d,d>` , `<d,_>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-221">Vi command mode: `<d,d>`, `<d,_>`</span></span>

### <a name="deletepreviouslines"></a><span data-ttu-id="1d3bc-222">DeletePreviousLines</span><span class="sxs-lookup"><span data-stu-id="1d3bc-222">DeletePreviousLines</span></span>

<span data-ttu-id="1d3bc-223">Tar bort föregående begärda logiska rader och den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-223">Deletes the previous requested logical lines and the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="1d3bc-224">Kommando läge för vi: `<d,k>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-224">Vi command mode: `<d,k>`</span></span>

### <a name="deleterelativelines"></a><span data-ttu-id="1d3bc-225">DeleteRelativeLines</span><span class="sxs-lookup"><span data-stu-id="1d3bc-225">DeleteRelativeLines</span></span>

<span data-ttu-id="1d3bc-226">Tar bort från buffertens början till den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-226">Deletes from the beginning of the buffer to the current logical line in a multiline buffer.</span></span>

<span data-ttu-id="1d3bc-227">Som de flesta vi-kommandon `<d,g,g>` kan kommandot vara anpassningsprefix med ett numeriskt argument som anger ett absolut rad nummer, som tillsammans med det aktuella rad numret, utgör ett intervall med rader som ska tas bort.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-227">As most Vi commands, the `<d,g,g>` command can be prepended with a numeric argument that specifies an absolute line number, which, together with the current line number, make up a range of lines to be deleted.</span></span>
<span data-ttu-id="1d3bc-228">Om inget värde anges är det numeriska argumentet standardvärdet 1, som refererar till den första logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-228">If not specified, the numeric argument defaults to 1, which refers to the first logical line in a multiline buffer.</span></span>

<span data-ttu-id="1d3bc-229">Det faktiska antalet rader som ska tas bort från flera rader beräknas som skillnaden mellan det aktuella logiska rad numret och det angivna numeriska argumentet, som därför kan vara negativt.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-229">The actual number of lines to be deleted from the multiline is computed as the difference between the current logical line number and the specified numeric argument, which can thus be negative.</span></span> <span data-ttu-id="1d3bc-230">Därför är den _relativa_ delen av metod namnet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-230">Hence the _relative_ part of method name.</span></span>

- <span data-ttu-id="1d3bc-231">Kommando läge för vi: `<d,g,g>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-231">Vi command mode: `<d,g,g>`</span></span>

### <a name="deletenextlines"></a><span data-ttu-id="1d3bc-232">DeleteNextLines</span><span class="sxs-lookup"><span data-stu-id="1d3bc-232">DeleteNextLines</span></span>

<span data-ttu-id="1d3bc-233">Tar bort den aktuella logiska raden och nästa begärda logiska rader i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-233">Deletes the current logical line and the next requested logical lines in a multiline buffer.</span></span>

- <span data-ttu-id="1d3bc-234">Kommando läge för vi: `<d,j>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-234">Vi command mode: `<d,j>`</span></span>

### <a name="deletelinetofirstchar"></a><span data-ttu-id="1d3bc-235">DeleteLineToFirstChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-235">DeleteLineToFirstChar</span></span>

<span data-ttu-id="1d3bc-236">Tar bort från det första icke-tomma tecken i den aktuella logiska linjen i en buffert med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-236">Deletes from the first non-blank character of the current logical line in a multiline buffer.</span></span>

- <span data-ttu-id="1d3bc-237">Kommando läge för vi: `<d,^>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-237">Vi command mode: `<d,^>`</span></span>

### <a name="deletetoend"></a><span data-ttu-id="1d3bc-238">DeleteToEnd</span><span class="sxs-lookup"><span data-stu-id="1d3bc-238">DeleteToEnd</span></span>

<span data-ttu-id="1d3bc-239">Ta bort till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-239">Delete to the end of the line.</span></span>

- <span data-ttu-id="1d3bc-240">Kommando läge för vi: `<D>` , `<d,$>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-240">Vi command mode: `<D>`, `<d,$>`</span></span>

### <a name="deleteword"></a><span data-ttu-id="1d3bc-241">DeleteWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-241">DeleteWord</span></span>

<span data-ttu-id="1d3bc-242">Ta bort nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-242">Delete the next word.</span></span>

- <span data-ttu-id="1d3bc-243">Kommando läge för vi: `<d,w>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-243">Vi command mode: `<d,w>`</span></span>

### <a name="forwarddeleteline"></a><span data-ttu-id="1d3bc-244">ForwardDeleteLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-244">ForwardDeleteLine</span></span>

<span data-ttu-id="1d3bc-245">Som ForwardKillLine – tar bort text från punkten till slutet av raden, men lägger inte till den borttagna texten i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-245">Like ForwardKillLine - deletes text from the point to the end of the line, but does not put the deleted text in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-246">Kommandot `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-246">Cmd: `<Ctrl+End>`</span></span>
- <span data-ttu-id="1d3bc-247">Vi infognings läge: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-247">Vi insert mode: `<Ctrl+End>`</span></span>
- <span data-ttu-id="1d3bc-248">Kommando läge för vi: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-248">Vi command mode: `<Ctrl+End>`</span></span>

### <a name="insertlineabove"></a><span data-ttu-id="1d3bc-249">InsertLineAbove</span><span class="sxs-lookup"><span data-stu-id="1d3bc-249">InsertLineAbove</span></span>

<span data-ttu-id="1d3bc-250">En ny tom rad skapas ovanför den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-250">A new empty line is created above the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="1d3bc-251">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-251">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="1d3bc-252">Kommandot `<Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-252">Cmd: `<Ctrl+Enter>`</span></span>

### <a name="insertlinebelow"></a><span data-ttu-id="1d3bc-253">InsertLineBelow</span><span class="sxs-lookup"><span data-stu-id="1d3bc-253">InsertLineBelow</span></span>

<span data-ttu-id="1d3bc-254">En ny tom rad skapas under den aktuella raden, oavsett var markören finns på den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-254">A new empty line is created below the current line regardless of where the cursor is on the current line.</span></span> <span data-ttu-id="1d3bc-255">Markören flyttas till början av den nya raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-255">The cursor moves to the beginning of the new line.</span></span>

- <span data-ttu-id="1d3bc-256">Kommandot `<Shift+Ctrl+Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-256">Cmd: `<Shift+Ctrl+Enter>`</span></span>

### <a name="invertcase"></a><span data-ttu-id="1d3bc-257">InvertCase</span><span class="sxs-lookup"><span data-stu-id="1d3bc-257">InvertCase</span></span>

<span data-ttu-id="1d3bc-258">Invertera Skift läget för det aktuella specialtecknet och gå till nästa.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-258">Invert the case of the current character and move to the next one.</span></span>

- <span data-ttu-id="1d3bc-259">Kommando läge för vi: `<~>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-259">Vi command mode: `<~>`</span></span>

### <a name="killline"></a><span data-ttu-id="1d3bc-260">KillLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-260">KillLine</span></span>

<span data-ttu-id="1d3bc-261">Ta bort indatamängden från markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-261">Clear the input from the cursor to the end of the input.</span></span> <span data-ttu-id="1d3bc-262">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-262">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-263">Emacs: `<Ctrl+k>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-263">Emacs: `<Ctrl+k>`</span></span>

### <a name="killregion"></a><span data-ttu-id="1d3bc-264">KillRegion</span><span class="sxs-lookup"><span data-stu-id="1d3bc-264">KillRegion</span></span>

<span data-ttu-id="1d3bc-265">Stoppa texten mellan markören och markeringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-265">Kill the text between the cursor and the mark.</span></span>

- <span data-ttu-id="1d3bc-266">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-266">Function is unbound.</span></span>

### <a name="killword"></a><span data-ttu-id="1d3bc-267">KillWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-267">KillWord</span></span>

<span data-ttu-id="1d3bc-268">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-268">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="1d3bc-269">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-269">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="1d3bc-270">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-270">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-271">CMD: `<Alt+d>` , `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-271">Cmd: `<Alt+d>`, `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="1d3bc-272">Emacs: `<Alt+d>` , `<Escape,d>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-272">Emacs: `<Alt+d>`, `<Escape,d>`</span></span>
- <span data-ttu-id="1d3bc-273">Vi infognings läge: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-273">Vi insert mode: `<Ctrl+Delete>`</span></span>
- <span data-ttu-id="1d3bc-274">Kommando läge för vi: `<Ctrl+Delete>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-274">Vi command mode: `<Ctrl+Delete>`</span></span>

### <a name="paste"></a><span data-ttu-id="1d3bc-275">Klistra in</span><span class="sxs-lookup"><span data-stu-id="1d3bc-275">Paste</span></span>

<span data-ttu-id="1d3bc-276">Klistra in text från Urklipp i systemet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-276">Paste text from the system clipboard.</span></span>

- <span data-ttu-id="1d3bc-277">CMD: `<Ctrl+v>` , `<Shift+Insert>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-277">Cmd: `<Ctrl+v>`, `<Shift+Insert>`</span></span>
- <span data-ttu-id="1d3bc-278">Vi infognings läge: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-278">Vi insert mode: `<Ctrl+v>`</span></span>
- <span data-ttu-id="1d3bc-279">Kommando läge för vi: `<Ctrl+v>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-279">Vi command mode: `<Ctrl+v>`</span></span>

> [!IMPORTANT]
> <span data-ttu-id="1d3bc-280">När du använder funktionen **Klistra** in klistras hela innehållet i bufferten i Urklipp in i indatabufferten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-280">When using the **Paste** function, the entire contents of the clipboard buffer is pasted into the input buffer of PSReadLine.</span></span> <span data-ttu-id="1d3bc-281">Indatabufferten skickas sedan till PowerShell-parsern.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-281">The input buffer is then passed to the PowerShell parser.</span></span> <span data-ttu-id="1d3bc-282">Inklistrade inklistrade med hjälp av konsol programmet **högerklickar du på** klistra in-metoden och kopierar den till indatabufferten ett i taget.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-282">Input pasted using the console application's **right-click** paste method is copied to the input buffer one character at a time.</span></span> <span data-ttu-id="1d3bc-283">Indatabufferten skickas till parsern när ett rad matnings tecknet kopieras.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-283">The input buffer is passed to the parser when a newline character is copied.</span></span> <span data-ttu-id="1d3bc-284">Därför parsas inmatarna en rad i taget.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-284">Therefore, the input is parsed one line at a time.</span></span> <span data-ttu-id="1d3bc-285">Skillnaden mellan Inklistrings metoder resulterar i olika körnings beteenden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-285">The difference between paste methods results in different execution behavior.</span></span>

### <a name="pasteafter"></a><span data-ttu-id="1d3bc-286">PasteAfter</span><span class="sxs-lookup"><span data-stu-id="1d3bc-286">PasteAfter</span></span>

<span data-ttu-id="1d3bc-287">Klistra in Urklipp efter markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-287">Paste the clipboard after the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="1d3bc-288">Kommando läge för vi: `<p>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-288">Vi command mode: `<p>`</span></span>

### <a name="pastebefore"></a><span data-ttu-id="1d3bc-289">PasteBefore</span><span class="sxs-lookup"><span data-stu-id="1d3bc-289">PasteBefore</span></span>

<span data-ttu-id="1d3bc-290">Klistra in Urklipp före markören och flytta markören till slutet av den inklistrade texten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-290">Paste the clipboard before the cursor, moving the cursor to the end of the pasted text.</span></span>

- <span data-ttu-id="1d3bc-291">Kommando läge för vi: `<P>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-291">Vi command mode: `<P>`</span></span>

### <a name="prependandaccept"></a><span data-ttu-id="1d3bc-292">PrependAndAccept</span><span class="sxs-lookup"><span data-stu-id="1d3bc-292">PrependAndAccept</span></span>

<span data-ttu-id="1d3bc-293">Lägga a # och acceptera raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-293">Prepend a '#' and accept the line.</span></span>

- <span data-ttu-id="1d3bc-294">Kommando läge för vi: `<#>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-294">Vi command mode: `<#>`</span></span>

### <a name="redo"></a><span data-ttu-id="1d3bc-295">Gör om</span><span class="sxs-lookup"><span data-stu-id="1d3bc-295">Redo</span></span>

<span data-ttu-id="1d3bc-296">Ångra en ångra-åtgärd.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-296">Undo an undo.</span></span>

- <span data-ttu-id="1d3bc-297">Kommandot `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-297">Cmd: `<Ctrl+y>`</span></span>
- <span data-ttu-id="1d3bc-298">Vi infognings läge: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-298">Vi insert mode: `<Ctrl+y>`</span></span>
- <span data-ttu-id="1d3bc-299">Kommando läge för vi: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-299">Vi command mode: `<Ctrl+y>`</span></span>

### <a name="repeatlastcommand"></a><span data-ttu-id="1d3bc-300">RepeatLastCommand</span><span class="sxs-lookup"><span data-stu-id="1d3bc-300">RepeatLastCommand</span></span>

<span data-ttu-id="1d3bc-301">Upprepa den senaste text ändringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-301">Repeat the last text modification.</span></span>

- <span data-ttu-id="1d3bc-302">Kommando läge för vi: `<.>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-302">Vi command mode: `<.>`</span></span>

### <a name="revertline"></a><span data-ttu-id="1d3bc-303">RevertLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-303">RevertLine</span></span>

<span data-ttu-id="1d3bc-304">Återställer alla inaktuella inaktuella inaktuella inaktuella ingångar.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-304">Reverts all of the input to the current input.</span></span>

- <span data-ttu-id="1d3bc-305">Kommandot `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-305">Cmd: `<Escape>`</span></span>
- <span data-ttu-id="1d3bc-306">Emacs: `<Alt+r>` , `<Escape,r>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-306">Emacs: `<Alt+r>`, `<Escape,r>`</span></span>

### <a name="shellbackwardkillword"></a><span data-ttu-id="1d3bc-307">ShellBackwardKillWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-307">ShellBackwardKillWord</span></span>

<span data-ttu-id="1d3bc-308">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-308">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1d3bc-309">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-309">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1d3bc-310">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-310">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="1d3bc-311">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-311">Function is unbound.</span></span>

### <a name="shellkillword"></a><span data-ttu-id="1d3bc-312">ShellKillWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-312">ShellKillWord</span></span>

<span data-ttu-id="1d3bc-313">Ta bort indatamängden från markören till slutet av det aktuella ordet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-313">Clear the input from the cursor to the end of the current word.</span></span> <span data-ttu-id="1d3bc-314">Om markören är mellan ord raderas indatatypen från markören till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-314">If the cursor is between words, the input is cleared from the cursor to the end of the next word.</span></span> <span data-ttu-id="1d3bc-315">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-315">The cleared text is placed in the kill-ring.</span></span>

<span data-ttu-id="1d3bc-316">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-316">Function is unbound.</span></span>

### <a name="swapcharacters"></a><span data-ttu-id="1d3bc-317">SwapCharacters</span><span class="sxs-lookup"><span data-stu-id="1d3bc-317">SwapCharacters</span></span>

<span data-ttu-id="1d3bc-318">Byt det aktuella tecknen och det som är före det.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-318">Swap the current character and the one before it.</span></span>

- <span data-ttu-id="1d3bc-319">Emacs: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-319">Emacs: `<Ctrl+t>`</span></span>
- <span data-ttu-id="1d3bc-320">Vi infognings läge: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-320">Vi insert mode: `<Ctrl+t>`</span></span>
- <span data-ttu-id="1d3bc-321">Kommando läge för vi: `<Ctrl+t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-321">Vi command mode: `<Ctrl+t>`</span></span>

### <a name="undo"></a><span data-ttu-id="1d3bc-322">Ångra</span><span class="sxs-lookup"><span data-stu-id="1d3bc-322">Undo</span></span>

<span data-ttu-id="1d3bc-323">Ångra en tidigare redigering.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-323">Undo a previous edit.</span></span>

- <span data-ttu-id="1d3bc-324">Kommandot `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-324">Cmd: `<Ctrl+z>`</span></span>
- <span data-ttu-id="1d3bc-325">Emacs: `<Ctrl+_>` , `<Ctrl+x,Ctrl+u>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-325">Emacs: `<Ctrl+_>`, `<Ctrl+x,Ctrl+u>`</span></span>
- <span data-ttu-id="1d3bc-326">Vi infognings läge: `<Ctrl+z>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-326">Vi insert mode: `<Ctrl+z>`</span></span>
- <span data-ttu-id="1d3bc-327">Kommando läge för vi: `<Ctrl+z>` , `<u>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-327">Vi command mode: `<Ctrl+z>`, `<u>`</span></span>

### <a name="undoall"></a><span data-ttu-id="1d3bc-328">UndoAll</span><span class="sxs-lookup"><span data-stu-id="1d3bc-328">UndoAll</span></span>

<span data-ttu-id="1d3bc-329">Ångra alla tidigare redigeringar för raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-329">Undo all previous edits for line.</span></span>

- <span data-ttu-id="1d3bc-330">Kommando läge för vi: `<U>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-330">Vi command mode: `<U>`</span></span>

### <a name="unixwordrubout"></a><span data-ttu-id="1d3bc-331">UnixWordRubout</span><span class="sxs-lookup"><span data-stu-id="1d3bc-331">UnixWordRubout</span></span>

<span data-ttu-id="1d3bc-332">Ta bort indatamängden från början av det aktuella ordet till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-332">Clear the input from the start of the current word to the cursor.</span></span> <span data-ttu-id="1d3bc-333">Om markören är mellan ord raderas indatatypen från början av föregående ord till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-333">If the cursor is between words, the input is cleared from the start of the previous word to the cursor.</span></span> <span data-ttu-id="1d3bc-334">Den avmarkerade texten placeras i stopp ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-334">The cleared text is placed in the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-335">Emacs: `<Ctrl+w>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-335">Emacs: `<Ctrl+w>`</span></span>

### <a name="validateandacceptline"></a><span data-ttu-id="1d3bc-336">ValidateAndAcceptLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-336">ValidateAndAcceptLine</span></span>

<span data-ttu-id="1d3bc-337">Försök att köra den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-337">Attempt to execute the current input.</span></span> <span data-ttu-id="1d3bc-338">Om den aktuella indatamängden är ofullständig (till exempel om en avslutande parentes, hak paren tes eller citat tecken saknas, visas fortsättnings frågan på nästa rad och PSReadLine väntar på att nycklar ska redigera den aktuella indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-338">If the current input is incomplete (for example there is a missing closing parenthesis, bracket, or quote, then the continuation prompt is displayed on the next line and PSReadLine waits for keys to edit the current input.</span></span>

- <span data-ttu-id="1d3bc-339">Emacs: `<Ctrl+m>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-339">Emacs: `<Ctrl+m>`</span></span>

### <a name="viacceptline"></a><span data-ttu-id="1d3bc-340">ViAcceptLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-340">ViAcceptLine</span></span>

<span data-ttu-id="1d3bc-341">Godkänn linjen och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-341">Accept the line and switch to Insert mode.</span></span>

- <span data-ttu-id="1d3bc-342">Kommando läge för vi: `<Enter>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-342">Vi command mode: `<Enter>`</span></span>

### <a name="viacceptlineorexit"></a><span data-ttu-id="1d3bc-343">ViAcceptLineOrExit</span><span class="sxs-lookup"><span data-stu-id="1d3bc-343">ViAcceptLineOrExit</span></span>

<span data-ttu-id="1d3bc-344">Som DeleteCharOrExit i emacs-läge, men accepterar raden i stället för att ta bort ett Character.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-344">Like DeleteCharOrExit in Emacs mode, but accepts the line instead of deleting a character.</span></span>

- <span data-ttu-id="1d3bc-345">Vi infognings läge: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-345">Vi insert mode: `<Ctrl+d>`</span></span>
- <span data-ttu-id="1d3bc-346">Kommando läge för vi: `<Ctrl+d>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-346">Vi command mode: `<Ctrl+d>`</span></span>

### <a name="viappendline"></a><span data-ttu-id="1d3bc-347">ViAppendLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-347">ViAppendLine</span></span>

<span data-ttu-id="1d3bc-348">En ny rad infogas under den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-348">A new line is inserted below the current line.</span></span>

- <span data-ttu-id="1d3bc-349">Kommando läge för vi: `<o>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-349">Vi command mode: `<o>`</span></span>

### <a name="vibackwarddeleteglob"></a><span data-ttu-id="1d3bc-350">ViBackwardDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-350">ViBackwardDeleteGlob</span></span>

<span data-ttu-id="1d3bc-351">Tar bort föregående ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-351">Deletes the previous word, using only white space as the word delimiter.</span></span>

- <span data-ttu-id="1d3bc-352">Kommando läge för vi: `<d,B>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-352">Vi command mode: `<d,B>`</span></span>

### <a name="vibackwardglob"></a><span data-ttu-id="1d3bc-353">ViBackwardGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-353">ViBackwardGlob</span></span>

<span data-ttu-id="1d3bc-354">Flyttar tillbaka markören till början av föregående ord, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-354">Moves the cursor back to the beginning of the previous word, using only white space as delimiters.</span></span>

- <span data-ttu-id="1d3bc-355">Kommando läge för vi: `<B>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-355">Vi command mode: `<B>`</span></span>

### <a name="videletebrace"></a><span data-ttu-id="1d3bc-356">ViDeleteBrace</span><span class="sxs-lookup"><span data-stu-id="1d3bc-356">ViDeleteBrace</span></span>

<span data-ttu-id="1d3bc-357">Hitta den matchande klammerparentesen, parentesen eller hakparentesen och ta bort allt innehåll inom, inklusive klammerparentesen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-357">Find the matching brace, parenthesis, or square bracket and delete all contents within, including the brace.</span></span>

- <span data-ttu-id="1d3bc-358">Kommando läge för vi: `<d,%>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-358">Vi command mode: `<d,%>`</span></span>

### <a name="videleteendofglob"></a><span data-ttu-id="1d3bc-359">ViDeleteEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-359">ViDeleteEndOfGlob</span></span>

<span data-ttu-id="1d3bc-360">Ta bort till slutet av ordet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-360">Delete to the end of the word.</span></span>

- <span data-ttu-id="1d3bc-361">Kommando läge för vi: `<d,E>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-361">Vi command mode: `<d,E>`</span></span>

### <a name="videleteglob"></a><span data-ttu-id="1d3bc-362">ViDeleteGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-362">ViDeleteGlob</span></span>

<span data-ttu-id="1d3bc-363">Ta bort nästa BLOB (tomt blank steg).</span><span class="sxs-lookup"><span data-stu-id="1d3bc-363">Delete the next glob (white space delimited word).</span></span>

- <span data-ttu-id="1d3bc-364">Kommando läge för vi: `<d,W>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-364">Vi command mode: `<d,W>`</span></span>

### <a name="videletetobeforechar"></a><span data-ttu-id="1d3bc-365">ViDeleteToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-365">ViDeleteToBeforeChar</span></span>

<span data-ttu-id="1d3bc-366">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-366">Deletes until given character.</span></span>

- <span data-ttu-id="1d3bc-367">Kommando läge för vi: `<d,t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-367">Vi command mode: `<d,t>`</span></span>

### <a name="videletetobeforecharbackward"></a><span data-ttu-id="1d3bc-368">ViDeleteToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-368">ViDeleteToBeforeCharBackward</span></span>

<span data-ttu-id="1d3bc-369">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-369">Deletes until given character.</span></span>

- <span data-ttu-id="1d3bc-370">Kommando läge för vi: `<d,T>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-370">Vi command mode: `<d,T>`</span></span>

### <a name="videletetochar"></a><span data-ttu-id="1d3bc-371">ViDeleteToChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-371">ViDeleteToChar</span></span>

<span data-ttu-id="1d3bc-372">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-372">Deletes until given character.</span></span>

- <span data-ttu-id="1d3bc-373">Kommando läge för vi: `<d,f>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-373">Vi command mode: `<d,f>`</span></span>

### <a name="videletetocharbackward"></a><span data-ttu-id="1d3bc-374">ViDeleteToCharBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-374">ViDeleteToCharBackward</span></span>

<span data-ttu-id="1d3bc-375">Tar bort baklänges tills angivet format.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-375">Deletes backwards until given character.</span></span>

- <span data-ttu-id="1d3bc-376">Kommando läge för vi: `<d,F>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-376">Vi command mode: `<d,F>`</span></span>

### <a name="viinsertatbegining"></a><span data-ttu-id="1d3bc-377">ViInsertAtBegining</span><span class="sxs-lookup"><span data-stu-id="1d3bc-377">ViInsertAtBegining</span></span>

<span data-ttu-id="1d3bc-378">Växla till infognings läge och placera markören i början av raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-378">Switch to Insert mode and position the cursor at the beginning of the line.</span></span>

- <span data-ttu-id="1d3bc-379">Kommando läge för vi: `<I>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-379">Vi command mode: `<I>`</span></span>

### <a name="viinsertatend"></a><span data-ttu-id="1d3bc-380">ViInsertAtEnd</span><span class="sxs-lookup"><span data-stu-id="1d3bc-380">ViInsertAtEnd</span></span>

<span data-ttu-id="1d3bc-381">Växla till infognings läge och placera markören i slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-381">Switch to Insert mode and position the cursor at the end of the line.</span></span>

- <span data-ttu-id="1d3bc-382">Kommando läge för vi: `<A>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-382">Vi command mode: `<A>`</span></span>

### <a name="viinsertline"></a><span data-ttu-id="1d3bc-383">ViInsertLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-383">ViInsertLine</span></span>

<span data-ttu-id="1d3bc-384">En ny rad infogas ovanför den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-384">A new line is inserted above the current line.</span></span>

- <span data-ttu-id="1d3bc-385">Kommando läge för vi: `<O>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-385">Vi command mode: `<O>`</span></span>

### <a name="viinsertwithappend"></a><span data-ttu-id="1d3bc-386">ViInsertWithAppend</span><span class="sxs-lookup"><span data-stu-id="1d3bc-386">ViInsertWithAppend</span></span>

<span data-ttu-id="1d3bc-387">Lägg till från den aktuella rad positionen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-387">Append from the current line position.</span></span>

- <span data-ttu-id="1d3bc-388">Kommando läge för vi: `<a>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-388">Vi command mode: `<a>`</span></span>

### <a name="viinsertwithdelete"></a><span data-ttu-id="1d3bc-389">ViInsertWithDelete</span><span class="sxs-lookup"><span data-stu-id="1d3bc-389">ViInsertWithDelete</span></span>

<span data-ttu-id="1d3bc-390">Ta bort det aktuella specialtecknet och växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-390">Delete the current character and switch to Insert mode.</span></span>

- <span data-ttu-id="1d3bc-391">Kommando läge för vi: `<s>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-391">Vi command mode: `<s>`</span></span>

### <a name="vijoinlines"></a><span data-ttu-id="1d3bc-392">ViJoinLines</span><span class="sxs-lookup"><span data-stu-id="1d3bc-392">ViJoinLines</span></span>

<span data-ttu-id="1d3bc-393">Kopplar ihop den aktuella raden och nästa rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-393">Joins the current line and the next line.</span></span>

- <span data-ttu-id="1d3bc-394">Kommando läge för vi: `<J>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-394">Vi command mode: `<J>`</span></span>

### <a name="vireplaceline"></a><span data-ttu-id="1d3bc-395">ViReplaceLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-395">ViReplaceLine</span></span>

<span data-ttu-id="1d3bc-396">Ta bort hela kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-396">Erase the entire command line.</span></span>

- <span data-ttu-id="1d3bc-397">Kommando läge för vi: `<S>` , `<c,c>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-397">Vi command mode: `<S>`, `<c,c>`</span></span>

### <a name="vireplacetobeforechar"></a><span data-ttu-id="1d3bc-398">ViReplaceToBeforeChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-398">ViReplaceToBeforeChar</span></span>

<span data-ttu-id="1d3bc-399">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-399">Replaces until given character.</span></span>

- <span data-ttu-id="1d3bc-400">Kommando läge för vi: `<c,t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-400">Vi command mode: `<c,t>`</span></span>

### <a name="vireplacetobeforecharbackward"></a><span data-ttu-id="1d3bc-401">ViReplaceToBeforeCharBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-401">ViReplaceToBeforeCharBackward</span></span>

<span data-ttu-id="1d3bc-402">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-402">Replaces until given character.</span></span>

- <span data-ttu-id="1d3bc-403">Kommando läge för vi: `<c,T>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-403">Vi command mode: `<c,T>`</span></span>

### <a name="vireplacetochar"></a><span data-ttu-id="1d3bc-404">ViReplaceToChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-404">ViReplaceToChar</span></span>

<span data-ttu-id="1d3bc-405">Raderas tills det tilldelas ett blank steg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-405">Deletes until given character.</span></span>

- <span data-ttu-id="1d3bc-406">Kommando läge för vi: `<c,f>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-406">Vi command mode: `<c,f>`</span></span>

### <a name="vireplacetocharbackward"></a><span data-ttu-id="1d3bc-407">ViReplaceToCharBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-407">ViReplaceToCharBackward</span></span>

<span data-ttu-id="1d3bc-408">Ersätter det tilldelade specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-408">Replaces until given character.</span></span>

- <span data-ttu-id="1d3bc-409">Kommando läge för vi: `<c,F>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-409">Vi command mode: `<c,F>`</span></span>

### <a name="viyankbeginningofline"></a><span data-ttu-id="1d3bc-410">ViYankBeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-410">ViYankBeginningOfLine</span></span>

<span data-ttu-id="1d3bc-411">YANK från buffertens början till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-411">Yank from the beginning of the buffer to the cursor.</span></span>

- <span data-ttu-id="1d3bc-412">Kommando läge för vi: `<y,0>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-412">Vi command mode: `<y,0>`</span></span>

### <a name="viyankendofglob"></a><span data-ttu-id="1d3bc-413">ViYankEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-413">ViYankEndOfGlob</span></span>

<span data-ttu-id="1d3bc-414">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-414">Yank from the cursor to the end of the WORD(s).</span></span>

- <span data-ttu-id="1d3bc-415">Kommando läge för vi: `<y,E>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-415">Vi command mode: `<y,E>`</span></span>

### <a name="viyankendofword"></a><span data-ttu-id="1d3bc-416">ViYankEndOfWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-416">ViYankEndOfWord</span></span>

<span data-ttu-id="1d3bc-417">YANK från markören till slutet av ordet/orden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-417">Yank from the cursor to the end of the word(s).</span></span>

- <span data-ttu-id="1d3bc-418">Kommando läge för vi: `<y,e>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-418">Vi command mode: `<y,e>`</span></span>

### <a name="viyankleft"></a><span data-ttu-id="1d3bc-419">ViYankLeft</span><span class="sxs-lookup"><span data-stu-id="1d3bc-419">ViYankLeft</span></span>

<span data-ttu-id="1d3bc-420">YANK-tecknen till vänster om markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-420">Yank character(s) to the left of the cursor.</span></span>

- <span data-ttu-id="1d3bc-421">Kommando läge för vi: `<y,h>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-421">Vi command mode: `<y,h>`</span></span>

### <a name="viyankline"></a><span data-ttu-id="1d3bc-422">ViYankLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-422">ViYankLine</span></span>

<span data-ttu-id="1d3bc-423">YANK hela bufferten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-423">Yank the entire buffer.</span></span>

- <span data-ttu-id="1d3bc-424">Kommando läge för vi: `<y,y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-424">Vi command mode: `<y,y>`</span></span>

### <a name="viyanknextglob"></a><span data-ttu-id="1d3bc-425">ViYankNextGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-425">ViYankNextGlob</span></span>

<span data-ttu-id="1d3bc-426">YANK från markören till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-426">Yank from cursor to the start of the next WORD(s).</span></span>

- <span data-ttu-id="1d3bc-427">Kommando läge för vi: `<y,W>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-427">Vi command mode: `<y,W>`</span></span>

### <a name="viyanknextword"></a><span data-ttu-id="1d3bc-428">ViYankNextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-428">ViYankNextWord</span></span>

<span data-ttu-id="1d3bc-429">YANK ordet (s) efter markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-429">Yank the word(s) after the cursor.</span></span>

- <span data-ttu-id="1d3bc-430">Kommando läge för vi: `<y,w>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-430">Vi command mode: `<y,w>`</span></span>

### <a name="viyankpercent"></a><span data-ttu-id="1d3bc-431">ViYankPercent</span><span class="sxs-lookup"><span data-stu-id="1d3bc-431">ViYankPercent</span></span>

<span data-ttu-id="1d3bc-432">YANK till/från matchande klammerparentes.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-432">Yank to/from matching brace.</span></span>

- <span data-ttu-id="1d3bc-433">Kommando läge för vi: `<y,%>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-433">Vi command mode: `<y,%>`</span></span>

### <a name="viyankpreviousglob"></a><span data-ttu-id="1d3bc-434">ViYankPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-434">ViYankPreviousGlob</span></span>

<span data-ttu-id="1d3bc-435">YANK från början av ordet/orden till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-435">Yank from beginning of the WORD(s) to cursor.</span></span>

- <span data-ttu-id="1d3bc-436">Kommando läge för vi: `<y,B>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-436">Vi command mode: `<y,B>`</span></span>

### <a name="viyankpreviousword"></a><span data-ttu-id="1d3bc-437">ViYankPreviousWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-437">ViYankPreviousWord</span></span>

<span data-ttu-id="1d3bc-438">YANK ordet (s) före markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-438">Yank the word(s) before the cursor.</span></span>

- <span data-ttu-id="1d3bc-439">Kommando läge för vi: `<y,b>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-439">Vi command mode: `<y,b>`</span></span>

### <a name="viyankright"></a><span data-ttu-id="1d3bc-440">ViYankRight</span><span class="sxs-lookup"><span data-stu-id="1d3bc-440">ViYankRight</span></span>

<span data-ttu-id="1d3bc-441">YANK-tecknen under och till höger om markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-441">Yank character(s) under and to the right of the cursor.</span></span>

- <span data-ttu-id="1d3bc-442">Kommando läge för vi: `<y,l>` , `<y,Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-442">Vi command mode: `<y,l>`, `<y,Spacebar>`</span></span>

### <a name="viyanktoendofline"></a><span data-ttu-id="1d3bc-443">ViYankToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-443">ViYankToEndOfLine</span></span>

<span data-ttu-id="1d3bc-444">YANK från markören till slutet av bufferten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-444">Yank from the cursor to the end of the buffer.</span></span>

- <span data-ttu-id="1d3bc-445">Kommando läge för vi: `<y,$>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-445">Vi command mode: `<y,$>`</span></span>

### <a name="viyanktofirstchar"></a><span data-ttu-id="1d3bc-446">ViYankToFirstChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-446">ViYankToFirstChar</span></span>

<span data-ttu-id="1d3bc-447">YANK från det första icke-tomt-tecken till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-447">Yank from the first non-whitespace character to the cursor.</span></span>

- <span data-ttu-id="1d3bc-448">Kommando läge för vi: `<y,^>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-448">Vi command mode: `<y,^>`</span></span>

### <a name="yank"></a><span data-ttu-id="1d3bc-449">Yank</span><span class="sxs-lookup"><span data-stu-id="1d3bc-449">Yank</span></span>

<span data-ttu-id="1d3bc-450">Lägg till den senast nedlagda texten i indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-450">Add the most recently killed text to the input.</span></span>

- <span data-ttu-id="1d3bc-451">Emacs: `<Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-451">Emacs: `<Ctrl+y>`</span></span>

### <a name="yanklastarg"></a><span data-ttu-id="1d3bc-452">YankLastArg</span><span class="sxs-lookup"><span data-stu-id="1d3bc-452">YankLastArg</span></span>

<span data-ttu-id="1d3bc-453">YANK det sista argumentet från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-453">Yank the last argument from the previous history line.</span></span> <span data-ttu-id="1d3bc-454">Med ett argument fungerar den första gången som den anropas, precis som YankNthArg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-454">With an argument, the first time it is invoked, behaves just like YankNthArg.</span></span> <span data-ttu-id="1d3bc-455">Om anropas flera gånger, så upprepas det genom historik och argument anger riktningen (negativa kastar om riktningen).</span><span class="sxs-lookup"><span data-stu-id="1d3bc-455">If invoked multiple times, instead it iterates through history and arg sets the direction (negative reverses the direction.)</span></span>

- <span data-ttu-id="1d3bc-456">Kommandot `<Alt+.>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-456">Cmd: `<Alt+.>`</span></span>
- <span data-ttu-id="1d3bc-457">Emacs: `<Alt+.>` , `<Alt+_>` , `<Escape,.>` , `<Escape,_>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-457">Emacs: `<Alt+.>`, `<Alt+_>`, `<Escape,.>`, `<Escape,_>`</span></span>

### <a name="yankntharg"></a><span data-ttu-id="1d3bc-458">YankNthArg</span><span class="sxs-lookup"><span data-stu-id="1d3bc-458">YankNthArg</span></span>

<span data-ttu-id="1d3bc-459">YANK det första argumentet (efter kommandot) från föregående historik rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-459">Yank the first argument (after the command) from the previous history line.</span></span>
<span data-ttu-id="1d3bc-460">Med ett argument, YANK det n:te argumentet (från 0) om argumentet är negativt, startar du från det sista argumentet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-460">With an argument, yank the nth argument (starting from 0), if the argument is negative, start from the last argument.</span></span>

- <span data-ttu-id="1d3bc-461">Emacs: `<Ctrl+Alt+y>` , `<Escape,Ctrl+y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-461">Emacs: `<Ctrl+Alt+y>`, `<Escape,Ctrl+y>`</span></span>

### <a name="yankpop"></a><span data-ttu-id="1d3bc-462">YankPop</span><span class="sxs-lookup"><span data-stu-id="1d3bc-462">YankPop</span></span>

<span data-ttu-id="1d3bc-463">Om den föregående åtgärden var YANK eller YankPop ersätter du den tidigare yanked-texten med nästa nedstängda text från stopp-ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-463">If the previous operation was Yank or YankPop, replace the previously yanked text with the next killed text from the kill-ring.</span></span>

- <span data-ttu-id="1d3bc-464">Emacs: `<Alt+y>` , `<Escape,y>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-464">Emacs: `<Alt+y>`, `<Escape,y>`</span></span>

## <a name="cursor-movement-functions"></a><span data-ttu-id="1d3bc-465">Markör rörelse funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-465">Cursor movement functions</span></span>

### <a name="backwardchar"></a><span data-ttu-id="1d3bc-466">BackwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-466">BackwardChar</span></span>

<span data-ttu-id="1d3bc-467">Flytta markören ett till vänster.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-467">Move the cursor one character to the left.</span></span> <span data-ttu-id="1d3bc-468">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-468">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="1d3bc-469">Kommandot `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-469">Cmd: `<LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-470">Emacs: `<LeftArrow>` , `<Ctrl+b>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-470">Emacs: `<LeftArrow>`, `<Ctrl+b>`</span></span>

### <a name="backwardword"></a><span data-ttu-id="1d3bc-471">BackwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-471">BackwardWord</span></span>

<span data-ttu-id="1d3bc-472">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-472">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1d3bc-473">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-473">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-474">Kommandot `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-474">Cmd: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-475">Emacs: `<Alt+b>` , `<Escape,b>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-475">Emacs: `<Alt+b>`, `<Escape,b>`</span></span>
- <span data-ttu-id="1d3bc-476">Vi infognings läge: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-476">Vi insert mode: `<Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-477">Kommando läge för vi: `<Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-477">Vi command mode: `<Ctrl+LeftArrow>`</span></span>

### <a name="beginningofline"></a><span data-ttu-id="1d3bc-478">BeginningOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-478">BeginningOfLine</span></span>

<span data-ttu-id="1d3bc-479">Om indatamängden har flera rader flyttar du till början av den aktuella raden, eller om den redan är i början av raden, flyttas du till början av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-479">If the input has multiple lines, move to the start of the current line, or if already at the start of the line, move to the start of the input.</span></span> <span data-ttu-id="1d3bc-480">Om indatamängden har en enda rad flyttar du till början av inmatade värden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-480">If the input has a single line, move to the start of the input.</span></span>

- <span data-ttu-id="1d3bc-481">Kommandot `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-481">Cmd: `<Home>`</span></span>
- <span data-ttu-id="1d3bc-482">Emacs: `<Home>` , `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-482">Emacs: `<Home>`, `<Ctrl+a>`</span></span>
- <span data-ttu-id="1d3bc-483">Vi infognings läge: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-483">Vi insert mode: `<Home>`</span></span>
- <span data-ttu-id="1d3bc-484">Kommando läge för vi: `<Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-484">Vi command mode: `<Home>`</span></span>

### <a name="endofline"></a><span data-ttu-id="1d3bc-485">EndOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-485">EndOfLine</span></span>

<span data-ttu-id="1d3bc-486">Om indatamängden har flera rader flyttar du till slutet av den aktuella raden, eller om den redan är i slutet av raden, flyttas till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-486">If the input has multiple lines, move to the end of the current line, or if already at the end of the line, move to the end of the input.</span></span> <span data-ttu-id="1d3bc-487">Om indatamängden har en enda rad, går du till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-487">If the input has a single line, move to the end of the input.</span></span>

- <span data-ttu-id="1d3bc-488">Kommandot `<End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-488">Cmd: `<End>`</span></span>
- <span data-ttu-id="1d3bc-489">Emacs: `<End>` , `<Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-489">Emacs: `<End>`, `<Ctrl+e>`</span></span>
- <span data-ttu-id="1d3bc-490">Vi infognings läge: `<End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-490">Vi insert mode: `<End>`</span></span>

### <a name="forwardchar"></a><span data-ttu-id="1d3bc-491">ForwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-491">ForwardChar</span></span>

<span data-ttu-id="1d3bc-492">Flytta markören ett till höger.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-492">Move the cursor one character to the right.</span></span> <span data-ttu-id="1d3bc-493">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-493">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="1d3bc-494">Kommandot `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-494">Cmd: `<RightArrow>`</span></span>
- <span data-ttu-id="1d3bc-495">Emacs: `<RightArrow>` , `<Ctrl+f>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-495">Emacs: `<RightArrow>`, `<Ctrl+f>`</span></span>

### <a name="forwardword"></a><span data-ttu-id="1d3bc-496">ForwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-496">ForwardWord</span></span>

<span data-ttu-id="1d3bc-497">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-497">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1d3bc-498">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-498">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-499">Emacs: `<Alt+f>` , `<Escape,f>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-499">Emacs: `<Alt+f>`, `<Escape,f>`</span></span>

### <a name="gotobrace"></a><span data-ttu-id="1d3bc-500">GotoBrace</span><span class="sxs-lookup"><span data-stu-id="1d3bc-500">GotoBrace</span></span>

<span data-ttu-id="1d3bc-501">Gå till den matchande klammerparentesen, parentesen eller hakparentesen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-501">Go to the matching brace, parenthesis, or square bracket.</span></span>

- <span data-ttu-id="1d3bc-502">Kommandot `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-502">Cmd: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1d3bc-503">Vi infognings läge: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-503">Vi insert mode: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1d3bc-504">Kommando läge för vi: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-504">Vi command mode: `<Ctrl+]>`</span></span>

### <a name="gotocolumn"></a><span data-ttu-id="1d3bc-505">GotoColumn</span><span class="sxs-lookup"><span data-stu-id="1d3bc-505">GotoColumn</span></span>

<span data-ttu-id="1d3bc-506">Flytta till kolumnen som anges av arg.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-506">Move to the column indicated by arg.</span></span>

- <span data-ttu-id="1d3bc-507">Kommando läge för vi: `<|>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-507">Vi command mode: `<|>`</span></span>

### <a name="gotofirstnonblankofline"></a><span data-ttu-id="1d3bc-508">GotoFirstNonBlankOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-508">GotoFirstNonBlankOfLine</span></span>

<span data-ttu-id="1d3bc-509">Flytta markören till det första icke-tomma tecken på raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-509">Move the cursor to the first non-blank character in the line.</span></span>

- <span data-ttu-id="1d3bc-510">Kommando läge för vi: `<^>` , `<_>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-510">Vi command mode: `<^>`, `<_>`</span></span>

### <a name="movetoendofline"></a><span data-ttu-id="1d3bc-511">MoveToEndOfLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-511">MoveToEndOfLine</span></span>

<span data-ttu-id="1d3bc-512">Flytta markören till slutet av indatamängden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-512">Move the cursor to the end of the input.</span></span>

- <span data-ttu-id="1d3bc-513">Kommando läge för vi: `<End>` , `<$>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-513">Vi command mode: `<End>`, `<$>`</span></span>

### <a name="nextline"></a><span data-ttu-id="1d3bc-514">NextLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-514">NextLine</span></span>

<span data-ttu-id="1d3bc-515">Flytta markören till nästa rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-515">Move the cursor to the next line.</span></span>

- <span data-ttu-id="1d3bc-516">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-516">Function is unbound.</span></span>

### <a name="nextword"></a><span data-ttu-id="1d3bc-517">NextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-517">NextWord</span></span>

<span data-ttu-id="1d3bc-518">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-518">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1d3bc-519">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-519">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-520">Kommandot `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-520">Cmd: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="1d3bc-521">Vi infognings läge: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-521">Vi insert mode: `<Ctrl+RightArrow>`</span></span>
- <span data-ttu-id="1d3bc-522">Kommando läge för vi: `<Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-522">Vi command mode: `<Ctrl+RightArrow>`</span></span>

### <a name="nextwordend"></a><span data-ttu-id="1d3bc-523">NextWordEnd</span><span class="sxs-lookup"><span data-stu-id="1d3bc-523">NextWordEnd</span></span>

<span data-ttu-id="1d3bc-524">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-524">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1d3bc-525">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-525">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-526">Kommando läge för vi: `<e>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-526">Vi command mode: `<e>`</span></span>

### <a name="previousline"></a><span data-ttu-id="1d3bc-527">PreviousLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-527">PreviousLine</span></span>

<span data-ttu-id="1d3bc-528">Flytta markören till föregående rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-528">Move the cursor to the previous line.</span></span>

- <span data-ttu-id="1d3bc-529">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-529">Function is unbound.</span></span>

### <a name="shellbackwardword"></a><span data-ttu-id="1d3bc-530">ShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-530">ShellBackwardWord</span></span>

<span data-ttu-id="1d3bc-531">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-531">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1d3bc-532">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-532">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1d3bc-533">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-533">Function is unbound.</span></span>

### <a name="shellforwardword"></a><span data-ttu-id="1d3bc-534">ShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-534">ShellForwardWord</span></span>

<span data-ttu-id="1d3bc-535">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-535">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1d3bc-536">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-536">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1d3bc-537">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-537">Function is unbound.</span></span>

### <a name="shellnextword"></a><span data-ttu-id="1d3bc-538">ShellNextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-538">ShellNextWord</span></span>

<span data-ttu-id="1d3bc-539">Flytta markören framåt till slutet av det aktuella ordet eller, om mellan orden, till slutet av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-539">Move the cursor forward to the end of the current word, or if between words, to the end of the next word.</span></span> <span data-ttu-id="1d3bc-540">Ord gränser definieras av PowerShell-token.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-540">Word boundaries are defined by PowerShell tokens.</span></span>

- <span data-ttu-id="1d3bc-541">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-541">Function is unbound.</span></span>

### <a name="vibackwardchar"></a><span data-ttu-id="1d3bc-542">ViBackwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-542">ViBackwardChar</span></span>

<span data-ttu-id="1d3bc-543">Flytta markören ett steg till vänster i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-543">Move the cursor one character to the left in the Vi edit mode.</span></span> <span data-ttu-id="1d3bc-544">Detta kan flytta markören till föregående rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-544">This may move the cursor to the previous line of multi-line input.</span></span>

- <span data-ttu-id="1d3bc-545">Vi infognings läge: `<LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-545">Vi insert mode: `<LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-546">Vi kommando läge: `<LeftArrow>` , `<Backspace>` , `<h>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-546">Vi command mode: `<LeftArrow>`, `<Backspace>`, `<h>`</span></span>

### <a name="vibackwardword"></a><span data-ttu-id="1d3bc-547">ViBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-547">ViBackwardWord</span></span>

<span data-ttu-id="1d3bc-548">Flytta markören tillbaka till början av det aktuella ordet eller, om mellan orden, början av föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-548">Move the cursor back to the start of the current word, or if between words, the start of the previous word.</span></span> <span data-ttu-id="1d3bc-549">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-549">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-550">Kommando läge för vi: `<b>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-550">Vi command mode: `<b>`</span></span>

### <a name="viforwardchar"></a><span data-ttu-id="1d3bc-551">ViForwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-551">ViForwardChar</span></span>

<span data-ttu-id="1d3bc-552">Flytta markören ett steg till höger i redigerings läget i vi.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-552">Move the cursor one character to the right in the Vi edit mode.</span></span> <span data-ttu-id="1d3bc-553">Detta kan flytta markören till nästa rad med flera rader.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-553">This may move the cursor to the next line of multi-line input.</span></span>

- <span data-ttu-id="1d3bc-554">Vi infognings läge: `<RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-554">Vi insert mode: `<RightArrow>`</span></span>
- <span data-ttu-id="1d3bc-555">Vi kommando läge: `<RightArrow>` , `<Spacebar>` , `<l>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-555">Vi command mode: `<RightArrow>`, `<Spacebar>`, `<l>`</span></span>

### <a name="viendofglob"></a><span data-ttu-id="1d3bc-556">ViEndOfGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-556">ViEndOfGlob</span></span>

<span data-ttu-id="1d3bc-557">Flyttar markören till slutet av ordet, med bara blank steg som avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-557">Moves the cursor to the end of the word, using only white space as delimiters.</span></span>

- <span data-ttu-id="1d3bc-558">Kommando läge för vi: `<E>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-558">Vi command mode: `<E>`</span></span>

### <a name="viendofpreviousglob"></a><span data-ttu-id="1d3bc-559">ViEndOfPreviousGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-559">ViEndOfPreviousGlob</span></span>

<span data-ttu-id="1d3bc-560">Flyttar till slutet av föregående ord, med bara blank steg som ett ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-560">Moves to the end of the previous word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="1d3bc-561">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-561">Function is unbound.</span></span>

### <a name="vigotobrace"></a><span data-ttu-id="1d3bc-562">ViGotoBrace</span><span class="sxs-lookup"><span data-stu-id="1d3bc-562">ViGotoBrace</span></span>

<span data-ttu-id="1d3bc-563">Liknar GotoBrace, men är ett tecken som baseras i stället för token-baserade.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-563">Similar to GotoBrace, but is character based instead of token based.</span></span>

- <span data-ttu-id="1d3bc-564">Kommando läge för vi: `<%>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-564">Vi command mode: `<%>`</span></span>

### <a name="vinextglob"></a><span data-ttu-id="1d3bc-565">ViNextGlob</span><span class="sxs-lookup"><span data-stu-id="1d3bc-565">ViNextGlob</span></span>

<span data-ttu-id="1d3bc-566">Flyttar till nästa ord, med bara blank steg som ord avgränsare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-566">Moves to the next word, using only white space as a word delimiter.</span></span>

- <span data-ttu-id="1d3bc-567">Kommando läge för vi: `<W>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-567">Vi command mode: `<W>`</span></span>

### <a name="vinextword"></a><span data-ttu-id="1d3bc-568">ViNextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-568">ViNextWord</span></span>

<span data-ttu-id="1d3bc-569">Flytta markören framåt till början av nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-569">Move the cursor forward to the start of the next word.</span></span> <span data-ttu-id="1d3bc-570">Ord gränser definieras med en konfigurerbar uppsättning tecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-570">Word boundaries are defined by a configurable set of characters.</span></span>

- <span data-ttu-id="1d3bc-571">Kommando läge för vi: `<w>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-571">Vi command mode: `<w>`</span></span>

## <a name="history-functions"></a><span data-ttu-id="1d3bc-572">Historik funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-572">History functions</span></span>

### <a name="beginningofhistory"></a><span data-ttu-id="1d3bc-573">BeginningOfHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-573">BeginningOfHistory</span></span>

<span data-ttu-id="1d3bc-574">Flytta till det första objektet i historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-574">Move to the first item in the history.</span></span>

- <span data-ttu-id="1d3bc-575">Emacs: `<Alt+<>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-575">Emacs: `<Alt+<>`</span></span>

### <a name="clearhistory"></a><span data-ttu-id="1d3bc-576">ClearHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-576">ClearHistory</span></span>

<span data-ttu-id="1d3bc-577">Rensar historiken i PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-577">Clears history in PSReadLine.</span></span> <span data-ttu-id="1d3bc-578">Detta påverkar inte PowerShell-historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-578">This does not affect PowerShell history.</span></span>

- <span data-ttu-id="1d3bc-579">Kommandot `<Alt+F7>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-579">Cmd: `<Alt+F7>`</span></span>

### <a name="endofhistory"></a><span data-ttu-id="1d3bc-580">EndOfHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-580">EndOfHistory</span></span>

<span data-ttu-id="1d3bc-581">Flytta till det sista objektet (den aktuella indatamängden) i historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-581">Move to the last item (the current input) in the history.</span></span>

- <span data-ttu-id="1d3bc-582">Emacs: `<Alt+>>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-582">Emacs: `<Alt+>>`</span></span>

### <a name="forwardsearchhistory"></a><span data-ttu-id="1d3bc-583">ForwardSearchHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-583">ForwardSearchHistory</span></span>

<span data-ttu-id="1d3bc-584">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-584">Perform an incremental forward search through history.</span></span>

- <span data-ttu-id="1d3bc-585">Kommandot `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-585">Cmd: `<Ctrl+s>`</span></span>
- <span data-ttu-id="1d3bc-586">Emacs: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-586">Emacs: `<Ctrl+s>`</span></span>

### <a name="historysearchbackward"></a><span data-ttu-id="1d3bc-587">HistorySearchBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-587">HistorySearchBackward</span></span>

<span data-ttu-id="1d3bc-588">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-588">Replace the current input with the 'previous' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="1d3bc-589">Kommandot `<F8>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-589">Cmd: `<F8>`</span></span>

### <a name="historysearchforward"></a><span data-ttu-id="1d3bc-590">HistorySearchForward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-590">HistorySearchForward</span></span>

<span data-ttu-id="1d3bc-591">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken som matchar tecknen mellan start och indatamängden och markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-591">Replace the current input with the 'next' item from PSReadLine history that matches the characters between the start and the input and the cursor.</span></span>

- <span data-ttu-id="1d3bc-592">Kommandot `<Shift+F8>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-592">Cmd: `<Shift+F8>`</span></span>

### <a name="nexthistory"></a><span data-ttu-id="1d3bc-593">NextHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-593">NextHistory</span></span>

<span data-ttu-id="1d3bc-594">Ersätt den aktuella indatamängden med objektet "Next" från PSReadLine-historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-594">Replace the current input with the 'next' item from PSReadLine history.</span></span>

- <span data-ttu-id="1d3bc-595">Kommandot `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-595">Cmd: `<DownArrow>`</span></span>
- <span data-ttu-id="1d3bc-596">Emacs: `<DownArrow>` , `<Ctrl+n>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-596">Emacs: `<DownArrow>`, `<Ctrl+n>`</span></span>
- <span data-ttu-id="1d3bc-597">Vi infognings läge: `<DownArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-597">Vi insert mode: `<DownArrow>`</span></span>
- <span data-ttu-id="1d3bc-598">Vi kommando läge: `<DownArrow>` , `<j>` , `<+>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-598">Vi command mode: `<DownArrow>`, `<j>`, `<+>`</span></span>

### <a name="previoushistory"></a><span data-ttu-id="1d3bc-599">PreviousHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-599">PreviousHistory</span></span>

<span data-ttu-id="1d3bc-600">Ersätt den aktuella indatamängden med det föregående objektet från PSReadLine historik.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-600">Replace the current input with the 'previous' item from PSReadLine history.</span></span>

- <span data-ttu-id="1d3bc-601">Kommandot `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-601">Cmd: `<UpArrow>`</span></span>
- <span data-ttu-id="1d3bc-602">Emacs: `<UpArrow>` , `<Ctrl+p>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-602">Emacs: `<UpArrow>`, `<Ctrl+p>`</span></span>
- <span data-ttu-id="1d3bc-603">Vi infognings läge: `<UpArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-603">Vi insert mode: `<UpArrow>`</span></span>
- <span data-ttu-id="1d3bc-604">Vi kommando läge: `<UpArrow>` , `<k>` , `<->`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-604">Vi command mode: `<UpArrow>`, `<k>`, `<->`</span></span>

### <a name="reversesearchhistory"></a><span data-ttu-id="1d3bc-605">ReverseSearchHistory</span><span class="sxs-lookup"><span data-stu-id="1d3bc-605">ReverseSearchHistory</span></span>

<span data-ttu-id="1d3bc-606">Utför en stegvis sökning i historiken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-606">Perform an incremental backward search through history.</span></span>

- <span data-ttu-id="1d3bc-607">Kommandot `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-607">Cmd: `<Ctrl+r>`</span></span>
- <span data-ttu-id="1d3bc-608">Emacs: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-608">Emacs: `<Ctrl+r>`</span></span>

### <a name="visearchhistorybackward"></a><span data-ttu-id="1d3bc-609">ViSearchHistoryBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-609">ViSearchHistoryBackward</span></span>

<span data-ttu-id="1d3bc-610">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-610">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="1d3bc-611">Vi infognings läge: `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-611">Vi insert mode: `<Ctrl+r>`</span></span>
- <span data-ttu-id="1d3bc-612">Kommando läge för vi: `</>` , `<Ctrl+r>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-612">Vi command mode: `</>`, `<Ctrl+r>`</span></span>

## <a name="completion-functions"></a><span data-ttu-id="1d3bc-613">Funktioner för slut för ande</span><span class="sxs-lookup"><span data-stu-id="1d3bc-613">Completion functions</span></span>

### <a name="complete"></a><span data-ttu-id="1d3bc-614">Klart</span><span class="sxs-lookup"><span data-stu-id="1d3bc-614">Complete</span></span>

<span data-ttu-id="1d3bc-615">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-615">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="1d3bc-616">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-616">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="1d3bc-617">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-617">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="1d3bc-618">Emacs: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-618">Emacs: `<Tab>`</span></span>

### <a name="menucomplete"></a><span data-ttu-id="1d3bc-619">MenuComplete</span><span class="sxs-lookup"><span data-stu-id="1d3bc-619">MenuComplete</span></span>

<span data-ttu-id="1d3bc-620">Försök att utföra slut för Ande på texten runt markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-620">Attempt to perform completion on the text surrounding the cursor.</span></span> <span data-ttu-id="1d3bc-621">Om det finns flera möjliga slut för ande, används det längsta entydiga prefixet för slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-621">If there are multiple possible completions, the longest unambiguous prefix is used for completion.</span></span> <span data-ttu-id="1d3bc-622">Om du försöker slutföra den längsta otvetydiga avsluten visas en lista över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-622">If trying to complete the longest unambiguous completion, a list of possible completions is displayed.</span></span>

- <span data-ttu-id="1d3bc-623">CMD: `<Ctrl+@>` , `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-623">Cmd: `<Ctrl+@>`, `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="1d3bc-624">Emacs: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-624">Emacs: `<Ctrl+Spacebar>`</span></span>

### <a name="possiblecompletions"></a><span data-ttu-id="1d3bc-625">PossibleCompletions</span><span class="sxs-lookup"><span data-stu-id="1d3bc-625">PossibleCompletions</span></span>

<span data-ttu-id="1d3bc-626">Visa listan över möjliga slut för ande.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-626">Display the list of possible completions.</span></span>

- <span data-ttu-id="1d3bc-627">Emacs: `<Alt+=>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-627">Emacs: `<Alt+=>`</span></span>
- <span data-ttu-id="1d3bc-628">Vi infognings läge: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-628">Vi insert mode: `<Ctrl+Spacebar>`</span></span>
- <span data-ttu-id="1d3bc-629">Kommando läge för vi: `<Ctrl+Spacebar>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-629">Vi command mode: `<Ctrl+Spacebar>`</span></span>

### <a name="tabcompletenext"></a><span data-ttu-id="1d3bc-630">TabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="1d3bc-630">TabCompleteNext</span></span>

<span data-ttu-id="1d3bc-631">Försök att slutföra den text som omger markören med nästa tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-631">Attempt to complete the text surrounding the cursor with the next available completion.</span></span>

- <span data-ttu-id="1d3bc-632">Kommandot `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-632">Cmd: `<Tab>`</span></span>
- <span data-ttu-id="1d3bc-633">Kommando läge för vi: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-633">Vi command mode: `<Tab>`</span></span>

### <a name="tabcompleteprevious"></a><span data-ttu-id="1d3bc-634">TabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="1d3bc-634">TabCompletePrevious</span></span>

<span data-ttu-id="1d3bc-635">Försök att slutföra den text som omger markören med föregående tillgängliga komplettering.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-635">Attempt to complete the text surrounding the cursor with the previous available completion.</span></span>

- <span data-ttu-id="1d3bc-636">Kommandot `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-636">Cmd: `<Shift+Tab>`</span></span>
- <span data-ttu-id="1d3bc-637">Kommando läge för vi: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-637">Vi command mode: `<Shift+Tab>`</span></span>

### <a name="vitabcompletenext"></a><span data-ttu-id="1d3bc-638">ViTabCompleteNext</span><span class="sxs-lookup"><span data-stu-id="1d3bc-638">ViTabCompleteNext</span></span>

<span data-ttu-id="1d3bc-639">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompleteNext.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-639">Ends the current edit group, if needed, and invokes TabCompleteNext.</span></span>

- <span data-ttu-id="1d3bc-640">Vi infognings läge: `<Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-640">Vi insert mode: `<Tab>`</span></span>

### <a name="vitabcompleteprevious"></a><span data-ttu-id="1d3bc-641">ViTabCompletePrevious</span><span class="sxs-lookup"><span data-stu-id="1d3bc-641">ViTabCompletePrevious</span></span>

<span data-ttu-id="1d3bc-642">Avslutar den aktuella redigera-gruppen, om det behövs, och anropar TabCompletePrevious.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-642">Ends the current edit group, if needed, and invokes TabCompletePrevious.</span></span>

- <span data-ttu-id="1d3bc-643">Vi infognings läge: `<Shift+Tab>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-643">Vi insert mode: `<Shift+Tab>`</span></span>

## <a name="miscellaneous-functions"></a><span data-ttu-id="1d3bc-644">Diverse-funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-644">Miscellaneous functions</span></span>

### <a name="acceptnextsuggestionword"></a><span data-ttu-id="1d3bc-645">AcceptNextSuggestionWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-645">AcceptNextSuggestionWord</span></span>

<span data-ttu-id="1d3bc-646">Godkänn nästa ord i det infogade eller markerade förslaget.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-646">Accept the next word of the inline or selected suggestion.</span></span>

- <span data-ttu-id="1d3bc-647">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-647">Function is unbound.</span></span>

### <a name="acceptsuggestion"></a><span data-ttu-id="1d3bc-648">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="1d3bc-648">AcceptSuggestion</span></span>

<span data-ttu-id="1d3bc-649">Godkänn det aktuella infogade eller valda förslaget.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-649">Accept the current inline or selected suggestion.</span></span>

- <span data-ttu-id="1d3bc-650">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-650">Function is unbound.</span></span>

### <a name="capturescreen"></a><span data-ttu-id="1d3bc-651">CaptureScreen</span><span class="sxs-lookup"><span data-stu-id="1d3bc-651">CaptureScreen</span></span>

<span data-ttu-id="1d3bc-652">Starta insamlingen av interaktiva skärms-/nedpilar Välj rader, skriv kopierar markerad text till Urklipp som text och HTML.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-652">Start interactive screen capture - up/down arrows select lines, enter copies selected text to clipboard as text and html.</span></span>

- <span data-ttu-id="1d3bc-653">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-653">Function is unbound.</span></span>

### <a name="clearscreen"></a><span data-ttu-id="1d3bc-654">ClearScreen</span><span class="sxs-lookup"><span data-stu-id="1d3bc-654">ClearScreen</span></span>

<span data-ttu-id="1d3bc-655">Ta bort skärmen och rita den aktuella raden överst på skärmen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-655">Clear the screen and draw the current line at the top of the screen.</span></span>

- <span data-ttu-id="1d3bc-656">Kommandot `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-656">Cmd: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1d3bc-657">Emacs: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-657">Emacs: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1d3bc-658">Vi infognings läge: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-658">Vi insert mode: `<Ctrl+l>`</span></span>
- <span data-ttu-id="1d3bc-659">Kommando läge för vi: `<Ctrl+l>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-659">Vi command mode: `<Ctrl+l>`</span></span>

### <a name="digitargument"></a><span data-ttu-id="1d3bc-660">DigitArgument</span><span class="sxs-lookup"><span data-stu-id="1d3bc-660">DigitArgument</span></span>

<span data-ttu-id="1d3bc-661">Starta ett nytt siffer argument för att skicka till andra funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-661">Start a new digit argument to pass to other functions.</span></span>

- <span data-ttu-id="1d3bc-662">CMD: `<Alt+0>` , `<Alt+1>` , `<Alt+2>` , `<Alt+3>` , `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` ,, `<Alt+9>` ,,,, `<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-662">Cmd: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="1d3bc-663">Emacs:,,,,,,,,, `<Alt+0>` `<Alt+1>` `<Alt+2>` `<Alt+3>` `<Alt+4>` `<Alt+5>` `<Alt+6>` `<Alt+7>` `<Alt+8>` `<Alt+9>``<Alt+->`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-663">Emacs: `<Alt+0>`, `<Alt+1>`, `<Alt+2>`, `<Alt+3>`, `<Alt+4>`, `<Alt+5>`, `<Alt+6>`, `<Alt+7>`, `<Alt+8>`, `<Alt+9>`, `<Alt+->`</span></span>
- <span data-ttu-id="1d3bc-664">Vi kommando läge: `<0>` , `<1>` , `<2>` , `<3>` , `<4>` `<5>` `<6>` , `<7>` , `<8>` ,, `<9>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-664">Vi command mode: `<0>`, `<1>`, `<2>`, `<3>`, `<4>`, `<5>`, `<6>`, `<7>`, `<8>`, `<9>`</span></span>

### <a name="invokeprompt"></a><span data-ttu-id="1d3bc-665">InvokePrompt</span><span class="sxs-lookup"><span data-stu-id="1d3bc-665">InvokePrompt</span></span>

<span data-ttu-id="1d3bc-666">Tar bort den aktuella prompten och anropar prompt-funktionen för att visa uppmaningen igen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-666">Erases the current prompt and calls the prompt function to redisplay the prompt.</span></span> <span data-ttu-id="1d3bc-667">Användbart för anpassade nyckel hanterare som ändrar tillstånd, t. ex. ändra den aktuella katalogen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-667">Useful for custom key handlers that change state, e.g. change the current directory.</span></span>

- <span data-ttu-id="1d3bc-668">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-668">Function is unbound.</span></span>

### <a name="scrolldisplaydown"></a><span data-ttu-id="1d3bc-669">ScrollDisplayDown</span><span class="sxs-lookup"><span data-stu-id="1d3bc-669">ScrollDisplayDown</span></span>

<span data-ttu-id="1d3bc-670">Rulla ned skärmen en skärm.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-670">Scroll the display down one screen.</span></span>

- <span data-ttu-id="1d3bc-671">Kommandot `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-671">Cmd: `<PageDown>`</span></span>
- <span data-ttu-id="1d3bc-672">Emacs: `<PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-672">Emacs: `<PageDown>`</span></span>

### <a name="scrolldisplaydownline"></a><span data-ttu-id="1d3bc-673">ScrollDisplayDownLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-673">ScrollDisplayDownLine</span></span>

<span data-ttu-id="1d3bc-674">Bläddra nedåt en rad.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-674">Scroll the display down one line.</span></span>

- <span data-ttu-id="1d3bc-675">Kommandot `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-675">Cmd: `<Ctrl+PageDown>`</span></span>
- <span data-ttu-id="1d3bc-676">Emacs: `<Ctrl+PageDown>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-676">Emacs: `<Ctrl+PageDown>`</span></span>

### <a name="scrolldisplaytocursor"></a><span data-ttu-id="1d3bc-677">ScrollDisplayToCursor</span><span class="sxs-lookup"><span data-stu-id="1d3bc-677">ScrollDisplayToCursor</span></span>

<span data-ttu-id="1d3bc-678">Rulla skärmen till markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-678">Scroll the display to the cursor.</span></span>

- <span data-ttu-id="1d3bc-679">Emacs: `<Ctrl+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-679">Emacs: `<Ctrl+End>`</span></span>

### <a name="scrolldisplaytop"></a><span data-ttu-id="1d3bc-680">ScrollDisplayTop</span><span class="sxs-lookup"><span data-stu-id="1d3bc-680">ScrollDisplayTop</span></span>

<span data-ttu-id="1d3bc-681">Rulla visningen längst upp.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-681">Scroll the display to the top.</span></span>

- <span data-ttu-id="1d3bc-682">Emacs: `<Ctrl+Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-682">Emacs: `<Ctrl+Home>`</span></span>

### <a name="scrolldisplayup"></a><span data-ttu-id="1d3bc-683">ScrollDisplayUp</span><span class="sxs-lookup"><span data-stu-id="1d3bc-683">ScrollDisplayUp</span></span>

<span data-ttu-id="1d3bc-684">Rulla ned skärmen som visas på en skärm.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-684">Scroll the display up one screen.</span></span>

- <span data-ttu-id="1d3bc-685">Kommandot `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-685">Cmd: `<PageUp>`</span></span>
- <span data-ttu-id="1d3bc-686">Emacs: `<PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-686">Emacs: `<PageUp>`</span></span>

### <a name="scrolldisplayupline"></a><span data-ttu-id="1d3bc-687">ScrollDisplayUpLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-687">ScrollDisplayUpLine</span></span>

<span data-ttu-id="1d3bc-688">Rulla upp en rad som visas.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-688">Scroll the display up one line.</span></span>

- <span data-ttu-id="1d3bc-689">Kommandot `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-689">Cmd: `<Ctrl+PageUp>`</span></span>
- <span data-ttu-id="1d3bc-690">Emacs: `<Ctrl+PageUp>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-690">Emacs: `<Ctrl+PageUp>`</span></span>

### <a name="selfinsert"></a><span data-ttu-id="1d3bc-691">SelfInsert</span><span class="sxs-lookup"><span data-stu-id="1d3bc-691">SelfInsert</span></span>

<span data-ttu-id="1d3bc-692">Infoga nyckeln.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-692">Insert the key.</span></span>

- <span data-ttu-id="1d3bc-693">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-693">Function is unbound.</span></span>

### <a name="showkeybindings"></a><span data-ttu-id="1d3bc-694">ShowKeyBindings</span><span class="sxs-lookup"><span data-stu-id="1d3bc-694">ShowKeyBindings</span></span>

<span data-ttu-id="1d3bc-695">Visa alla bindnings nycklar.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-695">Show all bound keys.</span></span>

- <span data-ttu-id="1d3bc-696">Kommandot `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-696">Cmd: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="1d3bc-697">Emacs: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-697">Emacs: `<Ctrl+Alt+?>`</span></span>
- <span data-ttu-id="1d3bc-698">Vi infognings läge: `<Ctrl+Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-698">Vi insert mode: `<Ctrl+Alt+?>`</span></span>

### <a name="vicommandmode"></a><span data-ttu-id="1d3bc-699">ViCommandMode</span><span class="sxs-lookup"><span data-stu-id="1d3bc-699">ViCommandMode</span></span>

<span data-ttu-id="1d3bc-700">Växla det aktuella operativ läget från Vi-Insert till vi-Command.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-700">Switch the current operating mode from Vi-Insert to Vi-Command.</span></span>

- <span data-ttu-id="1d3bc-701">Vi infognings läge: `<Escape>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-701">Vi insert mode: `<Escape>`</span></span>

### <a name="vidigitargumentinchord"></a><span data-ttu-id="1d3bc-702">ViDigitArgumentInChord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-702">ViDigitArgumentInChord</span></span>

<span data-ttu-id="1d3bc-703">Starta ett nytt siffer argument för att skicka till andra funktioner, i någon av vi Chords.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-703">Start a new digit argument to pass to other functions while in one of vi's chords.</span></span>

- <span data-ttu-id="1d3bc-704">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-704">Function is unbound.</span></span>

### <a name="vieditvisually"></a><span data-ttu-id="1d3bc-705">ViEditVisually</span><span class="sxs-lookup"><span data-stu-id="1d3bc-705">ViEditVisually</span></span>

<span data-ttu-id="1d3bc-706">Redigera kommando raden i en text redigerare som anges av $env: REDIGERARE eller $env: visuellt objekt.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-706">Edit the command line in a text editor specified by $env:EDITOR or $env:VISUAL.</span></span>

- <span data-ttu-id="1d3bc-707">Emacs: `<Ctrl+x,Ctrl+e>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-707">Emacs: `<Ctrl+x,Ctrl+e>`</span></span>
- <span data-ttu-id="1d3bc-708">Kommando läge för vi: `<v>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-708">Vi command mode: `<v>`</span></span>

### <a name="viexit"></a><span data-ttu-id="1d3bc-709">ViExit</span><span class="sxs-lookup"><span data-stu-id="1d3bc-709">ViExit</span></span>

<span data-ttu-id="1d3bc-710">Avslutar gränssnittet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-710">Exits the shell.</span></span>

- <span data-ttu-id="1d3bc-711">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-711">Function is unbound.</span></span>

### <a name="viinsertmode"></a><span data-ttu-id="1d3bc-712">ViInsertMode</span><span class="sxs-lookup"><span data-stu-id="1d3bc-712">ViInsertMode</span></span>

<span data-ttu-id="1d3bc-713">Växla till infognings läge.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-713">Switch to Insert mode.</span></span>

- <span data-ttu-id="1d3bc-714">Kommando läge för vi: `<i>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-714">Vi command mode: `<i>`</span></span>

### <a name="whatiskey"></a><span data-ttu-id="1d3bc-715">WhatIsKey</span><span class="sxs-lookup"><span data-stu-id="1d3bc-715">WhatIsKey</span></span>

<span data-ttu-id="1d3bc-716">Läs en nyckel och berätta vad nyckeln är kopplad till.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-716">Read a key and tell me what the key is bound to.</span></span>

- <span data-ttu-id="1d3bc-717">Kommandot `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-717">Cmd: `<Alt+?>`</span></span>
- <span data-ttu-id="1d3bc-718">Emacs: `<Alt+?>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-718">Emacs: `<Alt+?>`</span></span>

## <a name="selection-functions"></a><span data-ttu-id="1d3bc-719">Markerings funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-719">Selection functions</span></span>

### <a name="exchangepointandmark"></a><span data-ttu-id="1d3bc-720">ExchangePointAndMark</span><span class="sxs-lookup"><span data-stu-id="1d3bc-720">ExchangePointAndMark</span></span>

<span data-ttu-id="1d3bc-721">Markören placeras vid markeringens position och markeringen flyttas till positionen för markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-721">The cursor is placed at the location of the mark and the mark is moved to the location of the cursor.</span></span>

- <span data-ttu-id="1d3bc-722">Emacs: `<Ctrl+x,Ctrl+x>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-722">Emacs: `<Ctrl+x,Ctrl+x>`</span></span>

### <a name="selectall"></a><span data-ttu-id="1d3bc-723">SelectAll</span><span class="sxs-lookup"><span data-stu-id="1d3bc-723">SelectAll</span></span>

<span data-ttu-id="1d3bc-724">Markera hela raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-724">Select the entire line.</span></span>

- <span data-ttu-id="1d3bc-725">Kommandot `<Ctrl+a>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-725">Cmd: `<Ctrl+a>`</span></span>

### <a name="selectbackwardchar"></a><span data-ttu-id="1d3bc-726">SelectBackwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-726">SelectBackwardChar</span></span>

<span data-ttu-id="1d3bc-727">Justera det aktuella urvalet så att det innehåller föregående-tecknen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-727">Adjust the current selection to include the previous character.</span></span>

- <span data-ttu-id="1d3bc-728">Kommandot `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-728">Cmd: `<Shift+LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-729">Emacs: `<Shift+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-729">Emacs: `<Shift+LeftArrow>`</span></span>

### <a name="selectbackwardsline"></a><span data-ttu-id="1d3bc-730">SelectBackwardsLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-730">SelectBackwardsLine</span></span>

<span data-ttu-id="1d3bc-731">Justera det aktuella urvalet så att det tas från markören till början av raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-731">Adjust the current selection to include from the cursor to the start of the line.</span></span>

- <span data-ttu-id="1d3bc-732">Kommandot `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-732">Cmd: `<Shift+Home>`</span></span>
- <span data-ttu-id="1d3bc-733">Emacs: `<Shift+Home>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-733">Emacs: `<Shift+Home>`</span></span>

### <a name="selectbackwardword"></a><span data-ttu-id="1d3bc-734">SelectBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-734">SelectBackwardWord</span></span>

<span data-ttu-id="1d3bc-735">Justera det aktuella urvalet så att det innehåller föregående ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-735">Adjust the current selection to include the previous word.</span></span>

- <span data-ttu-id="1d3bc-736">Kommandot `<Shift+Ctrl+LeftArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-736">Cmd: `<Shift+Ctrl+LeftArrow>`</span></span>
- <span data-ttu-id="1d3bc-737">Emacs: `<Alt+B>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-737">Emacs: `<Alt+B>`</span></span>

### <a name="selectforwardchar"></a><span data-ttu-id="1d3bc-738">SelectForwardChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-738">SelectForwardChar</span></span>

<span data-ttu-id="1d3bc-739">Justera det aktuella urvalet så att det inkluderar nästa-tecknen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-739">Adjust the current selection to include the next character.</span></span>

- <span data-ttu-id="1d3bc-740">Kommandot `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-740">Cmd: `<Shift+RightArrow>`</span></span>
- <span data-ttu-id="1d3bc-741">Emacs: `<Shift+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-741">Emacs: `<Shift+RightArrow>`</span></span>

### <a name="selectforwardword"></a><span data-ttu-id="1d3bc-742">SelectForwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-742">SelectForwardWord</span></span>

<span data-ttu-id="1d3bc-743">Justera den aktuella markeringen för att inkludera nästa ord med ForwardWord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-743">Adjust the current selection to include the next word using ForwardWord.</span></span>

- <span data-ttu-id="1d3bc-744">Emacs: `<Alt+F>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-744">Emacs: `<Alt+F>`</span></span>

### <a name="selectline"></a><span data-ttu-id="1d3bc-745">SelectLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-745">SelectLine</span></span>

<span data-ttu-id="1d3bc-746">Justera det aktuella urvalet så att det tas från markören till slutet av raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-746">Adjust the current selection to include from the cursor to the end of the line.</span></span>

- <span data-ttu-id="1d3bc-747">Kommandot `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-747">Cmd: `<Shift+End>`</span></span>
- <span data-ttu-id="1d3bc-748">Emacs: `<Shift+End>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-748">Emacs: `<Shift+End>`</span></span>

### <a name="selectnextword"></a><span data-ttu-id="1d3bc-749">SelectNextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-749">SelectNextWord</span></span>

<span data-ttu-id="1d3bc-750">Justera det aktuella urvalet så att det inkluderar nästa ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-750">Adjust the current selection to include the next word.</span></span>

- <span data-ttu-id="1d3bc-751">Kommandot `<Shift+Ctrl+RightArrow>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-751">Cmd: `<Shift+Ctrl+RightArrow>`</span></span>

### <a name="selectshellbackwardword"></a><span data-ttu-id="1d3bc-752">SelectShellBackwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-752">SelectShellBackwardWord</span></span>

<span data-ttu-id="1d3bc-753">Justera det aktuella urvalet så att det innehåller föregående ord med ShellBackwardWord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-753">Adjust the current selection to include the previous word using ShellBackwardWord.</span></span>

- <span data-ttu-id="1d3bc-754">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-754">Function is unbound.</span></span>

### <a name="selectshellforwardword"></a><span data-ttu-id="1d3bc-755">SelectShellForwardWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-755">SelectShellForwardWord</span></span>

<span data-ttu-id="1d3bc-756">Justera den aktuella markeringen för att inkludera nästa ord med ShellForwardWord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-756">Adjust the current selection to include the next word using ShellForwardWord.</span></span>

- <span data-ttu-id="1d3bc-757">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-757">Function is unbound.</span></span>

### <a name="selectshellnextword"></a><span data-ttu-id="1d3bc-758">SelectShellNextWord</span><span class="sxs-lookup"><span data-stu-id="1d3bc-758">SelectShellNextWord</span></span>

<span data-ttu-id="1d3bc-759">Justera den aktuella markeringen för att inkludera nästa ord med ShellNextWord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-759">Adjust the current selection to include the next word using ShellNextWord.</span></span>

- <span data-ttu-id="1d3bc-760">Funktionen är obunden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-760">Function is unbound.</span></span>

### <a name="setmark"></a><span data-ttu-id="1d3bc-761">SetMark</span><span class="sxs-lookup"><span data-stu-id="1d3bc-761">SetMark</span></span>

<span data-ttu-id="1d3bc-762">Markera den aktuella platsen för markören som ska användas i ett efterföljande redigerings kommando.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-762">Mark the current location of the cursor for use in a subsequent editing command.</span></span>

- <span data-ttu-id="1d3bc-763">Emacs: `<Ctrl+@>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-763">Emacs: `<Ctrl+@>`</span></span>

## <a name="predictive-intellisense-functions"></a><span data-ttu-id="1d3bc-764">Förutsägande IntelliSense-funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-764">Predictive IntelliSense functions</span></span>

> [!NOTE]
> <span data-ttu-id="1d3bc-765">Förutsägelse IntelliSense måste aktive ras för att använda dessa funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-765">Predictive IntelliSense needs to be enabled to use these functions.</span></span>

### <a name="acceptnextwordsuggestion"></a><span data-ttu-id="1d3bc-766">AcceptNextWordSuggestion</span><span class="sxs-lookup"><span data-stu-id="1d3bc-766">AcceptNextWordSuggestion</span></span>

<span data-ttu-id="1d3bc-767">Accepterar nästa ord i det infogade förslaget från förutsägande IntelliSense.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-767">Accepts the next word of the inline suggestion from Predictive IntelliSense.</span></span>
<span data-ttu-id="1d3bc-768">Den här funktionen kan bindas till <kbd>CTRL</kbd> + <kbd>F</kbd> genom att köra följande kommando.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-768">This function can be bound with <kbd>Ctrl</kbd>+<kbd>F</kbd> by running the following command.</span></span>

```powershell
Set-PSReadLineKeyHandler -Chord "Ctrl+f" -Function ForwardWord
```

### <a name="acceptsuggestion"></a><span data-ttu-id="1d3bc-769">AcceptSuggestion</span><span class="sxs-lookup"><span data-stu-id="1d3bc-769">AcceptSuggestion</span></span>

<span data-ttu-id="1d3bc-770">Accepterar det aktuella infogade förslaget från förutsägande IntelliSense genom att trycka på <kbd>RightArrow</kbd> när markören är i slutet av den aktuella raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-770">Accepts the current inline suggestion from Predictive IntelliSense by pressing <kbd>RightArrow</kbd> when the cursor is at the end of the current line.</span></span>

## <a name="search-functions"></a><span data-ttu-id="1d3bc-771">Sök funktioner</span><span class="sxs-lookup"><span data-stu-id="1d3bc-771">Search functions</span></span>

### <a name="charactersearch"></a><span data-ttu-id="1d3bc-772">CharacterSearch</span><span class="sxs-lookup"><span data-stu-id="1d3bc-772">CharacterSearch</span></span>

<span data-ttu-id="1d3bc-773">Läs ett Character och Sök framåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-773">Read a character and search forward for the next occurrence of that character.</span></span>
<span data-ttu-id="1d3bc-774">Om ett argument anges söker du framåt (eller bakåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-774">If an argument is specified, search forward (or backward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="1d3bc-775">Kommandot `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-775">Cmd: `<F3>`</span></span>
- <span data-ttu-id="1d3bc-776">Emacs: `<Ctrl+]>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-776">Emacs: `<Ctrl+]>`</span></span>
- <span data-ttu-id="1d3bc-777">Vi infognings läge: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-777">Vi insert mode: `<F3>`</span></span>
- <span data-ttu-id="1d3bc-778">Kommando läge för vi: `<F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-778">Vi command mode: `<F3>`</span></span>

### <a name="charactersearchbackward"></a><span data-ttu-id="1d3bc-779">CharacterSearchBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-779">CharacterSearchBackward</span></span>

<span data-ttu-id="1d3bc-780">Läs ett Character och Sök bakåt för nästa förekomst av det här specialtecknet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-780">Read a character and search backward for the next occurrence of that character.</span></span> <span data-ttu-id="1d3bc-781">Om ett argument anges söker du bakåt (eller framåt om det är negativt) för den n:te förekomsten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-781">If an argument is specified, search backward (or forward if negative) for the nth occurrence.</span></span>

- <span data-ttu-id="1d3bc-782">Kommandot `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-782">Cmd: `<Shift+F3>`</span></span>
- <span data-ttu-id="1d3bc-783">Emacs: `<Ctrl+Alt+]>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-783">Emacs: `<Ctrl+Alt+]>`</span></span>
- <span data-ttu-id="1d3bc-784">Vi infognings läge: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-784">Vi insert mode: `<Shift+F3>`</span></span>
- <span data-ttu-id="1d3bc-785">Kommando läge för vi: `<Shift+F3>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-785">Vi command mode: `<Shift+F3>`</span></span>

### <a name="repeatlastcharsearch"></a><span data-ttu-id="1d3bc-786">RepeatLastCharSearch</span><span class="sxs-lookup"><span data-stu-id="1d3bc-786">RepeatLastCharSearch</span></span>

<span data-ttu-id="1d3bc-787">Upprepa den senast inspelade sökningen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-787">Repeat the last recorded character search.</span></span>

- <span data-ttu-id="1d3bc-788">Kommando läge för vi: `<;>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-788">Vi command mode: `<;>`</span></span>

### <a name="repeatlastcharsearchbackwards"></a><span data-ttu-id="1d3bc-789">RepeatLastCharSearchBackwards</span><span class="sxs-lookup"><span data-stu-id="1d3bc-789">RepeatLastCharSearchBackwards</span></span>

<span data-ttu-id="1d3bc-790">Upprepa den senast inspelade bokstavs sökningen, men i motsatt riktning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-790">Repeat the last recorded character search, but in the opposite direction.</span></span>

- <span data-ttu-id="1d3bc-791">Kommando läge för vi: `<,>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-791">Vi command mode: `<,>`</span></span>

### <a name="repeatsearch"></a><span data-ttu-id="1d3bc-792">RepeatSearch</span><span class="sxs-lookup"><span data-stu-id="1d3bc-792">RepeatSearch</span></span>

<span data-ttu-id="1d3bc-793">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-793">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="1d3bc-794">Kommando läge för vi: `<n>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-794">Vi command mode: `<n>`</span></span>

### <a name="repeatsearchbackward"></a><span data-ttu-id="1d3bc-795">RepeatSearchBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-795">RepeatSearchBackward</span></span>

<span data-ttu-id="1d3bc-796">Upprepa den senaste sökningen i samma riktning som tidigare.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-796">Repeat the last search in the same direction as before.</span></span>

- <span data-ttu-id="1d3bc-797">Kommando läge för vi: `<N>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-797">Vi command mode: `<N>`</span></span>

### <a name="searchchar"></a><span data-ttu-id="1d3bc-798">SearchChar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-798">SearchChar</span></span>

<span data-ttu-id="1d3bc-799">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-799">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="1d3bc-800">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-800">This is for 't' functionality.</span></span>

- <span data-ttu-id="1d3bc-801">Kommando läge för vi: `<f>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-801">Vi command mode: `<f>`</span></span>

### <a name="searchcharbackward"></a><span data-ttu-id="1d3bc-802">SearchCharBackward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-802">SearchCharBackward</span></span>

<span data-ttu-id="1d3bc-803">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-803">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="1d3bc-804">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-804">This is for 'T' functionality.</span></span>

- <span data-ttu-id="1d3bc-805">Kommando läge för vi: `<F>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-805">Vi command mode: `<F>`</span></span>

### <a name="searchcharbackwardwithbackoff"></a><span data-ttu-id="1d3bc-806">SearchCharBackwardWithBackoff</span><span class="sxs-lookup"><span data-stu-id="1d3bc-806">SearchCharBackwardWithBackoff</span></span>

<span data-ttu-id="1d3bc-807">Läs nästa steg och leta sedan reda på det, gå bakåt och stäng sedan på ett av tecknen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-807">Read the next character and then find it, going backward, and then back off a character.</span></span> <span data-ttu-id="1d3bc-808">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-808">This is for 'T' functionality.</span></span>

- <span data-ttu-id="1d3bc-809">Kommando läge för vi: `<T>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-809">Vi command mode: `<T>`</span></span>

### <a name="searchcharwithbackoff"></a><span data-ttu-id="1d3bc-810">SearchCharWithBackoff</span><span class="sxs-lookup"><span data-stu-id="1d3bc-810">SearchCharWithBackoff</span></span>

<span data-ttu-id="1d3bc-811">Läs nästa steg och leta sedan reda på det, gå framåt och ta sedan bort ett specialtecken.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-811">Read the next character and then find it, going forward, and then back off a character.</span></span> <span data-ttu-id="1d3bc-812">Detta är endast för funktioner.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-812">This is for 't' functionality.</span></span>

- <span data-ttu-id="1d3bc-813">Kommando läge för vi: `<t>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-813">Vi command mode: `<t>`</span></span>

### <a name="searchforward"></a><span data-ttu-id="1d3bc-814">SearchForward</span><span class="sxs-lookup"><span data-stu-id="1d3bc-814">SearchForward</span></span>

<span data-ttu-id="1d3bc-815">Söker efter en Sök sträng och påbörjar sökningen på AcceptLine.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-815">Prompts for a search string and initiates search upon AcceptLine.</span></span>

- <span data-ttu-id="1d3bc-816">Vi infognings läge: `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-816">Vi insert mode: `<Ctrl+s>`</span></span>
- <span data-ttu-id="1d3bc-817">Kommando läge för vi: `<?>` , `<Ctrl+s>`</span><span class="sxs-lookup"><span data-stu-id="1d3bc-817">Vi command mode: `<?>`, `<Ctrl+s>`</span></span>

## <a name="custom-key-bindings"></a><span data-ttu-id="1d3bc-818">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="1d3bc-818">Custom Key Bindings</span></span>

<span data-ttu-id="1d3bc-819">PSReadLine stöder anpassade nyckel bindningar med hjälp av cmdleten `Set-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-819">PSReadLine supports custom key bindings using the cmdlet `Set-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="1d3bc-820">De flesta anpassade nyckel bindningar anropar någon av ovanstående funktioner, till exempel</span><span class="sxs-lookup"><span data-stu-id="1d3bc-820">Most custom key bindings call one of the above functions, for example</span></span>

```powershell
Set-PSReadLineKeyHandler -Key UpArrow -Function HistorySearchBackward
```

<span data-ttu-id="1d3bc-821">Du kan binda en script block till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-821">You can bind a ScriptBlock to a key.</span></span> <span data-ttu-id="1d3bc-822">Script block kan göra det mycket du vill.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-822">The ScriptBlock can do pretty much anything you want.</span></span> <span data-ttu-id="1d3bc-823">Några användbara exempel är</span><span class="sxs-lookup"><span data-stu-id="1d3bc-823">Some useful examples include</span></span>

- <span data-ttu-id="1d3bc-824">redigera kommando raden</span><span class="sxs-lookup"><span data-stu-id="1d3bc-824">edit the command line</span></span>
- <span data-ttu-id="1d3bc-825">öppna ett nytt fönster (t. ex. hjälp)</span><span class="sxs-lookup"><span data-stu-id="1d3bc-825">opening a new window (e.g. help)</span></span>
- <span data-ttu-id="1d3bc-826">ändra kataloger utan att ändra kommando raden</span><span class="sxs-lookup"><span data-stu-id="1d3bc-826">change directories without changing the command line</span></span>

<span data-ttu-id="1d3bc-827">Script block tar emot två argument:</span><span class="sxs-lookup"><span data-stu-id="1d3bc-827">The ScriptBlock receives two arguments:</span></span>

- <span data-ttu-id="1d3bc-828">`$key` -Ett **[ConsoleKeyInfo]** -objekt som är nyckeln som utlöste den anpassade bindningen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-828">`$key` - A **[ConsoleKeyInfo]** object that is the key that triggered the custom binding.</span></span> <span data-ttu-id="1d3bc-829">Om du binder samma script block till flera nycklar och behöver utföra olika åtgärder beroende på nyckeln, kan du kontrol lera $key.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-829">If you bind the same ScriptBlock to multiple keys and need to perform different actions depending on the key, you can check $key.</span></span> <span data-ttu-id="1d3bc-830">Många anpassade bindningar ignorerar det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-830">Many custom bindings ignore this argument.</span></span>

- <span data-ttu-id="1d3bc-831">`$arg` – Ett godtyckligt argument.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-831">`$arg` - An arbitrary argument.</span></span> <span data-ttu-id="1d3bc-832">Oftast är detta ett heltals argument som användaren skickar från nyckel bindningarna DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-832">Most often, this would be an integer argument that the user passes from the key bindings DigitArgument.</span></span> <span data-ttu-id="1d3bc-833">Om bindningen inte accepterar argument är det rimligt att ignorera det här argumentet.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-833">If your binding doesn't accept arguments, it's reasonable to ignore this argument.</span></span>

<span data-ttu-id="1d3bc-834">Låt oss ta en titt på ett exempel som lägger till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-834">Let's take a look at an example that adds a command line to history without executing it.</span></span> <span data-ttu-id="1d3bc-835">Detta är användbart när du inser att du har glömt att göra något, men inte vill ange den kommando rad som du redan har angett.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-835">This is useful when you realize you forgot to do something, but don't want to re-enter the command line you've already entered.</span></span>

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

<span data-ttu-id="1d3bc-836">Du kan se många fler exempel i filen `SamplePSReadLineProfile.ps1` som är installerad i mappen PSReadLine module.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-836">You can see many more examples in the file `SamplePSReadLineProfile.ps1` which is installed in the PSReadLine module folder.</span></span>

<span data-ttu-id="1d3bc-837">De flesta nyckel bindningar använder vissa hjälp funktioner för att redigera kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-837">Most key bindings use some helper functions for editing the command line.</span></span>
<span data-ttu-id="1d3bc-838">Dessa API: er dokumenteras i nästa avsnitt.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-838">Those APIs are documented in the next section.</span></span>

## <a name="custom-key-binding-support-apis"></a><span data-ttu-id="1d3bc-839">API: er för anpassad nyckel bindning support</span><span class="sxs-lookup"><span data-stu-id="1d3bc-839">Custom Key Binding Support APIs</span></span>

<span data-ttu-id="1d3bc-840">Följande funktioner är offentliga i Microsoft. PowerShell. PSConsoleReadLine, men de kan inte vara direkt kopplade till en nyckel.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-840">The following functions are public in Microsoft.PowerShell.PSConsoleReadLine, but cannot be directly bound to a key.</span></span> <span data-ttu-id="1d3bc-841">De flesta är användbara i anpassade nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-841">Most are useful in custom key bindings.</span></span>

```csharp
void AddToHistory(string command)
```

<span data-ttu-id="1d3bc-842">Lägg till en kommando rad i historiken utan att köra den.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-842">Add a command line to history without executing it.</span></span>

```csharp
void ClearKillRing()
```

<span data-ttu-id="1d3bc-843">Rensa Kill-ringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-843">Clear the kill-ring.</span></span>  <span data-ttu-id="1d3bc-844">Detta används främst för testning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-844">This is mostly used for testing.</span></span>

```csharp
void Delete(int start, int length)
```

<span data-ttu-id="1d3bc-845">Ta bort tecken längd från början.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-845">Delete length characters from start.</span></span>  <span data-ttu-id="1d3bc-846">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-846">This operation supports undo/redo.</span></span>

```csharp
void Ding()
```

<span data-ttu-id="1d3bc-847">Utför instruktionen dings baserat på användarnas preferenser.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-847">Perform the Ding action based on the users preference.</span></span>

```csharp
void GetBufferState([ref] string input, [ref] int cursor)
void GetBufferState([ref] Ast ast, [ref] Token[] tokens,
  [ref] ParseError[] parseErrors, [ref] int cursor)
```

<span data-ttu-id="1d3bc-848">De här två funktionerna hämtar användbar information om den aktuella statusen för indatabufferten.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-848">These two functions retrieve useful information about the current state of the input buffer.</span></span>  <span data-ttu-id="1d3bc-849">Den första används ofta i enkla fall.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-849">The first is more commonly used for simple cases.</span></span>  <span data-ttu-id="1d3bc-850">Den andra används om bindningen gör något mer avancerat med AST.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-850">The second is used if your binding is doing something more advanced with the Ast.</span></span>

```csharp
IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(bool includeBound, bool includeUnbound)

IEnumerable[Microsoft.PowerShell.KeyHandler]
  GetKeyHandlers(string[] Chord)
```

<span data-ttu-id="1d3bc-851">Dessa två funktioner används av `Get-PSReadLineKeyHandler` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-851">These two functions are used by `Get-PSReadLineKeyHandler`.</span></span> <span data-ttu-id="1d3bc-852">Den första används för att hämta alla nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-852">The first is used to get all key bindings.</span></span> <span data-ttu-id="1d3bc-853">Den andra används för att hämta vissa nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-853">The second is used to get specific key bindings.</span></span>

```csharp
Microsoft.PowerShell.PSConsoleReadLineOptions GetOptions()
```

<span data-ttu-id="1d3bc-854">Den här funktionen används av Get-PSReadLineOption och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-854">This function is used by Get-PSReadLineOption and probably isn't too useful in a custom key binding.</span></span>

```csharp
void GetSelectionState([ref] int start, [ref] int length)
```

<span data-ttu-id="1d3bc-855">Om det inte finns något val på kommando raden returneras-1 både i Start-och längd.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-855">If there is no selection on the command line, -1 will be returned in both start and length.</span></span> <span data-ttu-id="1d3bc-856">Om det finns ett val på kommando raden returneras start och längden på markeringen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-856">If there is a selection on the command line, the start and length of the selection are returned.</span></span>

```csharp
void Insert(char c)
void Insert(string s)
```

<span data-ttu-id="1d3bc-857">Infoga ett tecken eller en sträng vid markören.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-857">Insert a character or string at the cursor.</span></span>  <span data-ttu-id="1d3bc-858">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-858">This operation supports undo/redo.</span></span>

```csharp
string ReadLine(runspace remoteRunspace,
  System.Management.Automation.EngineIntrinsics engineIntrinsics)
```

<span data-ttu-id="1d3bc-859">Detta är den huvudsakliga start punkten för PSReadLine.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-859">This is the main entry point to PSReadLine.</span></span> <span data-ttu-id="1d3bc-860">Den har inte stöd för rekursion, så det är inte användbart i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-860">It does not support recursion, so is not useful in a custom key binding.</span></span>

```csharp
void RemoveKeyHandler(string[] key)
```

<span data-ttu-id="1d3bc-861">Den här funktionen används av Remove-PSReadLineKeyHandler och är förmodligen inte för användbar i en anpassad nyckel bindning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-861">This function is used by Remove-PSReadLineKeyHandler and probably isn't too useful in a custom key binding.</span></span>

```csharp
void Replace(int start, int length, string replacement)
```

<span data-ttu-id="1d3bc-862">Ersätt några av inmatarna.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-862">Replace some of the input.</span></span> <span data-ttu-id="1d3bc-863">Den här åtgärden stöder ångra/gör om.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-863">This operation supports undo/redo.</span></span> <span data-ttu-id="1d3bc-864">Detta föredras framför borttagning följt av INSERT eftersom det behandlas som en enskild åtgärd för att ångra.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-864">This is preferred over Delete followed by Insert because it is treated as a single action for undo.</span></span>

```csharp
void SetCursorPosition(int cursor)
```

<span data-ttu-id="1d3bc-865">Flytta markören till den aktuella förskjutningen.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-865">Move the cursor to the given offset.</span></span> <span data-ttu-id="1d3bc-866">Markör förflyttning spåras inte för ångra.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-866">Cursor movement is not tracked for undo.</span></span>

```csharp
void SetOptions(Microsoft.PowerShell.SetPSReadLineOption options)
```

<span data-ttu-id="1d3bc-867">Den här funktionen är en hjälp metod som används av cmdlet Set-PSReadLineOption, men kan vara användbar för en anpassad nyckel bindning som tillfälligt vill ändra en inställning.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-867">This function is a helper method used by the cmdlet Set-PSReadLineOption, but might be useful to a custom key binding that wants to temporarily change a setting.</span></span>

```csharp
bool TryGetArgAsInt(System.Object arg, [ref] int numericArg,
  int defaultNumericArg)
```

<span data-ttu-id="1d3bc-868">Den här hjälp metoden används för anpassade bindningar som följer DigitArgument.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-868">This helper method is used for custom bindings that honor DigitArgument.</span></span> <span data-ttu-id="1d3bc-869">Ett typiskt anrop ser ut så här</span><span class="sxs-lookup"><span data-stu-id="1d3bc-869">A typical call looks like</span></span>

```powershell
[int]$numericArg = 0
[Microsoft.PowerShell.PSConsoleReadLine]::TryGetArgAsInt($arg,
  [ref]$numericArg, 1)
```

## <a name="notes"></a><span data-ttu-id="1d3bc-870">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1d3bc-870">Notes</span></span>

### <a name="command-history"></a><span data-ttu-id="1d3bc-871">Kommando historik</span><span class="sxs-lookup"><span data-stu-id="1d3bc-871">Command History</span></span>

<span data-ttu-id="1d3bc-872">PSReadLine underhåller en historik fil som innehåller alla kommandon och data som du har angett från kommando raden.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-872">PSReadLine maintains a history file containing all the commands and data you have entered from the command line.</span></span> <span data-ttu-id="1d3bc-873">Detta kan innehålla känsliga data, inklusive lösen ord.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-873">This may contain sensitive data including passwords.</span></span> <span data-ttu-id="1d3bc-874">Om du till exempel använder `ConvertTo-SecureString` cmdleten loggas lösen ordet i historik filen som oformaterad text.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-874">For example, if you use the `ConvertTo-SecureString` cmdlet the password is logged in the history file as plain text.</span></span> <span data-ttu-id="1d3bc-875">Historikfilerna är en fil med namnet `$($host.Name)_history.txt` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-875">The history files is a file named `$($host.Name)_history.txt`.</span></span> <span data-ttu-id="1d3bc-876">I Windows-system lagras historik filen på `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-876">On Windows systems the history file is stored at `$env:APPDATA\Microsoft\Windows\PowerShell\PSReadLine`.</span></span> <span data-ttu-id="1d3bc-877">På andra datorer än Windows-system lagras historikfilerna i `$env:XDG_DATA_HOME/powershell/PSReadLine` eller `$env:HOME/.local/share/powershell/PSReadLine` .</span><span class="sxs-lookup"><span data-stu-id="1d3bc-877">On non-Windows systems, the history files is stored at `$env:XDG_DATA_HOME/powershell/PSReadLine` or `$env:HOME/.local/share/powershell/PSReadLine`.</span></span>

### <a name="feedback--contributing-to-psreadline"></a><span data-ttu-id="1d3bc-878">Feedback & som bidrar till PSReadLine</span><span class="sxs-lookup"><span data-stu-id="1d3bc-878">Feedback & Contributing To PSReadLine</span></span>

[<span data-ttu-id="1d3bc-879">PSReadLine på GitHub</span><span class="sxs-lookup"><span data-stu-id="1d3bc-879">PSReadLine on GitHub</span></span>](https://github.com/PowerShell/PSReadLine)

<span data-ttu-id="1d3bc-880">Skicka gärna en pull-begäran eller skicka feedback på sidan GitHub.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-880">Feel free to submit a pull request or submit feedback on the GitHub page.</span></span>

## <a name="see-also"></a><span data-ttu-id="1d3bc-881">Se även</span><span class="sxs-lookup"><span data-stu-id="1d3bc-881">See Also</span></span>

<span data-ttu-id="1d3bc-882">PSReadLine påverkas kraftigt av GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) -biblioteket.</span><span class="sxs-lookup"><span data-stu-id="1d3bc-882">PSReadLine is heavily influenced by the GNU [readline](https://tiswww.case.edu/php/chet/readline/rltop.html) library.</span></span>
