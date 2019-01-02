---
title: Hur du replikerar ISE-upplevelsen i Visual Studio Code
description: Hur du replikerar ISE-upplevelsen i Visual Studio Code
ms.date: 08/06/2018
ms.openlocfilehash: 0ac38985a842a0dfc6118d0ae7116d12e1579daf
ms.sourcegitcommit: 548547b2d5fc73e726bb9fec6175d452a351d975
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/20/2018
ms.locfileid: "53655540"
---
# <a name="how-to-replicate-the-ise-experience-in-visual-studio-code"></a>Hur du replikerar ISE-upplevelsen i Visual Studio Code

PowerShell-tillägget för VSCode inte söker efter slutförd funktionsparitet med PowerShell ISE, men det finns funktioner för att göra VSCode-upplevelsen mer naturligt för användare av ISE.

Det här dokumentet försöker listinställningar som du kan konfigurera i VSCode för att användaren ska få lite mer bekant jämfört med ISE.

## <a name="key-bindings"></a>Nyckelbindningar

| Funktion                              | ISE-bindning                  | VSCode-bindning                              |
| ----------------                      | -----------                  | --------------                              |
| Felsökare för avbrott och reparation          | <kbd>CTRL</kbd>+<kbd>B</kbd> | <kbd>F6</kbd>                               |
| Köra aktuell rad/markerad text | <kbd>F8</kbd>                | <kbd>F8</kbd>                               |
| Lista tillgängliga kodfragment               | <kbd>CTRL</kbd>+<kbd>J</kbd> | <kbd>CTRL</kbd>+<kbd>Alt</kbd>+<kbd>J</kbd> |

### <a name="custom-key-bindings"></a>Den anpassade nyckeln bindningar

Du kan [konfigurera egna nyckelbindningar](https://code.visualstudio.com/docs/getstarted/keybindings#_custom-keybindings-for-refactorings) i VSCode samt.

## <a name="tab-completion"></a>Tabbifyllning

Lägg till den här inställningen om du vill aktivera fler ISE-liknande tabbifyllning:

```json
"editor.tabCompletion": "on"
```

> [!NOTE]
> Den här inställningen har lagts till direkt till VSCode (i stället för i tillägget). Sitt beteende bestäms av VSCode direkt och kan inte ändras av tillägget.

## <a name="no-focus-on-console-when-executing"></a>Inga fokus på konsolen när du kör

Att hålla fokus i redigeraren när du kör med <kbd>F8</kbd>:

```json
"powershell.integratedConsole.focusConsoleOnExecute": false
```

Standardvärdet är `true` för hjälpmedel.

## <a name="dont-start-integrated-console-on-startup"></a>Starta inte integrerad konsol vid start

Om du vill stoppa integrerad konsol vid start, ange:

```json
"powershell.integratedConsole.showOnStartup": false
```

> [!NOTE]
> Bakgrunden PowerShell-processen startar fortfarande eftersom som ger intellisense, skript analys, symbol navigering, osv. Men kommer inte att visas i konsolen.

## <a name="assume-files-are-powershell-by-default"></a>Anta att filer är PowerShell som standard

Registrera dig som PowerShell som standard för att se nya/Namnlös filer:

```json
"files.defaultLanguage": "powershell"
```

## <a name="color-scheme"></a>Färgschema

Det finns ett antal ISE teman för VSCode för att göra redigeraren Se mycket mer likt ISE.

I den [Kommandopalett] typ `theme` att hämta `Preferences: Color Theme` och tryck på <kbd>RETUR</kbd>.
I listrutan, väljer `PowerShell ISE`.

Du kan ange den här tema i inställningarna med:

```json
"workbench.colorTheme": "PowerShell ISE"
```

## <a name="powershell-command-explorer"></a>PowerShell-kommando Explorer

Tack vare verk som tillhör [ @corbob ](https://github.com/corbob), PowerShell-tillägget har början av en egen kommandot explorer.

I den [Kommandopalett], ange `PowerShell Command Explorer` och tryck på <kbd>RETUR</kbd>.

## <a name="open-in-the-ise"></a>Öppna i ISE

Om du hamnar vill öppna en fil i ISE ändå kan du använda <kbd>SKIFT</kbd>+<kbd>Alt</kbd>+<kbd>P</kbd>.

## <a name="other-resources"></a>Andra resurser

- 4sysops har [en bra artikel](https://4sysops.com/archives/make-visual-studio-code-look-and-behave-like-powershell-ise/) om hur du konfigurerar VSCode för att vara mer som ISE.
- Mike F Robbins har [ett bra inlägg](https://mikefrobbins.com/2017/08/24/how-to-install-visual-studio-code-and-configure-it-as-a-replacement-for-the-powershell-ise/) om hur du konfigurerar VSCode.
- Lär dig PowerShell har [en utmärkt Skriv upp](https://www.learnpwsh.com/setup-vs-code-for-powershell/) på att få VSCode installationsprogrammet för PowerShell.

## <a name="more-settings"></a>Fler inställningar

Om du känner av fler sätt att göra VSCode känna dig mer bekant för ISE-användare kan bidra till det här dokumentet. Om det finns en konfiguration för kompatibilitet som du letar efter, men du kan inte hitta några sätt att göra det möjligt för [öppna ett ärende](https://github.com/PowerShell/vscode-powershell/issues/new/choose) och fråga!

Vi är alltid glada över att acceptera pull-begäranden och bidrag samt!

## <a name="vscode-tips"></a>Tips för VSCode

### <a name="command-palette"></a>Kommandopalett

<kbd>F1</kbd> eller <kbd>Ctrl</kbd>+<kbd>SKIFT</kbd>+<kbd>P</kbd> (<kbd>Cmd</kbd> + <kbd> Flytta</kbd>+<kbd>P</kbd> på macOS)

Ett praktiskt sätt att köra kommandon i VSCode.
Mer information finns i [VSCode docs](https://code.visualstudio.com/docs/getstarted/userinterface#_command-palette).

[Kommandopalett]: #command-palette
