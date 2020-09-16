---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 6b0b8ce054695d6cc0fc578290c554e2dc1472bc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784630"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a><span data-ttu-id="fc4aa-103">Så här replikerar du ISE-upplevelsen i Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="fc4aa-103">How to replicate the ISE experience in Visual Studio Code</span></span>

<span data-ttu-id="fc4aa-104">Även om PowerShell-tillägget för VS Code inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VS Code-upplevelsen mer naturlig för användare av ISE.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-104">While the PowerShell extension for VS Code doesn't seek complete feature parity with the PowerShell ISE, there are features in place to make the VS Code experience more natural for users of the ISE.</span></span>

<span data-ttu-id="fc4aa-105">Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VS Code för att användar upplevelsen ska bli mer bekant jämfört med ISE.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-105">This document tries to list settings you can configure in VS Code to make the user experience a bit more familiar compared to the ISE.</span></span>

## <a name="ise-mode"></a><span data-ttu-id="fc4aa-106">ISE-läge</span><span class="sxs-lookup"><span data-stu-id="fc4aa-106">ISE Mode</span></span>

> [!NOTE]
> <span data-ttu-id="fc4aa-107">Den här funktionen är tillgänglig i PowerShell-tillägget för förhands granskning sedan version 2019.12.0 och i PowerShell-tillägget sedan version 2020.3.0.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-107">This feature is available in the PowerShell Preview extension since version 2019.12.0 and in the PowerShell extension since version 2020.3.0.</span></span>

<span data-ttu-id="fc4aa-108">Det enklaste sättet att replikera ISE-upplevelsen i Visual Studio Code är genom att aktivera "ISE-läge".</span><span class="sxs-lookup"><span data-stu-id="fc4aa-108">The easiest way to replicate the ISE experience in Visual Studio Code is by turning on "ISE Mode".</span></span>
<span data-ttu-id="fc4aa-109">Det gör du genom att öppna Command-paletten (<kbd>F1</kbd> eller <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> eller <kbd>cmd</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> på MacOS) och skriva i "ISE-läge".</span><span class="sxs-lookup"><span data-stu-id="fc4aa-109">To do this, open the command palette (<kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS) and type in "ISE Mode".</span></span> <span data-ttu-id="fc4aa-110">Välj "PowerShell: Aktivera ISE-läge" i listan.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-110">Select "PowerShell: Enable ISE Mode" from the list.</span></span>

<span data-ttu-id="fc4aa-111">Det här kommandot tillämpar automatiskt de inställningar som beskrivs nedan, vilket ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-111">This command automatically applies the settings described below The result looks like this:</span></span>

![Visual Studio Code i ISE-läge](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a><span data-ttu-id="fc4aa-113">Konfigurations inställningar för ISE-läge</span><span class="sxs-lookup"><span data-stu-id="fc4aa-113">ISE Mode configuration settings</span></span>

<span data-ttu-id="fc4aa-114">ISE-läget gör följande ändringar i VS Code-inställningar.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-114">ISE Mode makes the following changes to VS Code settings.</span></span>

- <span data-ttu-id="fc4aa-115">Nyckel bindningar</span><span class="sxs-lookup"><span data-stu-id="fc4aa-115">Key bindings</span></span>

  |               <span data-ttu-id="fc4aa-116">Funktion</span><span class="sxs-lookup"><span data-stu-id="fc4aa-116">Function</span></span>                |         <span data-ttu-id="fc4aa-117">ISE-bindning</span><span class="sxs-lookup"><span data-stu-id="fc4aa-117">ISE Binding</span></span>          |              <span data-ttu-id="fc4aa-118">VS-kod bindning</span><span class="sxs-lookup"><span data-stu-id="fc4aa-118">VS Code Binding</span></span>                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | <span data-ttu-id="fc4aa-119">Avbryta och bryta fel sökning</span><span class="sxs-lookup"><span data-stu-id="fc4aa-119">Interrupt and break debugger</span></span>          | <span data-ttu-id="fc4aa-120"><kbd>CTRL</kbd> + <kbd>B</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-120"><kbd>Ctrl</kbd>+<kbd>B</kbd></span></span> | <span data-ttu-id="fc4aa-121"><kbd>F6</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-121"><kbd>F6</kbd></span></span>                               |
  | <span data-ttu-id="fc4aa-122">Kör aktuell rad/markerad text</span><span class="sxs-lookup"><span data-stu-id="fc4aa-122">Execute current line/highlighted text</span></span> | <span data-ttu-id="fc4aa-123"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-123"><kbd>F8</kbd></span></span>                | <span data-ttu-id="fc4aa-124"><kbd>F8</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-124"><kbd>F8</kbd></span></span>                               |
  | <span data-ttu-id="fc4aa-125">Lista tillgängliga kodfragment</span><span class="sxs-lookup"><span data-stu-id="fc4aa-125">List available snippets</span></span>               | <span data-ttu-id="fc4aa-126"><kbd>CTRL</kbd> + <kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-126"><kbd>Ctrl</kbd>+<kbd>J</kbd></span></span> | <span data-ttu-id="fc4aa-127"><kbd>CTRL</kbd> + <kbd>Alt</kbd> + <kbd>J</kbd></span><span class="sxs-lookup"><span data-stu-id="fc4aa-127"><kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd></span></span> |

  > [!NOTE]
  > <span data-ttu-id="fc4aa-128">Du kan också [Konfigurera egna nyckel bindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i vs Code.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-128">You can [configure your own key bindings](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) in VS Code as well.</span></span>

- <span data-ttu-id="fc4aa-129">Förenklat ISE – liknande gränssnitt</span><span class="sxs-lookup"><span data-stu-id="fc4aa-129">Simplified ISE-like UI</span></span>

  <span data-ttu-id="fc4aa-130">Om du vill förenkla Visual Studio Code-ANVÄNDARGRÄNSSNITTET för att se närmare användar gränssnittet för ISE, använder du följande två inställningar:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-130">If you're looking to simplify the Visual Studio Code UI to look more closely to the UI of the ISE, apply these two settings:</span></span>

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  <span data-ttu-id="fc4aa-131">Dessa inställningar döljer avsnitten "aktivitets fält" och "Felsök sid fält" som visas i den röda rutan nedan:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-131">These settings hide the "Activity Bar" and the "Debug Side Bar" sections shown inside the red box below:</span></span>

  ![Avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  <span data-ttu-id="fc4aa-133">Slut resultatet ser ut så här:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-133">The end result looks like this:</span></span>

  ![Förenklad vy av VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- <span data-ttu-id="fc4aa-135">Slut för ande flik</span><span class="sxs-lookup"><span data-stu-id="fc4aa-135">Tab completion</span></span>

  <span data-ttu-id="fc4aa-136">Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-136">To enable more ISE-like tab completion, add this setting:</span></span>

  ```json
  "editor.tabCompletion": "on",
  ```

- <span data-ttu-id="fc4aa-137">Ingen fokus på konsolen vid körning</span><span class="sxs-lookup"><span data-stu-id="fc4aa-137">No focus on console when executing</span></span>

  <span data-ttu-id="fc4aa-138">För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-138">To keep the focus in the editor when you execute with <kbd>F8</kbd>:</span></span>

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  <span data-ttu-id="fc4aa-139">Standardvärdet är `true` för hjälpmedels syfte.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-139">The default is `true` for accessibility purposes.</span></span>

- <span data-ttu-id="fc4aa-140">Starta inte den integrerade konsolen vid start</span><span class="sxs-lookup"><span data-stu-id="fc4aa-140">Don't start integrated console on startup</span></span>

  <span data-ttu-id="fc4aa-141">Stoppa den integrerade konsolen vid start genom att ange:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-141">To stop the integrated console on startup, set:</span></span>

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > <span data-ttu-id="fc4aa-142">PowerShell-processen i bakgrunden börjar fortfarande tillhandahålla IntelliSense, skript analys, symbol navigering osv. konsolen visas inte.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-142">The background PowerShell process still starts to provide IntelliSense, script analysis, symbol navigation, etc., but the console won't be shown.</span></span>

- <span data-ttu-id="fc4aa-143">Anta att filerna är PowerShell som standard</span><span class="sxs-lookup"><span data-stu-id="fc4aa-143">Assume files are PowerShell by default</span></span>

  <span data-ttu-id="fc4aa-144">Om du vill skapa nya/namnlösa filer registrerar du som PowerShell som standard:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-144">To make new/untitled files, register as PowerShell by default:</span></span>

  ```json
  "files.defaultLanguage": "powershell",
  ```

- <span data-ttu-id="fc4aa-145">Färgschema</span><span class="sxs-lookup"><span data-stu-id="fc4aa-145">Color scheme</span></span>

  <span data-ttu-id="fc4aa-146">Det finns ett antal ISE-teman som är tillgängliga för VS Code för att göra redigeraren att se mycket mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-146">There are a number of ISE themes available for VS Code to make the editor look much more like the ISE.</span></span>

  <span data-ttu-id="fc4aa-147">I [paletten kommando][] typ `theme` `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-147">In the [Command Palette][] type `theme` to get `Preferences: Color Theme` and press <kbd>Enter</kbd>.</span></span> <span data-ttu-id="fc4aa-148">Välj i den nedrullningsbara listan `PowerShell ISE` .</span><span class="sxs-lookup"><span data-stu-id="fc4aa-148">In the drop-down list, select `PowerShell ISE`.</span></span>

  <span data-ttu-id="fc4aa-149">Du kan ange det här temat i inställningarna med:</span><span class="sxs-lookup"><span data-stu-id="fc4aa-149">You can set this theme in the settings with:</span></span>

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- <span data-ttu-id="fc4aa-150">PowerShell kommando Utforskaren</span><span class="sxs-lookup"><span data-stu-id="fc4aa-150">PowerShell Command Explorer</span></span>

  <span data-ttu-id="fc4aa-151">Till och med fungerar [@corbob](https://github.com/corbob) PowerShell-tillägget i början av en egen kommando Utforskare.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-151">Thanks to the work of [@corbob](https://github.com/corbob), the PowerShell extension has the beginnings of its own command explorer.</span></span>

  <span data-ttu-id="fc4aa-152">I [paletten kommando][]anger du `PowerShell Command Explorer` och trycker på <kbd>RETUR</kbd>.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-152">In the [Command Palette][], enter `PowerShell Command Explorer` and press <kbd>Enter</kbd>.</span></span>

- <span data-ttu-id="fc4aa-153">Öppna i ISE</span><span class="sxs-lookup"><span data-stu-id="fc4aa-153">Open in the ISE</span></span>

  <span data-ttu-id="fc4aa-154">Om du vill öppna en fil i Windows PowerShell ISE ändå öppnar du [kommando-paletten][], söker efter "öppna i ISE" och väljer sedan **PowerShell: öppna aktuell fil i PowerShell ISE**.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-154">If you want to open a file in the Windows PowerShell ISE anyway, open the [Command Palette][], search for "open in ise", then select **PowerShell: Open Current File in PowerShell ISE**.</span></span>

## <a name="other-resources"></a><span data-ttu-id="fc4aa-155">Andra resurser</span><span class="sxs-lookup"><span data-stu-id="fc4aa-155">Other resources</span></span>

- <span data-ttu-id="fc4aa-156">4sysops har [en bra artikel][4sysops] om att konfigurera vs Code för att vara mer som ISE.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-156">4sysops has [a great article][4sysops] on configuring VS Code to be more like the ISE.</span></span>
- <span data-ttu-id="fc4aa-157">Mike F Robbins har [en bra post][mikefrobbins] för att ställa in vs Code.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-157">Mike F Robbins has [a great post][mikefrobbins] on setting up VS Code.</span></span>
<!-- - Learn PowerShell has [an excellent write up][learnpwsh] setup for PowerShell. -->

## <a name="vs-code-tips"></a><span data-ttu-id="fc4aa-158">VS Code-tips</span><span class="sxs-lookup"><span data-stu-id="fc4aa-158">VS Code Tips</span></span>

- <span data-ttu-id="fc4aa-159">Kommando palett</span><span class="sxs-lookup"><span data-stu-id="fc4aa-159">Command Palette</span></span>

  <span data-ttu-id="fc4aa-160">Kommando paletten är ett praktiskt sätt att köra kommandon i VS Code.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-160">The Command Palette is handy way of executing commands in VS Code.</span></span> <span data-ttu-id="fc4aa-161">Öppna paletten kommando med <kbd>F1</kbd> eller <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> eller <kbd>cmd</kbd> + <kbd>Shift</kbd> + <kbd>p</kbd> på MacOS.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-161">Open the command palette using <kbd>F1</kbd> OR <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> OR <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS.</span></span>

  <span data-ttu-id="fc4aa-162">Mer information finns i [vs Code-dokumentationen][vsc-docs].</span><span class="sxs-lookup"><span data-stu-id="fc4aa-162">For more information, see [the VS Code documentation][vsc-docs].</span></span>

- <span data-ttu-id="fc4aa-163">Inaktivera fel söknings konsolen</span><span class="sxs-lookup"><span data-stu-id="fc4aa-163">Disable the Debug Console</span></span>

  <span data-ttu-id="fc4aa-164">Om du bara planerar att använda VS Code för PowerShell-skript kan du dölja **fel söknings konsolen** eftersom den inte används av PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-164">If you only plan on using VS Code for PowerShell scripting, you can hide the **Debug Console** since it is not used by the PowerShell extension.</span></span> <span data-ttu-id="fc4aa-165">Det gör du genom att högerklicka på **fel söknings konsolen** och sedan klicka på kryss markeringen för att dölja den.</span><span class="sxs-lookup"><span data-stu-id="fc4aa-165">To do so, right click on **Debug Console** then click on the check mark to hide it.</span></span>

## <a name="more-settings"></a><span data-ttu-id="fc4aa-166">Fler inställningar</span><span class="sxs-lookup"><span data-stu-id="fc4aa-166">More settings</span></span>

<span data-ttu-id="fc4aa-167">Om du känner till fler sätt att göra VS Code-känsla mer bekant för ISE-användare, bidrar till det här dokumentet. Om det finns en kompatibilitetsrapport som du letar efter, men du inte hittar något sätt att aktivera den, [öppnar du ett ärende][] och ber om det!</span><span class="sxs-lookup"><span data-stu-id="fc4aa-167">If you know of more ways to make VS Code feel more familiar for ISE users, contribute to this doc. If there's a compatibility configuration you're looking for, but you can't find any way to enable it, [open an issue][] and ask away!</span></span>

<span data-ttu-id="fc4aa-168">Vi är alltid glada att kunna ta emot pull och bidrag även!</span><span class="sxs-lookup"><span data-stu-id="fc4aa-168">We're always happy to accept PRs and contributions as well!</span></span>

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Kommando palett]: #vs-code-tips
[Command Palette]: #vs-code-tips
[öppna ett ärende]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose
[open an issue]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
