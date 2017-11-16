---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: aaf1809277f072c82e5a1a862ea64b75586e32d1
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="improvements-in-powershell-script-debugging"></a>Förbättringar i PowerShell-skript för felsökning

Ett antal förbättringar har gjorts i PowerShell 5.0 att förbättra Felsökning:

## <a name="break-all"></a>Bryt alla

PowerShell-konsolen och Windows PowerShell ISE nu kan du bryta in i felsökaren för att köra skript. Det här fungerar i både lokala och fjärranslutna sessioner.

I konsolen, trycker du på **Ctrl + Break**.

I ISE, trycker du på **Ctrl + B**, eller använda den **Debug -> Bryt alla** kommando.

## <a name="remote-debugging-and-remote-file-editing-in-windows-powershell-ise"></a>Fjärrfelsökning och Fjärrlagring redigering i Windows PowerShell ISE

Windows PowerShell ISE nu kan du öppna och redigera filer i en fjärrsession genom att köra kommandot PSEdit.
Du kan till exempel öppna en fil för redigering från kommandoraden i en fjärrsession på följande sätt:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Dessutom kan du nu redigera och spara ändringarna i en fjärrfil som öppnas automatiskt i Windows PowerShell ISE när du klickar på en brytpunkt.
Nu kan du felsöka en skriptfil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och kör sedan skriptet ändrade.

## <a name="advanced-script-debugging"></a>Felsökning av avancerade skript

Det finns nya, avancerad felsökning funktioner som gör att du kan ansluta till en lokal dator process som har lästs in Windows PowerShell och felsöka godtycklig körningsutrymmen i den här processen.

### <a name="runspace-debugging"></a>Runspace felsökning

Nya cmdletar har lagts till som du kan visa en lista över aktuella körningsutrymmen i en process och bifoga Windows PowerShell-konsolen eller ISE felsökare som runspace för felsökning av skript:

-   Get-Runspace
-   Felsök Runspace
-   Aktivera RunspaceDebug
-   Inaktivera RunspaceDebug
-   Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Koppla till Process som är värd för PowerShell

Nu kan du koppla till alla processer för datorn med Windows PowerShell som lästs in. Du kan göra detta genom att ange i en interaktiv session med processen, på samma sätt som hur du kan ange i en interaktiv fjärrsession genom att köra cmdleten Enter-PSSession:

-   Ange PSHostProcess
-   Avsluta PSHostProcess

