---
title: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
description: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
ms.date: 06/13/2019
ms.openlocfilehash: ae3b7a3709498fcd547a48d0849b0dc880217225
ms.sourcegitcommit: 13f24786ed39ca1c07eff2b73a1974c366e31cb8
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/19/2019
ms.locfileid: "67263979"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Använda Visual Studio Code för att fjärredigera och fjärrfelsöka

För dig som är bekanta med ISE, du kanske kommer ihåg att du kan köra `psedit file.ps1` från integrerad konsol för att öppna filer – lokal eller fjärransluten - Högerklicka i ISE.

Den här funktionen är också tillgänglig i PowerShell-tillägget för VSCode. Den här guiden visar hur du gör den.

## <a name="prerequisites"></a>Förutsättningar

Den här guiden förutsätter att du har:

- en fjärransluten resurs (t.ex.: en virtuell dator, en behållare) att du har åtkomst till
- PowerShell som körs på den och värddatorn
- VSCode och PowerShell-tillägget för VSCode

Den här funktionen fungerar i Windows PowerShell och PowerShell Core.

Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH. Om du vill använda SSH, men använder Windows, Kolla in den [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> Den `Open-EditorFile` och `psedit` kommandona fungerar bara den **PowerShell integrerad konsol** som skapas av PowerShell-tillägget för VSCode.

## <a name="usage-examples"></a>Exempel på användning

De här exemplen visar remote redigering och felsökning från en MacBook Pro för en Ubuntu-VM som körs i Azure. Processen är identiska på Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Lokal fil Redigera med öppen EditorFile

Med PowerShell-tillägget för VSCode igång och integrerad PowerShell-konsolen öppnas, vi kan skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` att öppna lokala foo.ps1 fil direkt i redigeraren.

![Öppna EditorFile foo.ps1 arbetar lokalt](images/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Filen `foo.ps1` måste redan finnas.

Därifrån kan vi:

- Lägga till brytpunkter fästmarginalen

  ![att lägga till brytpunkt till fästmarginalen](images/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Tryck på F5 för att felsöka PowerShell-skriptet.

  ![Felsökning av lokal PowerShell-skriptet](images/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

När du felsöker, kan du interagera med Felsökningskonsolen, Kolla in variabler i området till vänster och de andra vanliga felsökningsverktyg.

### <a name="remote-file-editing-with-open-editorfile"></a>Fjärrfil Redigera med öppen EditorFile

Nu ska vi gå in fjärrfil redigering och felsökning. Stegen är nästan desamma finns det bara en sak som vi behöver göra först - ange våra PowerShell-session till fjärrservern.

Det finns en cmdlet för att göra detta. Den kallas `Enter-PSSession`.

Watered ned förklaring av cmdlet: en är:

- `Enter-PSSession -ComputerName foo` startar en session via WinRM
- `Enter-PSSession -ContainerId foo` och `Enter-PSSession -VmId foo` starta en session via PowerShell Direct
- `Enter-PSSession -HostName foo` startar en session via SSH

Mer information finns i dokumentationen för [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Eftersom vi från macOS en Ubuntu VM i Azure, använder vi SSH för fjärrkommunikation.

Kör först följande i konsolen integrerad `Enter-PSSession`. Du är ansluten till fjärrsessionen när `[<hostname>]` visar upp till vänster om din fråga.

![Anropet till Enter-PSSession](images/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Nu kan vi göra likadant som om vi redigerar ett lokalt skript.

1. Kör `Open-EditorFile test.ps1` eller `psedit test.ps1` att öppna fjärransluten `test.ps1` fil

  ![Öppna EditorFile test.ps1-fil](images/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Redigera filen/set-brytpunkter

   ![Redigera och ange brytpunkter](images/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Starta felsökning (F5) fjärrfilen

   ![Felsökning fjärrfilen](images/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Om du har problem kan du öppna problem i den [GitHub-lagringsplatsen](https://github.com/powershell/vscode-powershell).
