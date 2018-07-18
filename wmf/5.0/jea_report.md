---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 2fb2e4b0c40322b5ec78fabede22a7e3ecbbd2aa
ms.sourcegitcommit: 77f62a55cac8c13d69d51eef5fade18f71d66955
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/17/2018
ms.locfileid: "39093770"
---
# <a name="reporting-on-jea"></a>Rapportering i JEA

Du kan använda för att rapportera om statusen hos din JEA-konfiguration:

1. **Get-PSSessionConfiguration** returnera en lista över alla registrerade slutpunkter på en viss dator.
1. **Get-PSSessionCapability** för att rapportera om funktionerna som har en viss användare på en viss slutpunkt.

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

Att rapportera om den _åtgärder_ användare tog i en JEA-session, kan du:
1. Aktivera ”over-the axeln” avskrifter för denna JEA-slutpunkt och en fullständig logg över varje användares åtgärder finns i katalogen avskrift
2. Aktivera loggning för PowerShell-modulen och Granska händelseloggarna för PowerShell.
