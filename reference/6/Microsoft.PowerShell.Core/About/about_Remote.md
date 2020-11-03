---
description: Beskriver hur du kör fjärrkommandon i PowerShell.
keywords: powershell,cmdlet
Locale: en-US
ms.date: 01/03/2018
online version: https://docs.microsoft.com/powershell/module/microsoft.powershell.core/about/about_remote?view=powershell-6&WT.mc_id=ps-gethelp
schema: 2.0.0
title: about_Remote
ms.openlocfilehash: 04c297f849a30ddabecec98a5a2250b8d9b3fbfa
ms.sourcegitcommit: f874dc1d4236e06a3df195d179f59e0a7d9f8436
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/13/2020
ms.locfileid: "93270495"
---
# <a name="about-remote"></a>Om fjärran sluten

## <a name="short-description"></a>KORT BESKRIVNING
Beskriver hur du kör fjärrkommandon i PowerShell.

## <a name="long-description"></a>LÅNG BESKRIVNING

Du kan köra fjärrkommandon på en enskild dator eller på flera datorer genom att använda en tillfällig eller permanent anslutning. Du kan också starta en interaktiv session med en enda fjärran sluten dator.

Det här avsnittet innehåller en serie exempel som visar hur du kör olika typer av fjärrkommandon. När du har provat de här grundläggande kommandona läser du de hjälp avsnitt som beskriver varje cmdlet som används i de här kommandona. Avsnitten innehåller information och förklarar hur du kan ändra kommandona så att de passar dina behov.

Obs: om du vill använda PowerShell-fjärrkommunikation måste lokala och fjärranslutna datorer konfigureras för fjärr kommunikation. Mer information finns i [about_Remote_Requirements](about_Remote_Requirements.md).

## <a name="how-to-start-an-interactive-session-enter-pssession"></a>STARTA EN INTERAKTIV SESSION (RETUR-PSSESSION)

Det enklaste sättet att köra fjärrkommandon är att starta en interaktiv session med en fjärran sluten dator.

När sessionen startar, de kommandon som du skriver körs på fjärrdatorn, precis som om du skrev dem direkt på fjärrdatorn. Du kan bara ansluta till en dator i varje interaktiv session.

Använd Enter-PSSession-cmdleten för att starta en interaktiv session. Följande kommando startar en interaktiv session med Server01-datorn:

```powershell
Enter-PSSession Server01
```

Kommando tolken ändras för att indikera att du är ansluten till Server01-datorn.

```
Server01\PS>
```

Nu kan du skriva kommandon på Server01-datorn.

Om du vill avsluta den interaktiva sessionen skriver du:

```powershell
Exit-PSSession
```

Mer information finns i Enter-PSSession.

## <a name="how-to-use-cmdlets-that-have-a-computername-parameter-to-get-remote-data"></a>SÅ HÄR ANVÄNDER DU CMDLETAR SOM HAR EN COMPUTERNAME-PARAMETER FÖR ATT HÄMTA FJÄRRDATA

Flera cmdlets har en ComputerName-parameter som låter dig hämta objekt från fjärrdatorer.

Eftersom dessa cmdlets inte använder WS-Management-baserade PowerShell-fjärrkommunikationer kan du använda parametern ComputerName för dessa cmdlet: ar på alla datorer som kör PowerShell. Datorerna behöver inte konfigureras för PowerShell-fjärrkommunikation och datorerna behöver inte uppfylla system kraven för fjärr kommunikation.

Följande cmdletar har en ComputerName-parameter:

```
Clear-EventLog    Limit-EventLog
Get-Counter       New-EventLog
Get-EventLog      Remove-EventLog
Get-HotFix        Restart-Computer
Get-Process       Show-EventLog
Get-Service       Stop-Computer
Get-WinEvent      Test-Connection
Get-WmiObject     Write-EventLog
```

Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn:

```powershell
Get-Service -ComputerName Server01
```

Normalt har cmdletar som stöder fjärr kommunikation utan särskild konfiguration en **computername** -parameter och har inte någon **session** -parameter. Om du vill hitta dessa cmdletar i din session skriver du:

```powershell
Get-Command | Where-Object {
  $_.Parameters.Keys -contains 'ComputerName' -and
  $_.Parameters.Keys -notcontains 'Session'
}
```

## <a name="how-to-run-a-remote-command"></a>SÅ HÄR KÖR DU ETT FJÄRRKOMMANDO

Använd Invoke-Command-cmdleten om du vill köra andra kommandon på fjärrdatorer.

Om du vill köra ett enda kommando eller några orelaterade kommandon använder du parametern ComputerName i Invoke-Command för att ange fjärrdatorerna. Använd parametern script block för att ange kommandot.

Följande kommando kör till exempel ett Get-Culture-kommando på Server01-datorn.

```powershell
Invoke-Command -ComputerName Server01 -ScriptBlock {Get-Culture}
```

Parametern ComputerName är utformad för situationer där du kör ett enda kommando eller flera orelaterade kommandon på en eller flera datorer. Använd parametern session för att upprätta en permanent anslutning till en fjärrdator.

## <a name="how-to-create-a-persistent-connection-pssession"></a>SÅ HÄR SKAPAR DU EN PERMANENT ANSLUTNING (PSSESSION)

När du använder parametern ComputerName i Invoke-Command-cmdlet: en upprättar Windows PowerShell en anslutning enbart för kommandot. Sedan stängs anslutningen när kommandot har slutförts. Variabler eller funktioner som definieras i kommandot går förlorade.

Använd New-PSSession-cmdleten om du vill skapa en permanent anslutning till en fjärrdator. Följande kommando skapar till exempel PSSessions på Server01-och Server02-datorerna och sparar PSSessions i variabeln $s.

```powershell
$s = New-PSSession -ComputerName Server01, Server02
```

## <a name="how-to-run-commands-in-a-pssession"></a>KÖRA KOMMANDON I EN PSSESSION

Med en PSSession kan du köra en serie fjärrkommandon som delar data, t. ex. funktioner, alias och värden för variabler. Om du vill köra kommandon i en PSSession använder du parametern session i Invoke-Command-cmdleten.

Följande kommando använder exempelvis cmdleten Invoke-Command för att köra ett Get-Process kommando i PSSessions på Server01-och Server02-datorerna.
Kommandot sparar processerna i en $p-variabel i varje PSSession.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p = Get-Process}
```

Eftersom PSSession använder en permanent anslutning kan du köra ett annat kommando i samma PSSession som använder variabeln $p. Följande kommando räknar antalet processer som har sparats i $p.

```powershell
Invoke-Command -Session $s -ScriptBlock {$p.count}
```

## <a name="how-to-run-a-remote-command-on-multiple-computers"></a>SÅ HÄR KÖR DU ETT FJÄRRKOMMANDO PÅ FLERA DATORER

Om du vill köra ett fjärrkommando på flera datorer skriver du alla dator namn i värdet för parametern ComputerName för Invoke-Command. Avgränsa namnen med kommatecken.

Följande kommando kör till exempel ett Get-Culture-kommando på tre datorer:

```powershell
Invoke-Command -ComputerName S1, S2, S3 -ScriptBlock {Get-Culture}
```

Du kan också köra ett kommando i flera PSSessions. Följande kommandon skapar PSSessions på Server01-, Server02-och Server03-datorerna och kör sedan ett Get-Culture-kommando i varje PSSessions.

```powershell
$s = New-PSSession -ComputerName S1, S2, S3
Invoke-Command -Session $s -ScriptBlock {Get-Culture}
```

Om du vill ta med listan med lokala datorer, skriver du namnet på den lokala datorn, anger en punkt (.) eller skriver "localhost".

```powershell
Invoke-Command -ComputerName S1, S2, S3, localhost -ScriptBlock {Get-Culture}
```

## <a name="how-to-run-a-script-on-remote-computers"></a>SÅ HÄR KÖR DU ETT SKRIPT PÅ FJÄRRDATORER

Om du vill köra ett lokalt skript på fjärrdatorer använder du parametern sökväg för Invoke-Command.

Följande kommando kör till exempel Sample.ps1-skriptet på datorerna S1 och S2:

```powershell
Invoke-Command -ComputerName S1, S2 -FilePath C:\Test\Sample.ps1
```

Resultatet av skriptet returneras till den lokala datorn. Du behöver inte kopiera några filer.

## <a name="how-to-stop-a-remote-command"></a>SÅ HÄR STOPPAR DU ETT FJÄRRKOMMANDO

Tryck på CTRL + C om du vill avbryta ett kommando. Avbrottsbegäran skickas till fjärrdatorn där den avslutar fjärrkommandot.

## <a name="for-more-information"></a>MER INFORMATION

- Information om system kraven för fjärr kommunikation finns i [about_Remote_Requirements](about_Remote_Requirements.md).

- Information om hur du formaterar fjärrutdata finns i [about_Remote_Output](about_Remote_Output.md).

- Information om hur fjärr kommunikation fungerar, hur du hanterar fjärrdata, särskilda konfigurationer, säkerhets problem och andra vanliga frågor finns [about_Remote_FAQ](about_Remote_FAQ.md).

- Information om hur du löser fjärr kommunikations fel finns i about_Remote_Troubleshooting.

- Information om PSSessions och beständiga anslutningar finns [about_PSSessions](about_PSSessions.md).

- Information om PowerShell-bakgrunds jobb finns i [about_Jobs](about_Jobs.md).

## <a name="keywords"></a>RESERVERADE

about_Remoting

## <a name="see-also"></a>SE ÄVEN

[about_PSSessions](about_PSSessions.md)

[about_Remote_Disconnected_Sessions](about_Remote_Disconnected_Sessions.md)

[about_Remote_Requirements](about_Remote_Requirements.md)

[about_Remote_FAQ](about_Remote_FAQ.md)

[about_Remote_TroubleShooting](about_Remote_TroubleShooting.md)

[about_Remote_Variables](about_Remote_Variables.md)

[Retur-PSSession](xref:Microsoft.PowerShell.Core.Enter-PSSession)

[Invoke-kommando](xref:Microsoft.PowerShell.Core.Invoke-Command)

[New-PSSession](xref:Microsoft.PowerShell.Core.New-PSSession)
