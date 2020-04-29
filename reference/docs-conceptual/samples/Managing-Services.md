---
ms.date: 06/05/2017
keywords: PowerShell, cmdlet
title: Hantera tjänster
ms.openlocfilehash: 7a238a3fea857c5dac1c12ca0d0371a49e6bf58c
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "75870531"
---
# <a name="managing-services"></a>Hantera tjänster

Det finns åtta Core Service-cmdletar som är utformade för ett brett utbud av tjänst uppgifter. Vi kommer bara att titta på att visa och ändra körnings tillstånd för tjänster, men du kan hämta en lista över tjänst- `Get-Help \*-Service`cmdletar med hjälp av, och du kan hitta information om `Get-Help <Cmdlet-Name>`varje tjänst- `Get-Help New-Service`cmdlet med hjälp av, till exempel.

## <a name="getting-services"></a>Hämtar tjänster

Du kan hämta tjänsterna på en lokal dator eller fjärrdator med hjälp av `Get-Service` cmdleten. Som med `Get-Process`kan du `Get-Service` använda kommandot utan parametrar för att returnera alla tjänster. Du kan filtrera efter namn, även använda en asterisk som jokertecken:

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

Du kan använda parametern ComputerName för Get-service-cmdlet: en för att hämta tjänsterna på fjärrdatorer. Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando. Följande kommando hämtar till exempel tjänsterna på den fjärranslutna Server01-datorn.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Hämtar nödvändiga och beroende tjänster

Cmdleten Get-service har två parametrar som är mycket användbara vid tjänst administration. Parametern DependentServices hämtar tjänster som är beroende av tjänsten. Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.

Dessa parametrar visar bara värdena för egenskaperna DependentServices och ServicesDependedOn (alias = RequiredServices) för objektet system. ServiceProcess. ServiceController som Get-service returnerar, men de fören klar kommandon och gör så att den här informationen blir mycket enklare.

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

Du kan till och med hämta alla tjänster som har beroenden. Följande kommando fungerar precis som och använder sedan Format-Table-cmdlet: en för att visa egenskaperna status, Name, RequiredServices och DependentServices för tjänsterna på datorn.

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

`Restart-Service` Cmdleten fungerar på samma sätt som de andra tjänst-cmdletarna, men vi kommer att visa några mer komplexa exempel för den. I den enklaste användningen anger du namnet på tjänsten:

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

Dessa tjänst-cmdletar har ingen ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command. Följande kommando startar till exempel om Spooler-tjänsten på fjärrdatorn Server01.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Ställer in tjänst egenskaper

`Set-Service` Cmdleten ändrar egenskaperna för en tjänst på en lokal eller fjärran sluten dator. Eftersom tjänstens status är en egenskap kan du använda denna cmdlet för att starta, stoppa och pausa en tjänst.
Cmdleten Set-service har också en Startuptype tjänst-parameter som låter dig ändra tjänstens starttyp.

Om du `Set-Service` vill använda i Windows Vista och senare versioner av Windows öppnar du Windows PowerShell med alternativet "kör som administratör".

Mer information finns i [set-service](/powershell/module/Microsoft.PowerShell.Management/set-service)

## <a name="see-also"></a>Se även

- [Get-Service](/powershell/module/Microsoft.PowerShell.Management/get-service)
- [Set-Service](/powershell/module/Microsoft.PowerShell.Management/set-service)
- [Restart-Service](/powershell/module/Microsoft.PowerShell.Management/restart-service)
- [Suspend-Service](/powershell/module/Microsoft.PowerShell.Management/suspend-service)
