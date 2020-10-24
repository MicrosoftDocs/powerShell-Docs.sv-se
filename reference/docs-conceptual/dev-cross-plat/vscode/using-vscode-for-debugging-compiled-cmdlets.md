---
ms.date: 10/19/2020
keywords: PowerShell, cmdlet, debug
title: Använda Visual Studio Code för att felsöka kompilerade cmdletar
description: Så här ställer du in en build-uppgift och startar konfigurationen för ett PSModule-projekt i .NET Core
ms.openlocfilehash: b51a69110c64b386f5c3ccf2527d1e184ef89257
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92501651"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a><span data-ttu-id="9da21-104">Använda Visual Studio Code för att felsöka kompilerade cmdletar</span><span class="sxs-lookup"><span data-stu-id="9da21-104">Using Visual Studio Code to debug compiled cmdlets</span></span>

<span data-ttu-id="9da21-105">Den här guiden visar hur du interaktivt kan felsöka C#-källkod för en kompilerad PowerShell-modul med Visual Studio Code (VS Code) och C#-tillägget.</span><span class="sxs-lookup"><span data-stu-id="9da21-105">This guide shows you how to interactively debug C# source code for a compiled PowerShell module using Visual Studio Code (VS Code) and the C# extension.</span></span>

<span data-ttu-id="9da21-106">En del som är bekant med Visual Studio kod fel sökning antas.</span><span class="sxs-lookup"><span data-stu-id="9da21-106">Some familiarity with the Visual Studio Code debugger is assumed.</span></span>

- <span data-ttu-id="9da21-107">En allmän introduktion till VS Code-felsökaren finns i [fel sökning i Visual Studio Code][].</span><span class="sxs-lookup"><span data-stu-id="9da21-107">For a general introduction to the VS Code debugger, see [Debugging in Visual Studio Code][].</span></span>

- <span data-ttu-id="9da21-108">Exempel på hur du felsöker PowerShell-skriptfiler och moduler finns i [använda Visual Studio Code för fjärran sluten redigering och fel sökning][].</span><span class="sxs-lookup"><span data-stu-id="9da21-108">For examples of debugging PowerShell script files and modules, see [Using Visual Studio Code for remote editing and debugging][].</span></span>

<span data-ttu-id="9da21-109">I den här guiden förutsätter vi att du har läst och följt anvisningarna i guiden [skriva bärbara moduler][] .</span><span class="sxs-lookup"><span data-stu-id="9da21-109">This guide assumes you have read and followed the instructions in the [Writing Portable Modules][] guide.</span></span>

## <a name="creating-a-build-task"></a><span data-ttu-id="9da21-110">Skapa en bygge-uppgift</span><span class="sxs-lookup"><span data-stu-id="9da21-110">Creating a build task</span></span>

<span data-ttu-id="9da21-111">Bygg ditt projekt automatiskt innan du startar en felsökningssession.</span><span class="sxs-lookup"><span data-stu-id="9da21-111">Build your project automatically before launching a debugging session.</span></span> <span data-ttu-id="9da21-112">Återskapande säkerställer att du felsöker den senaste versionen av koden.</span><span class="sxs-lookup"><span data-stu-id="9da21-112">Rebuilding ensures that you debug the latest version of your code.</span></span>

<span data-ttu-id="9da21-113">Konfigurera en versions uppgift:</span><span class="sxs-lookup"><span data-stu-id="9da21-113">Configure a build task:</span></span>

1. <span data-ttu-id="9da21-114">I **paletten kommando**kör du kommandot **Konfigurera standard versions uppgift** .</span><span class="sxs-lookup"><span data-stu-id="9da21-114">In the **Command Palette**, run the **Configure Default Build Task** command.</span></span>

   ![Kör konfigurera standard versions uppgift](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. <span data-ttu-id="9da21-116">I dialog rutan **Välj en aktivitet som ska konfigureras väljer du** **skapa tasks.jspå fil från mall**.</span><span class="sxs-lookup"><span data-stu-id="9da21-116">In the **Select a task to configure** dialog, choose **Create tasks.json file from template**.</span></span>

1. <span data-ttu-id="9da21-117">I dialog rutan **Välj en uppgiftsmall** väljer du **.net Core**.</span><span class="sxs-lookup"><span data-stu-id="9da21-117">In the **Select a Task Template** dialog, choose **.NET Core**.</span></span>

<span data-ttu-id="9da21-118">En ny `tasks.json` fil skapas om det inte finns någon än.</span><span class="sxs-lookup"><span data-stu-id="9da21-118">A new `tasks.json` file is created if one doesn't exist yet.</span></span>

<span data-ttu-id="9da21-119">Så här testar du din versions uppgift:</span><span class="sxs-lookup"><span data-stu-id="9da21-119">To test your build task:</span></span>

1. <span data-ttu-id="9da21-120">I **paletten kommando**kör du kommandot **Kör skapa uppgift** .</span><span class="sxs-lookup"><span data-stu-id="9da21-120">In the **Command Palette**, run the **Run Build Task** command.</span></span>

1. <span data-ttu-id="9da21-121">I dialog rutan **Välj Bygg uppgift att köra** väljer du **skapa**.</span><span class="sxs-lookup"><span data-stu-id="9da21-121">In the **Select the build task to run** dialog, choose **build**.</span></span>

### <a name="information-about-dll-files-being-locked"></a><span data-ttu-id="9da21-122">Information om DLL-filer som låses</span><span class="sxs-lookup"><span data-stu-id="9da21-122">Information about DLL files being locked</span></span>

<span data-ttu-id="9da21-123">Som standard visar en lyckad version inte utdata i terminalfönstret.</span><span class="sxs-lookup"><span data-stu-id="9da21-123">By default, a successful build doesn't show output in the terminal pane.</span></span> <span data-ttu-id="9da21-124">Om det inte finns några utdata som innehåller text **projekt filen**bör du redigera `tasks.json` filen.</span><span class="sxs-lookup"><span data-stu-id="9da21-124">If you see output that contains the text **Project file doesn't exist**, you should edit the `tasks.json` file.</span></span> <span data-ttu-id="9da21-125">Inkludera den explicita sökvägen till C#-projektet uttryckt som `"${workspaceFolder}/myModule"` .</span><span class="sxs-lookup"><span data-stu-id="9da21-125">Include the explicit path to the C# project expressed as `"${workspaceFolder}/myModule"`.</span></span> <span data-ttu-id="9da21-126">I det här exemplet `myModule` är namnet på projektmappen.</span><span class="sxs-lookup"><span data-stu-id="9da21-126">In this example, `myModule` is the name of the project folder.</span></span> <span data-ttu-id="9da21-127">Posten måste gå efter `build` posten i `args` listan enligt följande:</span><span class="sxs-lookup"><span data-stu-id="9da21-127">This entry must go after the `build` entry in the `args` list as follows:</span></span>

```json
    {
        "label": "build",
        "command": "dotnet",
        "type": "shell",
        "args": [
            "build",
            "${workspaceFolder}/myModule",
            // Ask dotnet build to generate full paths for file names.
            "/property:GenerateFullPaths=true",
            // Do not generate summary otherwise it leads to duplicate errors in Problems panel
            "/consoleloggerparameters:NoSummary",
        ],
        "group": "build",
        "presentation": {
            "reveal": "silent"
        },
        "problemMatcher": "$msCompile"
    }
```

<span data-ttu-id="9da21-128">Vid fel sökning importeras din modul-DLL till PowerShell-sessionen i VS Code Terminal.</span><span class="sxs-lookup"><span data-stu-id="9da21-128">When debugging, your module DLL is imported into the PowerShell session in the VS Code terminal.</span></span> <span data-ttu-id="9da21-129">DLL-filen blir låst.</span><span class="sxs-lookup"><span data-stu-id="9da21-129">The DLL becomes locked.</span></span> <span data-ttu-id="9da21-130">Följande meddelande visas när du kör åtgärden Skapa utan att stänga terminalfönstret:</span><span class="sxs-lookup"><span data-stu-id="9da21-130">The following message is displayed when you run the build task without closing the terminal session:</span></span>

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

<span data-ttu-id="9da21-131">Terminal-sessioner måste stängas innan du återskapar.</span><span class="sxs-lookup"><span data-stu-id="9da21-131">Terminal sessions must be closed before you rebuild.</span></span>

## <a name="setting-up-the-debugger"></a><span data-ttu-id="9da21-132">Konfigurera fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="9da21-132">Setting up the debugger</span></span>

<span data-ttu-id="9da21-133">Om du vill felsöka PowerShell-cmdleten måste du konfigurera en anpassad start konfiguration.</span><span class="sxs-lookup"><span data-stu-id="9da21-133">To debug the PowerShell cmdlet, you need to set up a custom launch configuration.</span></span> <span data-ttu-id="9da21-134">Den här konfigurationen används för att:</span><span class="sxs-lookup"><span data-stu-id="9da21-134">This configuration is used to:</span></span>

- <span data-ttu-id="9da21-135">Bygg din käll kod</span><span class="sxs-lookup"><span data-stu-id="9da21-135">Build your source code</span></span>
- <span data-ttu-id="9da21-136">Starta PowerShell med modulen inläst</span><span class="sxs-lookup"><span data-stu-id="9da21-136">Start PowerShell with your module loaded</span></span>
- <span data-ttu-id="9da21-137">Lämna PowerShell öppen i terminalfönstret</span><span class="sxs-lookup"><span data-stu-id="9da21-137">Leave PowerShell open in the terminal pane</span></span>

<span data-ttu-id="9da21-138">När du anropar din cmdlet i terminalsession stoppas fel söknings programmet vid eventuella Bryt punkter som anges i käll koden.</span><span class="sxs-lookup"><span data-stu-id="9da21-138">When you invoke your cmdlet in the terminal session, the debugger stops at any breakpoints set in your source code.</span></span>

### <a name="configuring-launchjson-for-powershell-core"></a><span data-ttu-id="9da21-139">Konfigurera launch.jspå för PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="9da21-139">Configuring launch.json for PowerShell Core</span></span>

1. <span data-ttu-id="9da21-140">Installera [C# för kod tillägget för Visual Studio][]</span><span class="sxs-lookup"><span data-stu-id="9da21-140">Install the [C# for Visual Studio Code][] extension</span></span>

1. <span data-ttu-id="9da21-141">I fel söknings fönstret lägger du till en fel söknings konfiguration</span><span class="sxs-lookup"><span data-stu-id="9da21-141">In the Debug pane, add a debug configuration</span></span>

1. <span data-ttu-id="9da21-142">I `Select environment` dialog rutan väljer du `.NET Core`</span><span class="sxs-lookup"><span data-stu-id="9da21-142">In the `Select environment` dialog, choose `.NET Core`</span></span>

1. <span data-ttu-id="9da21-143">`launch.json`Filen öppnas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="9da21-143">The `launch.json` file is opened in the editor.</span></span> <span data-ttu-id="9da21-144">Med markören inuti `configurations` matrisen visas `configuration` väljaren.</span><span class="sxs-lookup"><span data-stu-id="9da21-144">With your cursor inside the `configurations` array, you see the `configuration` picker.</span></span> <span data-ttu-id="9da21-145">Om du inte ser den här listan väljer du **Lägg till konfiguration**.</span><span class="sxs-lookup"><span data-stu-id="9da21-145">If you don't see this list, select **Add Configuration**.</span></span>

1. <span data-ttu-id="9da21-146">Om du vill skapa en standard fel söknings konfiguration väljer du **starta .net Core-konsol program**:</span><span class="sxs-lookup"><span data-stu-id="9da21-146">To create a default debug configuration, select **Launch .NET Core Console App**:</span></span>

   ![Starta .NET Core Console-appen](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. <span data-ttu-id="9da21-148">Redigera `name` fälten, `program` , `args` och `console` enligt följande:</span><span class="sxs-lookup"><span data-stu-id="9da21-148">Edit the `name`, `program`, `args`, and `console` fields as follows:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: pwsh",
        "type": "coreclr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "pwsh",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

<span data-ttu-id="9da21-149">`program`Fältet används för att starta `pwsh` så att cmdleten som felsöks kan köras.</span><span class="sxs-lookup"><span data-stu-id="9da21-149">The `program` field is used to launch `pwsh` so that the cmdlet being debugged can be run.</span></span> <span data-ttu-id="9da21-150">`-NoExit`Argumentet förhindrar att PowerShell-sessionen avslutas så fort modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="9da21-150">The `-NoExit` argument prevents the PowerShell session from exiting as soon as the module is imported.</span></span>
<span data-ttu-id="9da21-151">Sökvägen i `Import-Module` argumentet är standard för att bygga ut en sökväg när du har följt guiden [skriva portabla moduler][] .</span><span class="sxs-lookup"><span data-stu-id="9da21-151">The path in the `Import-Module` argument is the default build output path when you've followed the [Writing Portable Modules][] guide.</span></span> <span data-ttu-id="9da21-152">Om du har skapat ett modul manifest ( `.psd1` fil) bör du använda sökvägen till den i stället.</span><span class="sxs-lookup"><span data-stu-id="9da21-152">If you've created a module manifest (`.psd1` file), you should use the path to that instead.</span></span> <span data-ttu-id="9da21-153">`/`Sök vägs avgränsaren fungerar på Windows, Linux och MacOS.</span><span class="sxs-lookup"><span data-stu-id="9da21-153">The `/` path separator works on Windows, Linux, and macOS.</span></span> <span data-ttu-id="9da21-154">Du måste använda den integrerade terminalen för att köra de PowerShell-kommandon som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="9da21-154">You must use the integrated terminal to run the PowerShell commands you want to debug.</span></span>

> [!NOTE]
> <span data-ttu-id="9da21-155">Om fel söknings programmet inte slutar vid några Bryt punkter, tittar du på fel söknings konsolen i Visual Studio Code för en rad med texten:</span><span class="sxs-lookup"><span data-stu-id="9da21-155">If the debugger doesn't stop at any breakpoints, look in the Visual Studio Code Debug Console for a line that says:</span></span>
>
> ```
> Loaded '/path/to/myModule.dll'. Skipped loading symbols. Module is optimized and the debugger option 'Just My Code' is enabled.
> ```
>
> <span data-ttu-id="9da21-156">Om du ser detta lägger du till `"justMyCode": false` i Start konfigurationen (på samma nivå som `"console": "integratedTerminal"` .</span><span class="sxs-lookup"><span data-stu-id="9da21-156">If you see this, add `"justMyCode": false` to your launch config (at the same level as `"console": "integratedTerminal"`.</span></span>

### <a name="configuring-launchjson-for-windows-powershell"></a><span data-ttu-id="9da21-157">Konfigurera launch.jspå för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="9da21-157">Configuring launch.json for Windows PowerShell</span></span>

<span data-ttu-id="9da21-158">Den här start konfigurationen fungerar för att testa dina cmdletar i Windows PowerShell ( `powershell.exe` ).</span><span class="sxs-lookup"><span data-stu-id="9da21-158">This launch configuration works for testing your cmdlets in Windows PowerShell (`powershell.exe`).</span></span>
<span data-ttu-id="9da21-159">Skapa en andra start konfiguration med följande ändringar:</span><span class="sxs-lookup"><span data-stu-id="9da21-159">Create a second launch configuration with the following changes:</span></span>

1. <span data-ttu-id="9da21-160">`name` bör vara `PowerShell cmdlets: powershell`</span><span class="sxs-lookup"><span data-stu-id="9da21-160">`name` should be `PowerShell cmdlets: powershell`</span></span>

1. <span data-ttu-id="9da21-161">`type` bör vara `clr`</span><span class="sxs-lookup"><span data-stu-id="9da21-161">`type` should be `clr`</span></span>

1. <span data-ttu-id="9da21-162">`program` bör vara `powershell`</span><span class="sxs-lookup"><span data-stu-id="9da21-162">`program` should be `powershell`</span></span>

   <span data-ttu-id="9da21-163">Den bör se ut så här:</span><span class="sxs-lookup"><span data-stu-id="9da21-163">It should look like this:</span></span>

   ```json
    {
        "name": "PowerShell cmdlets: powershell",
        "type": "clr",
        "request": "launch",
        "preLaunchTask": "build",
        "program": "powershell",
        "args": [
            "-NoExit",
            "-NoProfile",
            "-Command",
            "Import-Module ${workspaceFolder}/myModule/bin/Debug/netstandard2.0/myModule.dll",
        ],
        "cwd": "${workspaceFolder}",
        "stopAtEntry": false,
        "console": "integratedTerminal"
    }
   ```

## <a name="launching-a-debugging-session"></a><span data-ttu-id="9da21-164">Starta en felsökningssession</span><span class="sxs-lookup"><span data-stu-id="9da21-164">Launching a debugging session</span></span>

<span data-ttu-id="9da21-165">Nu är allt klart för att påbörja fel sökning.</span><span class="sxs-lookup"><span data-stu-id="9da21-165">Now everything is ready to begin debugging.</span></span>

- <span data-ttu-id="9da21-166">Placera en Bryt punkt i käll koden för den cmdlet som du vill felsöka:</span><span class="sxs-lookup"><span data-stu-id="9da21-166">Place a breakpoint in the source code for the cmdlet you want to debug:</span></span>

  ![En Bryt punkt visas som en röd prick i fästmarginal](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- <span data-ttu-id="9da21-168">Se till att den relevanta **PowerShell-cmdlets** -konfigurationen är vald i list rutan konfiguration i vyn **fel sökning** :</span><span class="sxs-lookup"><span data-stu-id="9da21-168">Ensure that the relevant **PowerShell cmdlets** configuration is selected in the configuration drop-down menu in the **Debug** view:</span></span>

  ![Välj Starta konfigurationen](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <span data-ttu-id="9da21-170">Tryck på <kbd>F5</kbd> eller klicka på knappen **Starta fel sökning**</span><span class="sxs-lookup"><span data-stu-id="9da21-170">Press <kbd>F5</kbd> or click on the **Start Debugging** button</span></span>

- <span data-ttu-id="9da21-171">Växla till terminalfönstret och anropa din cmdlet:</span><span class="sxs-lookup"><span data-stu-id="9da21-171">Switch to the terminal pane and invoke your cmdlet:</span></span>

  ![Anropa cmdleten](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- <span data-ttu-id="9da21-173">Körningen stoppas vid Bryt punkten:</span><span class="sxs-lookup"><span data-stu-id="9da21-173">Execution stops at the breakpoint:</span></span>

  ![Körningar stannar vid Bryt punkten](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

<span data-ttu-id="9da21-175">Du kan gå igenom käll koden, granska variabler och granska anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="9da21-175">You can step through the source code, inspect variables, and inspect the call stack.</span></span>

<span data-ttu-id="9da21-176">Avsluta fel sökningen genom att klicka på **stoppa** i fel söknings verktygsfältet eller trycka på <kbd>SKIFT</kbd> - <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="9da21-176">To end debugging, click **Stop** in the debug toolbar or press <kbd>Shift</kbd>-<kbd>F5</kbd>.</span></span> <span data-ttu-id="9da21-177">Gränssnittet som används för fel sökning avslutas och släpper låset på den kompilerade DLL-filen.</span><span class="sxs-lookup"><span data-stu-id="9da21-177">The shell used for debugging exits and releases the lock on the compiled DLL file.</span></span>

<!-- reference links -->
[Fel sökning i Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Debugging in Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Använda Visual Studio Code för att fjärredigera och fjärrfelsöka]: using-vscode-for-remote-editing-and-debugging.md
[Using Visual Studio Code for remote editing and debugging]: using-vscode-for-remote-editing-and-debugging.md
[Skriva portabla moduler]: ../writing-portable-modules.md
[Writing Portable Modules]: ../writing-portable-modules.md
[C# för Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
