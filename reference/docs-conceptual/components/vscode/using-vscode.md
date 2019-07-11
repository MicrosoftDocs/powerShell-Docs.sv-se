---
title: Med Visual Studio Code för PowerShell-utveckling
description: Med Visual Studio Code för PowerShell-utveckling
ms.date: 08/06/2018
ms.openlocfilehash: 6a0da6e060693dc7cfc08d40fd658414dc23d660
ms.sourcegitcommit: 46bebe692689ebedfe65ff2c828fe666b443198d
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/10/2019
ms.locfileid: "67733886"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="92087-103">Med Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="92087-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="92087-104">Förutom den [PowerShell ISE][ise], PowerShell är också väl stöds i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="92087-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="92087-105">Dessutom stöds ISE inte med PowerShell Core Visual Studio Code har stöd för PowerShell Core på alla plattformar (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="92087-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="92087-106">Du kan använda Visual Studio Code på Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) för äldre Windows-operativsystem (t.ex. Windows 8.1, osv.).</span><span class="sxs-lookup"><span data-stu-id="92087-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="92087-107">Kontrollera att PowerShell finns i systemet innan du startar den.</span><span class="sxs-lookup"><span data-stu-id="92087-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="92087-108">Moderna arbetsbelastningar i Windows, macOS och Linux finns här:</span><span class="sxs-lookup"><span data-stu-id="92087-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="92087-109">[Installera PowerShell Core i Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="92087-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="92087-110">[Installera PowerShell Core i macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="92087-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="92087-111">[Installera PowerShell Core i Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="92087-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="92087-112">Traditionella Windows PowerShell-arbetsbelastningar, se [installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="92087-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="92087-113">Redigera med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="92087-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="92087-114">1. Installera Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="92087-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="92087-115">**Linux**: Följ installationsanvisningarna på den [som körs på Linux i VS Code](https://code.visualstudio.com/docs/setup/linux) sidan</span><span class="sxs-lookup"><span data-stu-id="92087-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="92087-116">**macOS**: Följ installationsanvisningarna på den [köra VS-kod i Mac OS](https://code.visualstudio.com/docs/setup/mac) sidan</span><span class="sxs-lookup"><span data-stu-id="92087-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="92087-117">I macOS, måste du installera OpenSSL för PowerShell-tillägget ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="92087-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="92087-118">Det enklaste sättet att göra detta är att installera [Homebrew](https://brew.sh/) och kör sedan `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="92087-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="92087-119">VS Code kan nu läsa in PowerShell-tillägget har.</span><span class="sxs-lookup"><span data-stu-id="92087-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="92087-120">**Windows**: Följ installationsanvisningarna på den [köra VS Code på Windows](https://code.visualstudio.com/docs/setup/windows) sidan</span><span class="sxs-lookup"><span data-stu-id="92087-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="92087-121">2. Installera PowerShell-tillägget</span><span class="sxs-lookup"><span data-stu-id="92087-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="92087-122">Starta Visual Studio Code app genom att:</span><span class="sxs-lookup"><span data-stu-id="92087-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="92087-123">**Windows**: att skriva `code` i PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="92087-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="92087-124">**Linux**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="92087-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="92087-125">**macOS**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="92087-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="92087-126">Starta **snabb öppna** genom att trycka på **Ctrl + P** (**Cmd + P** på Mac).</span><span class="sxs-lookup"><span data-stu-id="92087-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="92087-127">Snabb Skriv `ext install powershell` och därefter **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="92087-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="92087-128">Den **tillägg** öppnas i Sidopanel.</span><span class="sxs-lookup"><span data-stu-id="92087-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="92087-129">Välj tillägget PowerShell från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="92087-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="92087-130">Du bör se ut ungefär som nedan:</span><span class="sxs-lookup"><span data-stu-id="92087-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="92087-132">Klicka på den **installera** knappen på PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="92087-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="92087-133">Efter installationen visas den **installera** knappen övergår i **Reload**.</span><span class="sxs-lookup"><span data-stu-id="92087-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="92087-134">Klicka på **Reload**.</span><span class="sxs-lookup"><span data-stu-id="92087-134">Click on **Reload**.</span></span>
- <span data-ttu-id="92087-135">När Visual Studio Code har läs in igen, är det dags för redigering.</span><span class="sxs-lookup"><span data-stu-id="92087-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="92087-136">Exempelvis för att skapa en ny fil, klickar du på **File -> Nytt**.</span><span class="sxs-lookup"><span data-stu-id="92087-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="92087-137">Om du vill spara den, klickar du på **Arkiv -> Spara** och ange sedan ett filnamn, låt oss säga att `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="92087-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="92087-138">Stäng filen genom att klicka på ”x” bredvid namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="92087-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="92087-139">Avsluta Visual Studio Code **Arkiv -> Avsluta**.</span><span class="sxs-lookup"><span data-stu-id="92087-139">To exit Visual Studio Code, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="92087-140">Installera PowerShell-tillägget på begränsade system</span><span class="sxs-lookup"><span data-stu-id="92087-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="92087-141">Vissa system är inställda på ett sätt som kräver alla kod signaturer som ska kontrolleras och därför kräver PowerShell redigeraren tjänster att manuellt godkänna för att köras på systemet.</span><span class="sxs-lookup"><span data-stu-id="92087-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span>
<span data-ttu-id="92087-142">En uppdatering av grupprinciper som ändrar körningsprincipen är en trolig orsak om du har installerat tillägget PowerShell men ansluter till ett fel som:</span><span class="sxs-lookup"><span data-stu-id="92087-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="92087-143">Öppna ett PowerShell och kör för att manuellt godkänna PowerShell redigeraren tjänster och därmed PowerShell-tillägget för VSCode:</span><span class="sxs-lookup"><span data-stu-id="92087-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="92087-144">Du uppmanas via ”vill du köra programvaran från denna ej betrodda utgivare”?</span><span class="sxs-lookup"><span data-stu-id="92087-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span>
<span data-ttu-id="92087-145">Typ `R` att köra filen.</span><span class="sxs-lookup"><span data-stu-id="92087-145">Type `R` to run the file.</span></span> <span data-ttu-id="92087-146">Öppna Visual Studio Code och kontrollera att tillägget PowerShell fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="92087-146">Then, open Visual Studio Code and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="92087-147">Om du fortfarande har problem med att komma igång, berätta för oss på [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="92087-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="92087-148">Välja en version av PowerShell för att använda i tillägget</span><span class="sxs-lookup"><span data-stu-id="92087-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="92087-149">Med PowerShell Core installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en viss version av PowerShell i PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="92087-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="92087-150">Använd följande här för att välja versionen:</span><span class="sxs-lookup"><span data-stu-id="92087-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="92087-151">Öppna kommandot utbud (<kbd>Ctrl</kbd>+<kbd>SKIFT</kbd>+<kbd>P</kbd> på Windows och Linux, <kbd>Cmd</kbd> + <kbd>SKIFT</kbd>+<kbd>P</kbd> på macOS).</span><span class="sxs-lookup"><span data-stu-id="92087-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="92087-152">Sök efter ”Session”.</span><span class="sxs-lookup"><span data-stu-id="92087-152">Search for "Session".</span></span>
1. <span data-ttu-id="92087-153">Klicka på ”PowerShell: Visa Session menyn ”.</span><span class="sxs-lookup"><span data-stu-id="92087-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="92087-154">Välj versionen av PowerShell som du vill använda från listan – till exempel PowerShell Core ””.</span><span class="sxs-lookup"><span data-stu-id="92087-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

>[!IMPORTANT]
> <span data-ttu-id="92087-155">Den här funktionen tittar på några välkända sökvägar i olika operativsystem för att identifiera platser för installation av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92087-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="92087-156">Om du har installerat PowerShell på en icke-vanliga plats kan den inte visas först i menyn Session.</span><span class="sxs-lookup"><span data-stu-id="92087-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="92087-157">Du kan utöka menyn sessionen genom att [att lägga till dina egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="92087-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="92087-158">Det finns ett annat sätt att komma till menyn session.</span><span class="sxs-lookup"><span data-stu-id="92087-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="92087-159">När en PowerShell-fil är öppna i redigeringsprogram, visas en grön versionsnumret i det nedre högra hörnet.</span><span class="sxs-lookup"><span data-stu-id="92087-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="92087-160">Klicka på det här versionsnumret kommer du till menyn session.</span><span class="sxs-lookup"><span data-stu-id="92087-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="92087-161">Att lägga till egna PowerShell-sökvägar till menyn session</span><span class="sxs-lookup"><span data-stu-id="92087-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="92087-162">Du kan lägga till andra körbara sökvägar PowerShell session-menyn genom att VS Code.</span><span class="sxs-lookup"><span data-stu-id="92087-162">You can add other PowerShell executable paths to the session menu through a VS Code setting.</span></span>

<span data-ttu-id="92087-163">Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa listan om den inte finns i din `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="92087-163">Add an item to the list  `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="92087-164">Varje objekt måste ha:</span><span class="sxs-lookup"><span data-stu-id="92087-164">Each item must have:</span></span>

* <span data-ttu-id="92087-165">`exePath`: Sökvägen till den `pwsh` eller `powershell` körbara.</span><span class="sxs-lookup"><span data-stu-id="92087-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="92087-166">`versionName`: Den text som visas i menyn session.</span><span class="sxs-lookup"><span data-stu-id="92087-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="92087-167">Du kan ange standard PowerShell-version du använder med hjälp av den `powershell.powerShellDefaultVersion` inställningen av inställningen detta i texten visas i menyn session (även kallat den `versionName` i den senaste inställningen):</span><span class="sxs-lookup"><span data-stu-id="92087-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="92087-168">När du har ställt in den här inställningen kan starta om Visual Studio Code eller använda den i ”utvecklare: Läs in på nytt fönster ”utbud Kommandoåtgärden att uppdatera aktuella vscode-fönstret.</span><span class="sxs-lookup"><span data-stu-id="92087-168">Once you've set this setting, restart Visual Studio Code or use the the "Developer: Reload Window" command pallet action to reload the current vscode window.</span></span>

<span data-ttu-id="92087-169">Om du öppnar menyn sessionen, kommer du nu se ditt ytterligare PowerShell-versioner!</span><span class="sxs-lookup"><span data-stu-id="92087-169">If you open the session menu, you will now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="92087-170">Om du skapar PowerShell från källan, är det här ett bra sätt att testa din lokal version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92087-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="92087-171">Konfigurationsinställningar för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="92087-171">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="92087-172">Med hjälp av stegen i föregående stycke kan du lägga till konfigurationsinställningar i `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="92087-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="92087-173">Vi rekommenderar följande konfigurationsinställningar för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="92087-173">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="92087-174">Om du inte vill att dessa inställningar påverkar alla filtyper, kan VSCode också konfigurationer per språk.</span><span class="sxs-lookup"><span data-stu-id="92087-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="92087-175">Skapa en specifik språkinställning genom att ange inställningar i en `[<language-name>]` fält.</span><span class="sxs-lookup"><span data-stu-id="92087-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="92087-176">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="92087-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="92087-177">Mer information om filen kodning i VS Code finns i [förstå Filkodning](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="92087-177">For more information about file encoding in VS Code, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="92087-178">Felsöka med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="92087-178">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="92087-179">Ingen arbetsyta felsökning</span><span class="sxs-lookup"><span data-stu-id="92087-179">No-workspace debugging</span></span>

<span data-ttu-id="92087-180">Du kan felsöka PowerShell-skript utan att öppna den mapp som innehåller PowerShell-skriptet från och med Visual Studio Code-versionen 1.9.</span><span class="sxs-lookup"><span data-stu-id="92087-180">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="92087-181">Öppna PowerShell-skriptfil med **Arkiv -> Öppna fil...** , ange en brytpunkt på rad (tryck på F9) och tryck på F5 för att starta felsökningen.</span><span class="sxs-lookup"><span data-stu-id="92087-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span> <span data-ttu-id="92087-182">Du bör se Debug åtgärdsfönstret visas där du kan dela i felsökare, steg, återuppta och stoppa felsökning.</span><span class="sxs-lookup"><span data-stu-id="92087-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="92087-183">Felsökning av arbetsyta</span><span class="sxs-lookup"><span data-stu-id="92087-183">Workspace debugging</span></span>

<span data-ttu-id="92087-184">Felsökning av arbetsytan refererar till felsökning i samband med en mapp som du har öppnat i Visual Studio Code med **Öppna mapp...**  från den **filen** menyn.</span><span class="sxs-lookup"><span data-stu-id="92087-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="92087-185">Den mapp som du öppnar är vanligtvis projektmappen PowerShell och/eller roten för Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="92087-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="92087-186">Även i det här läget kan starta du felsökning markerade PowerShell-skriptet genom att bara trycka på F5.</span><span class="sxs-lookup"><span data-stu-id="92087-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="92087-187">Dock kan arbetsytan felsökning du definiera konfigurationer med flera debug än bara felsökning öppna filen.</span><span class="sxs-lookup"><span data-stu-id="92087-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="92087-188">Du kan exempelvis lägga till en konfigurationer för att:</span><span class="sxs-lookup"><span data-stu-id="92087-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="92087-189">Starta Pester tester i felsökningsprogrammet</span><span class="sxs-lookup"><span data-stu-id="92087-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="92087-190">Starta en viss fil med argumenten i Felsökning</span><span class="sxs-lookup"><span data-stu-id="92087-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="92087-191">Starta en interaktiv session i Felsökning</span><span class="sxs-lookup"><span data-stu-id="92087-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="92087-192">Bifoga felsökningsprogrammet till en värdprocess för PowerShell</span><span class="sxs-lookup"><span data-stu-id="92087-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="92087-193">Följ dessa steg för att skapa konfigurationsfilen debug:</span><span class="sxs-lookup"><span data-stu-id="92087-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="92087-194">Öppna den **felsöka** vyn genom att trycka på **Ctrl + Skift + D** (**Cmd + SKIFT + D** på Mac).</span><span class="sxs-lookup"><span data-stu-id="92087-194">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="92087-195">Tryck på den **konfigurera** kugghjulsikonen i verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="92087-195">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="92087-196">Visual Studio Code uppmanas du att **Välj miljö**.</span><span class="sxs-lookup"><span data-stu-id="92087-196">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="92087-197">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="92087-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="92087-198">När du gör detta skapar en katalog och en fil ”.vscode\launch.json” i roten av din arbetsytemapp Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="92087-198">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="92087-199">Det här är där din debug-konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="92087-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="92087-200">Om filerna finns i en Git-lagringsplats, vill du förmodligen att genomföra launch.json-filen.</span><span class="sxs-lookup"><span data-stu-id="92087-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="92087-201">Innehållet i launch.json-filen är:</span><span class="sxs-lookup"><span data-stu-id="92087-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="92087-202">Detta representerar vanliga scenarier för felsökning.</span><span class="sxs-lookup"><span data-stu-id="92087-202">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="92087-203">Men när du öppnar den här filen i redigeraren kan du se en **Lägg till konfiguration...**  knappen.</span><span class="sxs-lookup"><span data-stu-id="92087-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="92087-204">Du kan trycka på knappen för att lägga till fler konfigurationer för felsökning av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="92087-204">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="92087-205">Är en praktisk konfiguration för att lägga till **PowerShell: Starta skriptet**.</span><span class="sxs-lookup"><span data-stu-id="92087-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="92087-206">Med den här konfigurationen kan du ange en viss fil med valfria argument som ska startas varje gång du trycker på F5 oavsett vilken fil som är aktiva i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="92087-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="92087-207">När debug-konfigurationen har upprättats kan du välja vilken konfiguration som du vill använda under en felsökningssession genom att välja en från debug konfigurationen listrutan i den **felsöka** vyns verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="92087-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="92087-208">Det finns några bloggar som hjälper dig att komma igång med hjälp av PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="92087-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="92087-209">[PowerShell-tillägget][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="92087-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="92087-210">[Skriv och Felsök PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="92087-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="92087-211">[Felsökning av Visual Studio Code-vägledning][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="92087-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="92087-212">[Felsökning av PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="92087-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="92087-213">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="92087-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="92087-214">[Visual Studio Code redigeringsfunktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="92087-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="92087-215">[Visual Studio Code redigeringsfunktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="92087-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="92087-216">[Felsökning av PowerShell-skriptet i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="92087-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="92087-217">[Felsökning av PowerShell-skriptet i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="92087-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="92087-218">PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="92087-218">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="92087-219">Tillägget PowerShell källkoden finns på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="92087-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
