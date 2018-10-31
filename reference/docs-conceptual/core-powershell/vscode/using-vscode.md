---
title: Med Visual Studio Code för PowerShell-utveckling
description: Med Visual Studio Code för PowerShell-utveckling
ms.date: 08/06/2018
ms.openlocfilehash: 9c06ce72c39d08e75fcb7e5cf9d5f92ae5dd8ed9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225802"
---
# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="d1f26-103">Med Visual Studio Code för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="d1f26-103">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="d1f26-104">Förutom den [PowerShell ISE][ise], PowerShell är också väl stöds i Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d1f26-104">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="d1f26-105">Dessutom stöds ISE inte med PowerShell Core Visual Studio Code har stöd för PowerShell Core på alla plattformar (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="d1f26-105">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="d1f26-106">Du kan använda Visual Studio Code på Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) för äldre Windows-operativsystem (t.ex. Windows 8.1, osv.).</span><span class="sxs-lookup"><span data-stu-id="d1f26-106">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="d1f26-107">Kontrollera att PowerShell finns i systemet innan du startar den.</span><span class="sxs-lookup"><span data-stu-id="d1f26-107">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="d1f26-108">Moderna arbetsbelastningar i Windows, macOS och Linux finns här:</span><span class="sxs-lookup"><span data-stu-id="d1f26-108">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="d1f26-109">[Installera PowerShell Core i Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="d1f26-109">[Installing PowerShell Core on Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="d1f26-110">[Installera PowerShell Core i macOS][install-pscore-macos]</span><span class="sxs-lookup"><span data-stu-id="d1f26-110">[Installing PowerShell Core on macOS][install-pscore-macos]</span></span>
- <span data-ttu-id="d1f26-111">[Installera PowerShell Core i Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="d1f26-111">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="d1f26-112">Traditionella Windows PowerShell-arbetsbelastningar, se [installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="d1f26-112">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="d1f26-113">Redigera med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-113">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="d1f26-114">1. Installera Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-114">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="d1f26-115">**Linux**: Följ installationsanvisningarna på den [som körs på Linux i VS Code](https://code.visualstudio.com/docs/setup/linux) sidan</span><span class="sxs-lookup"><span data-stu-id="d1f26-115">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="d1f26-116">**macOS**: Följ installationsanvisningarna på den [köra VS-kod i Mac OS](https://code.visualstudio.com/docs/setup/mac) sidan</span><span class="sxs-lookup"><span data-stu-id="d1f26-116">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

  > [!IMPORTANT]
  > <span data-ttu-id="d1f26-117">I macOS, måste du installera OpenSSL för PowerShell-tillägget ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="d1f26-117">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
  > <span data-ttu-id="d1f26-118">Det enklaste sättet att göra detta är att installera [Homebrew](http://brew.sh/) och kör sedan `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="d1f26-118">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
  > <span data-ttu-id="d1f26-119">VS Code kan nu läsa in PowerShell-tillägget har.</span><span class="sxs-lookup"><span data-stu-id="d1f26-119">VS Code can now load the PowerShell extension successfully.</span></span>

- <span data-ttu-id="d1f26-120">**Windows**: Följ installationsanvisningarna på den [köra VS Code på Windows](https://code.visualstudio.com/docs/setup/windows) sidan</span><span class="sxs-lookup"><span data-stu-id="d1f26-120">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="d1f26-121">2. Installera PowerShell-tillägget</span><span class="sxs-lookup"><span data-stu-id="d1f26-121">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="d1f26-122">Starta Visual Studio Code app genom att:</span><span class="sxs-lookup"><span data-stu-id="d1f26-122">Launch the Visual Studio Code app by:</span></span>
  - <span data-ttu-id="d1f26-123">**Windows**: att skriva `code` i PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="d1f26-123">**Windows**: typing `code` in your PowerShell session</span></span>
  - <span data-ttu-id="d1f26-124">**Linux**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="d1f26-124">**Linux**: typing `code` in your terminal</span></span>
  - <span data-ttu-id="d1f26-125">**macOS**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="d1f26-125">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="d1f26-126">Starta **snabb öppna** genom att trycka på **Ctrl + P** (**Cmd + P** på Mac).</span><span class="sxs-lookup"><span data-stu-id="d1f26-126">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="d1f26-127">Snabb Skriv `ext install powershell` och därefter **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-127">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="d1f26-128">Den **tillägg** öppnas i Sidopanel.</span><span class="sxs-lookup"><span data-stu-id="d1f26-128">The **Extensions** view opens on the Side Bar.</span></span> <span data-ttu-id="d1f26-129">Välj tillägget PowerShell från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1f26-129">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="d1f26-130">Du bör se ut ungefär som nedan:</span><span class="sxs-lookup"><span data-stu-id="d1f26-130">You should see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="d1f26-132">Klicka på den **installera** knappen på PowerShell-tillägget från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="d1f26-132">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="d1f26-133">Efter installationen visas den **installera** knappen övergår i **Reload**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-133">After the install, you see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="d1f26-134">Klicka på **Reload**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-134">Click on **Reload**.</span></span>
- <span data-ttu-id="d1f26-135">När Visual Studio Code har läs in igen, är det dags för redigering.</span><span class="sxs-lookup"><span data-stu-id="d1f26-135">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="d1f26-136">Exempelvis för att skapa en ny fil, klickar du på **File -> Nytt**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-136">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="d1f26-137">Om du vill spara den, klickar du på **Arkiv -> Spara** och ange sedan ett filnamn, låt oss säga att `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="d1f26-137">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="d1f26-138">Stäng filen genom att klicka på ”x” bredvid namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-138">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="d1f26-139">Avsluta Visual Studio Code **Arkiv -> Avsluta**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-139">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="d1f26-140">Med hjälp av en specifik version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1f26-140">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="d1f26-141">Om du vill använda en specifik installation av PowerShell med Visual Studio Code kan behöva du lägga till en ny variabel i filen med inställningar.</span><span class="sxs-lookup"><span data-stu-id="d1f26-141">If you wish to use a specific installation of PowerShell with Visual Studio Code, you need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="d1f26-142">Klicka på **Arkiv -> Inställningar -> Inställningar**</span><span class="sxs-lookup"><span data-stu-id="d1f26-142">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="d1f26-143">Två rapportredigerarens fönster visas.</span><span class="sxs-lookup"><span data-stu-id="d1f26-143">Two editor panes appear.</span></span>
   <span data-ttu-id="d1f26-144">I fönstret höger (`settings.json`), infoga inställningen nedan lämpliga för ditt operativsystem någonstans mellan de två klammerparenteser (`{` och `}`) och Ersätt **\<version\>** med den installerade versionen av PowerShell:</span><span class="sxs-lookup"><span data-stu-id="d1f26-144">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace **\<version\>** with the installed PowerShell version:</span></span>

   ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
   ```

1. <span data-ttu-id="d1f26-145">Ersätt inställningen med sökvägen till den önskade PowerShell körbar</span><span class="sxs-lookup"><span data-stu-id="d1f26-145">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="d1f26-146">Spara filen och starta om Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-146">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="d1f26-147">Konfigurationsinställningar för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-147">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="d1f26-148">Med hjälp av stegen i föregående stycke kan du lägga till konfigurationsinställningar i `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="d1f26-148">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="d1f26-149">Vi rekommenderar följande konfigurationsinställningar för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="d1f26-149">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="d1f26-150">Felsöka med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-150">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="d1f26-151">Ingen arbetsyta felsökning</span><span class="sxs-lookup"><span data-stu-id="d1f26-151">No-workspace debugging</span></span>

<span data-ttu-id="d1f26-152">Du kan felsöka PowerShell-skript utan att öppna den mapp som innehåller PowerShell-skriptet från och med Visual Studio Code-versionen 1.9.</span><span class="sxs-lookup"><span data-stu-id="d1f26-152">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="d1f26-153">Öppna helt enkelt PowerShell-skriptfil med **Arkiv -> Öppna filen...** , ange en brytpunkt på rad (tryck på F9) och tryck på F5 för att starta felsökningen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-153">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="d1f26-154">Du bör se Debug åtgärdsfönstret visas där du kan dela i felsökare, steg, återuppta och stoppa felsökning.</span><span class="sxs-lookup"><span data-stu-id="d1f26-154">You should see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="d1f26-155">Felsökning av arbetsyta</span><span class="sxs-lookup"><span data-stu-id="d1f26-155">Workspace debugging</span></span>

<span data-ttu-id="d1f26-156">Felsökning av arbetsytan refererar till felsökning i samband med en mapp som du har öppnat i Visual Studio Code med **Öppna mapp...**  från den **filen** menyn.</span><span class="sxs-lookup"><span data-stu-id="d1f26-156">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="d1f26-157">Den mapp som du öppnar är vanligtvis projektmappen PowerShell och/eller roten för Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-157">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="d1f26-158">Även i det här läget kan starta du felsökning markerade PowerShell-skriptet genom att bara trycka på F5.</span><span class="sxs-lookup"><span data-stu-id="d1f26-158">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="d1f26-159">Dock kan arbetsytan felsökning du definiera konfigurationer med flera debug än bara felsökning öppna filen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-159">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="d1f26-160">Du kan exempelvis lägga till en konfigurationer för att:</span><span class="sxs-lookup"><span data-stu-id="d1f26-160">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="d1f26-161">Starta Pester tester i felsökningsprogrammet</span><span class="sxs-lookup"><span data-stu-id="d1f26-161">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="d1f26-162">Starta en viss fil med argumenten i Felsökning</span><span class="sxs-lookup"><span data-stu-id="d1f26-162">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="d1f26-163">Starta en interaktiv session i Felsökning</span><span class="sxs-lookup"><span data-stu-id="d1f26-163">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="d1f26-164">Bifoga felsökningsprogrammet till en värdprocess för PowerShell</span><span class="sxs-lookup"><span data-stu-id="d1f26-164">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="d1f26-165">Följ dessa steg för att skapa konfigurationsfilen debug:</span><span class="sxs-lookup"><span data-stu-id="d1f26-165">Follow these steps to create your debug configuration file:</span></span>

  1. <span data-ttu-id="d1f26-166">Öppna den **felsöka** vyn genom att trycka på **Ctrl + Skift + D** (**Cmd + SKIFT + D** på Mac).</span><span class="sxs-lookup"><span data-stu-id="d1f26-166">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
  2. <span data-ttu-id="d1f26-167">Tryck på den **konfigurera** kugghjulsikonen i verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="d1f26-167">Press the **Configure** gear icon in the toolbar.</span></span>
  3. <span data-ttu-id="d1f26-168">Visual Studio Code uppmanas du att **Välj miljö**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-168">Visual Studio Code prompts you to **Select Environment**.</span></span> <span data-ttu-id="d1f26-169">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-169">Choose **PowerShell**.</span></span>

  <span data-ttu-id="d1f26-170">När du gör detta skapar en katalog och en fil ”.vscode\launch.json” i roten av din arbetsytemapp Visual Studio Code.</span><span class="sxs-lookup"><span data-stu-id="d1f26-170">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
  <span data-ttu-id="d1f26-171">Det här är där din debug-konfiguration lagras.</span><span class="sxs-lookup"><span data-stu-id="d1f26-171">This is where your debug configuration is stored.</span></span> <span data-ttu-id="d1f26-172">Om filerna finns i en Git-lagringsplats, vill du förmodligen att genomföra launch.json-filen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-172">If your files are in a Git repository, you typically want to commit the launch.json file.</span></span>
  <span data-ttu-id="d1f26-173">Innehållet i launch.json-filen är:</span><span class="sxs-lookup"><span data-stu-id="d1f26-173">The contents of the launch.json file are:</span></span>

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

  <span data-ttu-id="d1f26-174">Detta representerar vanliga scenarier för felsökning.</span><span class="sxs-lookup"><span data-stu-id="d1f26-174">This represents the common debug scenarios.</span></span>
  <span data-ttu-id="d1f26-175">Men när du öppnar den här filen i redigeraren kan du se en **Lägg till konfiguration...**  knappen.</span><span class="sxs-lookup"><span data-stu-id="d1f26-175">However, when you open this file in the editor, you see an **Add Configuration...** button.</span></span>
  <span data-ttu-id="d1f26-176">Du kan trycka på knappen för att lägga till fler konfigurationer för felsökning av PowerShell.</span><span class="sxs-lookup"><span data-stu-id="d1f26-176">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="d1f26-177">En praktisk konfiguration för att lägga till är **PowerShell: starta skriptet**.</span><span class="sxs-lookup"><span data-stu-id="d1f26-177">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
  <span data-ttu-id="d1f26-178">Med den här konfigurationen kan du ange en viss fil med valfria argument som ska startas varje gång du trycker på F5 oavsett vilken fil som är aktiva i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="d1f26-178">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

  <span data-ttu-id="d1f26-179">När debug-konfigurationen har upprättats kan du välja vilken konfiguration som du vill använda under en felsökningssession genom att välja en från debug konfigurationen listrutan i den **felsöka** vyns verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="d1f26-179">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="d1f26-180">Det finns några bloggar som hjälper dig att komma igång med hjälp av PowerShell-tillägget för Visual Studio Code:</span><span class="sxs-lookup"><span data-stu-id="d1f26-180">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code:</span></span>

- <span data-ttu-id="d1f26-181">[PowerShell-tillägget][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="d1f26-181">[PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="d1f26-182">[Skriv och Felsök PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="d1f26-182">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="d1f26-183">[Felsökning av Visual Studio Code-vägledning][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="d1f26-183">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="d1f26-184">[Felsökning av PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="d1f26-184">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="d1f26-185">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="d1f26-185">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="d1f26-186">[Visual Studio Code redigeringsfunktioner för PowerShell-utveckling – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="d1f26-186">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="d1f26-187">[Visual Studio Code redigeringsfunktioner för PowerShell-utveckling – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="d1f26-187">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="d1f26-188">[Felsökning av PowerShell-skriptet i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="d1f26-188">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="d1f26-189">[Felsökning av PowerShell-skriptet i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="d1f26-189">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
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

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="d1f26-190">PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="d1f26-190">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="d1f26-191">Tillägget PowerShell källkoden finns på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="d1f26-191">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>
