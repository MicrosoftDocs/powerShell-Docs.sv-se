---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7b4e4dbeaf9c3c48e7b2dfc74435dfa2cd9c7ea7
ms.sourcegitcommit: 735ccab3fb3834ccd8559fab6700b798e8e5ffbf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/25/2018
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Enhetlig och konsekvent tillstånds- och statusrepresentation

Ett antal förbättringar har gjorts i den här versionen för automatiseringar inbyggda MGM tillstånd och DSC-status. Dessa inkluderar enhetlig och konsekvent tillstånd och status garantier, hanterbara datetime-egenskap för status-objekt som returneras av Get-DscConfigurationStatus cmdlet och förbättrad MGM tillstånd information egenskap returnerades av Get-DscLocalConfigurationManager cmdlet.

Representation av MGM tillstånd och DSC Åtgärdsstatus revisited och enhetlig enligt följande regler:
1.  Notprocessed resurs påverkar inte MGM tillstånd och DSC-status.
2.  MGM stoppa ytterligare bearbetningsresurser när den stöter på en resurs som kräver omstart.
3.  En resurs som begär omstart är inte status som önskas förrän omstart i själva verket inträffar.
4.  Efter en resurs som misslyckas, håller MGM bearbetningsresurser ytterligare så länge de inte är beroende av ett fel.
5.  Den allmänna statusen som returneras av Get-DscConfigurationStatus cmdlet är den överordnade uppsättningen status för alla resurser.
6.  PendingReboot tillstånd är en supermängd PendingConfiguration tillstånd.

I tabellen nedan visas resulterande tillstånd och status relaterade egenskaper under några vanliga scenarier.

| Scenario                    | LCMState       | Status | Omstart begärdes  | ResourcesInDesiredState  | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S**^**                          | Inaktiv                 | Klart    | $false        | S                            | $null                          |
| F**^**                          | PendingConfiguration | Fel    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Fel    | $false        | S                            | F                              |
| F, S                             | PendingConfiguration | Fel    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Fel    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Fel    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Klart    | $true         | S                            | R                              |
| F, r                            | PendingReboot        | Fel    | $true         | $null                        | F, r                           |
| r, S                            | PendingReboot        | Klart    | $true         | $null                        | R                              |
| r, F                            | PendingReboot        | Klart    | $true         | $null                        | R                              |

^ S<sub>jag</sub>: ett antal resurser som har tillämpats F<sub>jag</sub>: ett antal resurser som tillämpats fel r: en resurs som kräver omstart \*

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Förbättring i Get-DscConfigurationStatus cmdlet

Några förbättringar har gjorts till Get-DscConfigurationStatus cmdlet i den här versionen. Tidigare är egenskapen StartDate för objekt som returnerats av cmdleten av typen String. Nu är av typen Datetime, vilket gör att komplicerade att välja och filtrering lättare baserat på inbyggda egenskaper för ett Datetime-objekt.

```powershell
(Get-DscConfigurationStatus).StartDate | fl *
DateTime : Friday, November 13, 2015 1:39:44 PM
Date : 11/13/2015 12:00:00 AM
Day : 13
DayOfWeek : Friday
DayOfYear : 317
Hour : 13
Kind : Local
Millisecond : 886
Minute : 39
Month : 11
Second : 44
Ticks : 635830187848860000
TimeOfDay : 13:39:44.8860000
Year : 2015
```

Följande är ett exempel som returnerar alla poster för DSC-åtgärden som inträffat på samma dag i veckan som idag.

```powershell
(Get-DscConfigurationStatus –All) | where { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Posterna för åtgärder som inte du göra ändringar i nodens konfiguration (d.v.s. läsåtgärder endast) elimineras. Därför Test-DscConfiguration Get-DscConfiguration åtgärder är inte längre uppblandat i returnerade objekt från Get-DscConfigurationStatus cmdlet.
Poster med meta configuration inställningen åtgärden läggs till av Get-DscConfigurationStatus cmdlet.

Följande är ett exempel på resultat som returneras från Get-DscConfigurationStatus – alla cmdlet.

```powershell
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Förbättring i Get-DscLocalConfigurationManager cmdlet

Ett nytt fält av LCMStateDetail har lagts till i objektet som returnerades från Get-DscLocalConfigurationManager cmdlet. Det här fältet fylls när LCMState är ”upptagen”. De kan hämtas av följande cmdlet:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Följande är ett exempel på utdata för en kontinuerlig övervakning av en konfiguration som kräver två omstarter på en fjärr-nod.

```powershell
Start a configuration that requires two reboots

Monitor LCM State:
LCM State: Busy, LCM is applying a new configuration.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: PendingReboot,
Machine is rebooting...
LCM State: Busy, LCM is continuing applying configuration after last reboot.
LCM State: Idle,
LCM State: Busy, LCM is performing a consistency check.
LCM State: Idle,
```
