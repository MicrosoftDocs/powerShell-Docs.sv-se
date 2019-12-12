---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Uppdatera noder från en hämtningsserver
ms.openlocfilehash: 516e50b0c39e4747a123307cb3f5e25259ac7ce5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "74417709"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="34eef-103">Uppdatera noder från en hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="34eef-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="34eef-104">I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server.</span><span class="sxs-lookup"><span data-stu-id="34eef-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="34eef-105">Om du inte har konfigurerat din pull-server kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="34eef-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="34eef-106">Konfigurera en DSC SMB-pull-server</span><span class="sxs-lookup"><span data-stu-id="34eef-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="34eef-107">Konfigurera en DSC HTTP-pull-server</span><span class="sxs-lookup"><span data-stu-id="34eef-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="34eef-108">Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status.</span><span class="sxs-lookup"><span data-stu-id="34eef-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="34eef-109">Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="34eef-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="34eef-110">När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="34eef-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="34eef-111">Använda cmdleten Update-DSCConfiguration</span><span class="sxs-lookup"><span data-stu-id="34eef-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="34eef-112">Med början i PowerShell 5,0 är cmdleten [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) en nod för att uppdatera konfigurationen från den hämtnings server som kon figurer ATS i LCM.</span><span class="sxs-lookup"><span data-stu-id="34eef-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="34eef-113">Använda Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="34eef-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="34eef-114">I PowerShell 4,0 kan du fortfarande manuellt framtvinga en pull-klient för att uppdatera konfigurationen med [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="34eef-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="34eef-115">I följande exempel skapas en CIM-session med angivna autentiseringsuppgifter, en lämplig CIM-metod anropas och sessionen tas bort.</span><span class="sxs-lookup"><span data-stu-id="34eef-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="34eef-116">Se även</span><span class="sxs-lookup"><span data-stu-id="34eef-116">See Also</span></span>

[<span data-ttu-id="34eef-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="34eef-117">PerformRequiredConfigurationChecks</span></span>](/powershell/scripting/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
