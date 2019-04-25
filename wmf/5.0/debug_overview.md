---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 22a027ebc97e15075980bc77ce272d8ecdae0b5f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62058673"
---
# <a name="improvements-in-powershell-script-debugging"></a>Förbättringar i felsökning av PowerShell-skript

Ett antal förbättringar har gjorts i PowerShell 5.0 att förbättra felsökningen:

## <a name="break-all"></a>Bryt alla

PowerShell-konsolen och Windows PowerShell ISE nu kan du bryta in i felsökaren för att köra skript. Detta fungerar i både lokala och fjärrskrivbord-sessioner.

I konsolen, trycker du på **Ctrl + Break**.

I ISE, trycker du på **Ctrl + B**, eller Använd den **felsökning -> bryta alla** menykommandot.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Fjärrfelsökning och fjärrfil redigering i Windows PowerShell ISE

Windows PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.
Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i Windows PowerShell ISE när du når en brytpunkt.
Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan det ändrade skriptet.

## <a name="advanced-script-debugging"></a>Felsökning av avancerade skript

Det finns nya, avancerad felsökning funktioner som låter dig ansluta till en lokal dator-process som har lästs in Windows PowerShell och felsöka godtyckliga körningsutrymmen i den här processen.

### <a name="runspace-debugging"></a>Körningsutrymme felsökning

Nya cmdletar har lagts till som gör att du listan aktuella körningsutrymmen i en process och koppla i Windows PowerShell-konsolen eller ISE debugger till den körningsutrymme för felsökning av skript:

-   Get-Körningsutrymme
-   Debug-Runspace
-   Enable-RunspaceDebug
-   Disable-RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppla till Process som är värd för PowerShell

Nu kan du koppla till alla processer för datorn med Windows PowerShell som lästs in. Du kan göra detta genom att ange i en interaktiv session med processen, på samma sätt som hur du anger i en interaktiv fjärrsession genom att köra cmdleten Enter-PSSession:

-   Ange PSHostProcess
-   Avsluta PSHostProcess
