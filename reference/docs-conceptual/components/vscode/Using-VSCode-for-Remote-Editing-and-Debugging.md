---
title: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
description: Använda Visual Studio Code för att fjärredigera och fjärrfelsöka
ms.date: 06/13/2019
ms.openlocfilehash: 5ce7f575d90ff47fd6b8a0a2b567e972ec3a9fef
ms.sourcegitcommit: 01c60c0c97542dbad48ae34339cddbd813f1353b
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/04/2020
ms.locfileid: "78279179"
---
# <a name="using-visual-studio-code-for-remote-editing-and-debugging"></a>Använda Visual Studio Code för att fjärredigera och fjärrfelsöka

För de som är bekanta med ISE kan du återkalla att du kan köra `psedit file.ps1` från den integrerade konsolen för att öppna filer – lokalt eller fjärranslutna i ISE.

Den här funktionen är även tillgänglig i PowerShell-tillägget för VSCode. Den här guiden visar hur du gör.

## <a name="prerequisites"></a>Förutsättningar

Den här guiden förutsätter att du har:

- En fjär resurs (t. ex. en virtuell dator, en behållare) som du har åtkomst till
- PowerShell som körs på den och värddatorn
- VSCode och PowerShell-tillägget för VSCode

Den här funktionen fungerar i Windows PowerShell och PowerShell Core.

Den här funktionen fungerar även när du ansluter till en fjärrdator via WinRM, PowerShell Direct eller SSH. Om du vill använda SSH, men använder Windows, kontrollerar du [Win32-versionen av SSH](https://github.com/PowerShell/Win32-OpenSSH)!

> [!IMPORTANT]
> Kommandona `Open-EditorFile` och `psedit` fungerar bara i den **integrerade PowerShell-konsolen** som skapats av PowerShell-tillägget för VSCode.

## <a name="usage-examples"></a>Användnings exempel

De här exemplen visar fjärrredigering och fel sökning från en MacBook Pro till en Ubuntu-VM som körs i Azure. Processen är identisk med Windows.

### <a name="local-file-editing-with-open-editorfile"></a>Lokal fil redigering med Open-EditorFile

Med PowerShell-tillägget för VSCode igång och den integrerade PowerShell-konsolen öppnas, kan vi skriva `Open-EditorFile foo.ps1` eller `psedit foo.ps1` för att öppna den lokala foo. ps1-filen direkt i redigeraren.

![Open-EditorFile foo. ps1 fungerar lokalt](media/Using-VSCode-for-Remote-Editing-and-Debugging/1-open-local-file.png)

>[!NOTE]
> Filen `foo.ps1` måste redan finnas.

Därifrån kan vi:

- Lägga till Bryt punkter i fästmarginal

  ![lägga till Bryt punkt i fästmarginal](media/Using-VSCode-for-Remote-Editing-and-Debugging/2-adding-breakpoint-gutter.png)

- Tryck på F5 för att felsöka PowerShell-skriptet.

  ![Felsöka det lokala PowerShell-skriptet](media/Using-VSCode-for-Remote-Editing-and-Debugging/3-local-debug.png)

Vid fel sökning kan du interagera med fel söknings konsolen, kolla in variablerna i omfånget till vänster och alla andra standard verktyg för fel sökning.

### <a name="remote-file-editing-with-open-editorfile"></a>Fjärrstyrd redigering med Open-EditorFile

Nu ska vi komma igång med att redigera och felsöka filer. Stegen är nästan desamma, men det är bara en sak vi behöver göra för att först fylla i PowerShell-sessionen till fjärrservern.

Det finns en cmdlet för att göra detta. Den heter `Enter-PSSession`.

Den nedrullningsbara förklaringen av cmdleten är:

- `Enter-PSSession -ComputerName foo` startar en session via WinRM
- `Enter-PSSession -ContainerId foo` och `Enter-PSSession -VmId foo` starta en-session via PowerShell Direct
- `Enter-PSSession -HostName foo` startar en-session via SSH

Mer information finns i dokumentationen för [Enter-PSSession](/powershell/module/microsoft.powershell.core/enter-pssession).

Eftersom vi kommer från macOS till en virtuell Ubuntu-dator i Azure använder vi SSH för fjärr kommunikation.

Börja med att köra `Enter-PSSession`i den integrerade konsolen. Du är ansluten till fjärrsessionen när `[<hostname>]` visas till vänster om din prompt.

![Anropet till retur-PSSession](media/Using-VSCode-for-Remote-Editing-and-Debugging/4-enter-pssession.png)

Nu kan vi utföra samma steg som om vi redigerar ett lokalt skript.

1. Kör `Open-EditorFile test.ps1` eller `psedit test.ps1` för att öppna den fjärranslutna `test.ps1` filen

  ![Öppna – EditorFile filen test. ps1](media/Using-VSCode-for-Remote-Editing-and-Debugging/5-open-remote-file.png)

1. Redigera fil-/uppsättnings Bryt punkter

   ![Redigera och ange Bryt punkter](media/Using-VSCode-for-Remote-Editing-and-Debugging/6-set-breakpoints.png)

1. Starta fel sökning (F5) fjärrfilen

   ![Felsöka fjärrfilen](media/Using-VSCode-for-Remote-Editing-and-Debugging/7-start-debugging.png)

Om du har problem kan du öppna problem i [GitHub-lagrings platsen](https://github.com/powershell/vscode-powershell).
