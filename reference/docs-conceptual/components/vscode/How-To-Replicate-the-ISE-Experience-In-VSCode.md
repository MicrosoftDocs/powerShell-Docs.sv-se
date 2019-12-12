---
title: Så här replikerar du ISE-upplevelsen i Visual Studio Code
description: Så här replikerar du ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: d5542e9a3a48b1ae64356309be669418edf6c79e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74117468"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Så här replikerar du ISE-upplevelsen i Visual Studio Code

Även om PowerShell-tillägget för VSCode inte söker efter slut på funktions paritet med PowerShell ISE finns det funktioner för att göra VSCode-upplevelsen mer naturlig för användare av ISE.

Det här dokumentet försöker visa en lista över inställningar som du kan konfigurera i VSCode för att göra det enklare att komma åt användarna jämfört med ISE.

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

Avsnittet "aktivitets fält" och "Felsök sid List" visas i den röda rutan:

![avsnittet är markerat och innehåller aktivitets fält och sid list för fel sökning](images/How-To-Replicate-the-ISE-Experience-In-VSCode/1-highlighted-sidebar.png)

Slut resultatet ser ut så här:

![Förenklad vy av VS Code](images/How-To-Replicate-the-ISE-Experience-In-VSCode/2-simplified-ui.png)

## <a name="tab-completion"></a>Slut för ande flik

Lägg till den här inställningen om du vill aktivera fler ISE-liknande flikar:

```json
"editor.tabCompletion": "on",
```

> [!NOTE]
> Den här inställningen lades till direkt i VSCode (i stället för i tillägget). Dess beteende bestäms av VSCode direkt och kan inte ändras av tillägget.

## <a name="no-focus-on-console-when-executing"></a>Ingen fokus på konsolen vid körning

För att behålla fokus i redigeraren när du kör med <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

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

## <a name="color-scheme"></a>Färgschema

Det finns ett antal ISE-teman som är tillgängliga för VSCode för att göra redigeraren att se mycket mer som ISE.

I [Kommando palett] typ `theme` för att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.
I list rutan väljer du `PowerShell ISE`.

Du kan ange det här temat i inställningarna med:

```json
"workbench.colorTheme": "PowerShell ISE",
```

## <a name="powershell-command-explorer"></a>PowerShell kommando Utforskaren

Till [@corbob](https://github.com/corbob)kommer PowerShell-tillägget att ha början av en egen kommando Utforskare.

I [Kommando palett]anger du `PowerShell Command Explorer` och trycker på <kbd>RETUR</kbd>.

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
