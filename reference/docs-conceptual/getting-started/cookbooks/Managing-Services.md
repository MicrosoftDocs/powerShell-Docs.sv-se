---
ms.date: 06/05/2017
keywords: PowerShell-cmdlet
title: Hantera tjänster
ms.assetid: 7a410e4d-514b-4813-ba0c-0d8cef88df31
ms.openlocfilehash: f3231d1922568e552534f3d3face3864d1610d65
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
ms.locfileid: "30951206"
---
# <a name="managing-services"></a>Hantera tjänster

Det finns åtta kärnor cmdlet: ar, utformad för en mängd olika uppgifter för tjänsten. Beskrivs bara visa och ändra körs för tjänster, men du kan hämta en lista cmdlet: ar med hjälp av **Get-Help \&#42;-tjänsten**, och du kan hitta information om varje tjänst-cmdlet med hjälp av **Get-Help < Cmdlet Name >**, som **Get-Help ny tjänst**.

## <a name="getting-services"></a>Hämta tjänster

Du kan hämta tjänsterna på en lokal eller fjärransluten dator med hjälp av den **Get-Service** cmdlet. Precis som med **Get-Process**med hjälp av den **Get-Service** utan parametrar returnerar alla tjänster. Du kan filtrera efter namn, även med en asterisk som jokertecken:

```
PS> Get-Service -Name se*

Status   Name               DisplayName
------   ----               -----------
Running  seclogon           Secondary Logon
Running  SENS               System Event Notification
Stopped  ServiceLayer       ServiceLayer
```

Eftersom det inte alltid är uppenbara verkliga namn för tjänsten är, kanske du vill söka efter tjänster enligt visningsnamn. Du kan göra detta efter specifika namn med jokertecken eller med en lista över visningsnamn:

```
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

Du kan använda parametern ComputerName av cmdleten Get-Service för att hämta tjänsterna på fjärrdatorer. Parametern ComputerName accepterar flera värden och jokertecken, så du kan hämta tjänsterna på flera datorer med ett enda kommando. Till exempel hämtar följande kommando tjänster på fjärrdatorn Server01.

```powershell
Get-Service -ComputerName Server01
```

## <a name="getting-required-and-dependent-services"></a>Hämta krävs och beroende tjänster

Get-Service-cmdlet har två parametrar som är användbar om tjänsten administration. Parametern DependentServices hämtar tjänster som är beroende av tjänsten. Parametern RequiredServices hämtar tjänster som den här tjänsten är beroende.

Dessa parametrar kan bara visa värdena i DependentServices och ServicesDependedOn (alias = RequiredServices) egenskaper för objektet System.ServiceProcess.ServiceController som returnerar Get-Service, men de förenklar kommandon och göra komma den här informationen är mycket enklare.

Följande kommando hämtar de tjänster som krävs för LanmanWorkstation-tjänsten.

```
PS> Get-Service -Name LanmanWorkstation -RequiredServices

Status   Name               DisplayName
------   ----               -----------
Running  MRxSmb20           SMB 2.0 MiniRedirector
Running  bowser             Bowser
Running  MRxSmb10           SMB 1.x MiniRedirector
Running  NSI                Network Store Interface Service
```

Följande kommando hämtar de tjänster som kräver tjänsten LanmanWorkstation.

```
PS> Get-Service -Name LanmanWorkstation -DependentServices

Status   Name               DisplayName
------   ----               -----------
Running  SessionEnv         Terminal Services Configuration
Running  Netlogon           Netlogon
Stopped  Browser            Computer Browser
Running  BITS               Background Intelligent Transfer Ser...
```

Du kan även få alla tjänster som har beroenden. Följande kommando använder just och sedan används Format-Table-cmdlet för att visa Status, namn, RequiredServices och DependentServices egenskaperna för tjänsterna på datorn.

```powershell
Get-Service -Name * | Where-Object {$_.RequiredServices -or $_.DependentServices} | Format-Table -Property Status, Name, RequiredServices, DependentServices -auto
```

## <a name="stopping-starting-suspending-and-restarting-services"></a>Stoppa, starta, pausa och starta om tjänster
I cmdlet: ar alla har samma allmänna formulär. Tjänster kan anges med namn eller namn och ta listor och jokertecken som värden. Om du vill stoppa utskriftshanteraren, använder du:

```powershell
Stop-Service -Name spooler
```

Starta utskriftshanteraren när den har avbrutits med:

```powershell
Start-Service -Name spooler
```

Om du vill pausa Utskriftshanteraren, använder du:

```powershell
Suspend-Service -Name spooler
```

Den **Restart-Service** cmdlet fungerar på samma sätt som andra cmdletar för tjänsten, men vi visar exempel mer komplexa för den. Den enklaste används, kan du ange namnet på tjänsten:

```
PS> Restart-Service -Name spooler

WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
WARNING: Waiting for service 'Print Spooler (Spooler)' to finish starting...
PS>
```

Du ser att du får ett upprepade varningsmeddelande om utskriftshanteraren startas. När du utför en åtgärd i tjänsten som tar en stund, meddelar Windows PowerShell dig att den fortfarande försöker utföra åtgärden.

Om du vill starta om flera tjänster kan du hämta en lista över tjänster, filtrera dem och genomföra omstarten:

```
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

Dessa cmdlet: ar har inte en parameter för datornamn, men du kan köra dem på en fjärrdator med hjälp av cmdleten Invoke-Command. Till exempel följande kommando startar om utskriftshanteraren Server01 fjärrdatorn.

```powershell
Invoke-Command -ComputerName Server01 {Restart-Service Spooler}
```

## <a name="setting-service-properties"></a>Egenskaper för tjänsten

Cmdlet Set-tjänsten ändrar egenskaperna för en tjänst på en lokal eller fjärransluten dator. Eftersom tjänstestatus är en egenskap måste använda du denna cmdlet för att starta, stoppa och inaktivera en tjänst. Cmdlet Set-tjänsten har också en StartupType-parameter som låter dig ändra starttyp för tjänst.

För att använda Set-tjänst i Windows Vista och senare versioner av Windows, öppnar du Windows PowerShell med alternativet ”Kör som administratör”.

Mer information finns i [Set-tjänst [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)

## <a name="see-also"></a>Se även

- [Get-Service [m2]](https://technet.microsoft.com/en-us/library/0a09cb22-0a1c-4a79-9851-4e53075f9cf6)
- [Ange tjänst [m2]](https://technet.microsoft.com/library/b71e29ed-372b-4e32-a4b7-5eb6216e56c3)
- [Starta om tjänsten [m2]](https://technet.microsoft.com/en-us/library/45acf50d-2277-4523-baf7-ce7ced977d0f)
- [Pausa tjänst [m2]](https://technet.microsoft.com/en-us/library/c8492b87-0e21-4faf-8054-3c83c2ec2826)