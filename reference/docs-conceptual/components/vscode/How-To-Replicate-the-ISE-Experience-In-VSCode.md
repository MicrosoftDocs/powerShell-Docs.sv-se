---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279284"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="00b72-103">Så här replikerar du ISE-upplevelsen i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="00b72-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="00b72-104">Även om PowerShell-tillägget för VSCode inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VSCode-upplevelsen mer naturlig för användare av ISE.</span><span class="sxs-lookup"><span data-stu-id="00b72-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="00b72-105">Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VSCode för att göra det enklare att komma åt användarna jämfört med ISE.</span><span class="sxs-lookup"><span data-stu-id="00b72-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="00b72-106">ISE-läge</span><span class="sxs-lookup"><span data-stu-id="00b72-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="00b72-107">Den här funktionen är tillgänglig i PowerShell-tillägget för förhands granskning sedan version 2019.12.0 och i PowerShell-tillägget sedan version 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="00b72-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="00b72-108">Det enklaste sättet att replikera ISE-upplevelsen i Visual Studio Code är genom att aktivera "ISE-läge".</span><span class="sxs-lookup"><span data-stu-id="00b72-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="00b72-109">Det gör du genom att öppna kommandot pall (<kbd>F1</kbd> eller <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>P</kbd> eller <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS) och ange "ISE-läge".</span><span class="sxs-lookup"><span data-stu-id="00b72-109">To do this, open the command pallet (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span>
<span data-ttu-id="00b72-110">Välj "PowerShell: Aktivera ISE-läge" i listan.</span><span class="sxs-lookup"><span data-stu-id="00b72-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="00b72-111">Det här kommandot kommer att använda en mängd av inställningarna som påträffas i det här dokumentet automatiskt.</span><span class="sxs-lookup"><span data-stu-id="00b72-111">This command will apply a lot of the settings found in this document automatically.</span></span>
<span data-ttu-id="00b72-112">Resultatet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="00b72-112">The result looks like this:</span></span>

![ISE-läge](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

<span data-ttu-id="00b72-114">Resten av den här artikeln innehåller mer detaljerad information om inställningar i ISE-läge och vissa ytterligare inställningar.</span><span class="sxs-lookup"><span data-stu-id="00b72-114">The rest of this article includes more detailed information on settings in ISE Mode and some additional settings.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="00b72-115">Nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="00b72-115">Key bindings</span></span>

| <span data-ttu-id="00b72-116">Funktion</span><span class="sxs-lookup"><span data-stu-id="00b72-116">Function</span></span>                              | <span data-ttu-id="00b72-117">ISE-bindning</span><span class="sxs-lookup"><span data-stu-id="00b72-117">ISE Binding</span></span>                  | <span data-ttu-id="00b72-118">VSCode-bindning</span><span class="sxs-lookup"><span data-stu-id="00b72-118">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="00b72-119">Avbryta och bryta fel sökning</span><span class="sxs-lookup"><span data-stu-id="00b72-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="00b72-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="00b72-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-121"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="00b72-122">Kör aktuell rad/markerad text</span><span class="sxs-lookup"><span data-stu-id="00b72-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="00b72-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="00b72-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-124"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="00b72-125">Lista tillgängliga kodfragment</span><span class="sxs-lookup"><span data-stu-id="00b72-125">List available snippets</span></span>               | <span data-ttu-id="00b72-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="00b72-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="00b72-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="00b72-128">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="00b72-128">Custom Key bindings</span></span>

<span data-ttu-id="00b72-129">Du kan också [Konfigurera dina egna nyckel bindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i VSCode.</span><span class="sxs-lookup"><span data-stu-id="00b72-129">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="00b72-130">Förenklat ISE – liknande gränssnitt</span><span class="sxs-lookup"><span data-stu-id="00b72-130">Simplified ISE-like UI</span></span>

<span data-ttu-id="00b72-131">Om du vill förenkla Visual Studio Code-ANVÄNDARGRÄNSSNITTET för att se närmare användar gränssnittet för ISE, använder du följande två inställningar:</span><span class="sxs-lookup"><span data-stu-id="00b72-131">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> <span data-ttu-id="00b72-132">De här inställningarna ingår i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-132">These settings are included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="00b72-133">Avsnittet "aktivitets fält" och "Felsök sid List" visas i den röda rutan:</span><span class="sxs-lookup"><span data-stu-id="00b72-133">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="00b72-135">Slut resultatet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="00b72-135">The end result looks like this:</span></span>

![Förenklad vy av VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="00b72-137">Slut för ande flik</span><span class="sxs-lookup"><span data-stu-id="00b72-137">Tab completion</span></span>

<span data-ttu-id="00b72-138">Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:</span><span class="sxs-lookup"><span data-stu-id="00b72-138">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="00b72-139">Den här inställningen lades till direkt i VSCode (i stället för i tillägget).</span><span class="sxs-lookup"><span data-stu-id="00b72-139">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="00b72-140">Dess beteende bestäms av VSCode direkt och kan inte ändras av tillägget.</span><span class="sxs-lookup"><span data-stu-id="00b72-140">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

> [!NOTE]
> <span data-ttu-id="00b72-141">Den här inställningen ingår i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-141">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="00b72-142">Ingen fokus på konsolen vid körning</span><span class="sxs-lookup"><span data-stu-id="00b72-142">No focus on console when executing</span></span>

<span data-ttu-id="00b72-143">För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="00b72-143">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> <span data-ttu-id="00b72-144">Den här inställningen ingår i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-144">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

<span data-ttu-id="00b72-145">Standardvärdet är `true` i tillgänglighets syfte.</span><span class="sxs-lookup"><span data-stu-id="00b72-145">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="00b72-146">Starta inte den integrerade konsolen vid start</span><span class="sxs-lookup"><span data-stu-id="00b72-146">Don't start integrated console on startup</span></span>

<span data-ttu-id="00b72-147">Stoppa den integrerade konsolen vid start genom att ange:</span><span class="sxs-lookup"><span data-stu-id="00b72-147">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="00b72-148">PowerShell-processen för bakgrunden kommer fortfarande att starta eftersom den innehåller IntelliSense, skript analys, symbol navigering osv. Men konsolen visas inte.</span><span class="sxs-lookup"><span data-stu-id="00b72-148">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="00b72-149">Anta att filerna är PowerShell som standard</span><span class="sxs-lookup"><span data-stu-id="00b72-149">Assume files are PowerShell by default</span></span>

<span data-ttu-id="00b72-150">Om du vill skapa nya/namnlösa filer registrerar du som PowerShell som standard:</span><span class="sxs-lookup"><span data-stu-id="00b72-150">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> <span data-ttu-id="00b72-151">Den här inställningen ingår i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-151">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="color-scheme"></a><span data-ttu-id="00b72-152">Färg schema</span><span class="sxs-lookup"><span data-stu-id="00b72-152">Color scheme</span></span>

<span data-ttu-id="00b72-153">Det finns ett antal ISE-teman som är tillgängliga för VSCode för att göra redigeraren att se mycket mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="00b72-153">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="00b72-154">I [Kommando palett] typ `theme` för att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00b72-154">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="00b72-155">I list rutan väljer du `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="00b72-155">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="00b72-156">Du kan ange det här temat i inställningarna med:</span><span class="sxs-lookup"><span data-stu-id="00b72-156">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> <span data-ttu-id="00b72-157">Den här inställningen ingår i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-157">This setting is included in ["ISE Mode"](#ise-mode).</span></span>

## <a name="powershell-command-explorer"></a><span data-ttu-id="00b72-158">PowerShell kommando Utforskaren</span><span class="sxs-lookup"><span data-stu-id="00b72-158">PowerShell Command Explorer</span></span>

<span data-ttu-id="00b72-159">Till [@corbob](https://github.com/corbob)kommer PowerShell-tillägget att ha början av en egen kommando Utforskare.</span><span class="sxs-lookup"><span data-stu-id="00b72-159">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="00b72-160">I [Kommando palett]anger du `PowerShell Command Explorer` och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00b72-160">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

> [!NOTE]
> <span data-ttu-id="00b72-161">Detta visas automatiskt i ["ISE-läge"](#ise-mode).</span><span class="sxs-lookup"><span data-stu-id="00b72-161">This is shown automatically in ["ISE Mode"](#ise-mode).</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="00b72-162">Öppna i ISE</span><span class="sxs-lookup"><span data-stu-id="00b72-162">Open in the ISE</span></span>

<span data-ttu-id="00b72-163">Om du vill öppna en fil i ISE ändå kan du använda <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="00b72-163">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="00b72-164">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="00b72-164">Other resources</span></span>

- <span data-ttu-id="00b72-165">4sysops har [en bra artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) om hur du konfigurerar VSCode för att vara mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="00b72-165">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="00b72-166">Mike F Robbins har [en bra post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) för att ställa in VSCode.</span><span class="sxs-lookup"><span data-stu-id="00b72-166">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="00b72-167">Lär dig mer om PowerShell har [en utmärkt Skriv åtgärd](https://www.learnpwsh.com/setup-vs-code-for-powershell/) för att hämta VSCode-installationsprogrammet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="00b72-167">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="00b72-168">Fler inställningar</span><span class="sxs-lookup"><span data-stu-id="00b72-168">More settings</span></span>

<span data-ttu-id="00b72-169">Om du känner till fler sätt att göra VSCode mer bekant för ISE-användare, bidrar till det här dokumentet. Om det finns en kompatibilitetsrapport som du letar efter, men du inte hittar något sätt att aktivera den, [öppnar du ett ärende](https://github.com/PowerShell/vscode-powershell/issues/new/choose) och ber om det!</span><span class="sxs-lookup"><span data-stu-id="00b72-169">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="00b72-170">Vi är alltid glada att kunna ta emot pull och bidrag även!</span><span class="sxs-lookup"><span data-stu-id="00b72-170">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="00b72-171">VSCode-tips</span><span class="sxs-lookup"><span data-stu-id="00b72-171">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="00b72-172">Kommando palett</span><span class="sxs-lookup"><span data-stu-id="00b72-172">Command Palette</span></span>

<span data-ttu-id="00b72-173"><kbd>F1</kbd> ELLER <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS)</span><span class="sxs-lookup"><span data-stu-id="00b72-173"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="00b72-174">Ett praktiskt sätt att köra kommandon i VSCode.</span><span class="sxs-lookup"><span data-stu-id="00b72-174">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="00b72-175">Mer information finns i [VSCode-dokumenten](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="00b72-175">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Kommando palett]: #command-palette
[Command Palette]: #command-palette
