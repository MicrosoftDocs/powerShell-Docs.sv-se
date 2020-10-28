---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Uppdatera noder från en hämtningsserver
description: Den här artikeln förklarar hur du uppdaterar DSC-hanterade noder från en hämtnings Server
ms.openlocfilehash: 7256a0e1fdfaa8e56150c4f7299640bc95b82cee
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92656757"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="7d849-104">Uppdatera noder från en hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7d849-104">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="7d849-105">I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="7d849-105">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="7d849-106">Om du inte har konfigurerat din pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="7d849-106">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="7d849-107">Konfigurera en DSC SMB-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7d849-107">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7d849-108">Konfigurera en DSC HTTP-hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7d849-108">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7d849-109">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="7d849-109">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7d849-110">Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="7d849-110">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="7d849-111">När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="7d849-111">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="7d849-112">Använda Update-DSCConfiguration cmdlet</span><span class="sxs-lookup"><span data-stu-id="7d849-112">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="7d849-113">Med början i PowerShell 5,0 är cmdleten [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) en nod för att uppdatera konfigurationen från den hämtnings server som kon figurer ATS i LCM.</span><span class="sxs-lookup"><span data-stu-id="7d849-113">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="7d849-114">Använda Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="7d849-114">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="7d849-115">I PowerShell 4,0 kan du fortfarande manuellt framtvinga en pull-klient för att uppdatera konfigurationen med [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="7d849-115">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="7d849-116">I följande exempel skapas en CIM-session med angivna autentiseringsuppgifter, en lämplig CIM-metod anropas och sessionen tas bort.</span><span class="sxs-lookup"><span data-stu-id="7d849-116">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="7d849-117">Se även</span><span class="sxs-lookup"><span data-stu-id="7d849-117">See Also</span></span>

[<span data-ttu-id="7d849-118">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="7d849-118">PerformRequiredConfigurationChecks</span></span>](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
