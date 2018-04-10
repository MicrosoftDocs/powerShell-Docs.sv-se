---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
ms.openlocfilehash: 2af56be1915c148809f52cd9040c45da160ae0a2
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="reporting-on-jea"></a><span data-ttu-id="efa37-102">Rapportering i JEA</span><span class="sxs-lookup"><span data-stu-id="efa37-102">Reporting on JEA</span></span>
<span data-ttu-id="efa37-103">Du kan använda för att rapportera om konfigurationen av JEA tillstånd:</span><span class="sxs-lookup"><span data-stu-id="efa37-103">In order to report on the state of your JEA configuration, you can use:</span></span>
1.  <span data-ttu-id="efa37-104">**Get-PSSessionConfiguration** returnera en lista över alla registrerade slutpunkter på en viss dator.</span><span class="sxs-lookup"><span data-stu-id="efa37-104">**Get-PSSessionConfiguration** to return a list of all registered endpoints on a given machine.</span></span>
2.  <span data-ttu-id="efa37-105">**Get-PSSessionCapability** för att rapportera om funktionerna som har en viss användare på en viss slutpunkt.</span><span class="sxs-lookup"><span data-stu-id="efa37-105">**Get-PSSessionCapability** to report on the capabilities any given user has on a specific endpoint.</span></span>

<span data-ttu-id="efa37-106">Här är ett exempel på **Get-PSSessionCapability**:</span><span class="sxs-lookup"><span data-stu-id="efa37-106">Here’s an example of **Get-PSSessionCapability**:</span></span>
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

<span data-ttu-id="efa37-107">Rapportera om den _åtgärder_ användare tog under en session JEA, kan du:</span><span class="sxs-lookup"><span data-stu-id="efa37-107">To report on the _actions_ users took during a JEA session, you can:</span></span>
1. <span data-ttu-id="efa37-108">Aktivera ”over-det axel” betyg för denna JEA slutpunkt och se katalogen betyg för en fullständig logg över åtgärder för varje användare</span><span class="sxs-lookup"><span data-stu-id="efa37-108">Enable the "over-the-shoulder" transcripts for that JEA endpoint and consult the transcript directory for a full log of each user's actions</span></span>
2. <span data-ttu-id="efa37-109">Aktivera loggning för PowerShell-modulen och inspektera händelseloggarna PowerShell.</span><span class="sxs-lookup"><span data-stu-id="efa37-109">Turn on PowerShell module logging and inspect the PowerShell event logs.</span></span>