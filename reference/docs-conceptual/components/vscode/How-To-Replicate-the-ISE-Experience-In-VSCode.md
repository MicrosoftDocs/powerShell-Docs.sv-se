---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117468"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="99e81-103">Så här replikerar du ISE-upplevelsen i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="99e81-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="99e81-104">Även om PowerShell-tillägget för VSCode inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VSCode-upplevelsen mer naturlig för användare av ISE.</span><span class="sxs-lookup"><span data-stu-id="99e81-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="99e81-105">Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VSCode för att göra det enklare att komma åt användarna jämfört med ISE.</span><span class="sxs-lookup"><span data-stu-id="99e81-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="99e81-106">Nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="99e81-106">Key bindings</span></span>

| <span data-ttu-id="99e81-107">Funktion</span><span class="sxs-lookup"><span data-stu-id="99e81-107">Function</span></span>                              | <span data-ttu-id="99e81-108">ISE-bindning</span><span class="sxs-lookup"><span data-stu-id="99e81-108">ISE Binding</span></span>                  | <span data-ttu-id="99e81-109">VSCode-bindning</span><span class="sxs-lookup"><span data-stu-id="99e81-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="99e81-110">Avbryta och bryta fel sökning</span><span class="sxs-lookup"><span data-stu-id="99e81-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="99e81-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="99e81-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="99e81-113">Kör aktuell rad/markerad text</span><span class="sxs-lookup"><span data-stu-id="99e81-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="99e81-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="99e81-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="99e81-116">Lista tillgängliga kodfragment</span><span class="sxs-lookup"><span data-stu-id="99e81-116">List available snippets</span></span>               | <span data-ttu-id="99e81-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="99e81-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="99e81-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="99e81-119">Anpassade nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="99e81-119">Custom Key bindings</span></span>

<span data-ttu-id="99e81-120">Du kan också [Konfigurera dina egna nyckel bindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i VSCode.</span><span class="sxs-lookup"><span data-stu-id="99e81-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="simplified-ise-like-ui"></a><span data-ttu-id="99e81-121">Förenklat ISE – liknande gränssnitt</span><span class="sxs-lookup"><span data-stu-id="99e81-121">Simplified ISE-like UI</span></span>

<span data-ttu-id="99e81-122">Om du vill förenkla Visual Studio Code-ANVÄNDARGRÄNSSNITTET för att se närmare användar gränssnittet för ISE, använder du följande två inställningar:</span><span class="sxs-lookup"><span data-stu-id="99e81-122">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

<span data-ttu-id="99e81-123">Avsnittet "aktivitets fält" och "Felsök sid List" visas i den röda rutan:</span><span class="sxs-lookup"><span data-stu-id="99e81-123">This will hide the "Activity Bar" and the "Debug Side Bar" sections below inside of the red box:</span></span>

![avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

<span data-ttu-id="99e81-125">Slut resultatet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="99e81-125">The end result looks like this:</span></span>

![Förenklad vy av VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a><span data-ttu-id="99e81-127">Slut för ande flik</span><span class="sxs-lookup"><span data-stu-id="99e81-127">Tab completion</span></span>

<span data-ttu-id="99e81-128">Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:</span><span class="sxs-lookup"><span data-stu-id="99e81-128">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> <span data-ttu-id="99e81-129">Den här inställningen lades till direkt i VSCode (i stället för i tillägget).</span><span class="sxs-lookup"><span data-stu-id="99e81-129">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="99e81-130">Dess beteende bestäms av VSCode direkt och kan inte ändras av tillägget.</span><span class="sxs-lookup"><span data-stu-id="99e81-130">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="99e81-131">Ingen fokus på konsolen vid körning</span><span class="sxs-lookup"><span data-stu-id="99e81-131">No focus on console when executing</span></span>

<span data-ttu-id="99e81-132">För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="99e81-132">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="99e81-133">Standardvärdet är `true` i tillgänglighets syfte.</span><span class="sxs-lookup"><span data-stu-id="99e81-133">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="99e81-134">Starta inte den integrerade konsolen vid start</span><span class="sxs-lookup"><span data-stu-id="99e81-134">Don't start integrated console on startup</span></span>

<span data-ttu-id="99e81-135">Stoppa den integrerade konsolen vid start genom att ange:</span><span class="sxs-lookup"><span data-stu-id="99e81-135">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="99e81-136">PowerShell-processen för bakgrunden kommer fortfarande att starta eftersom den innehåller IntelliSense, skript analys, symbol navigering osv. Men konsolen visas inte.</span><span class="sxs-lookup"><span data-stu-id="99e81-136">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="99e81-137">Anta att filerna är PowerShell som standard</span><span class="sxs-lookup"><span data-stu-id="99e81-137">Assume files are PowerShell by default</span></span>

<span data-ttu-id="99e81-138">Om du vill skapa nya/namnlösa filer registrerar du som PowerShell som standard:</span><span class="sxs-lookup"><span data-stu-id="99e81-138">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell",
```

## <a name="color-scheme"></a><span data-ttu-id="99e81-139">Färgschema</span><span class="sxs-lookup"><span data-stu-id="99e81-139">Color scheme</span></span>

<span data-ttu-id="99e81-140">Det finns ett antal ISE-teman som är tillgängliga för VSCode för att göra redigeraren att se mycket mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="99e81-140">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="99e81-141">I [Kommando palett] typ `theme` för att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="99e81-141">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="99e81-142">I list rutan väljer du `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="99e81-142">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="99e81-143">Du kan ange det här temat i inställningarna med:</span><span class="sxs-lookup"><span data-stu-id="99e81-143">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="99e81-144">PowerShell kommando Utforskaren</span><span class="sxs-lookup"><span data-stu-id="99e81-144">PowerShell Command Explorer</span></span>

<span data-ttu-id="99e81-145">Till [@corbob](https://github.com/corbob)kommer PowerShell-tillägget att ha början av en egen kommando Utforskare.</span><span class="sxs-lookup"><span data-stu-id="99e81-145">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="99e81-146">I [Kommando palett]anger du `PowerShell Command Explorer` och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="99e81-146">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="99e81-147">Öppna i ISE</span><span class="sxs-lookup"><span data-stu-id="99e81-147">Open in the ISE</span></span>

<span data-ttu-id="99e81-148">Om du vill öppna en fil i ISE ändå kan du använda <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="99e81-148">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="99e81-149">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="99e81-149">Other resources</span></span>

- <span data-ttu-id="99e81-150">4sysops har [en bra artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) om hur du konfigurerar VSCode för att vara mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="99e81-150">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="99e81-151">Mike F Robbins har [en bra post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) för att ställa in VSCode.</span><span class="sxs-lookup"><span data-stu-id="99e81-151">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="99e81-152">Lär dig mer om PowerShell har [en utmärkt Skriv åtgärd](https://www.learnpwsh.com/setup-vs-code-for-powershell/) för att hämta VSCode-installationsprogrammet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="99e81-152">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="99e81-153">Fler inställningar</span><span class="sxs-lookup"><span data-stu-id="99e81-153">More settings</span></span>

<span data-ttu-id="99e81-154">Om du känner till fler sätt att göra VSCode mer bekant för ISE-användare, bidrar till det här dokumentet. Om det finns en kompatibilitetsrapport som du letar efter, men du inte hittar något sätt att aktivera den, [öppnar du ett ärende](https://github.com/PowerShell/vscode-powershell/issues/new/choose) och ber om det!</span><span class="sxs-lookup"><span data-stu-id="99e81-154">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="99e81-155">Vi är alltid glada att kunna ta emot pull och bidrag även!</span><span class="sxs-lookup"><span data-stu-id="99e81-155">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="99e81-156">VSCode-tips</span><span class="sxs-lookup"><span data-stu-id="99e81-156">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="99e81-157">Kommando palett</span><span class="sxs-lookup"><span data-stu-id="99e81-157">Command Palette</span></span>

<span data-ttu-id="99e81-158"><kbd>F1</kbd> ELLER <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS)</span><span class="sxs-lookup"><span data-stu-id="99e81-158"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="99e81-159">Ett praktiskt sätt att köra kommandon i VSCode.</span><span class="sxs-lookup"><span data-stu-id="99e81-159">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="99e81-160">Mer information finns i [VSCode-dokumenten](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="99e81-160">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Kommando palett]: #command-palette
[Command Palette]: #command-palette
