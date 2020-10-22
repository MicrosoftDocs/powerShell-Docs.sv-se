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
# <a name="using-visual-studio-code-to-debug-compiled-cmdlets"></a>Använda Visual Studio Code för att felsöka kompilerade cmdletar

Den här guiden visar hur du interaktivt kan felsöka C#-källkod för en kompilerad PowerShell-modul med Visual Studio Code (VS Code) och C#-tillägget.

En del som är bekant med Visual Studio kod fel sökning antas.

- En allmän introduktion till VS Code-felsökaren finns i [fel sökning i Visual Studio Code][].

- Exempel på hur du felsöker PowerShell-skriptfiler och moduler finns i [använda Visual Studio Code för fjärran sluten redigering och fel sökning][].

I den här guiden förutsätter vi att du har läst och följt anvisningarna i guiden [skriva bärbara moduler][] .

## <a name="creating-a-build-task"></a>Skapa en bygge-uppgift

Bygg ditt projekt automatiskt innan du startar en felsökningssession. Återskapande säkerställer att du felsöker den senaste versionen av koden.

Konfigurera en versions uppgift:

1. I **paletten kommando**kör du kommandot **Konfigurera standard versions uppgift** .

   ![Kör konfigurera standard versions uppgift](media/using-vscode-for-debugging-compiled-cmdlets/configure-default-build-task.png)

1. I dialog rutan **Välj en aktivitet som ska konfigureras väljer du** **skapa tasks.jspå fil från mall**.

1. I dialog rutan **Välj en uppgiftsmall** väljer du **.net Core**.

En ny `tasks.json` fil skapas om det inte finns någon än.

Så här testar du din versions uppgift:

1. I **paletten kommando**kör du kommandot **Kör skapa uppgift** .

1. I dialog rutan **Välj Bygg uppgift att köra** väljer du **skapa**.

### <a name="information-about-dll-files-being-locked"></a>Information om DLL-filer som låses

Som standard visar en lyckad version inte utdata i terminalfönstret. Om det inte finns några utdata som innehåller text **projekt filen**bör du redigera `tasks.json` filen. Inkludera den explicita sökvägen till C#-projektet uttryckt som `"${workspaceFolder}/myModule"` . I det här exemplet `myModule` är namnet på projektmappen. Posten måste gå efter `build` posten i `args` listan enligt följande:

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

Vid fel sökning importeras din modul-DLL till PowerShell-sessionen i VS Code Terminal. DLL-filen blir låst. Följande meddelande visas när du kör åtgärden Skapa utan att stänga terminalfönstret:

```Output
Could not copy "obj\Debug\netstandard2.0\myModule.dll" to "bin\Debug\netstandard2.0\myModule.dll"`.
```

Terminal-sessioner måste stängas innan du återskapar.

## <a name="setting-up-the-debugger"></a>Konfigurera fel söknings programmet

Om du vill felsöka PowerShell-cmdleten måste du konfigurera en anpassad start konfiguration. Den här konfigurationen används för att:

- Bygg din käll kod
- Starta PowerShell med modulen inläst
- Lämna PowerShell öppen i terminalfönstret

När du anropar din cmdlet i terminalsession stoppas fel söknings programmet vid eventuella Bryt punkter som anges i käll koden.

### <a name="configuring-launchjson-for-powershell-core"></a>Konfigurera launch.jspå för PowerShell Core

1. Installera [C# för kod tillägget för Visual Studio][]

1. I fel söknings fönstret lägger du till en fel söknings konfiguration

1. I `Select environment` dialog rutan väljer du `.NET Core`

1. `launch.json`Filen öppnas i redigeraren. Med markören inuti `configurations` matrisen visas `configuration` väljaren. Om du inte ser den här listan väljer du **Lägg till konfiguration**.

1. Om du vill skapa en standard fel söknings konfiguration väljer du **starta .net Core-konsol program**:

   ![Starta .NET Core Console-appen](media/using-vscode-for-debugging-compiled-cmdlets/add-configuration-dialog.png)

1. Redigera `name` fälten, `program` , `args` och `console` enligt följande:

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

`program`Fältet används för att starta `pwsh` så att cmdleten som felsöks kan köras. `-NoExit`Argumentet förhindrar att PowerShell-sessionen avslutas så fort modulen importeras.
Sökvägen i `Import-Module` argumentet är standard för att bygga ut en sökväg när du har följt guiden [skriva portabla moduler][] . Om du har skapat ett modul manifest ( `.psd1` fil) bör du använda sökvägen till den i stället. `/`Sök vägs avgränsaren fungerar på Windows, Linux och MacOS. Du måste använda den integrerade terminalen för att köra de PowerShell-kommandon som du vill felsöka.

### <a name="configuring-launchjson-for-windows-powershell"></a>Konfigurera launch.jspå för Windows PowerShell

Den här start konfigurationen fungerar för att testa dina cmdletar i Windows PowerShell ( `powershell.exe` ).
Skapa en andra start konfiguration med följande ändringar:

1. `name` bör vara `PowerShell cmdlets: powershell`

1. `type` bör vara `clr`

1. `program` bör vara `powershell`

   Den bör se ut så här:

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

## <a name="launching-a-debugging-session"></a>Starta en felsökningssession

Nu är allt klart för att påbörja fel sökning.

- Placera en Bryt punkt i käll koden för den cmdlet som du vill felsöka:

  ![En Bryt punkt visas som en röd prick i fästmarginal](media/using-vscode-for-debugging-compiled-cmdlets/set-breakpoint.png)

- Se till att den relevanta **PowerShell-cmdlets** -konfigurationen är vald i list rutan konfiguration i vyn **fel sökning** :

  ![Välj Starta konfigurationen](media/using-vscode-for-debugging-compiled-cmdlets/select-launch-configuration.png)

- Tryck på <kbd>F5</kbd> eller klicka på knappen **Starta fel sökning**

- Växla till terminalfönstret och anropa din cmdlet:

  ![Anropa cmdleten](media/using-vscode-for-debugging-compiled-cmdlets/invoke-the-cmdlet.png)

- Körningen stoppas vid Bryt punkten:

  ![Körningar stannar vid Bryt punkten](media/using-vscode-for-debugging-compiled-cmdlets/stopped-at-breakpoint.png)

Du kan gå igenom käll koden, granska variabler och granska anrops stacken.

Avsluta fel sökningen genom att klicka på **stoppa** i fel söknings verktygsfältet eller trycka på <kbd>SKIFT</kbd> - <kbd>F5</kbd>. Gränssnittet som används för fel sökning avslutas och släpper låset på den kompilerade DLL-filen.

<!-- reference links -->
[Fel sökning i Visual Studio Code]: https://code.visualstudio.com/docs/editor/debugging
[Använda Visual Studio Code för att fjärredigera och fjärrfelsöka]: using-vscode-for-remote-editing-and-debugging.md
[Skriva portabla moduler]: ../writing-portable-modules.md
[C# för Visual Studio Code]: https://marketplace.visualstudio.com/items?itemName=ms-dotnettools.csharp
