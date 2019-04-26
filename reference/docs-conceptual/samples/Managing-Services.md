---
ms.date: 06/05/2017
keywords: PowerShell cmdlet
title: Hantera tjänster
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: 81fd8802215da80ce22fa3fd4750b1df6efe8206
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62086195"
---
# <a name="managing-services"></a>Hantera tjänster

Det finns åtta kärnor cmdlet: ar, avsedd för en mängd olika uppgifter för tjänsten. Vi bara lista och ändra körningstillstånd för tjänster, men du kan hämta en lista över cmdlet: ar med hjälp av `Get-Help \*-Service`, och du hittar information om varje tjänst-cmdlet med hjälp av `Get-Help <Cmdlet-Name>`, till exempel `Get-Help New-Service`.

## <a name="getting-services"></a>Hämta tjänster

Du kan hämta tjänsterna på en lokal eller fjärransluten dator med hjälp av den `Get-Service` cmdlet. Precis som med `Get-Process`med hjälp av den `Get-Service` utan parametrar returnerar alla tjänster. Du kan filtrera efter namn, även med en asterisk som jokertecken:

```powershell
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Eftersom det inte är alltid uppenbart vad som är det verkliga namnet för tjänsten, kanske du vill söka efter tjänster efter visningsnamn. Du kan göra detta efter specifika namn med jokertecken eller med en lista med namn som visas:

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

Du kan använda parametern ComputerName för cmdlet Get-Service för att få tjänsterna på fjärrdatorer. Parametern ComputerName accepterar flera värden och jokertecken, så att du kan hämta tjänsterna på flera datorer med ett enda kommando. Följande kommando hämtar tjänsterna på fjärrdatorn Server01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Hämta krävs och beroende tjänster

Cmdleten Get-Service har två parametrar som är mycket användbar för administration av tjänster. Parametern DependentServices hämtar tjänster som är beroende av tjänsten. Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende av.

Dessa parametrar kan bara visa värdena i DependentServices och ServicesDependedOn (alias = RequiredServices) egenskaperna för objektet System.ServiceProcess.ServiceController som gör det enklare för Get-Service returnerar, men de kommandon och göra komma den här informationen är mycket enklare.

Följande kommando hämtar de tjänster som krävs för LanmanWorkstation-tjänsten.

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

Du kan även få alla tjänster som har beroenden. Kommandot gör just detta och sedan används Format-Table-cmdlet för att visa Status, namn, RequiredServices och DependentServices egenskaperna för tjänsterna på datorn.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Stoppa, starta, pausa och startar om tjänster

De cmdlet: ar alla ha samma allmänna formulär. Tjänster kan anges med egna namn eller visningsnamn och ta listor och jokertecken som värden. Om du vill stoppa utskriftshanteraren, använder du:

```powershell
Stop-Service -Name spooler
```

För att starta utskriftshanteraren när den är stoppad, använder du:

```powershell
Start-Service -Name spooler
```

Om du vill pausa Utskriftshanteraren, använder du:

```powershell
Suspend-Service -Name spooler
```

Den `Restart-Service` cmdlet fungerar på samma sätt som den andra cmdlet: ar, men vi visar några mer komplexa exempel för den. I det enklaste användningsområdet anger du namnet på tjänsten:

```powershell
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Du ser att du får ett upprepade varningsmeddelande om utskriftshanteraren startar. När du utför en åtgärd i tjänsten som tar lite tid, meddelar Windows PowerShell dig att den fortfarande försöker utföra åtgärden.

Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och genomföra omstarten:

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

Dessa cmdlet: ar har inte en ComputerName-parameter, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command. Till exempel följande kommando startar om utskriftshanteraren Server01 fjärrdatorn.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Egenskaper för tjänsten

Den `Set-Service` cmdlet ändrar egenskaperna för en tjänst på en lokal eller fjärransluten dator. Eftersom status för tjänsten är en egenskap, kan du använda denna cmdlet för att starta, stoppa och inaktivera en tjänst.
Cmdleten Set-Service har också en startuptype för parameter som du kan ändra starttypen för tjänsten.

Att använda `Set-Service` på Windows Vista och senare versioner av Windows, öppnar du Windows PowerShell med alternativet ”Kör som administratör”.

Mer information finns i [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Se även

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Set-Service [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Restart-Service [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Suspend-Service [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)