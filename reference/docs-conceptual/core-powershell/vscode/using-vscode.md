# <a name="using-visual-studio-code-for-powershell-development"></a>Med Visual Studio-koden för PowerShell-utveckling

Förutom den [PowerShell ISE][ise], PowerShell är också väl stöds i Visual Studio-koden.
Dessutom stöds av ISE inte med PowerShell Core när Visual Studio Code stöds för PowerShell Core på alla plattformar (Windows, macOS och Linux)

Du kan använda Visual Studio-koden i Windows med PowerShell version 5 med hjälp av Windows 10 eller genom att installera [Windows Management Framework 5.0 RTM](https://www.microsoft.com/en-us/download/details.aspx?id=50395) för äldre Windows-operativsystem (t.ex. Windows 8.1, etc.).

Kontrollera att PowerShell finns i systemet innan du startar den.
Moderna arbetsbelastningar på Windows och macOS Linux finns:

- [Installera PowerShell Core på macOS- och Linux][install-pscore-linux]
- [Installera PowerShell Core i Windows][install-pscore-windows]

Traditionella arbetsbelastningar i Windows PowerShell, se [installera Windows PowerShell][install-winps].

## <a name="editing-with-visual-studio-code"></a>Redigera med Visual Studio Code

### <a name="1-installing-visual-studio-codehttpscodevisualstudiocomdocssetupsetup-overview"></a>[1. Installera Visual Studio Code](https://code.visualstudio.com/Docs/setup/setup-overview)

- **Linux**: Följ installationsanvisningarna den [VS köra kod i Linux](https://code.visualstudio.com/docs/setup/linux) sidan

- **macOS**: Följ installationsanvisningarna den [VS köra kod i macOS](https://code.visualstudio.com/docs/setup/mac) sidan

> [!IMPORTANT]
> I macOS, måste du installera OpenSSL för PowerShell-tillägget ska fungera korrekt.
> Det enklaste sättet att göra detta är att installera [Homebrew](http://brew.sh/) och kör sedan `brew install openssl`.
> PowerShell-tillägget ska nu kunna läsas in.

- **Windows**: Följ installationsanvisningarna den [VS köra kod på Windows](https://code.visualstudio.com/docs/setup/windows) sidan

### <a name="2-installing-powershell-extension"></a>2. Installera PowerShell-tillägg

- Starta Visual Studio Code appen genom att:
    - **Windows**: att skriva `code` i PowerShell-sessionen
    - **Linux**: att skriva `code` i terminalen
    - **macOS**: att skriva `code` i terminalen

- Starta **snabbt öppna** genom att trycka på **Ctrl + P** (**Cmd + P** på Mac).
- Snabb Skriv `ext install powershell` och träffar **RETUR**.
- Den **tillägg** vyn öppnas på på sidorutan. Välj PowerShell-tillägg från Microsoft.
  Du ser något som nedan:

  ![VSCode](../../images/vscode.png)

- Klicka på den **installera** knappen på PowerShell-tillägg från Microsoft.
- Efter installationen visas den **installera** knappen övergår i **ladda**.
  Klicka på **ladda**.
- När Visual Studio-koden har ladda, är du redo för redigering.

Klicka till exempel om du vill skapa en ny fil **Arkiv -> Ny**.
Om du vill spara den, klickar du på **Arkiv -> Spara** och ange sedan ett filnamn, låt oss säga `HelloWorld.ps1`.
Stäng filen genom att klicka på ”x” bredvid namnet på filen.
Avsluta Visual Studio Code **Arkiv -> Avsluta**.

#### <a name="using-a-specific-installed-version-of-powershell"></a>Med hjälp av en viss version av PowerShell

Om du vill använda en specifik installation av PowerShell med Visual Studio Code behöver du lägga till en ny variabel i filen med inställningar.

1. Klicka på **Arkiv -> Inställningar -> Inställningar**
1. Två editor fönster visas.
   I rutan längst till höger (`settings.json`), infoga inställningen nedan lämpliga för ditt operativsystem någonstans mellan två klammerparenteser (`{` och `}`) och Ersätt  *<version>*  med den installerade PowerShell-version:

  ```json
    // On Windows:
    "powershell.powerShellExePath": "c:/Program Files/PowerShell/<version>/pwsh.exe"

    // On Linux:
    "powershell.powerShellExePath": "/opt/microsoft/powershell/<version>/pwsh"

    // On macOS:
    "powershell.powerShellExePath": "/usr/local/microsoft/powershell/<version>/pwsh"
  ```
1. Ersätt inställningen med sökvägen till den önskade PowerShell körbar
1. Spara filen och starta om Visual Studio Code

#### <a name="configuration-settings-for-visual-studio-code"></a>Konfigurationsinställningar för Visual Studio Code

Med hjälp av stegen i föregående stycke kan du lägga till konfigurationsinställningar i `settings.json`.

Vi rekommenderar följande konfigurationsinställningar för Visual Studio-koden:

```json
{
    "csharp.suppressDotnetRestoreNotification": true,
    "editor.renderWhitespace": "all",
    "editor.renderControlCharacters": true,
    "omnisharp.projectLoadTimeout": 120,
    "files.trimTrailingWhitespace": true
}
```

## <a name="debugging-with-visual-studio-code"></a>Felsökning med Visual Studio Code

### <a name="no-workspace-debugging"></a>Ingen arbetsyta felsökning

Du kan felsöka PowerShell-skript utan att öppna den mapp som innehåller PowerShell-skriptet från och med version av Visual Studio Code 1.9.
Öppnar den PowerShell-skript med **Arkiv -> Öppna fil...** , ange en brytpunkt på en rad (tryck på F9) och tryck på F5 för att starta felsökningen.
Felsök åtgärdsfönstret visas där du vill starta felsökningsprogrammet, steg, fortsätta och stoppa felsökning visas.

### <a name="workspace-debugging"></a>Arbetsytan felsökning

Arbetsytan felsökning refererar till felsökning i kontexten för en mapp som du har öppnat i Visual Studio Code med **öppna mappen...**  från den **filen** menyn.
Du öppnar mappen är vanligtvis projektmappen PowerShell och/eller roten för Git-lagringsplatsen.

Även i detta läge kan starta du felsökning markerade PowerShell-skriptet genom att bara trycka på F5.
Dock kan arbetsytan felsökning du definiera flera debug konfigurationer än bara felsökning filen är öppen.
Exempelvis kan du lägga till en konfigurationer för att:

- Starta Pester tester i Felsökning
- Starta en viss fil med argumenten i Felsökning
- Starta en interaktiv session i Felsökning
- Koppla felsökaren till en värdprocess för PowerShell

Följ dessa steg för att skapa konfigurationsfilen debug:

1. Öppna den **felsöka** vyn genom att trycka på **Ctrl + Skift + D** (**Cmd + SKIFT + D** på Mac).
1. Tryck på den **konfigurera** växeln-ikonen i verktygsfältet.
1. Visual Studio Code uppmanas du att **Välj miljö**.
   Välj **PowerShell**.

   När du gör detta skapar en katalog och en fil ”.vscode\launch.json” i roten på arbetsytemappen för Visual Studio-koden.
   Här sparas där debug-konfiguration. Om filerna finns i en Git-lagringsplats, vill du förmodligen att genomföra launch.json-filen.
   Innehållet i filen launch.json är:

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

Detta representerar vanliga scenarier för felsökning.
Men när du öppnar den här filen i redigeraren, visas en **Lägg till konfiguration...**  knappen.
Du kan trycka på knappen för att lägga till flera PowerShell debug-konfigurationer. Är en praktisk konfiguration för att lägga till **PowerShell: starta skriptet**.
Med den här konfigurationen kan du ange en viss fil med valfria argument som ska startas när du trycker på F5 oavsett vilken fil som för närvarande är aktiv i redigeraren.

När debug-konfigurationen har upprättats kan du välja vilken konfiguration som du vill använda i en debug-session genom att välja ett från debug konfigurationen listrutan i den **felsöka** vyns verktygsfältet.

Det finns några bloggar som kan vara till hjälp att komma igång med hjälp av PowerShell-tillägget för Visual Studio Code

- Visual Studio-koden: [PowerShell-tillägg][ps-extension]
- [Skriva och felsöka PowerShell-skript i Visual Studio Code][debug]
- [Riktlinjer för felsökning Visual Studio Code][vscode-guide]
- [Felsökning PowerShell i Visual Studio Code][ps-vscode]
- [Kom igång med PowerShell-utveckling i Visual Studio Code][getting-started]
- [Visual Studio Code redigera funktioner för utveckling av PowerShell – del 1][editing-part1]
- [Visual Studio Code redigera funktioner för utveckling av PowerShell – del 2][editing-part2]
- [Felsökning av PowerShell-skript i Visual Studio Code – del 1][debugging-part1]
- [Felsökning av PowerShell-skript i Visual Studio Code – del 2][debugging-part2]

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

## <a name="powershell-extension-for-visual-studio-code"></a>PowerShell-tillägget för Visual Studio Code

Källkoden för PowerShell-tillägg finns på [GitHub](https://github.com/PowerShell/vscode-powershell).
