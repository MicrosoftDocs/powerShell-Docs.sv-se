---
ms.date: 06/12/2017
keywords: dsc,powershell,configuration,setup
title: Uppdatera noder från en hämtningsserver
ms.openlocfilehash: 516e50b0c39e4747a123307cb3f5e25259ac7ce5
ms.sourcegitcommit: d43f66071f1f33b350d34fa1f46f3a35910c5d24
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/23/2019
ms.locfileid: "74417709"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="b5a84-103">Uppdatera noder från en hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="b5a84-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="b5a84-104">The sections below assume that you have already set up a Pull Server.</span><span class="sxs-lookup"><span data-stu-id="b5a84-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="b5a84-105">If you have not set up your Pull Server, you can use the following guides:</span><span class="sxs-lookup"><span data-stu-id="b5a84-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="b5a84-106">Set up a DSC SMB Pull Server</span><span class="sxs-lookup"><span data-stu-id="b5a84-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="b5a84-107">Set up a DSC HTTP Pull Server</span><span class="sxs-lookup"><span data-stu-id="b5a84-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="b5a84-108">Each target node can be configured to download configurations, resources, and even report its status.</span><span class="sxs-lookup"><span data-stu-id="b5a84-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="b5a84-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span><span class="sxs-lookup"><span data-stu-id="b5a84-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="b5a84-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span><span class="sxs-lookup"><span data-stu-id="b5a84-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="b5a84-111">Using the Update-DSCConfiguration cmdlet</span><span class="sxs-lookup"><span data-stu-id="b5a84-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="b5a84-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span><span class="sxs-lookup"><span data-stu-id="b5a84-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="b5a84-113">Using Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="b5a84-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="b5a84-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="b5a84-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="b5a84-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span><span class="sxs-lookup"><span data-stu-id="b5a84-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="b5a84-116">Se även</span><span class="sxs-lookup"><span data-stu-id="b5a84-116">See Also</span></span>

[<span data-ttu-id="b5a84-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="b5a84-117">PerformRequiredConfigurationChecks</span></span>](/powershell/scripting/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
