---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 7982acc111e95b4167f948314f176d53f39d3620
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="reporting-on-jea"></a>Rapportering i JEA
Du kan använda för att rapportera om konfigurationen av JEA tillstånd:
1.  **Get-PSSessionConfiguration** returnera en lista över alla registrerade slutpunkter på en viss dator.
2.  **Get-PSSessionCapability** för att rapportera om funktionerna som har en viss användare på en viss slutpunkt.

Här är ett exempel på **Get-PSSessionCapability**:
```powershell
Get-PSSessionCapability -ConfigurationName Maintenance -Username "CONTOSO\JohnDoe"

CommandType     Name                                               Version    Source
-----------     ----                                               -------    ------
Alias           clear -> Clear-Host
Alias           cls -> Clear-Host
Alias           exsn -> Exit-PSSession
Alias           gcm -> Get-Command
Alias           measure -> Measure-Object
Alias           select -> Select-Object
Function        Clear-Host
Function        Exit-PSSession
Function        Get-Command
Function        Get-FormatData
Function        Get-Help
Function        Get-UserInfo
Function        Measure-Object
Function        Out-Default
Function        Select-Object
Cmdlet          Restart-Service                                    3.0.0.0 Microsof...


```

Rapportera om den _åtgärder_ användare tog under en session JEA, kan du:
1. Aktivera ”over-det axel” betyg för denna JEA slutpunkt och se katalogen betyg för en fullständig logg över åtgärder för varje användare
2. Aktivera loggning för PowerShell-modulen och inspektera händelseloggarna PowerShell.
