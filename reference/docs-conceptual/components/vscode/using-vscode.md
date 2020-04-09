---
title: Använda Visual Studio Code för PowerShell-utveckling
description: Använda Visual Studio Code för PowerShell-utveckling
ms.date: 11/07/2019
ms.openlocfilehash: 5251094388f6abc7da7f2cc706537eade78df7c9
ms.sourcegitcommit: 7f2479edd329dfdc55726afff7019d45e45f9156
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/08/2020
ms.locfileid: "80978703"
---
# <a name="using-visual-studio-code-for-powershell-development"></a>Använda Visual Studio Code för PowerShell-utveckling

[Visual Studio Code][vscode] är en plattforms oberoende skript redigerare från Microsoft. Tillsammans med [PowerShell-tillägget][psext]ger det en omfattande och interaktiv skript redigerings upplevelse, vilket gör det enklare att skriva pålitliga PowerShell-skript. Visual Studio Code med PowerShell-tillägget är den rekommenderade redigeraren för att skriva PowerShell-skript.

Det stöder följande PowerShell-versioner:

- PowerShell 7 och uppåt (Windows, macOS och Linux)
- PowerShell Core 6 (Windows, macOS och Linux)
- Windows PowerShell 5,1 (endast Windows)

> [!NOTE]
> Visual Studio Code är inte samma sak som [Visual Studio][].

## <a name="getting-started"></a>Komma igång

Innan du börjar ska du kontrol lera att PowerShell finns i systemet. För moderna arbets belastningar på Windows, macOS och Linux, se följande länkar:

- [Installera PowerShell på Linux][install-pscore-linux]
- [Installera PowerShell på macOS][install-pscore-macos]
- [Installera PowerShell i Windows][install-pscore-windows]

För traditionella Windows PowerShell-arbetsbelastningar, se [Installera Windows PowerShell][install-winps].

> [!IMPORTANT]
> [Windows PowerShell ISE][ise] är fortfarande tillgängligt för Windows. Men det är inte längre i den aktiva funktions utvecklingen. ISE fungerar inte med PowerShell 6 och senare. Som en komponent i Windows fortsätter den att vara officiellt tillgänglig för säkerhets-och högprioriterade service-korrigeringar.
> Vi har inga planer på att ta bort ISE från Windows.

## <a name="editing-with-visual-studio-code"></a>Redigera med Visual Studio Code

1. Installera Visual Studio Code. Mer information finns i Översikt över [konfiguration av Visual Studio Code][vsc-setup].

   Det finns installations anvisningar för varje plattform:

   - **Windows**: följ installations anvisningarna på sidan som [körs i Visual Studio Code på Windows][vsc-setup-win] .
   - **MacOS**: följ installationsinstruktionerna på sidan [med Visual Studio Code på MacOS][vsc-setup-macOS] .
   - **Linux**: följ installations anvisningarna på sidan som [Kör Visual Studio Code på Linux][vsc-setup-linux] .

1. Installera PowerShell-tillägget.

   1. Starta Visual Studio Code-appen genom att skriva `code` i en konsol eller `code-insiders` om du har installerat Visual Studio Code-Insiders.
   1. Starta **Quick Open** på Windows eller Linux genom att trycka på <kbd>CTRL</kbd>+<kbd>P</kbd>. I macOS trycker du på <kbd>Cmd</kbd>+<kbd>P</kbd>.
   1. Skriv `ext install powershell` i snabb öppning och tryck på **RETUR**.
   1. Vyn **tillägg** öppnas i sido fältet. Välj PowerShell-tillägget från Microsoft.
      Du bör se en Visual Studio Code-skärm som liknar följande bild:

      ![Visual Studio Code](media/using-vscode/vscode.png)

   1. Klicka på knappen **Installera** i PowerShell-tillägget från Microsoft.
   1. När du har installerat klickar du på **Läs in**igen om du ser knappen **Installera** **igen.**
   1. När Visual Studio Code har lästs in på nytt är du redo för redigering.

Om du till exempel vill skapa en ny fil klickar du på **fil > ny**. Spara genom att klicka på **arkiv > Spara** och ange ett fil namn, till exempel `HelloWorld.ps1`. Stäng filen genom att klicka på `X` bredvid fil namnet. Avsluta Visual Studio Code genom att stänga av **filen >** .

### <a name="installing-the-powershell-extension-on-restricted-systems"></a>Installera PowerShell-tillägget på begränsade system

Vissa system är konfigurerade för att kräva validering av alla kod-signaturer. Du kan få följande fel:

```
Language server startup failed.
```

Det här problemet kan inträffa när PowerShell: s körnings princip anges av Windows grupprincip. Om du vill godkänna PowerShell Editor-tjänster och PowerShell-tillägget för Visual Studio Code manuellt öppnar du en PowerShell-kommandotolk och kör följande kommando:

```powershell
Import-Module $HOME\.vscode\extensions\ms-vscode.powershell*\modules\PowerShellEditorServices\PowerShellEditorServices.psd1
```

Du tillfrågas om **vill du köra program vara från den här ej betrodda utgivaren?** Skriv `A` för att köra filen. Öppna sedan Visual Studio Code och kontrol lera att PowerShell-tillägget fungerar korrekt. Om du fortfarande har problem med att komma igång kan du berätta för oss om [GitHub problem][].

> [!NOTE]
> PowerShell-tillägget för Visual Studio Code stöder inte körning i begränsat språk läge. Mer information finns i [GitHub issue #606][i606].

### <a name="choosing-a-version-of-powershell-to-use-with-the-extension"></a>Välja en version av PowerShell som ska användas med tillägget

Med PowerShell Core-installation sida vid sida med Windows PowerShell, är det nu möjligt att använda en speciell version av PowerShell med PowerShell-tillägget. Den här funktionen ser till att det finns några välkända sökvägar på olika operativ system för att identifiera installationer av PowerShell.

Använd följande steg för att välja version:

1. Öppna **paletten kommando** i Windows eller Linux med <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>. I macOS använder du <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd>.
1. Sök efter **session**.
1. Klicka på **PowerShell: Visa session-menyn**.
1. Välj den version av PowerShell som du vill använda i listan, till exempel: **PowerShell Core**.

Om du har installerat PowerShell på en icke-typisk plats kan det hända att den inte visas inlednings vis i session-menyn. Du kan utöka session-menyn genom [att lägga till egna anpassade sökvägar](#adding-your-own-powershell-paths-to-the-session-menu) enligt beskrivningen nedan.

> [!NOTE]
> Menyn PowerShell-session kan också nås från det gröna versions numret i det nedre högra hörnet av statusfältet. Om du klickar på det här versions numret öppnas session-menyn.

## <a name="configuration-settings-for-visual-studio-code"></a>Konfigurations inställningar för Visual Studio Code

Först, om du inte är bekant med hur du ändrar inställningarna i Visual Studio Code, rekommenderar vi att du läser dokumentationen för [Visual Studio-kodens inställningar][vsc-settings] .

När du har läst dokumentationen kan du lägga till konfigurations inställningar i `settings.json`.

```json
{
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "files.trimTrailingWhitespace": true,
    "files.encoding": "utf8bom",
    "files.autoGuessEncoding": true
}
```

Om du inte vill att de här inställningarna ska påverka alla filtyper kan du också använda Visual Studio Code för konfigurationer på olika språk. Skapa en språkspecifik inställning genom att lägga till inställningar i ett `[<language-name>]`s fält. Exempel:

```json
{
    "[powershell]": {
        "files.encoding": "utf8bom",
        "files.autoGuessEncoding": true
    }
}
```

> [!TIP]
> Mer information om fil kodning i Visual Studio Code finns i [förstå fil kodning][file-encoding].
>
> Lär dig också hur du kan [REPLIKERA ISE-upplevelsen i Visual Studio Code][vsc-ise] för andra tips om hur du konfigurerar Visual Studio Code för PowerShell-redigering.

### <a name="adding-your-own-powershell-paths-to-the-session-menu"></a>Lägga till egna PowerShell-sökvägar i session-menyn

Du kan lägga till andra sökvägar för PowerShell-körbara filer till sessionen via [Visual Studio-kod inställningen](https://code.visualstudio.com/docs/getstarted/settings): `powershell.powerShellAdditionalExePaths`.

Lägg till ett objekt i listan `powershell.powerShellAdditionalExePaths` eller skapa en lista om den inte finns i `settings.json`:

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

- `exePath`: sökvägen till `pwsh` eller `powershell` körbar fil.
- `versionName`: den text som visas i session-menyn.

Om du vill ange standard versionen för PowerShell ställer du in värdet `powershell.powerShellDefaultVersion` på den text som visas i menyn session (kallas även `versionName`):

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

När du har konfigurerat den här inställningen startar du om Visual Studio Code eller läser in det aktuella Visual Studio Code-fönstret från **kommando-paletten**. Skriv **Developer: Läs in igen**.

Om du öppnar session-menyn visas nu ytterligare PowerShell-versioner!

> [!NOTE]
> Om du skapar PowerShell från källa är det ett bra sätt att testa din lokala version av PowerShell.

### <a name="using-an-older-version-of-the-powershell-extension-for-windows-powershell-v3-and-v4"></a>Använda en äldre version av PowerShell-tillägget för Windows PowerShell v3 och v4

Det aktuella PowerShell-tillägget stöder inte [PowerShell v3 och v4][i1310]. Du kan dock använda den senaste versionen av tillägget som stöder PowerShell v3 och v4.

> [!CAUTION]
> Det kommer inte att finnas några ytterligare korrigeringar till den här äldre versionen av tillägget. Det tillhandahålls "i befintligt skick", men det är tillgängligt för dig om du fortfarande använder Windows PowerShell v3 och Windows PowerShell v4.

Öppna först fönstret tillägg och Sök efter `PowerShell`. Klicka sedan på kugg hjulet och välj **installera en annan version...** .

![Installera en annan version...](media/using-vscode/install-another-version.png)

Välj sedan **2020.1.0** -versionen. Den här versionen av tillägget var den senaste versionen som stöd för v3 och v4. Se till att lägga till följande inställning så att tilläggs versionen inte uppdateras automatiskt:

```json
{
    "extensions.autoUpdate": false
}
```

Version **2020.1.0** kommer att fungera för den förväntade framtiden. Visual Studio Code kan dock implementera en ändring som bryter mot den här versionen av tillägget. På grund av detta, och brist på support, rekommenderar vi följande:

- Uppgradera till Windows PowerShell 5,1
- Installera PowerShell 7, som är en sida-vid-sida-installation till Windows PowerShell och fungerar bäst med PowerShell-tillägget

## <a name="debugging-with-visual-studio-code"></a>Felsöka med Visual Studio Code

### <a name="no-workspace-debugging"></a>Ingen fel sökning på arbets ytan

I Visual Studio Code version 1,9 (eller senare) kan du felsöka PowerShell-skript utan att öppna mappen som innehåller PowerShell-skriptet.

1. Öppna PowerShell-skriptfilen med **fil > öppna fil...**
1. Ange en Bryt punkt – Markera en rad och tryck sedan på <kbd>F9</kbd>
1. Tryck på <kbd>F5</kbd> för att starta fel sökningen

Du bör se fönstret fel söknings åtgärder, vilket gör att du kan bryta i fel söknings programmet, steg, återuppta och stoppa fel sökningen.

### <a name="workspace-debugging"></a>Fel sökning av arbets yta

Fel sökning av arbets ytan avser fel sökning i kontexten för en mapp som du har öppnat från menyn **Arkiv** med **Öppna mapp..** .. Mappen som du öppnar är vanligt vis din PowerShell-projektmapp eller roten för git-lagringsplatsen. Med fel sökning av arbets ytan kan du definiera flera fel söknings konfigurationer förutom att bara Felsöka den för tillfället öppna filen.

Följ de här stegen för att skapa en fel söknings konfigurations fil:

1. Öppna **fel söknings** vyn i Windows eller Linux genom att trycka på <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>. I macOS trycker du på <kbd>Cmd</kbd>+<kbd>Shift</kbd>+<kbd>D</kbd>.
1. Klicka på länken **skapa en starta. JSON-fil** .
1. Välj **PowerShell**i dialog rutan **Välj miljö** .
1. Välj den typ av fel sökning du vill använda:

   - **Starta aktuell fil** – starta och Felsök filen i det för tillfället aktiva redigerings fönstret
   - **Starta skript** – starta och Felsök den angivna filen eller kommandot
   - **Interaktiv session** – Felsök kommandon som körs från den integrerade konsolen
   - **Koppla** -koppla fel sökaren till en PowerShell-värd process som körs

Visual Studio Code skapar en katalog och en fil `.vscode\launch.json` i roten i din arbetsytans mapp för att lagra fel söknings konfigurationen. Om filerna finns på en git-lagringsplats vill du vanligt vis bekräfta `launch.json`-filen. Innehållet i `launch.json`-filen är:

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

Den här filen representerar vanliga fel söknings scenarier. När du öppnar den här filen i redigeraren visas knappen **Lägg till konfiguration...** . Du kan klicka på den här knappen för att lägga till fler PowerShell-felsöknings konfigurationer. En användbar konfiguration för att lägga till är **PowerShell: starta skript**. Med den här konfigurationen kan du ange en fil som innehåller valfria argument som används när du trycker på <kbd>F5</kbd> oavsett vilken fil som är aktiv i redigeraren.

När du har upprättat fel söknings konfigurationen kan du välja vilken konfiguration du vill använda under en felsökningssession. Välj en konfiguration i list rutan Felsök konfiguration i **fel söknings** verktygsfältets verktygsfält.

## <a name="troubleshooting-the-powershell-extension-for-visual-studio-code"></a>Felsöka PowerShell-tillägget för Visual Studio Code

Om du får problem med att använda Visual Studio Code för att utveckla PowerShell-skript, se [fel söknings guiden][troubleshooting] på GitHub.

## <a name="useful-resources"></a>Användbara resurser

Det finns några videor och blogg inlägg som kan vara till hjälp för att komma igång med PowerShell-tillägget för Visual Studio Code:

### <a name="videos"></a>Videoklipp

- [Använda Visual Studio Code som standard-PowerShell-redigerare](https://youtu.be/bGn45vIeAMM)
- [Visual Studio Code: djup gå in i fel sökning av PowerShell-skript](https://youtu.be/cSbIXmlkr8o)

### <a name="blog-posts"></a>Blogginlägg

- [PowerShell-tillägg][pscdn]
- [Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]
- [Fel sökning av Visual Studio Code-vägledning][psdbgblog]
- [Felsöka PowerShell i Visual Studio Code][psdbg-gh]
- [Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]
- [Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 1][editing-part1]
- [Visual Studio Code Editing-funktioner för PowerShell-utveckling – del 2][editing-part2]
- [Felsöka PowerShell-skript i Visual Studio Code – del 1][debugging-part1]
- [Felsöka PowerShell-skript i Visual Studio Code – del 2][debugging-part2]

## <a name="powershell-extension-project-source-code"></a>Projekt käll kod för PowerShell-tillägg

Du hittar PowerShell-tilläggets källkod på [GitHub][psext-src].

Om du är intresse rad av att bidra är pull-begäranden mycket tacksam. Följ tillsammans med [Developer-dokumentationen][dev-docs] på GitHub för att komma igång.

<!-- related articles -->
[ise]:                    ../ise/Introducing-the-Windows-PowerShell-ISE.md
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
[pscdn]:                  https://blogs.msdn.microsoft.com/cdndevs/2015/12/11/visual-studio-code-powershell-extension/

<!-- issues -->
[GitHub problem]:          https://github.com/PowerShell/vscode-powershell/issues
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
