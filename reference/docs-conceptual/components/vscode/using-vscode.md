---
title: Använda Visual Studio Code för PowerShell-utveckling
description: Använda Visual Studio Code för PowerShell-utveckling
ms.date: 08/06/2018
ms.openlocfilehash: 0e082b74f99d214749f10224fb5aaf41e2ef8951
ms.sourcegitcommit: 4a2cf30351620a58ba95ff5d76b247e601907589
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/27/2019
ms.locfileid: "71325236"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="48c46-103">Använda Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="48c46-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="48c46-104">Förutom [POWERSHELL ISE][ise], stöds även PowerShell i Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="48c46-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="48c46-105">Dessutom stöds inte ISE med PowerShell Core, medan VSCode stöds för PowerShell Core på alla plattformar (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="48c46-105">Furthermore, the ISE is not supported with PowerShell Core, while VSCode is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="48c46-106">Du kan använda VSCode i Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5,0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) för Windows oss på en äldre nivå (t. ex. Windows 8,1 osv.).</span><span class="sxs-lookup"><span data-stu-id="48c46-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="48c46-107">Innan du startar det kontrollerar du att PowerShell finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="48c46-107">Before starting it, please make sure PowerShell exists on your system.</span></span> <span data-ttu-id="48c46-108">För moderna arbets belastningar på Windows, macOS och Linux, se:</span><span class="sxs-lookup"><span data-stu-id="48c46-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="48c46-109">[Installera PowerShell Core på Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="48c46-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="48c46-110">[Installera PowerShell Core på macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="48c46-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="48c46-111">[Installera PowerShell Core på Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="48c46-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="48c46-112">För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="48c46-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="48c46-113">Redigera med VSCode</span><span class="sxs-lookup"><span data-stu-id="48c46-113">Editing with VSCode</span></span>

1. [<span data-ttu-id="48c46-114">Installerar VSCode</span><span class="sxs-lookup"><span data-stu-id="48c46-114">Installing VSCode</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

   - <span data-ttu-id="48c46-115">**Linux**: följ installations anvisningarna på sidan för att [köra VSCode på Linux](https://code.visualstudio.com/docs/setup/linux)</span><span class="sxs-lookup"><span data-stu-id="48c46-115">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>
   - <span data-ttu-id="48c46-116">**MacOS**: följ installations anvisningarna på sidan för att [köra VSCode på MacOS](https://code.visualstudio.com/docs/setup/mac)</span><span class="sxs-lookup"><span data-stu-id="48c46-116">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="48c46-117">På macOS måste du installera OpenSSL för att PowerShell-tillägget ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="48c46-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="48c46-118">Det enklaste sättet att göra detta är att installera [homebrew](https://brew.sh/) och sedan köra `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="48c46-118">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="48c46-119">VSCode kan nu läsa in PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="48c46-119">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="48c46-120">**Windows**: följ installations anvisningarna på sidan för att [köra VSCode på Windows](https://code.visualstudio.com/docs/setup/windows)</span><span class="sxs-lookup"><span data-stu-id="48c46-120">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

2. <span data-ttu-id="48c46-121">Installera PowerShell-tillägg</span><span class="sxs-lookup"><span data-stu-id="48c46-121">Installing PowerShell Extension</span></span>

   - <span data-ttu-id="48c46-122">Starta VSCode-appen genom att:</span><span class="sxs-lookup"><span data-stu-id="48c46-122">Launch the VSCode app by:</span></span>
     - <span data-ttu-id="48c46-123">**Windows**: skriva `code` in PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="48c46-123">**Windows**: typing `code` in your PowerShell session</span></span>
     - <span data-ttu-id="48c46-124">**Linux**: skriva `code` in i terminalen</span><span class="sxs-lookup"><span data-stu-id="48c46-124">**Linux**: typing `code` in your terminal</span></span>
     - <span data-ttu-id="48c46-125">**MacOS**: skriva `code` in i terminalen</span><span class="sxs-lookup"><span data-stu-id="48c46-125">**macOS**: typing `code` in your terminal</span></span>
   - <span data-ttu-id="48c46-126">**Öppna snabb** start genom att trycka på <kbd>CTRL</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>p</kbd> på Mac).</span><span class="sxs-lookup"><span data-stu-id="48c46-126">Launch **Quick Open** by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd>+<kbd>P</kbd> on Mac).</span></span>
   - <span data-ttu-id="48c46-127">Skriv `ext install powershell` och tryck på **RETUR**i snabb öppning.</span><span class="sxs-lookup"><span data-stu-id="48c46-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
   - <span data-ttu-id="48c46-128">Vyn **tillägg** öppnas i sido fältet.</span><span class="sxs-lookup"><span data-stu-id="48c46-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="48c46-129">Välj PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="48c46-129">Select the PowerShell extension from Microsoft.</span></span>
     <span data-ttu-id="48c46-130">Du bör se något som liknar följande:</span><span class="sxs-lookup"><span data-stu-id="48c46-130">You should see something like below:</span></span>

     ![VSCode](../../images/using-vscode/vscode.png)

   - <span data-ttu-id="48c46-132">Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="48c46-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   - <span data-ttu-id="48c46-133">Efter installationen ser knappen **Installera** att **läsas in igen**.</span><span class="sxs-lookup"><span data-stu-id="48c46-133">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="48c46-134">Klicka på **Läs in igen**.</span><span class="sxs-lookup"><span data-stu-id="48c46-134">Click on **Reload**.</span></span>
   - <span data-ttu-id="48c46-135">När VSCode har lästs in på nytt är du redo för redigering.</span><span class="sxs-lookup"><span data-stu-id="48c46-135">After VSCode has reload, you are ready for editing.</span></span>

<span data-ttu-id="48c46-136">Om du till exempel vill skapa en ny fil klickar du på **fil-> ny**.</span><span class="sxs-lookup"><span data-stu-id="48c46-136">For example, to create a new file, click **File->New**.</span></span> <span data-ttu-id="48c46-137">Spara genom att klicka på **Arkiv-> Spara** och ange ett fil namn, låt oss säga `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="48c46-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span> <span data-ttu-id="48c46-138">Stäng filen genom att klicka på "x" bredvid fil namnet.</span><span class="sxs-lookup"><span data-stu-id="48c46-138">To close the file, click on "x" next to the file name.</span></span> <span data-ttu-id="48c46-139">Avsluta VSCode genom att avsluta **File->** .</span><span class="sxs-lookup"><span data-stu-id="48c46-139">To exit VSCode, **File->Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="48c46-140">Installera PowerShell-tillägget på begränsade system</span><span class="sxs-lookup"><span data-stu-id="48c46-140">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="48c46-141">Vissa system har kon figurer ATS på ett sätt som kräver att alla kod-signaturer kontrol leras, vilket kräver att PowerShell Editor-tjänster godkänns manuellt för att köras i systemet.</span><span class="sxs-lookup"><span data-stu-id="48c46-141">Some systems are set up in a way that requires all code signatures to be checked and thus requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="48c46-142">En grupprincip uppdatering som ändrar körnings principen är en sannolik orsak om du har installerat PowerShell-tillägget men når ett fel som:</span><span class="sxs-lookup"><span data-stu-id="48c46-142">A Group Policy update that changes execution policy is a likely cause if you have installed the PowerShell extension but are reaching an error like:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="48c46-143">Om du vill godkänna PowerShell Editor-tjänster manuellt och därmed PowerShell-tillägget för VSCode öppnar du en PowerShell-prompt och kör:</span><span class="sxs-lookup"><span data-stu-id="48c46-143">To manually approve PowerShell Editor Services and thus the PowerShell extension for VSCode open a PowerShell prompt and run:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="48c46-144">Du uppmanas att använda "vill du köra program vara från den här ej betrodda utgivaren?"</span><span class="sxs-lookup"><span data-stu-id="48c46-144">You are prompted with "Do you want to run software from this untrusted publisher?"</span></span> <span data-ttu-id="48c46-145">Skriv `R` för att köra filen.</span><span class="sxs-lookup"><span data-stu-id="48c46-145">Type `R` to run the file.</span></span> <span data-ttu-id="48c46-146">Öppna sedan VSCode och kontrol lera att PowerShell-tillägget fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="48c46-146">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="48c46-147">Om du fortfarande har problem med att komma igång kan du berätta om [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="48c46-147">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="48c46-148">Välja en version av PowerShell som ska användas med tillägget</span><span class="sxs-lookup"><span data-stu-id="48c46-148">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="48c46-149">Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en viss version av PowerShell med PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="48c46-149">With PowerShell Core installing side-by-side with Windows PowerShell, is it now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="48c46-150">Använd följande steg för att välja version:</span><span class="sxs-lookup"><span data-stu-id="48c46-150">Use the following these steps to choose the version:</span></span>

1. <span data-ttu-id="48c46-151">Öppna kommandot pall (<kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> på Windows & Linux, <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS).</span><span class="sxs-lookup"><span data-stu-id="48c46-151">Open the command pallet (<kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on Windows & Linux, <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> on macOS).</span></span>
1. <span data-ttu-id="48c46-152">Sök efter "session".</span><span class="sxs-lookup"><span data-stu-id="48c46-152">Search for "Session".</span></span>
1. <span data-ttu-id="48c46-153">Klicka på "PowerShell: Visa session-menyn ".</span><span class="sxs-lookup"><span data-stu-id="48c46-153">Click on "PowerShell: Show Session Menu".</span></span>
1. <span data-ttu-id="48c46-154">Välj den version av PowerShell som du vill använda från listan, till exempel "PowerShell Core".</span><span class="sxs-lookup"><span data-stu-id="48c46-154">Choose the version of PowerShell you want to use from the list - for example, "PowerShell Core".</span></span>

> [!IMPORTANT]
> <span data-ttu-id="48c46-155">Den här funktionen söker efter några välkända sökvägar på olika operativ system för att identifiera installations platser för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48c46-155">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="48c46-156">Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="48c46-156">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="48c46-157">Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="48c46-157">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="48c46-158">Det finns ett annat sätt att komma till session-menyn.</span><span class="sxs-lookup"><span data-stu-id="48c46-158">There is another way to get to the session menu.</span></span> <span data-ttu-id="48c46-159">När en PowerShell-fil är öppen i redigeraren visas ett grönt versions nummer längst ned till höger.</span><span class="sxs-lookup"><span data-stu-id="48c46-159">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="48c46-160">Om du klickar på det här versions numret visas session-menyn.</span><span class="sxs-lookup"><span data-stu-id="48c46-160">Clicking this version number will bring you to the session menu.</span></span>

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="48c46-161">Lägga till egna PowerShell-sökvägar i session-menyn</span><span class="sxs-lookup"><span data-stu-id="48c46-161">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="48c46-162">Du kan lägga till andra körbara sökvägar för PowerShell i sessionen via en VSCode-inställning.</span><span class="sxs-lookup"><span data-stu-id="48c46-162">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="48c46-163">Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa listan om den inte finns i din: `settings.json`</span><span class="sxs-lookup"><span data-stu-id="48c46-163">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="48c46-164">Varje objekt måste ha:</span><span class="sxs-lookup"><span data-stu-id="48c46-164">Each item must have:</span></span>

* <span data-ttu-id="48c46-165">`exePath`: Sökvägen till eller `powershell` den `pwsh` körbara filen.</span><span class="sxs-lookup"><span data-stu-id="48c46-165">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="48c46-166">`versionName`: Den text som visas i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="48c46-166">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="48c46-167">Du kan ange vilken standard version av PowerShell som ska användas `powershell.powerShellDefaultVersion` med inställningen genom att ställa in den på texten som visas i session-menyn `versionName` (aka i den sista inställningen):</span><span class="sxs-lookup"><span data-stu-id="48c46-167">You can set the default PowerShell version to use using the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (aka the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="48c46-168">När du har angett den här inställningen startar du om VSCode eller använder "Developer: Läs in kommando åtgärd för att läsa in den aktuella VSCode-fönstret igen.</span><span class="sxs-lookup"><span data-stu-id="48c46-168">Once you've set this setting, restart VSCode or use the the "Developer: Reload Window" command pallet action to reload the current VSCode window.</span></span>

<span data-ttu-id="48c46-169">Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!</span><span class="sxs-lookup"><span data-stu-id="48c46-169">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="48c46-170">Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="48c46-170">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

#### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="48c46-171">Konfigurations inställningar för VSCode</span><span class="sxs-lookup"><span data-stu-id="48c46-171">Configuration settings for VSCode</span></span>

<span data-ttu-id="48c46-172">Genom att följa stegen i föregående stycke kan du lägga till konfigurations inställningar `settings.json`i.</span><span class="sxs-lookup"><span data-stu-id="48c46-172">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="48c46-173">Vi rekommenderar följande konfigurations inställningar för VSCode:</span><span class="sxs-lookup"><span data-stu-id="48c46-173">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="48c46-174">Om du inte vill att de här inställningarna ska påverka alla filtyper kan VSCode också använda konfigurationer för flera språk.</span><span class="sxs-lookup"><span data-stu-id="48c46-174">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="48c46-175">Skapa en språkspecifik inställning genom att placera inställningarna i `[<language-name>]` ett fält.</span><span class="sxs-lookup"><span data-stu-id="48c46-175">Create a language specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="48c46-176">Exempel:</span><span class="sxs-lookup"><span data-stu-id="48c46-176">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="48c46-177">Mer information om fil kodning i VSCode finns i [förstå fil kodning](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="48c46-177">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="48c46-178">Fel sökning med VSCode</span><span class="sxs-lookup"><span data-stu-id="48c46-178">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="48c46-179">Ingen fel sökning på arbets ytan</span><span class="sxs-lookup"><span data-stu-id="48c46-179">No-workspace debugging</span></span>

<span data-ttu-id="48c46-180">Från och med VSCode version 1,9 kan du felsöka PowerShell-skript utan att behöva öppna mappen som innehåller PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="48c46-180">As of VSCode version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span> <span data-ttu-id="48c46-181">Öppna PowerShell-skriptfilen med **fil-> öppna fil...** , ange en Bryt punkt på en rad (tryck på <kbd>F9</kbd>) och tryck sedan på <kbd>F5</kbd> för att starta fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="48c46-181">Open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press <kbd>F9</kbd>) and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="48c46-182">Du bör se fönstret fel söknings åtgärder som gör att du kan dela upp i fel sökning, steg, återuppta och stoppa fel sökning.</span><span class="sxs-lookup"><span data-stu-id="48c46-182">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="48c46-183">Fel sökning av arbets yta</span><span class="sxs-lookup"><span data-stu-id="48c46-183">Workspace debugging</span></span>

<span data-ttu-id="48c46-184">Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat i Visual Studio Code med **Öppna mapp...** från menyn **Arkiv** .</span><span class="sxs-lookup"><span data-stu-id="48c46-184">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span> <span data-ttu-id="48c46-185">Mappen som du öppnar är vanligt vis din PowerShell-projektmapp och/eller roten för git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="48c46-185">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="48c46-186">Även i det här läget kan du börja felsöka det markerade PowerShell-skriptet genom att helt enkelt trycka på <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="48c46-186">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="48c46-187">Med fel sökning av arbets yta kan du dock definiera flera fel söknings konfigurationer förutom att bara Felsöka den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="48c46-187">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="48c46-188">Du kan till exempel lägga till en konfiguration för att:</span><span class="sxs-lookup"><span data-stu-id="48c46-188">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="48c46-189">Starta pester-tester i fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="48c46-189">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="48c46-190">Starta en speciell fil med argument i fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="48c46-190">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="48c46-191">Starta en interaktiv session i fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="48c46-191">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="48c46-192">Koppla fel söknings programmet till en PowerShell-värd process</span><span class="sxs-lookup"><span data-stu-id="48c46-192">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="48c46-193">Följ de här stegen för att skapa en fel söknings konfigurations fil:</span><span class="sxs-lookup"><span data-stu-id="48c46-193">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="48c46-194">Öppna vyn **fel sökning** genom att trycka på <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>d</kbd> (<kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>d</kbd> på Mac).</span><span class="sxs-lookup"><span data-stu-id="48c46-194">Open the **Debug** view by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> (<kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd> on Mac).</span></span>
  2. <span data-ttu-id="48c46-195">Klicka på ikonen **Konfigurera** kugg hjul i verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="48c46-195">Click the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="48c46-196">VSCode där du ombeds att **välja miljö**.</span><span class="sxs-lookup"><span data-stu-id="48c46-196">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="48c46-197">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="48c46-197">Choose **PowerShell**.</span></span>

  <span data-ttu-id="48c46-198">När du gör detta skapar VSCode en katalog och en fil ". vscode\launch.JSON" i roten i din arbetsytans mapp.</span><span class="sxs-lookup"><span data-stu-id="48c46-198">When you do this, VSCode creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span> <span data-ttu-id="48c46-199">Det är här som din fel söknings konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="48c46-199">This is where your debug configuration is stored.</span></span> <span data-ttu-id="48c46-200">Om filerna finns på en git-lagringsplats vill du vanligt vis allokera filen Launch. JSON.</span><span class="sxs-lookup"><span data-stu-id="48c46-200">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span> <span data-ttu-id="48c46-201">Innehållet i filen Launch. JSON är:</span><span class="sxs-lookup"><span data-stu-id="48c46-201">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="48c46-202">Detta representerar vanliga fel söknings scenarier.</span><span class="sxs-lookup"><span data-stu-id="48c46-202">This represents the common debug scenarios.</span></span> <span data-ttu-id="48c46-203">När du öppnar den här filen i redigeraren visas dock knappen **Lägg till konfiguration...** .</span><span class="sxs-lookup"><span data-stu-id="48c46-203">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="48c46-204">Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="48c46-204">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="48c46-205">En praktisk konfiguration för att lägga **till är PowerShell: Starta skript**.</span><span class="sxs-lookup"><span data-stu-id="48c46-205">One handy configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="48c46-206">Med den här konfigurationen kan du ange en fil med valfria argument som ska startas när du trycker på <kbd>F5</kbd> oavsett vilken fil som för närvarande är aktiv i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="48c46-206">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="48c46-207">När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession genom att välja en från List rutan Felsök konfiguration i verktygsfältet för **fel** söknings läge.</span><span class="sxs-lookup"><span data-stu-id="48c46-207">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="48c46-208">Det finns några Bloggar som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="48c46-208">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="48c46-209">[PowerShell-tillägg][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="48c46-209">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="48c46-210">[Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="48c46-210">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="48c46-211">[Fel sökning av Visual Studio Code-vägledning][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="48c46-211">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="48c46-212">[Felsöka PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="48c46-212">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="48c46-213">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="48c46-213">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="48c46-214">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="48c46-214">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="48c46-215">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="48c46-215">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="48c46-216">[Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="48c46-216">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="48c46-217">[Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="48c46-217">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

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

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="48c46-218">PowerShell-tillägg för VSCode</span><span class="sxs-lookup"><span data-stu-id="48c46-218">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="48c46-219">Du hittar PowerShell-tilläggets källkod på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="48c46-219">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
