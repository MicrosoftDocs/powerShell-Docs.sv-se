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
# <a name="using-visual-studio-code-for-powershell-development"></a>Använda Visual Studio Code för PowerShell-utveckling

Förutom [POWERSHELL ISE][ise], stöds även PowerShell i Visual Studio Code (VSCode). Dessutom stöds inte ISE med PowerShell Core, medan VSCode stöds för PowerShell Core på alla plattformar (Windows, macOS och Linux)

Du kan använda VSCode i Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5,0 RTM](https://devblogs.microsoft.com/powershell/windows-management-framework-wmf-5-0-rtm-is-now-available-via-the-microsoft-update-catalog/) för Windows oss på en äldre nivå (t. ex. Windows 8,1 osv.).

Innan du startar det kontrollerar du att PowerShell finns i systemet. För moderna arbets belastningar på Windows, macOS och Linux, se:

- [Installera PowerShell Core på Linux][install-pscore-linux]
- [Installera PowerShell Core på macOS][install-pscore-macos]
- [Installera PowerShell Core på Windows][install-pscore-windows]

För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].

## <a name="editing-with-vscode"></a>Redigera med VSCode

1. [Installerar VSCode](https://code.visualstudio.com/Docs/setup/setup-overview)

   - **Linux**: följ installations anvisningarna på sidan för att [köra VSCode på Linux](https://code.visualstudio.com/docs/setup/linux)
   - **MacOS**: följ installations anvisningarna på sidan för att [köra VSCode på MacOS](https://code.visualstudio.com/docs/setup/mac)

     > [!IMPORTANT]
     > På macOS måste du installera OpenSSL för att PowerShell-tillägget ska fungera korrekt. Det enklaste sättet att göra detta är att installera [homebrew](https://brew.sh/) och sedan köra `brew install openssl`. VSCode kan nu läsa in PowerShell-tillägget.

   - **Windows**: följ installations anvisningarna på sidan för att [köra VSCode på Windows](https://code.visualstudio.com/docs/setup/windows)

2. Installera PowerShell-tillägg

   - Starta VSCode-appen genom att:
     - **Windows**: skriva `code` in PowerShell-sessionen
     - **Linux**: skriva `code` in i terminalen
     - **MacOS**: skriva `code` in i terminalen
   - **Öppna snabb** start genom att trycka på <kbd>CTRL</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>p</kbd> på Mac).
   - Skriv `ext install powershell` och tryck på **RETUR**i snabb öppning.
   - Vyn **tillägg** öppnas i sido fältet. Välj PowerShell-tillägget från Microsoft.
     Du bör se något som liknar följande:

     ![VSCode](../../images/using-vscode/vscode.png)

   - Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.
   - Efter installationen ser knappen **Installera** att **läsas in igen**. Klicka på **Läs in igen**.
   - När VSCode har lästs in på nytt är du redo för redigering.

Om du till exempel vill skapa en ny fil klickar du på **fil-> ny**. Spara genom att klicka på **Arkiv-> Spara** och ange ett fil namn, låt oss säga `HelloWorld.ps1`. Stäng filen genom att klicka på "x" bredvid fil namnet. Avsluta VSCode genom att avsluta **File->** .

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installera PowerShell-tillägget på begränsade system

Vissa system har kon figurer ATS på ett sätt som kräver att alla kod-signaturer kontrol leras, vilket kräver att PowerShell Editor-tjänster godkänns manuellt för att köras i systemet. En grupprincip uppdatering som ändrar körnings principen är en sannolik orsak om du har installerat PowerShell-tillägget men når ett fel som:

```
Language server startup failed.
```

Om du vill godkänna PowerShell Editor-tjänster manuellt och därmed PowerShell-tillägget för VSCode öppnar du en PowerShell-prompt och kör:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Du uppmanas att använda "vill du köra program vara från den här ej betrodda utgivaren?" Skriv `R` för att köra filen. Öppna sedan VSCode och kontrol lera att PowerShell-tillägget fungerar korrekt. Om du fortfarande har problem med att komma igång kan du berätta om [GitHub](https://github.com/PowerShell/vscode-powershell/issues).

#### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Välja en version av PowerShell som ska användas med tillägget

Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en viss version av PowerShell med PowerShell-tillägget. Använd följande steg för att välja version:

1. Öppna kommandot pall (<kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> på Windows & Linux, <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS).
1. Sök efter "session".
1. Klicka på "PowerShell: Visa session-menyn ".
1. Välj den version av PowerShell som du vill använda från listan, till exempel "PowerShell Core".

> [!IMPORTANT]
> Den här funktionen söker efter några välkända sökvägar på olika operativ system för att identifiera installations platser för PowerShell. Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn. Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.

>[!NOTE]
> Det finns ett annat sätt att komma till session-menyn. När en PowerShell-fil är öppen i redigeraren visas ett grönt versions nummer längst ned till höger. Om du klickar på det här versions numret visas session-menyn.

##### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Lägga till egna PowerShell-sökvägar i session-menyn

Du kan lägga till andra körbara sökvägar för PowerShell i sessionen via en VSCode-inställning.

Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa listan om den inte finns i din: `settings.json`

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

Varje objekt måste ha:

* `exePath`: Sökvägen till eller `powershell` den `pwsh` körbara filen.
* `versionName`: Den text som visas i session-menyn.

Du kan ange vilken standard version av PowerShell som ska användas `powershell.powerShellDefaultVersion` med inställningen genom att ställa in den på texten som visas i session-menyn `versionName` (aka i den sista inställningen):

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

När du har angett den här inställningen startar du om VSCode eller använder "Developer: Läs in kommando åtgärd för att läsa in den aktuella VSCode-fönstret igen.

Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!

> [!NOTE]
> Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.

#### <a name="configuration-settings-for-vscode"></a>Konfigurations inställningar för VSCode

Genom att följa stegen i föregående stycke kan du lägga till konfigurations inställningar `settings.json`i.

Vi rekommenderar följande konfigurations inställningar för VSCode:

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

Om du inte vill att de här inställningarna ska påverka alla filtyper kan VSCode också använda konfigurationer för flera språk. Skapa en språkspecifik inställning genom att placera inställningarna i `[<language-name>]` ett fält. Exempel:

```json
"[powershell]": {
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Mer information om fil kodning i VSCode finns i [förstå fil kodning](understanding-file-encoding.md).

## <a name="debugging-with-vscode"></a>Fel sökning med VSCode

### <a name="no-workspace-debugging"></a>Ingen fel sökning på arbets ytan

Från och med VSCode version 1,9 kan du felsöka PowerShell-skript utan att behöva öppna mappen som innehåller PowerShell-skriptet. Öppna PowerShell-skriptfilen med **fil-> öppna fil...** , ange en Bryt punkt på en rad (tryck på <kbd>F9</kbd>) och tryck sedan på <kbd>F5</kbd> för att starta fel sökningen. Du bör se fönstret fel söknings åtgärder som gör att du kan dela upp i fel sökning, steg, återuppta och stoppa fel sökning.

### <a name="workspace-debugging"></a>Fel sökning av arbets yta

Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat i Visual Studio Code med **Öppna mapp...** från menyn **Arkiv** . Mappen som du öppnar är vanligt vis din PowerShell-projektmapp och/eller roten för git-lagringsplatsen.

Även i det här läget kan du börja felsöka det markerade PowerShell-skriptet genom att helt enkelt trycka på <kbd>F5</kbd>. Med fel sökning av arbets yta kan du dock definiera flera fel söknings konfigurationer förutom att bara Felsöka den öppna filen. Du kan till exempel lägga till en konfiguration för att:

- Starta pester-tester i fel söknings programmet
- Starta en speciell fil med argument i fel söknings programmet
- Starta en interaktiv session i fel söknings programmet
- Koppla fel söknings programmet till en PowerShell-värd process

Följ de här stegen för att skapa en fel söknings konfigurations fil:

  1. Öppna vyn **fel sökning** genom att trycka på <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>d</kbd> (<kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>d</kbd> på Mac).
  2. Klicka på ikonen **Konfigurera** kugg hjul i verktygsfältet.
  3. VSCode där du ombeds att **välja miljö**. Välj **PowerShell**.

  När du gör detta skapar VSCode en katalog och en fil ". vscode\launch.JSON" i roten i din arbetsytans mapp. Det är här som din fel söknings konfiguration lagras. Om filerna finns på en git-lagringsplats vill du vanligt vis allokera filen Launch. JSON. Innehållet i filen Launch. JSON är:

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

  Detta representerar vanliga fel söknings scenarier. När du öppnar den här filen i redigeraren visas dock knappen **Lägg till konfiguration...** . Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer. En praktisk konfiguration för att lägga **till är PowerShell: Starta skript**. Med den här konfigurationen kan du ange en fil med valfria argument som ska startas när du trycker på <kbd>F5</kbd> oavsett vilken fil som för närvarande är aktiv i redigeraren.

  När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession genom att välja en från List rutan Felsök konfiguration i verktygsfältet för **fel** söknings läge.

Det finns några Bloggar som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:

- [PowerShell-tillägg][ps-extension]
- [Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]
- [Fel sökning av Visual Studio Code-vägledning][vscode-guide]
- [Felsöka PowerShell i Visual Studio Code][ps-vscode]
- [Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]
- [Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]
- [Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]
- [Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]
- [Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]

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

## <a name="powershell-extension-for-vscode"></a>PowerShell-tillägg för VSCode

Du hittar PowerShell-tilläggets källkod på [GitHub](https://github.com/PowerShell/vscode-powershell).
