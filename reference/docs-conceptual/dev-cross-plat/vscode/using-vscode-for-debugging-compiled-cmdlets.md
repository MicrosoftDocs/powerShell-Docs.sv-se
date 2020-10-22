---
ms.date: 10/19/2020
keywords: PowerShell, cmdlet, debug
title: Använda Visual Studio Code för att felsöka kompilerade cmdletar
description: Så här ställer du in en build-uppgift och startar konfigurationen för ett PSModule-projekt i .NET Core
ms.openlocfilehash: ffae03b1edaf9d5ffa5da6381e301f829c8bc8f7
ms.sourcegitcommit: 57c3527ec6c3124cb9cdab7b07ebb92ed159cb64
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/22/2020
ms.locfileid: "92374230"
---
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a><span data-ttu-id="f1dfd-104">Använda Visual Studio Code för att felsöka kompilerade cmdletar</span><span class="sxs-lookup"><span data-stu-id="f1dfd-104">Using Visual Studio Code to debug compiled cmdlets</span></span>

<span data-ttu-id="f1dfd-105">Den här guiden visar hur du interaktivt kan felsöka C#-källkod för en kompilerad PowerShell-modul med Visual Studio Code (VS Code) och C#-tillägget.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-105">This guide shows you how to interactively debug C# source code for a compiled PowerShell module using Visual Studio Code (VS Code) and the C# extension.</span></span>

<span data-ttu-id="f1dfd-106">En del som är bekant med Visual Studio kod fel sökning antas.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-106">Some familiarity with the Visual Studio Code debugger is assumed.</span></span>

- <span data-ttu-id="f1dfd-107">En allmän introduktion till VS Code-felsökaren finns i [fel sökning i Visual Studio Code][].</span><span class="sxs-lookup"><span data-stu-id="f1dfd-107">For a general introduction to the VS Code debugger, see [Debugging in Visual Studio Code][].</span></span>

- <span data-ttu-id="f1dfd-108">Exempel på hur du felsöker PowerShell-skriptfiler och moduler finns i [använda Visual Studio Code för fjärran sluten redigering och fel sökning][].</span><span class="sxs-lookup"><span data-stu-id="f1dfd-108">For examples of debugging PowerShell script files and modules, see [Using Visual Studio Code for remote editing and debugging][].</span></span>

<span data-ttu-id="f1dfd-109">I den här guiden förutsätter vi att du har läst och följt anvisningarna i guiden [skriva bärbara moduler][] .</span><span class="sxs-lookup"><span data-stu-id="f1dfd-109">This guide assumes you have read and followed the instructions in the [Writing Portable Modules][] guide.</span></span>

## <a name="creating-a-build-task"></a><span data-ttu-id="f1dfd-110">Skapa en bygge-uppgift</span><span class="sxs-lookup"><span data-stu-id="f1dfd-110">Creating a build task</span></span>

<span data-ttu-id="f1dfd-111">Bygg ditt projekt automatiskt innan du startar en felsökningssession.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-111">Build your project automatically before launching a debugging session.</span></span> <span data-ttu-id="f1dfd-112">Återskapande säkerställer att du felsöker den senaste versionen av koden.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-112">Rebuilding ensures that you debug the latest version of your code.</span></span>

<span data-ttu-id="f1dfd-113">Konfigurera en versions uppgift:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-113">Configure a build task:</span></span>

1. <span data-ttu-id="f1dfd-114">I **paletten kommando**kör du kommandot **Konfigurera standard versions uppgift** .</span><span class="sxs-lookup"><span data-stu-id="f1dfd-114">In the **Command Palette**, run the **Configure Default Build Task** command.</span></span>

   ![Kör konfigurera standard versions uppgift](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. <span data-ttu-id="f1dfd-116">I dialog rutan **Välj en aktivitet som ska konfigureras väljer du** **skapa tasks.jspå fil från mall**.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-116">In the **Select a task to configure** dialog, choose **Create tasks.json file from template**.</span></span>

1. <span data-ttu-id="f1dfd-117">I dialog rutan **Välj en uppgiftsmall** väljer du **.net Core**.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-117">In the **Select a Task Template** dialog, choose **.NET Core**.</span></span>

<span data-ttu-id="f1dfd-118">En ny `tasks.json` fil skapas om det inte finns någon än.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-118">A new `tasks.json` file is created if one doesn't exist yet.</span></span>

<span data-ttu-id="f1dfd-119">Så här testar du din versions uppgift:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-119">To test your build task:</span></span>

1. <span data-ttu-id="f1dfd-120">I **paletten kommando**kör du kommandot **Kör skapa uppgift** .</span><span class="sxs-lookup"><span data-stu-id="f1dfd-120">In the **Command Palette**, run the **Run Build Task** command.</span></span>

1. <span data-ttu-id="f1dfd-121">I dialog rutan **Välj Bygg uppgift att köra** väljer du **skapa**.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-121">In the **Select the build task to run** dialog, choose **build**.</span></span>

### <a name="information-about-dll-files-being-locked"></a><span data-ttu-id="f1dfd-122">Information om DLL-filer som låses</span><span class="sxs-lookup"><span data-stu-id="f1dfd-122">Information about DLL files being locked</span></span>

<span data-ttu-id="f1dfd-123">Som standard visar en lyckad version inte utdata i terminalfönstret.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-123">By default, a successful build doesn't show output in the terminal pane.</span></span> <span data-ttu-id="f1dfd-124">Om det inte finns några utdata som innehåller text **projekt filen**bör du redigera `tasks.json` filen.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-124">If you see output that contains the text **Project file doesn't exist**, you should edit the `tasks.json` file.</span></span> <span data-ttu-id="f1dfd-125">Inkludera den explicita sökvägen till C#-projektet uttryckt som `"${workspaceFolder}/myModule"` .</span><span class="sxs-lookup"><span data-stu-id="f1dfd-125">Include the explicit path to the C# project expressed as `"${workspaceFolder}/myModule"`.</span></span> <span data-ttu-id="f1dfd-126">I det här exemplet `myModule` är namnet på projektmappen.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-126">In this example, `myModule` is the name of the project folder.</span></span> <span data-ttu-id="f1dfd-127">Posten måste gå efter `build` posten i `args` listan enligt följande:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-127">This entry must go after the `build` entry in the `args` list as follows:</span></span>

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

<span data-ttu-id="f1dfd-128">Vid fel sökning importeras din modul-DLL till PowerShell-sessionen i VS Code Terminal.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-128">When debugging, your module DLL is imported into the PowerShell session in the VS Code terminal.</span></span> <span data-ttu-id="f1dfd-129">DLL-filen blir låst.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-129">The DLL becomes locked.</span></span> <span data-ttu-id="f1dfd-130">Följande meddelande visas när du kör åtgärden Skapa utan att stänga terminalfönstret:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-130">The following message is displayed when you run the build task without closing the terminal session:</span></span>

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

<span data-ttu-id="f1dfd-131">Terminal-sessioner måste stängas innan du återskapar.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-131">Terminal sessions must be closed before you rebuild.</span></span>

## <a name="setting-up-the-debugger"></a><span data-ttu-id="f1dfd-132">Konfigurera fel söknings programmet</span><span class="sxs-lookup"><span data-stu-id="f1dfd-132">Setting up the debugger</span></span>

<span data-ttu-id="f1dfd-133">Om du vill felsöka PowerShell-cmdleten måste du konfigurera en anpassad start konfiguration.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-133">To debug the PowerShell cmdlet, you need to set up a custom launch configuration.</span></span> <span data-ttu-id="f1dfd-134">Den här konfigurationen används för att:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-134">This configuration is used to:</span></span>

- <span data-ttu-id="f1dfd-135">Bygg din käll kod</span><span class="sxs-lookup"><span data-stu-id="f1dfd-135">Build your source code</span></span>
- <span data-ttu-id="f1dfd-136">Starta PowerShell med modulen inläst</span><span class="sxs-lookup"><span data-stu-id="f1dfd-136">Start PowerShell with your module loaded</span></span>
- <span data-ttu-id="f1dfd-137">Lämna PowerShell öppen i terminalfönstret</span><span class="sxs-lookup"><span data-stu-id="f1dfd-137">Leave PowerShell open in the terminal pane</span></span>

<span data-ttu-id="f1dfd-138">När du anropar din cmdlet i terminalsession stoppas fel söknings programmet vid eventuella Bryt punkter som anges i käll koden.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-138">When you invoke your cmdlet in the terminal session, the debugger stops at any breakpoints set in your source code.</span></span>

### <a name="configuring-launchjson-for-powershell-core"></a><span data-ttu-id="f1dfd-139">Konfigurera launch.jspå för PowerShell Core</span><span class="sxs-lookup"><span data-stu-id="f1dfd-139">Configuring launch.json for PowerShell Core</span></span>

1. <span data-ttu-id="f1dfd-140">Installera [C# för kod tillägget för Visual Studio][]</span><span class="sxs-lookup"><span data-stu-id="f1dfd-140">Install the [C# for Visual Studio Code][] extension</span></span>

1. <span data-ttu-id="f1dfd-141">I fel söknings fönstret lägger du till en fel söknings konfiguration</span><span class="sxs-lookup"><span data-stu-id="f1dfd-141">In the Debug pane, add a debug configuration</span></span>

1. <span data-ttu-id="f1dfd-142">I `Select environment` dialog rutan väljer du `.NET Core`</span><span class="sxs-lookup"><span data-stu-id="f1dfd-142">In the `Select environment` dialog, choose `.NET Core`</span></span>

1. <span data-ttu-id="f1dfd-143">`launch.json`Filen öppnas i redigeraren.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-143">The `launch.json` file is opened in the editor.</span></span> <span data-ttu-id="f1dfd-144">Med markören inuti `configurations` matrisen visas `configuration` väljaren.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-144">With your cursor inside the `configurations` array, you see the `configuration` picker.</span></span> <span data-ttu-id="f1dfd-145">Om du inte ser den här listan väljer du **Lägg till konfiguration**.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-145">If you don't see this list, select **Add Configuration**.</span></span>

1. <span data-ttu-id="f1dfd-146">Om du vill skapa en standard fel söknings konfiguration väljer du **starta .net Core-konsol program**:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-146">To create a default debug configuration, select **Launch .NET Core Console App**:</span></span>

   ![Starta .NET Core Console-appen](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. <span data-ttu-id="f1dfd-148">Redigera `name` fälten, `program` , `args` och `console` enligt följande:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-148">Edit the `name`, `program`, `args`, and `console` fields as follows:</span></span>

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

<span data-ttu-id="f1dfd-149">`program`Fältet används för att starta `pwsh` så att cmdleten som felsöks kan köras.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-149">The `program` field is used to launch `pwsh` so that the cmdlet being debugged can be run.</span></span> <span data-ttu-id="f1dfd-150">`-NoExit`Argumentet förhindrar att PowerShell-sessionen avslutas så fort modulen importeras.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-150">The `-NoExit` argument prevents the PowerShell session from exiting as soon as the module is imported.</span></span>
<span data-ttu-id="f1dfd-151">Sökvägen i `Import-Module` argumentet är standard för att bygga ut en sökväg när du har följt guiden [skriva portabla moduler][] .</span><span class="sxs-lookup"><span data-stu-id="f1dfd-151">The path in the `Import-Module` argument is the default build output path when you've followed the [Writing Portable Modules][] guide.</span></span> <span data-ttu-id="f1dfd-152">Om du har skapat ett modul manifest ( `.psd1` fil) bör du använda sökvägen till den i stället.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-152">If you've created a module manifest (`.psd1` file), you should use the path to that instead.</span></span> <span data-ttu-id="f1dfd-153">`/`Sök vägs avgränsaren fungerar på Windows, Linux och MacOS.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-153">The `/` path separator works on Windows, Linux, and macOS.</span></span> <span data-ttu-id="f1dfd-154">Du måste använda den integrerade terminalen för att köra de PowerShell-kommandon som du vill felsöka.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-154">You must use the integrated terminal to run the PowerShell commands you want to debug.</span></span>

### <a name="configuring-launchjson-for-windows-powershell"></a><span data-ttu-id="f1dfd-155">Konfigurera launch.jspå för Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="f1dfd-155">Configuring launch.json for Windows PowerShell</span></span>

<span data-ttu-id="f1dfd-156">Den här start konfigurationen fungerar för att testa dina cmdletar i Windows PowerShell ( `powershell.exe` ).</span><span class="sxs-lookup"><span data-stu-id="f1dfd-156">This launch configuration works for testing your cmdlets in Windows PowerShell (`powershell.exe`).</span></span>
<span data-ttu-id="f1dfd-157">Skapa en andra start konfiguration med följande ändringar:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-157">Create a second launch configuration with the following changes:</span></span>

1. <span data-ttu-id="f1dfd-158">`name` bör vara `PowerShell cmdlets: powershell`</span><span class="sxs-lookup"><span data-stu-id="f1dfd-158">`name` should be `PowerShell cmdlets: powershell`</span></span>

1. <span data-ttu-id="f1dfd-159">`type` bör vara `clr`</span><span class="sxs-lookup"><span data-stu-id="f1dfd-159">`type` should be `clr`</span></span>

1. <span data-ttu-id="f1dfd-160">`program` bör vara `powershell`</span><span class="sxs-lookup"><span data-stu-id="f1dfd-160">`program` should be `powershell`</span></span>

   <span data-ttu-id="f1dfd-161">Den bör se ut så här:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-161">It should look like this:</span></span>

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

## <a name="launching-a-debugging-session"></a><span data-ttu-id="f1dfd-162">Starta en felsökningssession</span><span class="sxs-lookup"><span data-stu-id="f1dfd-162">Launching a debugging session</span></span>

<span data-ttu-id="f1dfd-163">Nu är allt klart för att påbörja fel sökning.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-163">Now everything is ready to begin debugging.</span></span>

- <span data-ttu-id="f1dfd-164">Placera en Bryt punkt i käll koden för den cmdlet som du vill felsöka:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-164">Place a breakpoint in the source code for the cmdlet you want to debug:</span></span>

  ![En Bryt punkt visas som en röd prick i fästmarginal](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- <span data-ttu-id="f1dfd-166">Se till att den relevanta **PowerShell-cmdlets** -konfigurationen är vald i list rutan konfiguration i vyn **fel sökning** :</span><span class="sxs-lookup"><span data-stu-id="f1dfd-166">Ensure that the relevant **PowerShell cmdlets** configuration is selected in the configuration drop-down menu in the **Debug** view:</span></span>

  ![Välj Starta konfigurationen](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- <span data-ttu-id="f1dfd-168">Tryck på <kbd>F5</kbd> eller klicka på knappen **Starta fel sökning**</span><span class="sxs-lookup"><span data-stu-id="f1dfd-168">Press <kbd>F5</kbd> or click on the **Start Debugging** button</span></span>

- <span data-ttu-id="f1dfd-169">Växla till terminalfönstret och anropa din cmdlet:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-169">Switch to the terminal pane and invoke your cmdlet:</span></span>

  ![Anropa cmdleten](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- <span data-ttu-id="f1dfd-171">Körningen stoppas vid Bryt punkten:</span><span class="sxs-lookup"><span data-stu-id="f1dfd-171">Execution stops at the breakpoint:</span></span>

  ![Körningar stannar vid Bryt punkten](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

<span data-ttu-id="f1dfd-173">Du kan gå igenom käll koden, granska variabler och granska anrops stacken.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-173">You can step through the source code, inspect variables, and inspect the call stack.</span></span>

<span data-ttu-id="f1dfd-174">Avsluta fel sökningen genom att klicka på **stoppa** i fel söknings verktygsfältet eller trycka på <kbd>SKIFT</kbd> - <kbd>F5</kbd>.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-174">To end debugging, click **Stop** in the debug toolbar or press <kbd>Shift</kbd>-<kbd>F5</kbd>.</span></span> <span data-ttu-id="f1dfd-175">Gränssnittet som används för fel sökning avslutas och släpper låset på den kompilerade DLL-filen.</span><span class="sxs-lookup"><span data-stu-id="f1dfd-175">The shell used for debugging exits and releases the lock on the compiled DLL file.</span></span>

<!-- reference links -->
[Fel sökning i Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Debugging in Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Använda Visual Studio Code för att fjärredigera och fjärrfelsöka]: using-vscode-for-remote-editing-and-debugging.md
[Using Visual Studio Code for remote editing and debugging]: using-vscode-for-remote-editing-and-debugging.md
[Skriva portabla moduler]: ../writing-portable-modules.md
[Writing Portable Modules]: ../writing-portable-modules.md
[C# för Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
[C# for Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
