---
title: Använda Visual Studio Code för PowerShell-utveckling
description: Använda Visual Studio Code för PowerShell-utveckling
ms.date: 11/07/2019
ms.openlocfilehash: b083388174dbae4a50da73156d2fce41412613a7
ms.sourcegitcommit: 14b50e5446f69729f72231f5dc6f536cdd1084c3
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/12/2019
ms.locfileid: "73933873"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="df072-103">Använda Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="df072-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="df072-104">Förutom [POWERSHELL ISE][ise], stöds även PowerShell i Visual Studio Code (VSCode).</span><span class="sxs-lookup"><span data-stu-id="df072-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code (VSCode).</span></span> <span data-ttu-id="df072-105">ISE stöds inte med PowerShell Core, men VSCode stöds för PowerShell Core på alla plattformar: Windows, macOS och Linux.</span><span class="sxs-lookup"><span data-stu-id="df072-105">The ISE isn't supported with PowerShell Core, but VSCode is supported for PowerShell Core on all platforms: Windows, macOS, and Linux.</span></span>

<span data-ttu-id="df072-106">Du kan använda VSCode i Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera Windows Management Framework 5,1 för Windows-OSs som Windows 8,1.</span><span class="sxs-lookup"><span data-stu-id="df072-106">You can use VSCode on Windows with PowerShell version 5 by using Windows 10 or by installing Windows Management Framework 5.1 for down-level Windows OSs such as Windows 8.1.</span></span> <span data-ttu-id="df072-107">Mer information finns i [Installera och konfigurera WMF 5,1](/powershell/scripting/wmf/setup/install-configure).</span><span class="sxs-lookup"><span data-stu-id="df072-107">For more information, see [Install and Configure WMF 5.1](/powershell/scripting/wmf/setup/install-configure).</span></span>

<span data-ttu-id="df072-108">Innan du börjar ska du kontrol lera att PowerShell finns i systemet.</span><span class="sxs-lookup"><span data-stu-id="df072-108">Before you begin, make sure PowerShell exists on your system.</span></span> <span data-ttu-id="df072-109">För moderna arbets belastningar på Windows, macOS och Linux, se följande länkar:</span><span class="sxs-lookup"><span data-stu-id="df072-109">For modern workloads on Windows, macOS, and Linux, see the following links:</span></span>

- <span data-ttu-id="df072-110">[Installera PowerShell Core på Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="df072-110">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="df072-111">[Installera PowerShell Core på macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="df072-111">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="df072-112">[Installera PowerShell Core på Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="df072-112">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="df072-113">För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="df072-113">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-vscode"></a><span data-ttu-id="df072-114">Redigera med VSCode</span><span class="sxs-lookup"><span data-stu-id="df072-114">Editing with VSCode</span></span>

1. <span data-ttu-id="df072-115">Installera VSCode.</span><span class="sxs-lookup"><span data-stu-id="df072-115">Install VSCode.</span></span> <span data-ttu-id="df072-116">Mer information finns i Översikt över [konfiguration av Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span><span class="sxs-lookup"><span data-stu-id="df072-116">For more information, see the overview [Setting up Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview).</span></span>

   <span data-ttu-id="df072-117">Det finns installations anvisningar för varje plattform:</span><span class="sxs-lookup"><span data-stu-id="df072-117">There are installation instructions for each platform:</span></span>

   - <span data-ttu-id="df072-118">**Linux**: följ installations anvisningarna på sidan för att [köra VSCode på Linux](https://code.visualstudio.com/docs/setup/linux) .</span><span class="sxs-lookup"><span data-stu-id="df072-118">**Linux**: follow the installation instructions on the [Running VSCode on Linux](https://code.visualstudio.com/docs/setup/linux) page.</span></span>
   - <span data-ttu-id="df072-119">**MacOS**: följ installations anvisningarna på sidan för att [köra VSCode på MacOS](https://code.visualstudio.com/docs/setup/mac) .</span><span class="sxs-lookup"><span data-stu-id="df072-119">**macOS**: follow the installation instructions on the [Running VSCode on macOS](https://code.visualstudio.com/docs/setup/mac) page.</span></span>

     > [!IMPORTANT]
     > <span data-ttu-id="df072-120">På macOS måste du installera OpenSSL för att PowerShell-tillägget ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="df072-120">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span> <span data-ttu-id="df072-121">Det enklaste sättet att göra detta är att installera [homebrew](https://brew.sh/) och sedan köra `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="df072-121">The easiest way to accomplish this is to install [Homebrew](https://brew.sh/) and then run `brew install openssl`.</span></span> <span data-ttu-id="df072-122">VSCode kan nu läsa in PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="df072-122">VSCode can now load the PowerShell extension successfully.</span></span>

   - <span data-ttu-id="df072-123">**Windows**: följ installations anvisningarna på sidan för att [köra VSCode på Windows](https://code.visualstudio.com/docs/setup/windows) .</span><span class="sxs-lookup"><span data-stu-id="df072-123">**Windows**: follow the installation instructions on the [Running VSCode on Windows](https://code.visualstudio.com/docs/setup/windows) page.</span></span>

1. <span data-ttu-id="df072-124">Installera PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="df072-124">Install the PowerShell Extension.</span></span>

   1. <span data-ttu-id="df072-125">Starta VSCode-appen genom att:</span><span class="sxs-lookup"><span data-stu-id="df072-125">Launch the VSCode app by:</span></span>
      - <span data-ttu-id="df072-126">**Windows**: skriva `code` i PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="df072-126">**Windows**: typing `code` in your PowerShell session</span></span>
      - <span data-ttu-id="df072-127">**Linux**: skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="df072-127">**Linux**: typing `code` in your terminal</span></span>
      - <span data-ttu-id="df072-128">**MacOS**: skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="df072-128">**macOS**: typing `code` in your terminal</span></span>
   1. <span data-ttu-id="df072-129">Starta **Quick Open** på Windows eller Linux genom att trycka på <kbd>CTRL</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-129">Launch **Quick Open** on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="df072-130">I macOS trycker du på <kbd>Cmd</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-130">On macOS, press <kbd>Cmd</kbd>+<kbd>P</kbd>.</span></span>
   1. <span data-ttu-id="df072-131">Skriv `ext install powershell` i snabb öppning och tryck på **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="df072-131">In Quick Open, type `ext install powershell` and press **Enter**.</span></span>
   1. <span data-ttu-id="df072-132">Vyn **tillägg** öppnas i sido fältet.</span><span class="sxs-lookup"><span data-stu-id="df072-132">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="df072-133">Välj PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df072-133">Select the PowerShell extension from Microsoft.</span></span>
      <span data-ttu-id="df072-134">Du bör se en VSCode-skärm som liknar följande bild:</span><span class="sxs-lookup"><span data-stu-id="df072-134">You should see a VSCode screen similar to the following image:</span></span>

      ![VSCode](../../images/using-vscode/vscode.png)

   1. <span data-ttu-id="df072-136">Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="df072-136">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
   1. <span data-ttu-id="df072-137">Efter installationen ser knappen **Installera** att **läsas in igen**.</span><span class="sxs-lookup"><span data-stu-id="df072-137">After the install, you see the **Install** button turns to **Reload**.</span></span> <span data-ttu-id="df072-138">Klicka på **Läs in igen**.</span><span class="sxs-lookup"><span data-stu-id="df072-138">Click on **Reload**.</span></span>
   1. <span data-ttu-id="df072-139">När VSCode har lästs in på nytt är du redo för redigering.</span><span class="sxs-lookup"><span data-stu-id="df072-139">After VSCode has reloaded, you're ready for editing.</span></span>

<span data-ttu-id="df072-140">Om du till exempel vill skapa en ny fil klickar du på **fil > ny**.</span><span class="sxs-lookup"><span data-stu-id="df072-140">For example, to create a new file, click **File > New**.</span></span> <span data-ttu-id="df072-141">Spara genom att klicka på **arkiv > Spara** och ange ett fil namn, till exempel `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="df072-141">To save it, click **File > Save** and then provide a file name, such as `HelloWorld.ps1`.</span></span> <span data-ttu-id="df072-142">Stäng filen genom att klicka på `X` bredvid fil namnet.</span><span class="sxs-lookup"><span data-stu-id="df072-142">To close the file, click the `X` next to the file name.</span></span> <span data-ttu-id="df072-143">Om du vill avsluta VSCode **avslutar du filen >** .</span><span class="sxs-lookup"><span data-stu-id="df072-143">To exit VSCode, **File > Exit**.</span></span>

### <a name="installing-the-powershell-extension-on-restricted-systems"></a><span data-ttu-id="df072-144">Installera PowerShell-tillägget på begränsade system</span><span class="sxs-lookup"><span data-stu-id="df072-144">Installing the PowerShell Extension on Restricted Systems</span></span>

<span data-ttu-id="df072-145">Vissa system har kon figurer ATS på ett sätt som kräver att alla kod-signaturer kontrol leras och kräver att PowerShell Editor-tjänster godkänns manuellt för att köras i systemet.</span><span class="sxs-lookup"><span data-stu-id="df072-145">Some systems are set up in a way that requires all code signatures to be checked and requires PowerShell Editor Services to be manually approved to run on the system.</span></span> <span data-ttu-id="df072-146">En grupprincip uppdatering som ändrar körnings principen är en sannolik orsak om du har installerat PowerShell-tillägget men får ett fel som:</span><span class="sxs-lookup"><span data-stu-id="df072-146">A Group Policy update that changes execution policy is a likely cause if you've installed the PowerShell extension but are receiving an error such as:</span></span>

```
Language server startup failed.
```

<span data-ttu-id="df072-147">Om du vill godkänna PowerShell Editor-tjänster och PowerShell-tillägget för VSCode manuellt öppnar du en PowerShell-kommandotolk och kör följande kommando:</span><span class="sxs-lookup"><span data-stu-id="df072-147">To manually approve PowerShell Editor Services and the PowerShell extension for VSCode, open a PowerShell prompt and run the following command:</span></span>

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

<span data-ttu-id="df072-148">Du tillfrågas om **vill du köra program vara från den här ej betrodda utgivaren?**</span><span class="sxs-lookup"><span data-stu-id="df072-148">You're prompted with **Do you want to run software from this untrusted publisher?**</span></span> <span data-ttu-id="df072-149">Skriv `A` för att köra filen.</span><span class="sxs-lookup"><span data-stu-id="df072-149">Type `A` to run the file.</span></span> <span data-ttu-id="df072-150">Öppna sedan VSCode och kontrol lera att PowerShell-tillägget fungerar korrekt.</span><span class="sxs-lookup"><span data-stu-id="df072-150">Then, open VSCode and check that the PowerShell extension is functioning properly.</span></span> <span data-ttu-id="df072-151">Om du fortfarande har problem med att komma igång kan du berätta om [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span><span class="sxs-lookup"><span data-stu-id="df072-151">If you still have issues getting started, let us know on [GitHub](https://github.com/PowerShell/vscode-powershell/issues).</span></span>

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a><span data-ttu-id="df072-152">Välja en version av PowerShell som ska användas med tillägget</span><span class="sxs-lookup"><span data-stu-id="df072-152">Choosing a version of PowerShell to use with the extension</span></span>

<span data-ttu-id="df072-153">Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en viss version av PowerShell med PowerShell-tillägget.</span><span class="sxs-lookup"><span data-stu-id="df072-153">With PowerShell Core installing side-by-side with Windows PowerShell, it's now possible to use a particular version of PowerShell with the PowerShell extension.</span></span> <span data-ttu-id="df072-154">Använd följande steg för att välja version:</span><span class="sxs-lookup"><span data-stu-id="df072-154">Use the following steps to choose the version:</span></span>

1. <span data-ttu-id="df072-155">Öppna **paletten kommando** i Windows eller Linux med <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-155">Open the **Command Palette** on Windows or Linux with <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span> <span data-ttu-id="df072-156">I macOS använder du <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-156">On macOS, use <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.</span></span>
1. <span data-ttu-id="df072-157">Sök efter **session**.</span><span class="sxs-lookup"><span data-stu-id="df072-157">Search for **Session**.</span></span>
1. <span data-ttu-id="df072-158">Klicka på **PowerShell: Visa session-menyn**.</span><span class="sxs-lookup"><span data-stu-id="df072-158">Click on **PowerShell: Show Session Menu**.</span></span>
1. <span data-ttu-id="df072-159">Välj den version av PowerShell som du vill använda i listan, till exempel: **PowerShell Core**.</span><span class="sxs-lookup"><span data-stu-id="df072-159">Choose the version of PowerShell you want to use from the list, for example: **PowerShell Core**.</span></span>

> [!IMPORTANT]
> <span data-ttu-id="df072-160">Den här funktionen söker efter några välkända sökvägar på olika operativ system för att identifiera installations platser för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df072-160">This feature looks at a few well-known paths on different operating systems to discover install locations of PowerShell.</span></span> <span data-ttu-id="df072-161">Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="df072-161">If you installed PowerShell to a non-typical location, it might not show up initially in the Session Menu.</span></span> <span data-ttu-id="df072-162">Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.</span><span class="sxs-lookup"><span data-stu-id="df072-162">You can extend the session menu by [adding your own custom paths](#adding-your-own-powershell-paths-to-the-session-menu) as described below.</span></span>

>[!NOTE]
> <span data-ttu-id="df072-163">Det finns ett annat sätt att komma till session-menyn.</span><span class="sxs-lookup"><span data-stu-id="df072-163">There's another way to get to the session menu.</span></span> <span data-ttu-id="df072-164">När en PowerShell-fil är öppen i redigeraren visas ett grönt versions nummer längst ned till höger.</span><span class="sxs-lookup"><span data-stu-id="df072-164">When a PowerShell file is open in your editor, you see a green version number in the bottom right.</span></span> <span data-ttu-id="df072-165">Om du klickar på det här versions numret visas session-menyn.</span><span class="sxs-lookup"><span data-stu-id="df072-165">Clicking this version number will bring you to the session menu.</span></span>

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a><span data-ttu-id="df072-166">Lägga till egna PowerShell-sökvägar i session-menyn</span><span class="sxs-lookup"><span data-stu-id="df072-166">Adding your own PowerShell paths to the session menu</span></span>

<span data-ttu-id="df072-167">Du kan lägga till andra körbara sökvägar för PowerShell i sessionen via en VSCode-inställning.</span><span class="sxs-lookup"><span data-stu-id="df072-167">You can add other PowerShell executable paths to the session menu through a VSCode setting.</span></span>

<span data-ttu-id="df072-168">Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa en lista om den inte finns i `settings.json`:</span><span class="sxs-lookup"><span data-stu-id="df072-168">Add an item to the list `powershell.powerShellAdditionalExePaths` or create the list if it doesn't exist in your `settings.json`:</span></span>

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

<span data-ttu-id="df072-169">Varje objekt måste ha:</span><span class="sxs-lookup"><span data-stu-id="df072-169">Each item must have:</span></span>

* <span data-ttu-id="df072-170">`exePath`: sökvägen till `pwsh` eller `powershell` körbar fil.</span><span class="sxs-lookup"><span data-stu-id="df072-170">`exePath`: The path to the `pwsh` or `powershell` executable.</span></span>
* <span data-ttu-id="df072-171">`versionName`: den text som visas i session-menyn.</span><span class="sxs-lookup"><span data-stu-id="df072-171">`versionName`: The text that will show up in the session menu.</span></span>

<span data-ttu-id="df072-172">Du kan ställa in standard versionen av PowerShell att använda `powershell.powerShellDefaultVersion` inställningen genom att ställa in den på texten som visas i session-menyn (kallas även `versionName` i den senaste inställningen):</span><span class="sxs-lookup"><span data-stu-id="df072-172">You can set the default PowerShell version to use the `powershell.powerShellDefaultVersion` setting by setting this to the text displayed in the session menu (also known as the `versionName` in the last setting):</span></span>

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

<span data-ttu-id="df072-173">När du har konfigurerat den här inställningen startar du om VSCode eller laddar om den aktuella VSCode-fönstret från **kommando-paletten**. Skriv **Developer: Läs in igen**.</span><span class="sxs-lookup"><span data-stu-id="df072-173">After you've configured this setting, restart VSCode or to reload the current VSCode window from the **Command Palette**, type **Developer: Reload Window**.</span></span>

<span data-ttu-id="df072-174">Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!</span><span class="sxs-lookup"><span data-stu-id="df072-174">If you open the session menu, you now see your additional PowerShell versions!</span></span>

> [!NOTE]
> <span data-ttu-id="df072-175">Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="df072-175">If you build PowerShell from source, this is a great way to test out your local build of PowerShell.</span></span>

### <a name="configuration-settings-for-vscode"></a><span data-ttu-id="df072-176">Konfigurations inställningar för VSCode</span><span class="sxs-lookup"><span data-stu-id="df072-176">Configuration settings for VSCode</span></span>

<span data-ttu-id="df072-177">Genom att följa stegen i föregående stycke kan du lägga till konfigurations inställningar i `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="df072-177">By using the steps in the previous paragraph, you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="df072-178">Vi rekommenderar följande konfigurations inställningar för VSCode:</span><span class="sxs-lookup"><span data-stu-id="df072-178">We recommend the following configuration settings for VSCode:</span></span>

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

<span data-ttu-id="df072-179">Om du inte vill att de här inställningarna ska påverka alla filtyper kan VSCode också använda konfigurationer för flera språk.</span><span class="sxs-lookup"><span data-stu-id="df072-179">If you don't want these settings to affect all files types, VSCode also allows per-language configurations.</span></span> <span data-ttu-id="df072-180">Skapa en språkspecifik inställning genom att lägga till inställningar i ett `[<language-name>]`s fält.</span><span class="sxs-lookup"><span data-stu-id="df072-180">Create a language-specific setting by putting settings in a `[<language-name>]` field.</span></span> <span data-ttu-id="df072-181">Till exempel:</span><span class="sxs-lookup"><span data-stu-id="df072-181">For example:</span></span>

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

<span data-ttu-id="df072-182">Mer information om fil kodning i VSCode finns i [förstå fil kodning](understanding-file-encoding.md).</span><span class="sxs-lookup"><span data-stu-id="df072-182">For more information about file encoding in VSCode, see [Understanding file encoding](understanding-file-encoding.md).</span></span>

## <a name="debugging-with-vscode"></a><span data-ttu-id="df072-183">Fel sökning med VSCode</span><span class="sxs-lookup"><span data-stu-id="df072-183">Debugging with VSCode</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="df072-184">Ingen fel sökning på arbets ytan</span><span class="sxs-lookup"><span data-stu-id="df072-184">No-workspace debugging</span></span>

<span data-ttu-id="df072-185">Från och med VSCode version 1,9 kan du felsöka PowerShell-skript utan att öppna mappen som innehåller PowerShell-skriptet.</span><span class="sxs-lookup"><span data-stu-id="df072-185">As of VSCode version 1.9 you can debug PowerShell scripts without opening the folder that contains the PowerShell script.</span></span> <span data-ttu-id="df072-186">Öppna PowerShell-skriptfilen med **filen > öppna fil...** , ange en Bryt punkt på en rad, tryck på <kbd>F9</kbd>och tryck sedan på <kbd>F5</kbd> för att starta fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="df072-186">Open the PowerShell script file with **File > Open File...**, set a breakpoint on a line, press <kbd>F9</kbd>, and then press <kbd>F5</kbd> to start debugging.</span></span> <span data-ttu-id="df072-187">Du bör se fönstret fel söknings åtgärder, vilket gör att du kan bryta i fel söknings programmet, steg, återuppta och stoppa fel sökningen.</span><span class="sxs-lookup"><span data-stu-id="df072-187">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume, and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="df072-188">Fel sökning av arbets yta</span><span class="sxs-lookup"><span data-stu-id="df072-188">Workspace debugging</span></span>

<span data-ttu-id="df072-189">Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat i Visual Studio Code från menyn **Arkiv** med **Öppna mapp..** .. Mappen som du öppnar är vanligt vis din PowerShell-projektmapp och/eller roten för git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="df072-189">Workspace debugging refers to debugging in the context of a folder that you've opened in Visual Studio Code from the **File** menu using **Open Folder...**. The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="df072-190">Även i det här läget kan du börja felsöka det markerade PowerShell-skriptet genom att trycka på <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-190">Even in this mode, you can start debugging the currently selected PowerShell script by pressing <kbd>F5</kbd>.</span></span> <span data-ttu-id="df072-191">Med fel sökning av arbets yta kan du dock definiera flera fel söknings konfigurationer förutom att bara Felsöka den öppna filen.</span><span class="sxs-lookup"><span data-stu-id="df072-191">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span> <span data-ttu-id="df072-192">Du kan till exempel lägga till en konfiguration för att:</span><span class="sxs-lookup"><span data-stu-id="df072-192">For instance, you can add a configuration to:</span></span>

- <span data-ttu-id="df072-193">Starta pester-tester i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="df072-193">Launch Pester tests in the debugger.</span></span>
- <span data-ttu-id="df072-194">Starta en speciell fil med argument i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="df072-194">Launch a specific file with arguments in the debugger.</span></span>
- <span data-ttu-id="df072-195">Starta en interaktiv session i fel söknings programmet.</span><span class="sxs-lookup"><span data-stu-id="df072-195">Launch an interactive session in the debugger.</span></span>
- <span data-ttu-id="df072-196">Koppla fel sökaren till en PowerShell-värd process.</span><span class="sxs-lookup"><span data-stu-id="df072-196">Attach the debugger to a PowerShell host process.</span></span>

<span data-ttu-id="df072-197">Följ de här stegen för att skapa en fel söknings konfigurations fil:</span><span class="sxs-lookup"><span data-stu-id="df072-197">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="df072-198">Öppna **fel söknings** vyn i Windows eller Linux genom att trycka på <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-198">Open the **Debug** view on Windows or Linux by pressing <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span> <span data-ttu-id="df072-199">I macOS trycker du på <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span><span class="sxs-lookup"><span data-stu-id="df072-199">On macOS, press <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.</span></span>
  1. <span data-ttu-id="df072-200">Klicka på ikonen **Konfigurera** kugg hjul i verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="df072-200">Click the **Configure** gear icon in the toolbar.</span></span>
  1. <span data-ttu-id="df072-201">VSCode där du ombeds att **välja miljö**.</span><span class="sxs-lookup"><span data-stu-id="df072-201">VSCode prompts you to **Select Environment**.</span></span> <span data-ttu-id="df072-202">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="df072-202">Choose **PowerShell**.</span></span>

<span data-ttu-id="df072-203">Resultatet är att VSCode skapar en katalog och en fil `.vscode\launch.json` i roten i din arbetsytans mapp.</span><span class="sxs-lookup"><span data-stu-id="df072-203">The result is that VSCode creates a directory and a file `.vscode\launch.json` in the root of your workspace folder.</span></span> <span data-ttu-id="df072-204">Den här platsen är den plats där fel söknings konfigurationen lagras.</span><span class="sxs-lookup"><span data-stu-id="df072-204">This location is where your debug configuration is stored.</span></span> <span data-ttu-id="df072-205">Om filerna finns på en git-lagringsplats vill du vanligt vis bekräfta `launch.json`-filen.</span><span class="sxs-lookup"><span data-stu-id="df072-205">If your files are in a Git repository, you typically want to commit the `launch.json` file.</span></span> <span data-ttu-id="df072-206">Innehållet i `launch.json`-filen är:</span><span class="sxs-lookup"><span data-stu-id="df072-206">The contents of the `launch.json` file are:</span></span>

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

<span data-ttu-id="df072-207">Den här filen representerar vanliga fel söknings scenarier.</span><span class="sxs-lookup"><span data-stu-id="df072-207">This file represents the common debug scenarios.</span></span> <span data-ttu-id="df072-208">När du öppnar den här filen i redigeraren visas knappen **Lägg till konfiguration...** .</span><span class="sxs-lookup"><span data-stu-id="df072-208">When you open this file in the editor, you see an **Add Configuration...** button.</span></span> <span data-ttu-id="df072-209">Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="df072-209">You can click this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="df072-210">En användbar konfiguration för att lägga till är **PowerShell: starta skript**.</span><span class="sxs-lookup"><span data-stu-id="df072-210">One useful configuration to add is **PowerShell: Launch Script**.</span></span> <span data-ttu-id="df072-211">Med den här konfigurationen kan du ange en fil med valfria argument som ska startas när du trycker på <kbd>F5</kbd> oavsett vilken fil som för närvarande är aktiv i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="df072-211">With this configuration, you can specify a file with optional arguments that should be launched whenever you press <kbd>F5</kbd> no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="df072-212">När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession.</span><span class="sxs-lookup"><span data-stu-id="df072-212">After the debug configuration is established, you can select which configuration you want to use during a debug session.</span></span> <span data-ttu-id="df072-213">Välj en konfiguration i list rutan Felsök konfiguration i **fel söknings** verktygsfältets verktygsfält.</span><span class="sxs-lookup"><span data-stu-id="df072-213">Select a configuration from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="df072-214">Det finns några Bloggar som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="df072-214">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="df072-215">[PowerShell-tillägg][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="df072-215">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="df072-216">[Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="df072-216">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="df072-217">[Fel sökning av Visual Studio Code-vägledning][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="df072-217">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="df072-218">[Felsöka PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="df072-218">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="df072-219">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="df072-219">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="df072-220">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="df072-220">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="df072-221">[Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="df072-221">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="df072-222">[Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="df072-222">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="df072-223">[Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="df072-223">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise/Introducing-the-Windows-PowerShell-ISE.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-Linux.md
[install-pscore-macos]:  ../../setup/Installing-PowerShell-Core-on-macOS.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]: https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]: https://devblogs.microsoft.com/powershell/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]: https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]: https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]: https://devblogs.microsoft.com/scripting/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]: https://devblogs.microsoft.com/scripting/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]: https://devblogs.microsoft.com/scripting/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-vscode"></a><span data-ttu-id="df072-224">PowerShell-tillägg för VSCode</span><span class="sxs-lookup"><span data-stu-id="df072-224">PowerShell Extension for VSCode</span></span>

<span data-ttu-id="df072-225">Du hittar PowerShell-tilläggets källkod på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="df072-225">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
