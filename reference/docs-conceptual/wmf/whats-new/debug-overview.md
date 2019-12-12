---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
title: Förbättringar i felsökning av PowerShell-skript
ms.openlocfilehash: f1771a451ba671da2371fcfc95374e6131573ddc
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71145182"
---
# <a name="improvements-in-powershell-script-debugging"></a>Förbättringar i felsökning av PowerShell-skript

PowerShell 5,0 innehåller flera förbättringar som förbättrar fel söknings upplevelsen.

## <a name="break-all"></a>Bryt alla

Med PowerShell-konsolen och PowerShell ISE kan du nu dela upp det i fel söknings programmet för skript körning. Detta fungerar både i lokala och fjärranslutna sessioner.

Tryck på <kbd>Ctrl</kbd>+<kbd>Break</kbd>i-konsolen.

Tryck på <kbd>Ctrl</kbd>+<kbd>B</kbd>i ISE eller använd kommandot **Debug-> Bryt alla** Meny kommandon.

## <a name="remote-debugging-and-remote-file-editing-in-powershell-ise"></a>Fjärrfelsökning och fjärrstyrd fil redigering i PowerShell ISE

Nu kan du öppna och redigera filer i en fjärrsession med PowerShell ISE genom att köra kommandot PSEdit.
Du kan till exempel öppna en fil för redigering från kommando raden i en fjärrsession enligt följande:

```powershell
[RemoteComputer1]: PS C:\> PSEdit C:\DebugDemoScripts\Test-GetMutex.ps1
```

Dessutom kan du nu redigera och spara ändringar i en fjärrfil som öppnas automatiskt i PowerShell ISE när du trycker på en Bryt punkt. Nu kan du Felsöka en skript fil som körs på en fjärrdator, redigera filen för att åtgärda ett fel och sedan köra det ändrade skriptet igen.

## <a name="advanced-script-debugging"></a>Avancerad skript fel sökning

Det finns nya, avancerade fel söknings funktioner som gör att du kan ansluta till en lokal dator process som har läst in PowerShell och felsöka godtyckliga körnings utrymmen i den processen.

### <a name="runspace-debugging"></a>Körnings utrymme-felsökning

Nya cmdletar har lagts till som gör att du kan lista aktuella körnings utrymmen i en process och koppla PowerShell-konsolen eller PowerShell ISE-felsökaren till den körnings utrymme för skript fel sökning:

- Get-körnings utrymme
- Felsök – körnings utrymme
- Aktivera – RunspaceDebug
- Disable-RunspaceDebug
- Get-RunspaceDebug

### <a name="attach-to-process-hosting-powershell"></a>Ansluta till process hosting PowerShell

Nu kan du ansluta till en dator process som har PowerShell inläst. Du gör detta genom att ange en interaktiv session med värd processen. Mer information finns i följande avsnitt:

- [Retur-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Enter-PSHostProcess)
- [Avsluta-PSHostProcess](/powershell/module/Microsoft.PowerShell.Core/Exit-PSHostProcess)
