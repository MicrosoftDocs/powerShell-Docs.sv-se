---
ms.date: 06/05/2017
keywords: powershell,cmdlet
title: Hantera tjänster
description: PowerShell innehåller flera cmdletar som hjälper dig att hantera tjänster på lokala och fjärranslutna datorer.
ms.openlocfilehash: 003803cdaa37e51b3788f3f897cbec7d6e243ca8
ms.sourcegitcommit: 9080316e3ca4f11d83067b41351531672b667b7a
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/24/2020
ms.locfileid: "92500359"
---
# <a name="managing-services"></a>Hantera tjänster

Det finns åtta Core Service-cmdletar som är utformade för ett brett utbud av tjänst uppgifter. Vi kommer bara att titta på att visa och ändra körnings tillstånd för tjänster, men du kan hämta en lista över tjänst-cmdletar med hjälp av `Get-Help \*-Service` , och du kan hitta information om varje tjänst-cmdlet med hjälp av `Get-Help <Cmdlet-Name>` , till exempel `Get-Help New-Service` .

## <a name="getting-services"></a>Hämtar tjänster

Du kan hämta tjänsterna på en lokal dator eller fjärrdator med hjälp av `Get-Service` cmdleten. Som med `Get-Process` kan du använda `Get-Service` kommandot utan parametrar för att returnera alla tjänster. Du kan filtrera efter namn, även använda en asterisk som jokertecken:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Eftersom det inte alltid är uppenbart vad det riktiga namnet för tjänsten är, kan du hitta tjänster efter visnings namn. Du kan göra detta med ett angivet namn, använda jokertecken eller med en lista med visnings namn:

```powershell
PS> Get-Service -DisplayName se*

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Running  SamSs              Security Accounts Manager
Running  seclogon           Secondary Logon
Stopped  ServiceLayer       ServiceLayer
Running  wscsvc             Security Center

PS> Get-Service -DisplayName ServiceLayer,Server

Status   Name               DisplayName
------   ----               -----------
Running  lanmanserver       Server
Stopped  ServiceLayer       ServiceLayer
```

Du kan använda parametern ComputerName i Get-Service-cmdlet: en för att hämta tjänsterna på fjärrdatorer. Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando. Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Hämtar nödvändiga och beroende tjänster

Get-Service-cmdlet har två parametrar som är mycket användbara i tjänst administration. Parametern DependentServices hämtar tjänster som är beroende av tjänsten. Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.

Dessa parametrar visar bara värdena för egenskaperna DependentServices och ServicesDependedOn (alias = RequiredServices) för objektet system. ServiceProcess. ServiceController som Get-Service returnerar, men de fören klar kommandona och gör att den här informationen blir mycket enklare.

Följande kommando hämtar de tjänster som LanmanWorkstation-tjänsten kräver.

```powershell
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Följande kommando hämtar de tjänster som kräver LanmanWorkstation-tjänsten.

```powershell
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Du kan till och med hämta alla tjänster som har beroenden. Följande kommando gör bara det och använder sedan Format-Table-cmdlet för att visa egenskaperna status, Name, RequiredServices och DependentServices för tjänsterna på datorn.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} |
  Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Stoppa, starta, pausa och starta om tjänster

Alla tjänst-cmdletar har samma generella form. Tjänster kan anges med eget namn eller visnings namn och ta listor och jokertecken som värden. Om du vill stoppa utskrifts hanteraren använder du:

```powershell
Stop-Service -Name spooler
```

Starta utskrifts hanteraren när den har stoppats genom att använda:

```powershell
Start-Service -Name spooler
```

Om du vill pausa utskrifts hanteraren använder du:

```powershell
Suspend-Service -Name spooler
```

`Restart-Service`Cmdleten fungerar på samma sätt som de andra tjänst-cmdletarna, men vi kommer att visa några mer komplexa exempel för den. I den enklaste användningen anger du namnet på tjänsten:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Du ser att du får ett upprepande varnings meddelande om utskrifts hanteraren startar. När du utför en tjänst åtgärd som tar en stund meddelar Windows PowerShell dig att den fortfarande försöker utföra uppgiften.

Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och sedan utföra omstarten:

```powershell
PS> Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service

WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
WARNING: Waiting for service 'Computer Browser (Browser)' to finish stopping...
Restart-Service : Cannot stop service 'Logical Disk Manager (dmserver)' because
 it has dependent services. It can only be stopped if the Force flag is set.
At line:1 char:57
+ Get-Service | Where-Object -FilterScript {$_.CanStop} | Restart-Service <<<<
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
```

Dessa tjänst-cmdletar har ingen ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av Invoke-Command-cmdleten. Följande kommando startar till exempel om Spooler-tjänsten på fjärrdatorn Server01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Ställer in tjänst egenskaper

`Set-Service`Cmdleten ändrar egenskaperna för en tjänst på en lokal eller fjärran sluten dator. Eftersom tjänstens status är en egenskap kan du använda denna cmdlet för att starta, stoppa och pausa en tjänst.
Set-Service cmdlet har också en Startuptype tjänst-parameter som låter dig ändra tjänstens starttyp.

Om du vill använda `Set-Service` i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet "kör som administratör".

Mer information finns i [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service)

## <a name="see-also"></a>Se även

- [Get-Service](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [Restart-Service](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [Suspend-Service](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
