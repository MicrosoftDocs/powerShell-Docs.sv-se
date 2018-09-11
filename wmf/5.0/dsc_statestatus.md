---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: ff2c2bd7369893d72db001ecabf63991ded0bfd5
ms.sourcegitcommit: ac20e0faaa37142e9c6e4507a21df2f4a3fdbece
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/10/2018
ms.locfileid: "44339879"
---
# <a name="unified-and-consistent-state-and-status-representation"></a>Enhetlig och konsekvent tillstånds- och statusrepresentation

Ett antal förbättringar har gjorts i den här versionen för arbetsflöden som bygger LCM-tillstånd och status för DSC. Dessa inkluderar enhetlig och konsekvent tillstånd och status visning hanterbara datetime-egenskap för statusobjekt som returneras av `Get-DscConfigurationStatus` tillstånd information-egenskapen som returneras av cmdlet och förbättrad LCM `Get-DscLocalConfigurationManager` cmdlet.

En representation av LCM-tillstånd och status för DSC revisited och enhetlig enligt följande regler:

1. Notprocessed resource påverkar inte LCM-tillstånd och status för DSC.
2. LCM stoppa ytterligare bearbetningsresurser när den stöter på en resurs som begär omstart.
3. En resurs som begär omstart är inte i önskat läge tills omstart faktiskt händer.
4. Efter en resurs som misslyckas, ser till att MGM bearbeta ytterligare resurser så länge de inte är beroende av ett fel.
5. Den övergripande statusen som returneras av `Get-DscConfigurationStatus` cmdlet är den överordnade uppsättningen status för alla resurser.
6. PendingReboot tillståndet är en supermängd PendingConfiguration tillstånd.

I tabellen nedan visas resulterande tillstånd och status relaterade egenskaper under några vanliga scenarier.

| Scenario                        | LCMState             | Status     | Omstart har begärts | ResourcesInDesiredState   | ResourcesNotInDesiredState |
|---------------------------------|----------------------|------------|---------------|------------------------------|--------------------------------|
| S<sub>jag</sub>                   | Inaktiv                 | Klart    | $false        | S                            | $null                          |
| F<sub>jag</sub>                   | PendingConfiguration | Fel    | $false        | $null                        | F                              |
| S, F                             | PendingConfiguration | Fel    | $false        | S                            | F                              |
| F-S                             | PendingConfiguration | Fel    | $false        | S                            | F                              |
| S<sub>1</sub>, F, S<sub>2</sub> | PendingConfiguration | Fel    | $false        | S<sub>1</sub>, S<sub>2</sub> | F                              |
| F<sub>1</sub>, S, F<sub>2</sub> | PendingConfiguration | Fel    | $false        | S                            | F<sub>1</sub>, F<sub>2</sub>   |
| S, r                            | PendingReboot        | Klart    | $true         | S                            | r                              |
| F-, r                            | PendingReboot        | Fel    | $true         | $null                        | F-, r                           |
| r, S                            | PendingReboot        | Klart    | $true         | $null                        | r                              |
| r, F                            | PendingReboot        | Klart    | $true         | $null                        | r                              |

- S<sub>jag</sub>: ett antal resurser som har tillämpats
- F<sub>jag</sub>: ett antal resurser som används med fel
- r: en resurs som kräver omstart

```powershell
$LCMState = (Get-DscLocalConfigurationManager).LCMState
$Status = (Get-DscConfigurationStatus).Status

$RebootRequested = (Get-DscConfigurationStatus).RebootRequested

$ResourcesInDesiredState = (Get-DscConfigurationStatus).ResourcesInDesiredState

$ResourcesNotInDesiredState = (Get-DscConfigurationStatus).ResourcesNotInDesiredState
```

## <a name="enhancement-in-get-dscconfigurationstatus-cmdlet"></a>Förbättring i Get-DscConfigurationStatus cmdlet

Några förbättringar har gjorts `Get-DscConfigurationStatus` cmdlet i den här versionen. Tidigare är StartDate-egenskapen för objekt som returneras av cmdlet: en av typen sträng. Nu är av typen Datetime, vilket gör att komplexa att välja och filtrera utifrån enklare inbäddade egenskaperna för ett Datetime-objekt.

```powershell
(Get-DscConfigurationStatus).StartDate | Format-List *

DateTime    : Friday, November 13, 2015 1:39:44 PM
Date        : 11/13/2015 12:00:00 AM
Day         : 13
DayOfWeek   : Friday
DayOfYear   : 317
Hour        : 13
Kind        : Local
Millisecond : 886
Minute      : 39
Month       : 11
Second      : 44
Ticks       : 635830187848860000
TimeOfDay   : 13:39:44.8860000
Year        : 2015
```

I följande exempel returneras alla DSC-åtgärdsposter som inträffat på samma dag i veckan som den aktuella dagen.

```powershell
(Get-DscConfigurationStatus –All) | Where-Object { $_.startdate.dayofweek -eq (Get-Date).DayOfWeek }
```

Poster med åtgärder som inte du göra ändringar i nodens konfiguration (d.v.s. läsåtgärder endast) elimineras. Därför `Test-DscConfiguration`, `Get-DscConfiguration` åtgärder är inte längre uppblandat i returnerade objekt från `Get-DscConfigurationStatus` cmdlet. Poster i meta configuration frö läggs till i avkastningen på `Get-DscConfigurationStatus` cmdlet.

Följande är ett exempel på resultatet som returneras från `Get-DscConfigurationStatus –All` cmdlet.

```output
All configuration operations:

Status StartDate Type RebootRequested
------ --------- ---- ---------------
Success 11/13/2015 11:38:16 AM Consistency False
Success 11/13/2015 11:23:16 AM Reboot False
Success 11/13/2015 11:21:43 AM Reboot True
Success 11/13/2015 11:20:44 AM Initial True
Success 11/13/2015 11:20:44 AM LocalConfigurationManager False
```

## <a name="enhancement-in-get-dsclocalconfigurationmanager-cmdlet"></a>Förbättring i cmdleten Get-DscLocalConfigurationManager

Ett nytt fält av LCMStateDetail har lagts till i objektet som returnerades från `Get-DscLocalConfigurationManager` cmdlet. Det här fältet fylls när LCMState är ”upptagen”. Den kan hämtas med följande cmdlet:

```powershell
(Get-DscLocalConfigurationManager).LCMStateDetail
```

Följande är ett exempel på utdata för en kontinuerlig övervakning av en konfiguration som kräver två omstarter på en fjärransluten nod.

```output
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
