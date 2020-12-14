---
description: Beskriver hur du hämtar och kör kommandon i kommando historiken.
Locale: en-US
ms.date: 05/13/2020
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_history?view=powershell-7.2&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_History
ms.openlocfilehash: 44e03bd37b0b2c5928fb3aa850f3f5b554ccf123
ms.sourcegitcommit: 95d41698c7a2450eeb70ef2fb6507fe7e6eff3b6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/17/2020
ms.locfileid: "94710584"
---
# <a name="about-history"></a><span data-ttu-id="8ba20-103">Om historik</span><span class="sxs-lookup"><span data-stu-id="8ba20-103">About History</span></span>

## <a name="short-description"></a><span data-ttu-id="8ba20-104">Kort beskrivning</span><span class="sxs-lookup"><span data-stu-id="8ba20-104">Short Description</span></span>
<span data-ttu-id="8ba20-105">Beskriver hur du hämtar och kör kommandon i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-105">Describes how to get and run commands in the command history.</span></span>

## <a name="long-description"></a><span data-ttu-id="8ba20-106">Lång beskrivning</span><span class="sxs-lookup"><span data-stu-id="8ba20-106">Long Description</span></span>

<span data-ttu-id="8ba20-107">När du anger ett kommando i kommando tolken, sparar PowerShell kommandot i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-107">When you enter a command at the command prompt, PowerShell saves the command in the command history.</span></span> <span data-ttu-id="8ba20-108">Du kan använda kommandona i historiken som en post för ditt arbete.</span><span class="sxs-lookup"><span data-stu-id="8ba20-108">You can use the commands in the history as a record of your work.</span></span> <span data-ttu-id="8ba20-109">Du kan också återkalla och köra kommandona från kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-109">And, you can recall and run the commands from the command history.</span></span>

<span data-ttu-id="8ba20-110">PowerShell har två olika historik leverantörer: den inbyggda historiken och historiken som hanteras av **PSReadLine** -modulen.</span><span class="sxs-lookup"><span data-stu-id="8ba20-110">PowerShell has two different history providers: the built-in history and the history managed by the **PSReadLine** module.</span></span> <span data-ttu-id="8ba20-111">Historiken hanteras separat, men båda historiken är tillgängliga i sessioner där **PSReadLine** läses in.</span><span class="sxs-lookup"><span data-stu-id="8ba20-111">The histories are managed separately, but both histories are available in sessions where **PSReadLine** is loaded.</span></span>

## <a name="using-the-psreadline-history"></a><span data-ttu-id="8ba20-112">Använda PSReadLine historik</span><span class="sxs-lookup"><span data-stu-id="8ba20-112">Using the PSReadLine history</span></span>

<span data-ttu-id="8ba20-113">PSReadLine-historiken spårar de kommandon som används i alla PowerShell-sessioner.</span><span class="sxs-lookup"><span data-stu-id="8ba20-113">The PSReadLine history tracks the commands used in all PowerShell sessions.</span></span>
<span data-ttu-id="8ba20-114">Historiken skrivs till en central fil per värd.</span><span class="sxs-lookup"><span data-stu-id="8ba20-114">The history is written to a central file per host.</span></span> <span data-ttu-id="8ba20-115">Historik filen är tillgänglig för alla sessioner och innehåller tidigare historik.</span><span class="sxs-lookup"><span data-stu-id="8ba20-115">That history file is available to all sessions and contains all past history.</span></span> <span data-ttu-id="8ba20-116">Historiken tas inte bort när sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="8ba20-116">The history is not deleted when the session ends.</span></span> <span data-ttu-id="8ba20-117">Den historiken kan inte heller hanteras av `*-History` cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="8ba20-117">Also, that history cannot be managed by the `*-History` cmdlets.</span></span> <span data-ttu-id="8ba20-118">Mer information finns i [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="8ba20-118">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

## <a name="using-the-built-in-session-history"></a><span data-ttu-id="8ba20-119">Använda den inbyggda tidigare sessionen</span><span class="sxs-lookup"><span data-stu-id="8ba20-119">Using the built-in session history</span></span>

<span data-ttu-id="8ba20-120">Den inbyggda historiken spårar bara de kommandon som används i den aktuella sessionen.</span><span class="sxs-lookup"><span data-stu-id="8ba20-120">The built-in history only tracks the commands used in the current session.</span></span> <span data-ttu-id="8ba20-121">Historiken är inte tillgänglig för andra sessioner och tas bort när sessionen avslutas.</span><span class="sxs-lookup"><span data-stu-id="8ba20-121">The history is not available to other sessions and is deleted when the session ends.</span></span>

### <a name="history-cmdlets"></a><span data-ttu-id="8ba20-122">Historik-cmdletar</span><span class="sxs-lookup"><span data-stu-id="8ba20-122">History Cmdlets</span></span>

<span data-ttu-id="8ba20-123">PowerShell har en uppsättning cmdletar som hanterar kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-123">PowerShell has a set of cmdlets that manage the command history.</span></span>

| <span data-ttu-id="8ba20-124">Cmdlet</span><span class="sxs-lookup"><span data-stu-id="8ba20-124">Cmdlet</span></span>           | <span data-ttu-id="8ba20-125">Alias</span><span class="sxs-lookup"><span data-stu-id="8ba20-125">Alias</span></span>  | <span data-ttu-id="8ba20-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8ba20-126">Description</span></span>                                |
| ---------------- | ------ | ------------------------------------------ |
| `Get-History`    | `h`    | <span data-ttu-id="8ba20-127">Hämtar kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-127">Gets the command history.</span></span>                  |
| `Invoke-History` | `r`    | <span data-ttu-id="8ba20-128">Kör ett kommando i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-128">Runs a command in the command history.</span></span>     |
| `Add-History`    |        | <span data-ttu-id="8ba20-129">Lägger till ett kommando i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-129">Adds a command to the command history.</span></span>     |
| `Clear-History`  | `clhy` | <span data-ttu-id="8ba20-130">Tar bort kommandon från kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-130">Deletes commands from the command history.</span></span> |

### <a name="keyboard-shortcuts-for-managing-history"></a><span data-ttu-id="8ba20-131">Kortkommandon för att hantera historik</span><span class="sxs-lookup"><span data-stu-id="8ba20-131">Keyboard Shortcuts for Managing History</span></span>

<span data-ttu-id="8ba20-132">I PowerShell-konsolen kan du använda följande kortkommandon för att hantera kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-132">In the PowerShell console, you can use the following shortcuts to manage the command history.</span></span>

- <span data-ttu-id="8ba20-133"><kbd>Nedåtpil</kbd> – visar föregående kommando.</span><span class="sxs-lookup"><span data-stu-id="8ba20-133"><kbd>UpArrow</kbd> - Displays the previous command.</span></span>
- <span data-ttu-id="8ba20-134"><kbd>NEDPIL</kbd> – visar nästa kommando.</span><span class="sxs-lookup"><span data-stu-id="8ba20-134"><kbd>DownArrow</kbd> - Displays the next command.</span></span>
- <span data-ttu-id="8ba20-135"><kbd>F7</kbd> – visar kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-135"><kbd>F7</kbd> - Displays the command history.</span></span>
- <span data-ttu-id="8ba20-136"><kbd>ESC</kbd> – för att dölja historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-136"><kbd>ESC</kbd> - To hide the history.</span></span>
- <span data-ttu-id="8ba20-137"><kbd>F8</kbd> – hittar ett kommando.</span><span class="sxs-lookup"><span data-stu-id="8ba20-137"><kbd>F8</kbd> - Finds a command.</span></span> <span data-ttu-id="8ba20-138">Skriv ett eller flera tecken och tryck sedan på <kbd>F8</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8ba20-138">Type one or more characters then press <kbd>F8</kbd>.</span></span> <span data-ttu-id="8ba20-139">Tryck på <kbd>F8</kbd> igen nästa instans.</span><span class="sxs-lookup"><span data-stu-id="8ba20-139">Press <kbd>F8</kbd> again the next instance.</span></span>
- <span data-ttu-id="8ba20-140"><kbd>F9</kbd> – hitta ett kommando efter historik-ID.</span><span class="sxs-lookup"><span data-stu-id="8ba20-140"><kbd>F9</kbd> - Find a command by history ID.</span></span> <span data-ttu-id="8ba20-141">Skriv in historik-ID och tryck sedan på <kbd>F9</kbd>.</span><span class="sxs-lookup"><span data-stu-id="8ba20-141">Type the history ID then press <kbd>F9</kbd>.</span></span> <span data-ttu-id="8ba20-142">Tryck på <kbd>F7</kbd> för att hitta ID: t.</span><span class="sxs-lookup"><span data-stu-id="8ba20-142">Press <kbd>F7</kbd> to find the ID.</span></span>
- <span data-ttu-id="8ba20-143"><kbd>#</kbd>`<string>`</kbd><kbd>TABB</kbd> – Sök igenom historiken efter `*<string>*` och returnerar den senaste matchningen.</span><span class="sxs-lookup"><span data-stu-id="8ba20-143"><kbd>#</kbd>`<string>`</kbd><kbd>Tab</kbd> - Search the history for `*<string>*` and returns the most recent match.</span></span> <span data-ttu-id="8ba20-144">Om du trycker på <kbd>TABB</kbd> flera gånger går det att använda matchande objekt i historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-144">If you press <kbd>Tab</kbd> repeatedly, it cycles through the matching items in your history.</span></span>

> [!NOTE]
> <span data-ttu-id="8ba20-145">Dessa nyckel bindningar implementeras av konsol värd programmet.</span><span class="sxs-lookup"><span data-stu-id="8ba20-145">These key bindings are implemented by the console host application.</span></span> <span data-ttu-id="8ba20-146">Andra program, till exempel Visual Studio Code eller Windows Terminal, kan ha olika nyckel bindningar.</span><span class="sxs-lookup"><span data-stu-id="8ba20-146">Other applications, such as Visual Studio Code or Windows Terminal, can have different key bindings.</span></span> <span data-ttu-id="8ba20-147">Bindningarna kan åsidosättas av PSReadLine-modulen.</span><span class="sxs-lookup"><span data-stu-id="8ba20-147">The bindings can be overridden by the PSReadLine module.</span></span> <span data-ttu-id="8ba20-148">PSReadLine läses in automatiskt när du startar en PowerShell-session.</span><span class="sxs-lookup"><span data-stu-id="8ba20-148">PSReadLine loads automatically when you start a PowerShell session.</span></span>
> <span data-ttu-id="8ba20-149">Med PSReadLine inläst är <kbd>F7</kbd> och <kbd>F9</kbd> inte kopplade till någon funktion.</span><span class="sxs-lookup"><span data-stu-id="8ba20-149">With PSReadLine loaded, <kbd>F7</kbd> and <kbd>F9</kbd> are not bound to any function.</span></span> <span data-ttu-id="8ba20-150">PSReadLine tillhandahåller inte motsvarande funktioner.</span><span class="sxs-lookup"><span data-stu-id="8ba20-150">PSReadLine does not provide equivalent functionality.</span></span> <span data-ttu-id="8ba20-151">Mer information finns i [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span><span class="sxs-lookup"><span data-stu-id="8ba20-151">For more information, see [about_PSReadLine](../../PSReadLine/About/about_PSReadLine.md).</span></span>

### <a name="maximumhistorycount"></a><span data-ttu-id="8ba20-152">MaximumHistoryCount</span><span class="sxs-lookup"><span data-stu-id="8ba20-152">MaximumHistoryCount</span></span>

<span data-ttu-id="8ba20-153">`$MaximumHistoryCount`Variabeln Preference fastställer det maximala antalet kommandon som PowerShell sparar i kommando historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-153">The `$MaximumHistoryCount` preference variable determines the maximum number of commands that PowerShell saves in the command history.</span></span> <span data-ttu-id="8ba20-154">Standardvärdet är </span><span class="sxs-lookup"><span data-stu-id="8ba20-154">The default value is</span></span>
4096.

<span data-ttu-id="8ba20-155">Följande kommando sänker till exempel `$MaximumHistoryCount` till 100-kommandon:</span><span class="sxs-lookup"><span data-stu-id="8ba20-155">For example, the following command lowers the `$MaximumHistoryCount` to 100 commands:</span></span>

```powershell
$MaximumHistoryCount = 100
```

<span data-ttu-id="8ba20-156">Tillämpa inställningen genom att starta om PowerShell.</span><span class="sxs-lookup"><span data-stu-id="8ba20-156">To apply the setting, restart PowerShell.</span></span>

<span data-ttu-id="8ba20-157">Om du vill spara det nya variabelvärdet för alla PowerShell-sessioner lägger du till tilldelnings uttrycket i en PowerShell-profil.</span><span class="sxs-lookup"><span data-stu-id="8ba20-157">To save the new variable value for all your PowerShell sessions, add the assignment statement to a PowerShell profile.</span></span> <span data-ttu-id="8ba20-158">Mer information om profiler finns [about_Profiles](about_Profiles.md).</span><span class="sxs-lookup"><span data-stu-id="8ba20-158">For more information about profiles, see [about_Profiles](about_Profiles.md).</span></span>

<span data-ttu-id="8ba20-159">Mer information om `$MaximumHistoryCount` variabeln Preference finns [about_Preference_Variables](about_Preference_Variables.md).</span><span class="sxs-lookup"><span data-stu-id="8ba20-159">For more information about the `$MaximumHistoryCount` preference variable, see [about_Preference_Variables](about_Preference_Variables.md).</span></span>

### <a name="order-of-commands-in-the-history"></a><span data-ttu-id="8ba20-160">Ordning för kommandon i historiken</span><span class="sxs-lookup"><span data-stu-id="8ba20-160">Order of Commands in the History</span></span>

<span data-ttu-id="8ba20-161">Kommandon läggs till i historiken när kommandot har körts, inte när kommandot anges.</span><span class="sxs-lookup"><span data-stu-id="8ba20-161">Commands are added to the history when the command finishes executing, not when the command is entered.</span></span> <span data-ttu-id="8ba20-162">Om kommandona tar lite tid att slutföra, eller om kommandona körs i en kapslad prompt, kan det hända att kommandona verkar vara i historiken.</span><span class="sxs-lookup"><span data-stu-id="8ba20-162">If commands take some time to be completed, or if the commands are executing in a nested prompt, the commands might appear to be out of order in the history.</span></span> <span data-ttu-id="8ba20-163">Kommandon som körs i en kapslad prompt slutförs bara när du avslutar prompt-nivån.</span><span class="sxs-lookup"><span data-stu-id="8ba20-163">Commands that are executing in a nested prompt are completed only when you exit the prompt level.</span></span>

## <a name="see-also"></a><span data-ttu-id="8ba20-164">Se även</span><span class="sxs-lookup"><span data-stu-id="8ba20-164">See Also</span></span>

- [<span data-ttu-id="8ba20-165">about_Line_Editing</span><span class="sxs-lookup"><span data-stu-id="8ba20-165">about_Line_Editing</span></span>](about_Line_Editing.md)
- [<span data-ttu-id="8ba20-166">about_Preference_Variables</span><span class="sxs-lookup"><span data-stu-id="8ba20-166">about_Preference_Variables</span></span>](about_Preference_Variables.md)
- [<span data-ttu-id="8ba20-167">about_Profiles</span><span class="sxs-lookup"><span data-stu-id="8ba20-167">about_Profiles</span></span>](about_Profiles.md)
- [<span data-ttu-id="8ba20-168">about_Variables</span><span class="sxs-lookup"><span data-stu-id="8ba20-168">about_Variables</span></span>](about_Variables.md)
- [<span data-ttu-id="8ba20-169">about_PSReadLine</span><span class="sxs-lookup"><span data-stu-id="8ba20-169">about_PSReadLine</span></span>](../../PSReadLine/About/about_PSReadLine.md)

