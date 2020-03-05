---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 193243dc2e3e921b22a6ee068370200ae84ce4ac
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279284"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Så här replikerar du ISE-upplevelsen i Visual Studio Code

Även om PowerShell-tillägget för VSCode inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VSCode-upplevelsen mer naturlig för användare av ISE.

Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VSCode för att göra det enklare att komma åt användarna jämfört med ISE.

## <a name="ise-mode"></a>ISE-läge

> [!NOTE]
> Den här funktionen är tillgänglig i PowerShell-tillägget för förhands granskning sedan version 2019.12.0 och i PowerShell-tillägget sedan version 2020.3.0.

Det enklaste sättet att replikera ISE-upplevelsen i Visual Studio Code är genom att aktivera "ISE-läge".
Det gör du genom att öppna kommandot pall (<kbd>F1</kbd> eller <kbd>Ctrl</kbd>+<kbd>shift</kbd>+<kbd>P</kbd> eller <kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS) och ange "ISE-läge".
Välj "PowerShell: Aktivera ISE-läge" i listan.

Det här kommandot kommer att använda en mängd av inställningarna som påträffas i det här dokumentet automatiskt.
Resultatet ser ut så här:

![ISE-läge](media/How-To-Replicate-the-ISE-Experience-In-VSCode/3-ise-mode.png)

Resten av den här artikeln innehåller mer detaljerad information om inställningar i ISE-läge och vissa ytterligare inställningar.

## <a name="key-bindings"></a>Nyckel bindningar

| Funktion                              | ISE-bindning                  | VSCode-bindning                              |
| ----------------                      | -----------                  | --------------                              |
| Avbryta och bryta fel sökning          | <kbd>Ctrl</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Kör aktuell rad/markerad text | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista tillgängliga kodfragment               | <kbd>Ctrl</kbd>+<kbd>J</kbd> | <kbd>Ctrl</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Anpassade nyckel bindningar

Du kan också [Konfigurera dina egna nyckel bindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i VSCode.

## <a name="simplified-ise-like-ui"></a>Förenklat ISE – liknande gränssnitt

Om du vill förenkla Visual Studio Code-ANVÄNDARGRÄNSSNITTET för att se närmare användar gränssnittet för ISE, använder du följande två inställningar:

```json
"workbench.activityBar.visible": false,
"debug.openDebug": "neverOpen",
```

> [!NOTE]
> De här inställningarna ingår i ["ISE-läge"](#ise-mode).

Avsnittet "aktivitets fält" och "Felsök sid List" visas i den röda rutan:

![avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](media/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Slut resultatet ser ut så här:

![Förenklad vy av VS Code](media/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Slut för ande flik

Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Den här inställningen lades till direkt i VSCode (i stället för i tillägget). Dess beteende bestäms av VSCode direkt och kan inte ändras av tillägget.

> [!NOTE]
> Den här inställningen ingår i ["ISE-läge"](#ise-mode).

## <a name="no-focus-on-console-when-executing"></a>Ingen fokus på konsolen vid körning

För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

> [!NOTE]
> Den här inställningen ingår i ["ISE-läge"](#ise-mode).

Standardvärdet är `true` i tillgänglighets syfte.

## <a name="dont-start-integrated-console-on-startup"></a>Starta inte den integrerade konsolen vid start

Stoppa den integrerade konsolen vid start genom att ange:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> PowerShell-processen för bakgrunden kommer fortfarande att starta eftersom den innehåller IntelliSense, skript analys, symbol navigering osv. Men konsolen visas inte.

## <a name="assume-files-are-powershell-by-default"></a>Anta att filerna är PowerShell som standard

Om du vill skapa nya/namnlösa filer registrerar du som PowerShell som standard:

```json
"files.defaultLanguage": "powershell",
```

> [!NOTE]
> Den här inställningen ingår i ["ISE-läge"](#ise-mode).

## <a name="color-scheme"></a>Färg schema

Det finns ett antal ISE-teman som är tillgängliga för VSCode för att göra redigeraren att se mycket mer som ISE.

I [Kommando palett] typ `theme` för att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.
I list rutan väljer du `PowerShell ISE`.

Du kan ange det här temat i inställningarna med:

```json
"workbench.colorTheme": "PowerShell ISE",
```

> [!NOTE]
> Den här inställningen ingår i ["ISE-läge"](#ise-mode).

## <a name="powershell-command-explorer"></a>PowerShell kommando Utforskaren

Till [@corbob](https://github.com/corbob)kommer PowerShell-tillägget att ha början av en egen kommando Utforskare.

I [Kommando palett]anger du `PowerShell Command Explorer` och trycker på <kbd>RETUR</kbd>.

> [!NOTE]
> Detta visas automatiskt i ["ISE-läge"](#ise-mode).

## <a name="open-in-the-ise"></a>Öppna i ISE

Om du vill öppna en fil i ISE ändå kan du använda <kbd>Shift</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Andra resurser

- 4sysops har [en bra artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) om hur du konfigurerar VSCode för att vara mer som ISE.
- Mike F Robbins har [en bra post](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) för att ställa in VSCode.
- Lär dig mer om PowerShell har [en utmärkt Skriv åtgärd](https://www.learnpwsh.com/setup-vs-code-for-powershell/) för att hämta VSCode-installationsprogrammet för PowerShell.

## <a name="more-settings"></a>Fler inställningar

Om du känner till fler sätt att göra VSCode mer bekant för ISE-användare, bidrar till det här dokumentet. Om det finns en kompatibilitetsrapport som du letar efter, men du inte hittar något sätt att aktivera den, [öppnar du ett ärende](https://github.com/PowerShell/vscode-powershell/issues/new/choose) och ber om det!

Vi är alltid glada att kunna ta emot pull och bidrag även!

## <a name="vscode-tips"></a>VSCode-tips

### <a name="command-palette"></a>Kommando palett

<kbd>F1</kbd> ELLER <kbd>Ctrl</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> (<kbd>cmd</kbd>+<kbd>Shift</kbd>+<kbd>P</kbd> på MacOS)

Ett praktiskt sätt att köra kommandon i VSCode.
Mer information finns i [VSCode-dokumenten](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Kommando palett]: #command-palette
