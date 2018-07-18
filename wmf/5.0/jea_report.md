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
# <a name="reporting-on-jea"></a><span data-ttu-id="5656a-102">Rapportering i JEA</span><span class="sxs-lookup"><span data-stu-id="5656a-102">Reporting on JEA</span></span>

<span data-ttu-id="5656a-103">Du kan använda för att rapportera om statusen hos din JEA-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="5656a-103">In order to report on the state of your JEA configuration, you can use:</span></span>

1. <span data-ttu-id="5656a-104">**Get-PSSessionConfiguration** returnera en lista över alla registrerade slutpunkter på en viss dator.</span><span class="sxs-lookup"><span data-stu-id="5656a-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
1. <span data-ttu-id="5656a-105">**Get-PSSessionCapability** för att rapportera om funktionerna som har en viss användare på en viss slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="5656a-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="5656a-106">Här är ett exempel på **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="5656a-106">Here's an example of **Get-PSSessionCapability**:</span></span>

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

<span data-ttu-id="5656a-107">Att rapportera om den _åtgärder_ användare tog i en JEA-session, kan du:</span><span class="sxs-lookup"><span data-stu-id="5656a-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="5656a-108">Aktivera ”over-the axeln” avskrifter för denna JEA-slutpunkt och en fullständig logg över varje användares åtgärder finns i katalogen avskrift</span><span class="sxs-lookup"><span data-stu-id="5656a-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="5656a-109">Aktivera loggning för PowerShell-modulen och Granska händelseloggarna för PowerShell.</span><span class="sxs-lookup"><span data-stu-id="5656a-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>
