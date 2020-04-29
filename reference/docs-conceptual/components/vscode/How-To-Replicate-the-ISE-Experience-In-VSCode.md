---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 899e1c393fd49b0659631b88d610e80ec885e69e
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "81005609"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Så här replikerar du ISE-upplevelsen i Visual Studio Code

Även om PowerShell-tillägget för VS Code inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VS Code-upplevelsen mer naturlig för användare av ISE.

Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VS Code för att användar upplevelsen ska bli mer bekant jämfört med ISE.

## <a name="ise-mode"></a>ISE-läge

> [!NOTE]
> Den här funktionen är tillgänglig i PowerShell-tillägget för förhands granskning sedan version 2019.12.0 och i PowerShell-tillägget sedan version 2020.3.0.

Det enklaste sättet att replikera ISE-upplevelsen i Visual Studio Code är genom att aktivera "ISE-läge".
Det gör du genom att öppna Command-paletten (<kbd>F1</kbd> eller <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> eller <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> på MacOS) och skriva i "ISE-läge". Välj "PowerShell: Aktivera ISE-läge" i listan.

Det här kommandot tillämpar automatiskt de inställningar som beskrivs nedan, vilket ser ut så här:

![ISE-läge](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

## <a name="ise-mode-configuration-settings"></a>Konfigurations inställningar för ISE-läge

ISE-läget gör följande ändringar i VS Code-inställningar.

- Nyckel bindningar

  |               Funktion                |         ISE-bindning          |              VS-kod bindning                |
  | ------------------------------------- | ---------------------------- | ------------------------------------------- |
  | Avbryta och bryta fel sökning          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
  | Kör aktuell rad/markerad text | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
  | Lista tillgängliga kodfragment               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>Alt+<kbd>J</kbd> |

  > [!NOTE]
  > Du kan också [Konfigurera egna nyckel bindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i vs Code.

- Förenklat ISE – liknande gränssnitt

  Om du vill förenkla Visual Studio Code-ANVÄNDARGRÄNSSNITTET för att se närmare användar gränssnittet för ISE, använder du följande två inställningar:

  ```json
  "workbench.activityBar.visible": false,
  "debug.openDebug": "neverOpen",
  ```

  Dessa inställningar döljer avsnitten "aktivitets fält" och "Felsök sid fält" som visas i den röda rutan nedan:

  ![avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

  Slut resultatet ser ut så här:

  ![Förenklad vy av VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

- Slut för ande flik

  Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:

  ```json
  "editor.tabCompletion": "on",
  ```

- Ingen fokus på konsolen vid körning

  För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:

  ```json
  "powershell.integratedConsole.focusConsoleOnExecute": false
  ```

  Standardvärdet `true` är för hjälpmedels syfte.

- Starta inte den integrerade konsolen vid start

  Stoppa den integrerade konsolen vid start genom att ange:

  ```json
  "powershell.integratedConsole.showOnStartup": false
  ```

  > [!NOTE]
  > PowerShell-processen i bakgrunden börjar fortfarande tillhandahålla IntelliSense, skript analys, symbol navigering osv. konsolen visas inte.

- Anta att filerna är PowerShell som standard

  Om du vill skapa nya/namnlösa filer registrerar du som PowerShell som standard:

  ```json
  "files.defaultLanguage": "powershell",
  ```

- Färgschema

  Det finns ett antal ISE-teman som är tillgängliga för VS Code för att göra redigeraren att se mycket mer som ISE.

  I [paletten kommando][] typ `theme` `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>. Välj `PowerShell ISE`i den nedrullningsbara listan.

  Du kan ange det här temat i inställningarna med:

  ```json
  "workbench.colorTheme": "PowerShell ISE",
  ```

- PowerShell kommando Utforskaren

  Till [@corbob](https://github.com/corbob)och med fungerar PowerShell-tillägget i början av en egen kommando Utforskare.

  I [paletten kommando][]anger `PowerShell Command Explorer` du och trycker på <kbd>RETUR</kbd>.

- Öppna i ISE

  Om du vill öppna en fil i Windows PowerShell ISE ändå öppnar du [kommando-paletten][], söker efter "öppna i ISE" och väljer sedan **PowerShell: öppna aktuell fil i PowerShell ISE**.

## <a name="other-resources"></a>Andra resurser

- 4sysops har [en bra artikel][4sysops] om att konfigurera vs Code för att vara mer som ISE.
- Mike F Robbins har [en bra post][mikefrobbins] för att ställa in vs Code.
- Lär dig mer om PowerShell har [en utmärkt Skriv][learnpwsh] konfiguration för PowerShell.

## <a name="vs-code-tips"></a>VS Code-tips

- Kommando palett

  Kommando paletten är ett praktiskt sätt att köra kommandon i VS Code. Öppna paletten kommando med <kbd>F1</kbd> eller <kbd>CTRL</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> eller <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>p</kbd> på MacOS.

  Mer information finns i [vs Code-dokumentationen][vsc-docs].

- Inaktivera fel söknings konsolen

  Om du bara planerar att använda VS Code för PowerShell-skript kan du dölja **fel söknings konsolen** eftersom den inte används av PowerShell-tillägget. Det gör du genom att högerklicka på **fel söknings konsolen** och sedan klicka på kryss markeringen för att dölja den.

## <a name="more-settings"></a>Fler inställningar

Om du känner till fler sätt att göra VS Code-känsla mer bekant för ISE-användare, bidrar till det här dokumentet. Om det finns en kompatibilitetsrapport som du letar efter, men du inte hittar något sätt att aktivera den, [öppnar du ett ärende][] och ber om det!

Vi är alltid glada att kunna ta emot pull och bidrag även!

<!-- link references -->
[vsc-docs]: https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette
[Kommando palett]: #vs-code-tips
[öppna ett ärende]: https://github.com/PowerShell/VSCode-powershell/issues/new/choose

[4sysops]: https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/
[mikefrobbins]: https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/
[learnpwsh]: https://www.learnpwsh.com/setup-vs-code-for-powershell/
