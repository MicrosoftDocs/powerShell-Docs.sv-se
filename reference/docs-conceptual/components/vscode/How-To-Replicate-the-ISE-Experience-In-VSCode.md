---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 983da850c13d72bcdc7b2d33970c6e9e06b3d869
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058530"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="ed52d-103">Så här replikerar du ISE-upplevelsen i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="ed52d-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="ed52d-104">PowerShell-tillägget för VSCode inte söker efter slutförd funktionsparitet med PowerShell ISE, men det finns funktioner för att göra VSCode-upplevelsen mer naturligt för användare av ISE.</span><span class="sxs-lookup"><span data-stu-id="ed52d-104">While the PowerShell extension for VSCode doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VSCode experience more natural for users of the ISE.</span></span>

<span data-ttu-id="ed52d-105">Det här dokumentet försöker listinställningar som du kan konfigurera i VSCode för att användaren ska få lite mer bekant jämfört med ISE.</span><span class="sxs-lookup"><span data-stu-id="ed52d-105">This document tries to list settings you can configure in VSCode to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="key-bindings"></a><span data-ttu-id="ed52d-106">Nyckelbindningar</span><span class="sxs-lookup"><span data-stu-id="ed52d-106">Key bindings</span></span>

| <span data-ttu-id="ed52d-107">Funktion</span><span class="sxs-lookup"><span data-stu-id="ed52d-107">Function</span></span>                              | <span data-ttu-id="ed52d-108">ISE-bindning</span><span class="sxs-lookup"><span data-stu-id="ed52d-108">ISE Binding</span></span>                  | <span data-ttu-id="ed52d-109">VSCode Binding</span><span class="sxs-lookup"><span data-stu-id="ed52d-109">VSCode Binding</span></span>                              |
| ----------------                      | -----------                  | --------------                              |
| <span data-ttu-id="ed52d-110">Felsökare för avbrott och reparation</span><span class="sxs-lookup"><span data-stu-id="ed52d-110">Interrupt and break debugger</span></span>          | <span data-ttu-id="ed52d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-111"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="ed52d-112"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-112"><kbd>F6</kbd></span></span>                               |
| <span data-ttu-id="ed52d-113">Köra aktuell rad/markerad text</span><span class="sxs-lookup"><span data-stu-id="ed52d-113">Execute current line/highlighted text</span></span> | <span data-ttu-id="ed52d-114"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-114"><kbd>F8</kbd></span></span>                | <span data-ttu-id="ed52d-115"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-115"><kbd>F8</kbd></span></span>                               |
| <span data-ttu-id="ed52d-116">Lista tillgängliga kodfragment</span><span class="sxs-lookup"><span data-stu-id="ed52d-116">List available snippets</span></span>               | <span data-ttu-id="ed52d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-117"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="ed52d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="ed52d-118"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

### <a name="custom-key-bindings"></a><span data-ttu-id="ed52d-119">Den anpassade nyckeln bindningar</span><span class="sxs-lookup"><span data-stu-id="ed52d-119">Custom Key bindings</span></span>

<span data-ttu-id="ed52d-120">Du kan [konfigurera egna nyckelbindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i VSCode samt.</span><span class="sxs-lookup"><span data-stu-id="ed52d-120">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VSCode as well.</span></span>

## <a name="tab-completion"></a><span data-ttu-id="ed52d-121">Tabbifyllning</span><span class="sxs-lookup"><span data-stu-id="ed52d-121">Tab completion</span></span>

<span data-ttu-id="ed52d-122">Lägg till den här inställningen om du vill aktivera fler ISE-liknande tabbifyllning:</span><span class="sxs-lookup"><span data-stu-id="ed52d-122">To enable more ISE-like tab completion, add this setting:</span></span>

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> <span data-ttu-id="ed52d-123">Den här inställningen har lagts till direkt till VSCode (i stället för i tillägget).</span><span class="sxs-lookup"><span data-stu-id="ed52d-123">This setting was added directly to VSCode (rather than in the extension).</span></span> <span data-ttu-id="ed52d-124">Sitt beteende bestäms av VSCode direkt och kan inte ändras av tillägget.</span><span class="sxs-lookup"><span data-stu-id="ed52d-124">Its behavior is determined by VSCode directly and cannot be changed by the extension.</span></span>

## <a name="no-focus-on-console-when-executing"></a><span data-ttu-id="ed52d-125">Inga fokus på konsolen när du kör</span><span class="sxs-lookup"><span data-stu-id="ed52d-125">No focus on console when executing</span></span>

<span data-ttu-id="ed52d-126">Att hålla fokus i redigeraren när du kör med <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="ed52d-126">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

<span data-ttu-id="ed52d-127">Standardvärdet är `true` för hjälpmedel.</span><span class="sxs-lookup"><span data-stu-id="ed52d-127">The default is `true` for accessibility purposes.</span></span>

## <a name="dont-start-integrated-console-on-startup"></a><span data-ttu-id="ed52d-128">Starta inte integrerad konsol vid start</span><span class="sxs-lookup"><span data-stu-id="ed52d-128">Don't start integrated console on startup</span></span>

<span data-ttu-id="ed52d-129">Om du vill stoppa integrerad konsol vid start, ange:</span><span class="sxs-lookup"><span data-stu-id="ed52d-129">To stop the integrated console on startup, set:</span></span>

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> <span data-ttu-id="ed52d-130">Bakgrunden PowerShell-processen startar fortfarande eftersom som ger IntelliSense, analys av skriptet, symbol navigering osv. Men kommer inte att visas i konsolen.</span><span class="sxs-lookup"><span data-stu-id="ed52d-130">The background PowerShell process will still start since that provides IntelliSense, script analysis, symbol navigation, etc. But the console won't be shown.</span></span>

## <a name="assume-files-are-powershell-by-default"></a><span data-ttu-id="ed52d-131">Anta att filer är PowerShell som standard</span><span class="sxs-lookup"><span data-stu-id="ed52d-131">Assume files are PowerShell by default</span></span>

<span data-ttu-id="ed52d-132">Registrera dig som PowerShell som standard för att se nya/Namnlös filer:</span><span class="sxs-lookup"><span data-stu-id="ed52d-132">To make new/untitled files, register as PowerShell by default:</span></span>

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a><span data-ttu-id="ed52d-133">Färgschema</span><span class="sxs-lookup"><span data-stu-id="ed52d-133">Color scheme</span></span>

<span data-ttu-id="ed52d-134">Det finns ett antal ISE teman för VSCode för att göra redigeraren Se mycket mer likt ISE.</span><span class="sxs-lookup"><span data-stu-id="ed52d-134">There are a number of ISE themes available for VSCode to make the editor look much more like the ISE.</span></span>

<span data-ttu-id="ed52d-135">I den [Kommandopalett] typ `theme` att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ed52d-135">In the [Command Palette] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span>
<span data-ttu-id="ed52d-136">I listrutan, väljer `PowerShell ISE`.</span><span class="sxs-lookup"><span data-stu-id="ed52d-136">In the drop-down list, select `PowerShell ISE`.</span></span>

<span data-ttu-id="ed52d-137">Du kan ange den här tema i inställningarna med:</span><span class="sxs-lookup"><span data-stu-id="ed52d-137">You can set this theme in the settings with:</span></span>

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a><span data-ttu-id="ed52d-138">PowerShell-kommando Explorer</span><span class="sxs-lookup"><span data-stu-id="ed52d-138">PowerShell Command Explorer</span></span>

<span data-ttu-id="ed52d-139">Tack vare verk som tillhör [ @corbob ](https://github.com/corbob), PowerShell-tillägget har början av en egen kommandot explorer.</span><span class="sxs-lookup"><span data-stu-id="ed52d-139">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

<span data-ttu-id="ed52d-140">I den [Kommandopalett], ange `PowerShell Command Explorer` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ed52d-140">In the [Command Palette], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

## <a name="open-in-the-ise"></a><span data-ttu-id="ed52d-141">Öppna i ISE</span><span class="sxs-lookup"><span data-stu-id="ed52d-141">Open in the ISE</span></span>

<span data-ttu-id="ed52d-142">Om du hamnar vill öppna en fil i ISE ändå kan du använda <kbd>SKIFT</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="ed52d-142">If you end up wanting to open a file in the ISE anyway, you can use <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.</span></span>

## <a name="other-resources"></a><span data-ttu-id="ed52d-143">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="ed52d-143">Other resources</span></span>

- <span data-ttu-id="ed52d-144">4sysops har [en bra artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) om hur du konfigurerar VSCode för att vara mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="ed52d-144">4sysops has [a great article](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) on configuring VSCode to be more like the ISE.</span></span>
- <span data-ttu-id="ed52d-145">Mike F Robbins har [ett bra inlägg](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) om hur du konfigurerar VSCode.</span><span class="sxs-lookup"><span data-stu-id="ed52d-145">Mike F Robbins has [a great post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) on setting up VSCode.</span></span>
- <span data-ttu-id="ed52d-146">Lär dig PowerShell har [en utmärkt Skriv upp](https://www.learnpwsh.com/setup-vs-code-for-powershell/) på att få VSCode installationsprogrammet för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="ed52d-146">Learn PowerShell has [an excellent write up](https://www.learnpwsh.com/setup-vs-code-for-powershell/) on getting VSCode setup for PowerShell.</span></span>

## <a name="more-settings"></a><span data-ttu-id="ed52d-147">Fler inställningar</span><span class="sxs-lookup"><span data-stu-id="ed52d-147">More settings</span></span>

<span data-ttu-id="ed52d-148">Om du känner av fler sätt att göra VSCode känna dig mer bekant för ISE-användare kan bidra till det här dokumentet. Om det finns en konfiguration för kompatibilitet som du letar efter, men du kan inte hitta några sätt att göra det möjligt för [öppna ett ärende](https://github.com/PowerShell/vscode-powershell/issues/new/choose) och fråga!</span><span class="sxs-lookup"><span data-stu-id="ed52d-148">If you know of more ways to make VSCode feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue](https://github.com/PowerShell/vscode-powershell/issues/new/choose) and ask away!</span></span>

<span data-ttu-id="ed52d-149">Vi är alltid glada över att acceptera pull-begäranden och bidrag samt!</span><span class="sxs-lookup"><span data-stu-id="ed52d-149">We're always happy to accept PRs and contributions as well!</span></span>

## <a name="vscode-tips"></a><span data-ttu-id="ed52d-150">Tips för VSCode</span><span class="sxs-lookup"><span data-stu-id="ed52d-150">VSCode Tips</span></span>

### <a name="command-palette"></a><span data-ttu-id="ed52d-151">Kommandopalett</span><span class="sxs-lookup"><span data-stu-id="ed52d-151">Command Palette</span></span>

<span data-ttu-id="ed52d-152"><kbd>F1</kbd> eller <kbd>Ctrl</kbd>+<kbd>SKIFT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Flytta</kbd>+<kbd>P</kbd> på macOS)</span><span class="sxs-lookup"><span data-stu-id="ed52d-152"><kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS)</span></span>

<span data-ttu-id="ed52d-153">Ett praktiskt sätt att köra kommandon i VSCode.</span><span class="sxs-lookup"><span data-stu-id="ed52d-153">A handy way of executing commands in VSCode.</span></span>
<span data-ttu-id="ed52d-154">Mer information finns i [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span><span class="sxs-lookup"><span data-stu-id="ed52d-154">For more information, see [the VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).</span></span>

[Kommandopalett]: #command-palette
[Command Palette]: #command-palette
