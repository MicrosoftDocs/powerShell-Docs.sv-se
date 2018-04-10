# <a name="using-visual-studio-code-for-powershell-development"></a><span data-ttu-id="5a205-101">Med Visual Studio-koden för PowerShell-utveckling</span><span class="sxs-lookup"><span data-stu-id="5a205-101">Using Visual Studio Code for PowerShell Development</span></span>

<span data-ttu-id="5a205-102">Förutom den [PowerShell ISE][ise], PowerShell är också väl stöds i Visual Studio-koden.</span><span class="sxs-lookup"><span data-stu-id="5a205-102">In addition to the [PowerShell ISE][ise], PowerShell is also well-supported in Visual Studio Code.</span></span>
<span data-ttu-id="5a205-103">Dessutom stöds av ISE inte med PowerShell Core när Visual Studio Code stöds för PowerShell Core på alla plattformar (Windows, macOS och Linux)</span><span class="sxs-lookup"><span data-stu-id="5a205-103">Furthermore, the ISE is not supported with PowerShell Core, while Visual Studio Code is supported for PowerShell Core on all platforms (Windows, macOS, and Linux)</span></span>

<span data-ttu-id="5a205-104">Du kan använda Visual Studio-koden i Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) för äldre Windows-operativsystem (t.ex. Windows 8.1, etc.).</span><span class="sxs-lookup"><span data-stu-id="5a205-104">You can use Visual Studio Code on Windows with PowerShell version 5 by using Windows 10 or by installing [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) for down-level Windows OSs (e.g. Windows 8.1, etc.).</span></span>

<span data-ttu-id="5a205-105">Kontrollera att PowerShell finns i systemet innan du startar den.</span><span class="sxs-lookup"><span data-stu-id="5a205-105">Before starting it, please make sure PowerShell exists on your system.</span></span>
<span data-ttu-id="5a205-106">Moderna arbetsbelastningar på Windows och macOS Linux finns:</span><span class="sxs-lookup"><span data-stu-id="5a205-106">For modern workloads on Windows, macOS, and Linux, see:</span></span>

- <span data-ttu-id="5a205-107">[Installera PowerShell Core på macOS- och Linux][install-pscore-linux]</span><span class="sxs-lookup"><span data-stu-id="5a205-107">[Installing PowerShell Core on macOS and Linux][install-pscore-linux]</span></span>
- <span data-ttu-id="5a205-108">[Installera PowerShell Core i Windows][install-pscore-windows]</span><span class="sxs-lookup"><span data-stu-id="5a205-108">[Installing PowerShell Core on Windows][install-pscore-windows]</span></span>

<span data-ttu-id="5a205-109">Traditionella arbetsbelastningar i Windows PowerShell, se [installera Windows PowerShell][install-winps].</span><span class="sxs-lookup"><span data-stu-id="5a205-109">For traditional Windows PowerShell workloads, see [Installing Windows PowerShell][install-winps].</span></span>

## <a name="editing-with-visual-studio-code"></a><span data-ttu-id="5a205-110">Redigera med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-110">Editing with Visual Studio Code</span></span>

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[<span data-ttu-id="5a205-111">1. Installera Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-111">1. Installing Visual Studio Code</span></span>](https://code.visualstudio.com/Docs/setup/setup-overview)

- <span data-ttu-id="5a205-112">**Linux**: Följ installationsanvisningarna den [VS köra kod i Linux](https://code.visualstudio.com/docs/setup/linux) sidan</span><span class="sxs-lookup"><span data-stu-id="5a205-112">**Linux**: follow the installation instructions on the [Running VS Code on Linux](https://code.visualstudio.com/docs/setup/linux) page</span></span>

- <span data-ttu-id="5a205-113">**macOS**: Följ installationsanvisningarna den [VS köra kod i macOS](https://code.visualstudio.com/docs/setup/mac) sidan</span><span class="sxs-lookup"><span data-stu-id="5a205-113">**macOS**: follow the installation instructions on the [Running VS Code on macOS](https://code.visualstudio.com/docs/setup/mac) page</span></span>

> [!IMPORTANT]
> <span data-ttu-id="5a205-114">I macOS, måste du installera OpenSSL för PowerShell-tillägget ska fungera korrekt.</span><span class="sxs-lookup"><span data-stu-id="5a205-114">On macOS, you must install OpenSSL for the PowerShell extension to work correctly.</span></span>
> <span data-ttu-id="5a205-115">Det enklaste sättet att göra detta är att installera [Homebrew](http://brew.sh/) och kör sedan `brew install openssl`.</span><span class="sxs-lookup"><span data-stu-id="5a205-115">The easiest way to accomplish this is to install [Homebrew](http://brew.sh/) and then run `brew install openssl`.</span></span>
> <span data-ttu-id="5a205-116">PowerShell-tillägget ska nu kunna läsas in.</span><span class="sxs-lookup"><span data-stu-id="5a205-116">The PowerShell extension will now be able to load successfully.</span></span>

- <span data-ttu-id="5a205-117">**Windows**: Följ installationsanvisningarna den [VS köra kod på Windows](https://code.visualstudio.com/docs/setup/windows) sidan</span><span class="sxs-lookup"><span data-stu-id="5a205-117">**Windows**: follow the installation instructions on the [Running VS Code on Windows](https://code.visualstudio.com/docs/setup/windows) page</span></span>

### <a name="2-installing-powershell-extension"></a><span data-ttu-id="5a205-118">2. Installera PowerShell-tillägg</span><span class="sxs-lookup"><span data-stu-id="5a205-118">2. Installing PowerShell Extension</span></span>

- <span data-ttu-id="5a205-119">Starta Visual Studio Code appen genom att:</span><span class="sxs-lookup"><span data-stu-id="5a205-119">Launch the Visual Studio Code app by:</span></span>
    - <span data-ttu-id="5a205-120">**Windows**: att skriva `code` i PowerShell-sessionen</span><span class="sxs-lookup"><span data-stu-id="5a205-120">**Windows**: typing `code` in your PowerShell session</span></span>
    - <span data-ttu-id="5a205-121">**Linux**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="5a205-121">**Linux**: typing `code` in your terminal</span></span>
    - <span data-ttu-id="5a205-122">**macOS**: att skriva `code` i terminalen</span><span class="sxs-lookup"><span data-stu-id="5a205-122">**macOS**: typing `code` in your terminal</span></span>

- <span data-ttu-id="5a205-123">Starta **snabbt öppna** genom att trycka på **Ctrl + P** (**Cmd + P** på Mac).</span><span class="sxs-lookup"><span data-stu-id="5a205-123">Launch **Quick Open** by pressing **Ctrl+P** (**Cmd+P** on Mac).</span></span>
- <span data-ttu-id="5a205-124">Snabb Skriv `ext install powershell` och träffar **RETUR**.</span><span class="sxs-lookup"><span data-stu-id="5a205-124">In Quick Open, type `ext install powershell` and hit **Enter**.</span></span>
- <span data-ttu-id="5a205-125">Den **tillägg** vyn öppnas på på sidorutan.</span><span class="sxs-lookup"><span data-stu-id="5a205-125">The **Extensions** view will open on the Side Bar.</span></span> <span data-ttu-id="5a205-126">Välj PowerShell-tillägg från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a205-126">Select the PowerShell extension from Microsoft.</span></span>
  <span data-ttu-id="5a205-127">Du ser något som nedan:</span><span class="sxs-lookup"><span data-stu-id="5a205-127">You will see something like below:</span></span>

  ![VSCode](../../images/vscode.png)

- <span data-ttu-id="5a205-129">Klicka på den **installera** knappen på PowerShell-tillägg från Microsoft.</span><span class="sxs-lookup"><span data-stu-id="5a205-129">Click the **Install** button on the PowerShell extension from Microsoft.</span></span>
- <span data-ttu-id="5a205-130">Efter installationen visas den **installera** knappen övergår i **ladda**.</span><span class="sxs-lookup"><span data-stu-id="5a205-130">After the install, you will see the **Install** button turns to **Reload**.</span></span>
  <span data-ttu-id="5a205-131">Klicka på **ladda**.</span><span class="sxs-lookup"><span data-stu-id="5a205-131">Click on **Reload**.</span></span>
- <span data-ttu-id="5a205-132">När Visual Studio-koden har ladda, är du redo för redigering.</span><span class="sxs-lookup"><span data-stu-id="5a205-132">After Visual Studio Code has reload, you are ready for editing.</span></span>

<span data-ttu-id="5a205-133">Klicka till exempel om du vill skapa en ny fil **Arkiv -> Ny**.</span><span class="sxs-lookup"><span data-stu-id="5a205-133">For example, to create a new file, click **File->New**.</span></span>
<span data-ttu-id="5a205-134">Om du vill spara den, klickar du på **Arkiv -> Spara** och ange sedan ett filnamn, låt oss säga `HelloWorld.ps1`.</span><span class="sxs-lookup"><span data-stu-id="5a205-134">To save it, click **File->Save** and then provide a file name, let's say `HelloWorld.ps1`.</span></span>
<span data-ttu-id="5a205-135">Stäng filen genom att klicka på ”x” bredvid namnet på filen.</span><span class="sxs-lookup"><span data-stu-id="5a205-135">To close the file, click on "x" next to the file name.</span></span>
<span data-ttu-id="5a205-136">Avsluta Visual Studio Code **Arkiv -> Avsluta**.</span><span class="sxs-lookup"><span data-stu-id="5a205-136">To exit Visual Studio Code, **File->Exit**.</span></span>

#### <a name="using-a-specific-installed-version-of-powershell"></a><span data-ttu-id="5a205-137">Med hjälp av en viss version av PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a205-137">Using a specific installed version of PowerShell</span></span>

<span data-ttu-id="5a205-138">Om du vill använda en specifik installation av PowerShell med Visual Studio Code behöver du lägga till en ny variabel i filen med inställningar.</span><span class="sxs-lookup"><span data-stu-id="5a205-138">If you wish to use a specific installation of PowerShell with Visual Studio Code, you will need to add a new variable to your user settings file.</span></span>

1. <span data-ttu-id="5a205-139">Klicka på **Arkiv -> Inställningar -> Inställningar**</span><span class="sxs-lookup"><span data-stu-id="5a205-139">Click **File -> Preferences -> Settings**</span></span>
1. <span data-ttu-id="5a205-140">Två editor fönster visas.</span><span class="sxs-lookup"><span data-stu-id="5a205-140">Two editor panes will appear.</span></span>
   <span data-ttu-id="5a205-141">I rutan längst till höger (`settings.json`), infoga inställningen nedan lämpliga för ditt operativsystem någonstans mellan två klammerparenteser (`{` och `}`) och Ersätt *<version>* med den installerade PowerShell-version:</span><span class="sxs-lookup"><span data-stu-id="5a205-141">In the right-most pane (`settings.json`), insert the setting below appropriate for your OS somewhere between the two curly brackets (`{` and `}`) and replace *<version>* with the installed PowerShell version:</span></span>

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. <span data-ttu-id="5a205-142">Ersätt inställningen med sökvägen till den önskade PowerShell körbar</span><span class="sxs-lookup"><span data-stu-id="5a205-142">Replace the setting with the path to the desired PowerShell executable</span></span>
1. <span data-ttu-id="5a205-143">Spara filen och starta om Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-143">Save the settings file and restart Visual Studio Code</span></span>

#### <a name="configuration-settings-for-visual-studio-code"></a><span data-ttu-id="5a205-144">Konfigurationsinställningar för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-144">Configuration settings for Visual Studio Code</span></span>

<span data-ttu-id="5a205-145">Med hjälp av stegen i föregående stycke kan du lägga till konfigurationsinställningar i `settings.json`.</span><span class="sxs-lookup"><span data-stu-id="5a205-145">By using the steps in the previous paragraph you can add configuration settings in `settings.json`.</span></span>

<span data-ttu-id="5a205-146">Vi rekommenderar följande konfigurationsinställningar för Visual Studio-koden:</span><span class="sxs-lookup"><span data-stu-id="5a205-146">We recommend the following configuration settings for Visual Studio Code:</span></span>

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a><span data-ttu-id="5a205-147">Felsökning med Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-147">Debugging with Visual Studio Code</span></span>

### <a name="no-workspace-debugging"></a><span data-ttu-id="5a205-148">Ingen arbetsyta felsökning</span><span class="sxs-lookup"><span data-stu-id="5a205-148">No-workspace debugging</span></span>

<span data-ttu-id="5a205-149">Du kan felsöka PowerShell-skript utan att öppna den mapp som innehåller PowerShell-skriptet från och med version av Visual Studio Code 1.9.</span><span class="sxs-lookup"><span data-stu-id="5a205-149">As of Visual Studio Code version 1.9 you can debug PowerShell scripts without having to open the folder containing the PowerShell script.</span></span>
<span data-ttu-id="5a205-150">Öppnar den PowerShell-skript med **Arkiv -> Öppna fil...** , ange en brytpunkt på en rad (tryck på F9) och tryck på F5 för att starta felsökningen.</span><span class="sxs-lookup"><span data-stu-id="5a205-150">Simply open the PowerShell script file with **File->Open File...**, set a breakpoint on a line (press F9) and then press F5 to start debugging.</span></span>
<span data-ttu-id="5a205-151">Felsök åtgärdsfönstret visas där du vill starta felsökningsprogrammet, steg, fortsätta och stoppa felsökning visas.</span><span class="sxs-lookup"><span data-stu-id="5a205-151">You will see the Debug actions pane appear which allows you to break into the debugger, step, resume and stop debugging.</span></span>

### <a name="workspace-debugging"></a><span data-ttu-id="5a205-152">Arbetsytan felsökning</span><span class="sxs-lookup"><span data-stu-id="5a205-152">Workspace debugging</span></span>

<span data-ttu-id="5a205-153">Arbetsytan felsökning refererar till felsökning i kontexten för en mapp som du har öppnat i Visual Studio Code med **öppna mappen...**  från den **filen** menyn.</span><span class="sxs-lookup"><span data-stu-id="5a205-153">Workspace debugging refers to debugging in the context of a folder that you have opened in Visual Studio Code using **Open Folder...** from the **File** menu.</span></span>
<span data-ttu-id="5a205-154">Du öppnar mappen är vanligtvis projektmappen PowerShell och/eller roten för Git-lagringsplatsen.</span><span class="sxs-lookup"><span data-stu-id="5a205-154">The folder you open is typically your PowerShell project folder and/or the root of your Git repository.</span></span>

<span data-ttu-id="5a205-155">Även i detta läge kan starta du felsökning markerade PowerShell-skriptet genom att bara trycka på F5.</span><span class="sxs-lookup"><span data-stu-id="5a205-155">Even in this mode, you can start debugging the currently selected PowerShell script by simply pressing F5.</span></span>
<span data-ttu-id="5a205-156">Dock kan arbetsytan felsökning du definiera flera debug konfigurationer än bara felsökning filen är öppen.</span><span class="sxs-lookup"><span data-stu-id="5a205-156">However, workspace debugging allows you to define multiple debug configurations other than just debugging the currently open file.</span></span>
<span data-ttu-id="5a205-157">Exempelvis kan du lägga till en konfigurationer för att:</span><span class="sxs-lookup"><span data-stu-id="5a205-157">For instance, you can add a configurations to:</span></span>

- <span data-ttu-id="5a205-158">Starta Pester tester i Felsökning</span><span class="sxs-lookup"><span data-stu-id="5a205-158">Launch Pester tests in the debugger</span></span>
- <span data-ttu-id="5a205-159">Starta en viss fil med argumenten i Felsökning</span><span class="sxs-lookup"><span data-stu-id="5a205-159">Launch a specific file with arguments in the debugger</span></span>
- <span data-ttu-id="5a205-160">Starta en interaktiv session i Felsökning</span><span class="sxs-lookup"><span data-stu-id="5a205-160">Launch an interactive session in the debugger</span></span>
- <span data-ttu-id="5a205-161">Koppla felsökaren till en värdprocess för PowerShell</span><span class="sxs-lookup"><span data-stu-id="5a205-161">Attach the debugger to a PowerShell host process</span></span>

<span data-ttu-id="5a205-162">Följ dessa steg för att skapa konfigurationsfilen debug:</span><span class="sxs-lookup"><span data-stu-id="5a205-162">Follow these steps to create your debug configuration file:</span></span>

1. <span data-ttu-id="5a205-163">Öppna den **felsöka** vyn genom att trycka på **Ctrl + Skift + D** (**Cmd + SKIFT + D** på Mac).</span><span class="sxs-lookup"><span data-stu-id="5a205-163">Open the **Debug** view by pressing **Ctrl+Shift+D** (**Cmd+Shift+D** on Mac).</span></span>
1. <span data-ttu-id="5a205-164">Tryck på den **konfigurera** växeln-ikonen i verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="5a205-164">Press the **Configure** gear icon in the toolbar.</span></span>
1. <span data-ttu-id="5a205-165">Visual Studio Code uppmanas du att **Välj miljö**.</span><span class="sxs-lookup"><span data-stu-id="5a205-165">Visual Studio Code will prompt you to **Select Environment**.</span></span>
   <span data-ttu-id="5a205-166">Välj **PowerShell**.</span><span class="sxs-lookup"><span data-stu-id="5a205-166">Choose **PowerShell**.</span></span>

   <span data-ttu-id="5a205-167">När du gör detta skapar en katalog och en fil ”.vscode\launch.json” i roten på arbetsytemappen för Visual Studio-koden.</span><span class="sxs-lookup"><span data-stu-id="5a205-167">When you do this, Visual Studio Code creates a directory and a file ".vscode\launch.json" in the root of your workspace folder.</span></span>
   <span data-ttu-id="5a205-168">Här sparas där debug-konfiguration.</span><span class="sxs-lookup"><span data-stu-id="5a205-168">This is where your debug configuration is stored.</span></span> <span data-ttu-id="5a205-169">Om filerna finns i en Git-lagringsplats, vill du förmodligen att genomföra launch.json-filen.</span><span class="sxs-lookup"><span data-stu-id="5a205-169">If your files are in a Git repository, you will typically want to commit the launch.json file.</span></span>
   <span data-ttu-id="5a205-170">Innehållet i filen launch.json är:</span><span class="sxs-lookup"><span data-stu-id="5a205-170">The contents of the launch.json file are:</span></span>

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

<span data-ttu-id="5a205-171">Detta representerar vanliga scenarier för felsökning.</span><span class="sxs-lookup"><span data-stu-id="5a205-171">This represents the common debug scenarios.</span></span>
<span data-ttu-id="5a205-172">Men när du öppnar den här filen i redigeraren, visas en **Lägg till konfiguration...**  knappen.</span><span class="sxs-lookup"><span data-stu-id="5a205-172">However, when you open this file in the editor, you will see an **Add Configuration...** button.</span></span>
<span data-ttu-id="5a205-173">Du kan trycka på knappen för att lägga till flera PowerShell debug-konfigurationer.</span><span class="sxs-lookup"><span data-stu-id="5a205-173">You can press this button to add more PowerShell debug configurations.</span></span> <span data-ttu-id="5a205-174">Är en praktisk konfiguration för att lägga till **PowerShell: starta skriptet**.</span><span class="sxs-lookup"><span data-stu-id="5a205-174">One handy configuration to add is **PowerShell: Launch Script**.</span></span>
<span data-ttu-id="5a205-175">Med den här konfigurationen kan du ange en viss fil med valfria argument som ska startas när du trycker på F5 oavsett vilken fil som för närvarande är aktiv i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="5a205-175">With this configuration, you can specify a specific file with optional arguments that should be launched whenever you press F5 no matter which file is currently active in the editor.</span></span>

<span data-ttu-id="5a205-176">När debug-konfigurationen har upprättats kan du välja vilken konfiguration som du vill använda i en debug-session genom att välja ett från debug konfigurationen listrutan i den **felsöka** vyns verktygsfältet.</span><span class="sxs-lookup"><span data-stu-id="5a205-176">Once the debug configuration is established, you can select which configuration you want to use during a debug session by selecting one from the debug configuration drop-down in the **Debug** view's toolbar.</span></span>

<span data-ttu-id="5a205-177">Det finns några bloggar som kan vara till hjälp att komma igång med hjälp av PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-177">There are a few blogs that may be helpful to get you started using PowerShell extension for Visual Studio Code</span></span>

- <span data-ttu-id="5a205-178">Visual Studio-koden: [PowerShell-tillägg][ps-extension]</span><span class="sxs-lookup"><span data-stu-id="5a205-178">Visual Studio Code: [PowerShell Extension][ps-extension]</span></span>
- <span data-ttu-id="5a205-179">[Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]</span><span class="sxs-lookup"><span data-stu-id="5a205-179">[Write and debug PowerShell scripts in Visual Studio Code][debug]</span></span>
- <span data-ttu-id="5a205-180">[Riktlinjer för felsökning Visual Studio Code][vscode-guide]</span><span class="sxs-lookup"><span data-stu-id="5a205-180">[Debugging Visual Studio Code Guidance][vscode-guide]</span></span>
- <span data-ttu-id="5a205-181">[Felsökning PowerShell i Visual Studio Code][ps-vscode]</span><span class="sxs-lookup"><span data-stu-id="5a205-181">[Debugging PowerShell in Visual Studio Code][ps-vscode]</span></span>
- <span data-ttu-id="5a205-182">[Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]</span><span class="sxs-lookup"><span data-stu-id="5a205-182">[Get started with PowerShell development in Visual Studio Code][getting-started]</span></span>
- <span data-ttu-id="5a205-183">[Visual Studio Code redigera funktioner för utveckling av PowerShell – del 1][editing-part1]</span><span class="sxs-lookup"><span data-stu-id="5a205-183">[Visual Studio Code editing features for PowerShell development – Part 1][editing-part1]</span></span>
- <span data-ttu-id="5a205-184">[Visual Studio Code redigera funktioner för utveckling av PowerShell – del 2][editing-part2]</span><span class="sxs-lookup"><span data-stu-id="5a205-184">[Visual Studio Code editing features for PowerShell development – Part 2][editing-part2]</span></span>
- <span data-ttu-id="5a205-185">[Felsökning av PowerShell-skript i Visual Studio Code – del 1][debugging-part1]</span><span class="sxs-lookup"><span data-stu-id="5a205-185">[Debugging PowerShell script in Visual Studio Code – Part 1][debugging-part1]</span></span>
- <span data-ttu-id="5a205-186">[Felsökning av PowerShell-skript i Visual Studio Code – del 2][debugging-part2]</span><span class="sxs-lookup"><span data-stu-id="5a205-186">[Debugging PowerShell script in Visual Studio Code – Part 2][debugging-part2]</span></span>

[ise]: ../ise-guide.md
[install-pscore-linux]:  ../../setup/Installing-PowerShell-Core-on-macOS-and-Linux.md
[install-pscore-windows]: ../../setup/Installing-PowerShell-Core-on-Windows.md
[install-winps]: ../../setup/Installing-Windows-PowerShell.md
[ps-extension]:https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/
[debug]:https://blogs.msdn.microsoft.com/powershell/2015/11/16/announcing-powershell-language-support-for-visual-studio-code-and-more/
[vscode-guide]:https://johnpapa.net/debugging-with-visual-studio-code/
[ps-vscode]:https://github.com/PowerShell/vscode-powershell/tree/master/examples
[getting-started]:https://blogs.technet.microsoft.com/heyscriptingguy/2016/12/05/get-started-with-powershell-development-in-visual-studio-code/
[editing-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/11/visual-studio-code-editing-features-for-powershell-development-part-1/
[editing-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/01/12/visual-studio-code-editing-features-for-powershell-development-part-2/
[debugging-part1]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/06/debugging-powershell-script-in-visual-studio-code-part-1/
[debugging-part2]:https://blogs.technet.microsoft.com/heyscriptingguy/2017/02/13/debugging-powershell-script-in-visual-studio-code-part-2/

## <a name="powershell-extension-for-visual-studio-code"></a><span data-ttu-id="5a205-187">PowerShell-tillägget för Visual Studio Code</span><span class="sxs-lookup"><span data-stu-id="5a205-187">PowerShell Extension for Visual Studio Code</span></span>

<span data-ttu-id="5a205-188">Källkoden för PowerShell-tillägg finns på [GitHub](https://github.com/PowerShell/vscode-powershell).</span><span class="sxs-lookup"><span data-stu-id="5a205-188">The PowerShell extension's source code can be found on [GitHub](https://github.com/PowerShell/vscode-powershell).</span></span>