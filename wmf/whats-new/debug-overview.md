---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i felsökning av PowerShell-skript
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: 01b81317029b28dd9b61d167045fd31f1ec7bc06
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2019
ms.locfileid: "65856177"
---
# <a name="improvements-in-powershell-script-debugging"></a>Förbättringar i felsökning av PowerShell-skript

PowerShell 5.0 innehåller flera förbättringar som förbättrar upplevelsen för felsökning.

## <a name="break-all"></a>Bryt alla

PowerShell-konsolen och PowerShell ISE nu kan du bryta in i felsökaren för att köra skript. Detta fungerar i både lokala och fjärrskrivbord-sessioner.

I konsolen, trycker du på <kbd>Ctrl</kbd>+<kbd>bryta</kbd>.

I ISE, trycker du på <kbd>Ctrl</kbd>+<kbd>B</kbd>, eller Använd den **felsökning -> bryta alla** menykommandot.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Fjärrfelsökning och fjärrfil redigering i PowerShell ISE

PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.
Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i PowerShell ISE när du når en brytpunkt. Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan det ändrade skriptet.

## <a name="advanced-script-debugging"></a>Felsökning av avancerade skript

Det finns nya, avancerad felsökning funktioner som låter dig ansluta till en lokal dator-process som har lästs in PowerShell och felsöka godtyckliga körningsutrymmen i den här processen.

### <a name="runspace-debugging"></a>Körningsutrymme felsökning

Nya cmdletar har lagts till som gör att du listan aktuella körningsutrymmen i en process och koppla PowerShell-konsolen eller PowerShell ISE debugger till den körningsutrymme för felsökning av skript:

- Get-Körningsutrymme
- Debug-Runspace
- Enable-RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppla till Process som är värd för PowerShell

Nu kan du koppla till en dator-process som har lästs in PowerShell. Du kan göra detta genom att ange i en interaktiv session med värdprocessen. Mer information finns i följande avsnitt:

- [Ange PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Avsluta PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
