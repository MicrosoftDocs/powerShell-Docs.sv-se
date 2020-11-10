---
title: Använda Visual Studio Code för PowerShell-utveckling
description: Använda Visual Studio Code för PowerShell-utveckling
ms.date: 11/07/2019
ms.openlocfilehash: 8a4ceb3da669716915449af2d211aaf2ae61bb4f
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94390312"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="4bcb8-103">Använda Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="4bcb8-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="4bcb8-104">[Visual Studio Code][vscode] är en plattforms oberoende skript redigerare från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-104">[Visual Studio Code][vscode] is a cross-platform script editor by Microsoft.</span></span> <span data-ttu-id="4bcb8-105">Tillsammans med [PowerShell-tillägget][psext]ger det en omfattande och interaktiv skript redigerings upplevelse, vilket gör det enklare att skriva pålitliga PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-105">Together with the [PowerShell extension][psext], it provides a rich and interactive script editing experience, making it easier to write reliable PowerShell scripts.</span></span> <span data-ttu-id="4bcb8-106">Visual Studio Code med PowerShell-tillägget är den rekommenderade redigeraren för att skriva PowerShell-skript.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-106">Visual Studio Code with the PowerShell extension is the recommended editor for writing PowerShell scripts.</span></span>

<span data-ttu-id="4bcb8-107">Det stöder följande PowerShell-versioner:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-107">It supports the following PowerShell versions:</span></span>

- <span data-ttu-id="4bcb8-108">PowerShell 7 och uppåt (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="4bcb8-108">PowerShell 7 and up (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="4bcb8-109">PowerShell Core 6 (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="4bcb8-109">PowerShell Core 6 (Windows, macOS, and Linux)</span></span>
- <span data-ttu-id="4bcb8-110">Windows PowerShell 5,1 (endast Windows)</span><span class="sxs-lookup"><span data-stu-id="4bcb8-110">Windows PowerShell 5.1 (Windows-only)</span></span>

> [!NOTE]
> <span data-ttu-id="4bcb8-111">Visual Studio Code är inte samma sak som [Visual Studio][].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-111">Visual Studio Code is not the same as [Visual Studio][].</span></span>

## <a name="getting-started"></a><span data-ttu-id="4bcb8-112">Komma igång</span><span class="sxs-lookup"><span data-stu-id="4bcb8-112">Getting started</span></span>

<span data-ttu-id="4bcb8-113">Innan du börjar ska du kontrol lera att PowerShell finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-113">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="4bcb8-114">För moderna arbets belastningar på Windows, macOS och Linux, se följande länkar:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-114">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="4bcb8-115">[Installera PowerShell i Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-115">[Installing PowerShell on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="4bcb8-116">[Installera PowerShell i macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-116">[Installing PowerShell on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="4bcb8-117">[Installera PowerShell i Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-117">[Installing PowerShell on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="4bcb8-118">För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-118">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

> [!IMPORTANT]
> <span data-ttu-id="4bcb8-119">[Windows PowerShell ISE][ise] är fortfarande tillgängligt för Windows.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-119">The [Windows PowerShell ISE][ise] is still available for Windows.</span></span> <span data-ttu-id="4bcb8-120">Men det är inte längre i den aktiva funktions utvecklingen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-120">However, it is no longer in active feature development.</span></span> <span data-ttu-id="4bcb8-121">ISE fungerar inte med PowerShell 6 och senare.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-121">The ISE does not work with PowerShell 6 and higher.</span></span> <span data-ttu-id="4bcb8-122">Som en komponent i Windows fortsätter den att vara officiellt tillgänglig för säkerhets-och högprioriterade service-korrigeringar.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-122">As a component of Windows, it continues to be officially supported for security and high-priority servicing fixes.</span></span>
> <span data-ttu-id="4bcb8-123">Vi har inga planer på att ta bort ISE från Windows.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-123">We have no plans to remove the ISE from Windows.</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="4bcb8-124">Redigera med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bcb8-124">Editing with Visual Studio Code</span></span>

1. <span data-ttu-id="4bcb8-125">Installera Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-125">Install Visual Studio Code.</span></span> <span data-ttu-id="4bcb8-126">Mer information finns i Översikt över [konfiguration av Visual Studio Code][vsc-setup].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-126">For more information, see the overview [Setting up Visual Studio Code][vsc-setup].</span></span>

   <span data-ttu-id="4bcb8-127">Det finns installations anvisningar för varje plattform:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-127">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="4bcb8-128">**Windows** : följ installations anvisningarna på sidan som [körs i Visual Studio Code på Windows][vsc-setup-win] .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-128">**Windows** : follow the installation instructions on the [Running Visual Studio Code on Windows][vsc-setup-win] page.</span></span>
   - <span data-ttu-id="4bcb8-129">**MacOS** : följ installationsinstruktionerna på sidan [med Visual Studio Code på MacOS][vsc-setup-macOS] .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-129">**macOS** : follow the installation instructions on the [Running Visual Studio Code on macOS][vsc-setup-macOS] page.</span></span>
   - <span data-ttu-id="4bcb8-130">**Linux** : följ installations anvisningarna på sidan som [Kör Visual Studio Code på Linux][vsc-setup-linux] .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-130">**Linux** : follow the installation instructions on the [Running Visual Studio Code on Linux][vsc-setup-linux] page.</span></span>

1. <span data-ttu-id="4bcb8-131">Installera PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-131">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="4bcb8-132">Starta Visual Studio Code-appen genom att skriva `code` i en-konsol eller `code-insiders` om du har installerat Visual Studio Codes-Insiders.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-132">Launch the Visual Studio Code app by typing `code` in a console or `code-insiders` if you installed Visual Studio Code Insiders.</span></span>
   1. <span data-ttu-id="4bcb8-133">Starta **Quick Open** på Windows eller Linux genom att trycka på <kbd>CTRL</kbd> + <kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-133">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4bcb8-134">I MacOS trycker du på <kbd>cmd</kbd> + <kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-134">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="4bcb8-135">I snabb öppning skriver du `ext install powershell` och trycker på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-135">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="4bcb8-136">Vyn **tillägg** öppnas i sido fältet.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-136">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="4bcb8-137">Välj PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-137">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="4bcb8-138">Du bör se en Visual Studio Code-skärm som liknar följande bild:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-138">You should see a Visual Studio Code screen similar to the following image:</span></span>

      ![Visual Studio Code – vy över PowerShell-tillägget](media/using-vscode/vscode.png)

   1. <span data-ttu-id="4bcb8-140">Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-140">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="4bcb8-141">När du har installerat klickar du på **Läs in** igen om du ser knappen **Installera** **igen.**</span><span class="sxs-lookup"><span data-stu-id="4bcb8-141">After the install, if you see the **Install** button turn into **Reload** , Click on **Reload**.</span></span>
   1. <span data-ttu-id="4bcb8-142">När Visual Studio Code har lästs in på nytt är du redo för redigering.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-142">After Visual Studio Code has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="4bcb8-143">Om du till exempel vill skapa en ny fil klickar du på **fil > ny**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-143">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="4bcb8-144">Spara genom att klicka på **arkiv > Spara** och ange ett fil namn, till exempel `HelloWorld.ps1` .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-144">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="4bcb8-145">Stäng filen genom att klicka på `X` bredvid fil namnet.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-145">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="4bcb8-146">Avsluta Visual Studio Code genom att stänga av **filen >**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-146">To exit Visual Studio Code, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="4bcb8-147">Installera PowerShell-tillägget på begränsade system</span><span class="sxs-lookup"><span data-stu-id="4bcb8-147">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="4bcb8-148">Vissa system är konfigurerade för att kräva validering av alla kod-signaturer.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-148">Some systems are set up to require validation of all code signatures.</span></span> <span data-ttu-id="4bcb8-149">Du kan få följande fel:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-149">You may receive the following error:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="4bcb8-150">Det här problemet kan inträffa när PowerShell: s körnings princip anges av Windows grupprincip.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-150">This problem can occur when PowerShell's execution policy is set by Windows Group Policy.</span></span> <span data-ttu-id="4bcb8-151">Om du vill godkänna PowerShell Editor-tjänster och PowerShell-tillägget för Visual Studio Code manuellt öppnar du en PowerShell-kommandotolk och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-151">To manually approve PowerShell Editor Services and the PowerShell extension for Visual Studio Code, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="4bcb8-152">Du tillfrågas om **vill du köra program vara från den här ej betrodda utgivaren?**</span><span class="sxs-lookup"><span data-stu-id="4bcb8-152">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="4bcb8-153">Skriv `A` för att köra filen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-153">Type `A` to run the file.</span></span> <span data-ttu-id="4bcb8-154">Öppna sedan Visual Studio Code och kontrol lera att PowerShell-tillägget fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-154">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="4bcb8-155">Om du fortfarande har problem med att komma igång kan du berätta för oss om [GitHub-problem][].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-155">If you still have problems getting started, let us know on [GitHub issues][].</span></span>

> [!NOTE]
> <span data-ttu-id="4bcb8-156">PowerShell-tillägget för Visual Studio Code stöder inte körning i begränsat språk läge.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-156">The PowerShell extension for Visual Studio Code does not support running in constrained language mode.</span></span> <span data-ttu-id="4bcb8-157">Mer information finns i [GitHub issue #606][i606].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-157">For more information, see [GitHub issue #606][i606].</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="4bcb8-158">Välja en version av PowerShell som ska användas med tillägget</span><span class="sxs-lookup"><span data-stu-id="4bcb8-158">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="4bcb8-159">Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en speciell version av PowerShell med PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-159">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a specific version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="4bcb8-160">Den här funktionen ser till att det finns några välkända sökvägar på olika operativ system för att identifiera installationer av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-160">This feature looks at a few well-known paths on different operating systems to discover installations of PowerShell.</span></span>

<span data-ttu-id="4bcb8-161">Använd följande steg för att välja version:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-161">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="4bcb8-162">Öppna **paletten kommando** i Windows eller Linux med <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-162">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="4bcb8-163">Använd <kbd>cmd</kbd> + <kbd>Shift</kbd> + <kbd>P</kbd>på MacOS.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-163">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="4bcb8-164">Sök efter **session**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-164">Search for **Session**.</span></span>
1. <span data-ttu-id="4bcb8-165">Klicka på **PowerShell: Visa session-menyn**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-165">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="4bcb8-166">Välj den version av PowerShell som du vill använda i listan, till exempel: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-166">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

<span data-ttu-id="4bcb8-167">Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-167">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="4bcb8-168">Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-168">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

> [!NOTE]
> <span data-ttu-id="4bcb8-169">Menyn PowerShell-session kan också nås från det gröna versions numret i det nedre högra hörnet av statusfältet.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-169">The PowerShell session menu can also be accessed from the green version number in the bottom right corner of status bar.</span></span> <span data-ttu-id="4bcb8-170">Om du klickar på det här versions numret öppnas session-menyn.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-170">Clicking this version number opens the session menu.</span></span>

## <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="4bcb8-171">Konfigurations inställningar för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bcb8-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="4bcb8-172">Först, om du inte är bekant med hur du ändrar inställningarna i Visual Studio Code, rekommenderar vi att du läser dokumentationen för [Visual Studio-kodens inställningar][vsc-settings] .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-172">First, if you're not familiar with how to change settings in Visual Studio Code, we recommend reading [Visual Studio Code's settings][vsc-settings] documentation.</span></span>

<span data-ttu-id="4bcb8-173">När du har läst dokumentationen kan du lägga till konfigurations inställningar i `settings.json` .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-173">After reading the documentation, you can add configuration settings in `settings.json`.</span></span>

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="4bcb8-174">Om du inte vill att de här inställningarna ska påverka alla filtyper kan du också använda Visual Studio Code för konfigurationer på olika språk.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-174">If you don't want these settings to affect all files types, Visual Studio Code also allows per-language configurations.</span></span> <span data-ttu-id="4bcb8-175">Skapa en språkspecifik inställning genom att placera inställningarna i ett `[<language-name>]` fält.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-175">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="4bcb8-176">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-176">For example:</span></span>

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> <span data-ttu-id="4bcb8-177">Mer information om fil kodning i Visual Studio Code finns i [förstå fil kodning][file-encoding].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-177">For more information about file encoding in Visual Studio Code, see [Understanding file encoding][file-encoding].</span></span>
>
> <span data-ttu-id="4bcb8-178">Lär dig också hur du kan [REPLIKERA ISE-upplevelsen i Visual Studio Code][vsc-ise] för andra tips om hur du konfigurerar Visual Studio Code för PowerShell-redigering.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-178">Also, check out [How to replicate the ISE experience in Visual Studio Code][vsc-ise] for other tips on how to configure Visual Studio Code for PowerShell editing.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="4bcb8-179">Lägga till egna PowerShell-sökvägar i session-menyn</span><span class="sxs-lookup"><span data-stu-id="4bcb8-179">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="4bcb8-180">Du kan lägga till andra sökvägar för PowerShell-körbara filer till sessionen via [Visual Studio-kod inställningen](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths` .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-180">You can add other PowerShell executable paths to the session menu through the [Visual Studio Code setting](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.</span></span>

<span data-ttu-id="4bcb8-181">Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa listan om den inte finns i din `settings.json` :</span><span class="sxs-lookup"><span data-stu-id="4bcb8-181">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    // other settings...
}
```

<span data-ttu-id="4bcb8-182">Varje objekt måste ha:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-182">Each item must have:</span></span>

- <span data-ttu-id="4bcb8-183">`exePath`: Sökvägen till eller den `pwsh` `powershell` körbara filen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-183">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
- <span data-ttu-id="4bcb8-184">`versionName`: Den text som visas i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-184">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="4bcb8-185">Om du vill ange standard versionen för PowerShell ställer du in värdet `powershell.powerShellDefaultVersion` på texten som visas på session-menyn (även kallat `versionName` ):</span><span class="sxs-lookup"><span data-stu-id="4bcb8-185">To set the default PowerShell version, set the value `powershell.powerShellDefaultVersion` to the text displayed in the session menu (also known as the `versionName`):</span></span>

```json
{
    // other settings...

    "powershell.powerShellAdditionalExePaths": [
        {
            "exePath": "C:\\Users\\tyler\\Downloads\\PowerShell\\pwsh.exe",
            "versionName": "Downloaded PowerShell"
        }
    ],

    "powershell.powerShellDefaultVersion": "Downloaded PowerShell",

    // other settings...
}
```

<span data-ttu-id="4bcb8-186">När du har konfigurerat den här inställningen startar du om Visual Studio Code eller läser in det aktuella Visual Studio Code-fönstret från **kommando-paletten**. Skriv **Developer: Läs in igen**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-186">After you've configured this setting, restart Visual Studio Code or to reload the current Visual Studio Code window from the **Command Palette** , type **Developer: Reload Window**.</span></span>

<span data-ttu-id="4bcb8-187">Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!</span><span class="sxs-lookup"><span data-stu-id="4bcb8-187">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="4bcb8-188">Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-188">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a><span data-ttu-id="4bcb8-189">Använda en äldre version av PowerShell-tillägget för Windows PowerShell v3 och v4</span><span class="sxs-lookup"><span data-stu-id="4bcb8-189">Using an older version of the PowerShell Extension for Windows PowerShell v3 and v4</span></span>

<span data-ttu-id="4bcb8-190">Det aktuella PowerShell-tillägget stöder inte [PowerShell v3 och v4][i1310].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-190">The current PowerShell extension doesn't support [PowerShell v3 and v4][i1310].</span></span> <span data-ttu-id="4bcb8-191">Du kan dock använda den senaste versionen av tillägget som stöder PowerShell v3 och v4.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-191">However, you can use the last version of the extension that supports PowerShell v3 and v4.</span></span>

> [!CAUTION]
> <span data-ttu-id="4bcb8-192">Det kommer inte att finnas några ytterligare korrigeringar till den här äldre versionen av tillägget.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-192">There will be no additional fixes to this older version of the extension.</span></span> <span data-ttu-id="4bcb8-193">Det tillhandahålls "i befintligt skick", men det är tillgängligt för dig om du fortfarande använder Windows PowerShell v3 och Windows PowerShell v4.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-193">It's provided "AS IS" but is available for you if you are still using Windows PowerShell v3 and Windows PowerShell v4.</span></span>

<span data-ttu-id="4bcb8-194">Öppna först fönstret tillägg och Sök efter `PowerShell` .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-194">First, open the Extension pane and search for `PowerShell`.</span></span> <span data-ttu-id="4bcb8-195">Klicka sedan på kugg hjulet och välj **installera en annan version...**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-195">Then click the gear and select **Install another version...**.</span></span>

![Meny objekt – installera en annan version...](media/using-vscode/install-another-version.png)

<span data-ttu-id="4bcb8-197">Välj sedan **2020.1.0** -versionen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-197">Then select the **2020.1.0** version.</span></span> <span data-ttu-id="4bcb8-198">Den här versionen av tillägget var den senaste versionen som stöd för v3 och v4.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-198">This version of the extension was the last version to support v3 and v4.</span></span> <span data-ttu-id="4bcb8-199">Se till att lägga till följande inställning så att tilläggs versionen inte uppdateras automatiskt:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-199">Be sure to add the following setting so that your extension version doesn't update automatically:</span></span>

```json
{
    "extensions.autoUpdate": false
}
```

<span data-ttu-id="4bcb8-200">Version **2020.1.0** kommer att fungera för den förväntade framtiden.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-200">Version **2020.1.0** will work for the foreseeable future.</span></span> <span data-ttu-id="4bcb8-201">Visual Studio Code kan dock implementera en ändring som bryter mot den här versionen av tillägget.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-201">However, Visual Studio Code could implement a change that breaks this version of the extension.</span></span> <span data-ttu-id="4bcb8-202">På grund av detta, och brist på support, rekommenderar vi följande:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-202">Because of this, and lack of support, we recommend:</span></span>

- <span data-ttu-id="4bcb8-203">Uppgradera till Windows PowerShell 5,1</span><span class="sxs-lookup"><span data-stu-id="4bcb8-203">Upgrading to Windows PowerShell 5.1</span></span>
- <span data-ttu-id="4bcb8-204">Installera PowerShell 7, som är en sida-vid-sida-installation till Windows PowerShell och fungerar bäst med PowerShell-tillägget</span><span class="sxs-lookup"><span data-stu-id="4bcb8-204">Install PowerShell 7, which is a side-by-side install to Windows PowerShell and works the best with the PowerShell extension</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="4bcb8-205">Felsöka med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bcb8-205">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="4bcb8-206">Ingen fel sökning på arbets ytan</span><span class="sxs-lookup"><span data-stu-id="4bcb8-206">No-workspace debugging</span></span>

<span data-ttu-id="4bcb8-207">I Visual Studio Code version 1,9 (eller senare) kan du felsöka PowerShell-skript utan att öppna mappen som innehåller PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-207">In Visual Studio Code version 1.9 (or higher), you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span>

1. <span data-ttu-id="4bcb8-208">Öppna PowerShell-skriptfilen med **fil > öppna fil...**</span><span class="sxs-lookup"><span data-stu-id="4bcb8-208">Open the PowerShell script file with **File > Open File...**</span></span>
1. <span data-ttu-id="4bcb8-209">Ange en Bryt punkt – Markera en rad och tryck sedan på <kbd>F9</kbd></span><span class="sxs-lookup"><span data-stu-id="4bcb8-209">Set a breakpoint - select a line then press <kbd>F9</kbd></span></span>
1. <span data-ttu-id="4bcb8-210">Tryck på <kbd>F5</kbd> för att starta fel sökningen</span><span class="sxs-lookup"><span data-stu-id="4bcb8-210">Press <kbd>F5</kbd> to start debugging</span></span>

<span data-ttu-id="4bcb8-211">Du bör se fönstret fel söknings åtgärder, vilket gör att du kan bryta i fel söknings programmet, steg, återuppta och stoppa fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-211">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="4bcb8-212">Fel sökning av arbets yta</span><span class="sxs-lookup"><span data-stu-id="4bcb8-212">Workspace debugging</span></span>

<span data-ttu-id="4bcb8-213">Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat från menyn **Arkiv** med **Öppna mapp..**.. Mappen som du öppnar är vanligt vis din PowerShell-projektmapp eller roten för git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-213">Workspace debugging refers to debugging in the context of a folder that you've opened from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder or the root of your Git repository.</span></span> <span data-ttu-id="4bcb8-214">Med fel sökning av arbets ytan kan du definiera flera fel söknings konfigurationer förutom att bara Felsöka den för tillfället öppna filen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-214">Workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>

<span data-ttu-id="4bcb8-215">Följ de här stegen för att skapa en fel söknings konfigurations fil:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-215">Follow these steps to create a debug configuration file:</span></span>

1. <span data-ttu-id="4bcb8-216">Öppna vyn **fel sökning** på Windows eller Linux genom att trycka på <kbd>CTRL</kbd> + <kbd>Shift</kbd> + <kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-216">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="4bcb8-217">I MacOS trycker du på <kbd>cmd</kbd> + <kbd>Shift</kbd> + <kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-217">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
1. <span data-ttu-id="4bcb8-218">Klicka på länken **skapa en launch.jspå fil** .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-218">Click the **create a launch.json file** link.</span></span>
1. <span data-ttu-id="4bcb8-219">Välj **PowerShell** i dialog rutan **Välj miljö** .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-219">From the **Select Environment** prompt, choose **PowerShell**.</span></span>
1. <span data-ttu-id="4bcb8-220">Välj den typ av fel sökning du vill använda:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-220">Choose the type of debugging you'd like to use:</span></span>

   - <span data-ttu-id="4bcb8-221">**Starta aktuell fil** – starta och Felsök filen i det för tillfället aktiva redigerings fönstret</span><span class="sxs-lookup"><span data-stu-id="4bcb8-221">**Launch Current File** - Launch and debug the file in the currently active editor window</span></span>
   - <span data-ttu-id="4bcb8-222">**Starta skript** – starta och Felsök den angivna filen eller kommandot</span><span class="sxs-lookup"><span data-stu-id="4bcb8-222">**Launch Script** - Launch and debug the specified file or command</span></span>
   - <span data-ttu-id="4bcb8-223">**Interaktiv session** – Felsök kommandon som körs från den integrerade konsolen</span><span class="sxs-lookup"><span data-stu-id="4bcb8-223">**Interactive Session** - Debug commands executed from the Integrated Console</span></span>
   - <span data-ttu-id="4bcb8-224">**Koppla** -koppla fel sökaren till en PowerShell-värd process som körs</span><span class="sxs-lookup"><span data-stu-id="4bcb8-224">**Attach** - Attach the debugger to a running PowerShell Host Process</span></span>

<span data-ttu-id="4bcb8-225">Visual Studio Code skapar en katalog och en fil `.vscode\launch.json` i roten i din arbetsytans mapp för att lagra fel söknings konfigurationen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-225">Visual Studio Code creates a directory and a file `.vscode\launch.json` in the root of your workspace folder to store the debug configuration.</span></span> <span data-ttu-id="4bcb8-226">Om filerna finns på en git-lagringsplats vill du vanligt vis spara `launch.json` filen.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-226">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="4bcb8-227">`launch.json`Filens innehåll är:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-227">The contents of the `launch.json` file are:</span></span>

```json
{
  "version": "0.2.0",
  "configurations": [
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Launch (current file)",
          "script": "${file}",
          "args": [],
          "cwd": "${file}"
      },
      {
          "type": "PowerShell",
          "request": "attach",
          "name": "PowerShell Attach to Host Process",
          "processId": "${command.PickPSHostProcess}",
          "runspaceId": 1
      },
      {
          "type": "PowerShell",
          "request": "launch",
          "name": "PowerShell Interactive Session",
          "cwd": "${workspaceRoot}"
      }
  ]
}
```

<span data-ttu-id="4bcb8-228">Den här filen representerar vanliga fel söknings scenarier.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-228">This file represents the common debug scenarios.</span></span> <span data-ttu-id="4bcb8-229">När du öppnar den här filen i redigeraren visas knappen **Lägg till konfiguration...** .</span><span class="sxs-lookup"><span data-stu-id="4bcb8-229">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="4bcb8-230">Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-230">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="4bcb8-231">En användbar konfiguration för att lägga till är **PowerShell: starta skript**.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-231">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="4bcb8-232">Med den här konfigurationen kan du ange en fil som innehåller valfria argument som används när du trycker på <kbd>F5</kbd> oavsett vilken fil som är aktiv i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-232">With this configuration, you can specify a file containing optional arguments that are used whenever you press <kbd>F5</kbd> no matter which file is active in the editor.</span></span>

<span data-ttu-id="4bcb8-233">När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-233">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="4bcb8-234">Välj en konfiguration i list rutan Felsök konfiguration i **fel söknings** verktygsfältets verktygsfält.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-234">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a><span data-ttu-id="4bcb8-235">Felsöka PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="4bcb8-235">Troubleshooting the PowerShell extension for Visual Studio Code</span></span>

<span data-ttu-id="4bcb8-236">Om du får problem med att använda Visual Studio Code för att utveckla PowerShell-skript, se [fel söknings guiden][troubleshooting] på GitHub.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-236">If you experience any issues using Visual Studio Code for PowerShell script development, see the [troubleshooting guide][troubleshooting] on GitHub.</span></span>

## <a name="useful-resources"></a><span data-ttu-id="4bcb8-237">Användbara resurser</span><span class="sxs-lookup"><span data-stu-id="4bcb8-237">Useful resources</span></span>

<span data-ttu-id="4bcb8-238">Det finns några videor och blogg inlägg som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="4bcb8-238">There are a few videos and blog posts that may be helpful to get you started using the PowerShell extension for Visual Studio Code:</span></span>

### <a name="videos"></a><span data-ttu-id="4bcb8-239">Video</span><span class="sxs-lookup"><span data-stu-id="4bcb8-239">Videos</span></span>

- [<span data-ttu-id="4bcb8-240">Använda Visual Studio Code som standard-PowerShell-redigerare</span><span class="sxs-lookup"><span data-stu-id="4bcb8-240">Using Visual Studio Code as Your Default PowerShell Editor</span></span>](https://youtu.be/bGn45vIeAMM)
- [<span data-ttu-id="4bcb8-241">Visual Studio Code: djup gå in i fel sökning av PowerShell-skript</span><span class="sxs-lookup"><span data-stu-id="4bcb8-241">Visual Studio Code: deep dive into debugging your PowerShell scripts</span></span>](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a><span data-ttu-id="4bcb8-242">Blogginlägg</span><span class="sxs-lookup"><span data-stu-id="4bcb8-242">Blog posts</span></span>

- <span data-ttu-id="4bcb8-243">[PowerShell-tillägg][pscdn]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-243">[PowerShell Extension][pscdn]</span></span>
- <span data-ttu-id="4bcb8-244">[Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-244">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="4bcb8-245">[Fel sökning av Visual Studio Code-vägledning][psdbgblog]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-245">[Debugging Visual Studio Code Guidance][psdbgblog]</span></span>
- <span data-ttu-id="4bcb8-246">[Felsöka PowerShell i Visual Studio Code][psdbg-gh]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-246">[Debugging PowerShell in Visual Studio Code][psdbg-gh]</span></span>
- <span data-ttu-id="4bcb8-247">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-247">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="4bcb8-248">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-248">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="4bcb8-249">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-249">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="4bcb8-250">[Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-250">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="4bcb8-251">[Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="4bcb8-251">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

## <a name="powershell-extension-project-source-code"></a><span data-ttu-id="4bcb8-252">Projekt käll kod för PowerShell-tillägg</span><span class="sxs-lookup"><span data-stu-id="4bcb8-252">PowerShell extension project source code</span></span>

<span data-ttu-id="4bcb8-253">Du hittar PowerShell-tilläggets källkod på [GitHub][psext-src].</span><span class="sxs-lookup"><span data-stu-id="4bcb8-253">The PowerShell extension's source code can be found on [GitHub][psext-src].</span></span>

<span data-ttu-id="4bcb8-254">Om du är intresse rad av att bidra är pull-begäranden mycket tacksam.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-254">If you're interested in contributing, Pull Requests are greatly appreciated.</span></span> <span data-ttu-id="4bcb8-255">Följ tillsammans med [Developer-dokumentationen][dev-docs] på GitHub för att komma igång.</span><span class="sxs-lookup"><span data-stu-id="4bcb8-255">Follow along with the [developer documentation][dev-docs] on GitHub to get started.</span></span>

<!-- related articles -->
[ise]:                    ../../windows-powershell/ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:   ../../install/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:   ../../install/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../install/Installing-PowerShell-Core-on-Windows.md
[install-winps]:          ../../install/Installing-Windows-PowerShell.md
[file-encoding]:          understanding-file-encoding.md
[vsc-ise]:                How-To-Replicate-the-ISE-Experience-In-VSCode.md

<!-- blogs -->
[debug]:                  https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[debugging-part1]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:        https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/
[editing-part1]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:          https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[getting-started]:        https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[psdbgblog]:              https://johnpapa.net/debugging-with-visual-studio-code/
[psdbg-gh]:               https://github.com/PowerShell/vscode-powershell/tree/master/examples
[pscdn]:                  https://docs.microsoft.com/archive/blogs/cdndevs/visual-studio-code-powershell-extension

<!-- issues -->
[GitHub-problem]:          https://github.com/PowerShell/vscode-powershell/issues
[GitHub issues]:          https://github.com/PowerShell/vscode-powershell/issues
[i1310]:                  https://github.com/PowerShell/vscode-powershell/issues/1310
[i606]:                   https://github.com/PowerShell/vscode-powershell/issues/606

<!-- product links -->
[Visual Studio]:          https://visualstudio.microsoft.com/
[vscode]:                 https://code.visualstudio.com/
[psext]:                  https://marketplace.visualstudio.com/items?itemName=ms-vscode.PowerShell
[vsc-settings]:           https://code.visualstudio.com/docs/getstarted/settings
[vsc-setup]:              https://code.visualstudio.com/Docs/setup/setup-overview
[vsc-setup-win]:          https://code.visualstudio.com/docs/setup/windows
[vsc-setup-macos]:        https://code.visualstudio.com/docs/setup/mac
[vsc-setup-linux]:        https://code.visualstudio.com/docs/setup/linux
[psext-src]:              https://github.com/PowerShell/vscode-powershell
[troubleshooting]:        https://github.com/PowerShell/vscode-powershell/blob/master/docs/troubleshooting.md
[dev-docs]:               https://github.com/PowerShell/vscode-powershell/blob/master/docs/development.md
