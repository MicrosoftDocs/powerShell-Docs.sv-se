---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Uppdatera noder från en hämtningsserver
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62079106"
---
# <a name="update-nodes-from-a-pull-server"></a><span data-ttu-id="7ca27-103">Uppdatera noder från en hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7ca27-103">Update Nodes from a Pull Server</span></span>

<span data-ttu-id="7ca27-104">I avsnitten nedan förutsätter att du har ställt in en Pull-servern.</span><span class="sxs-lookup"><span data-stu-id="7ca27-104">The sections below assume that you have already set up a Pull Server.</span></span> <span data-ttu-id="7ca27-105">Om du inte har konfigurerat din Pull-servern kan du använda följande guider:</span><span class="sxs-lookup"><span data-stu-id="7ca27-105">If you have not set up your Pull Server, you can use the following guides:</span></span>

- [<span data-ttu-id="7ca27-106">Konfigurera en DSC SMB-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7ca27-106">Set up a DSC SMB Pull Server</span></span>](pullServerSmb.md)
- [<span data-ttu-id="7ca27-107">Konfigurera en DSC HTTP-Hämtningsserver</span><span class="sxs-lookup"><span data-stu-id="7ca27-107">Set up a DSC HTTP Pull Server</span></span>](pullServer.md)

<span data-ttu-id="7ca27-108">Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen.</span><span class="sxs-lookup"><span data-stu-id="7ca27-108">Each target node can be configured to download configurations, resources, and even report its status.</span></span> <span data-ttu-id="7ca27-109">Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt.</span><span class="sxs-lookup"><span data-stu-id="7ca27-109">This article will show you how to upload resources so they are available to be downloaded, and configure clients to download resources automatically.</span></span> <span data-ttu-id="7ca27-110">När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.</span><span class="sxs-lookup"><span data-stu-id="7ca27-110">When the Node's receives an assigned Configuration, through **Pull** or **Push** (v5), it automatically downloads any resources required by the Configuration from the location specified in the LCM.</span></span>

## <a name="using-the-update-dscconfiguration-cmdlet"></a><span data-ttu-id="7ca27-111">Med hjälp av Update-DSCConfiguration-cmdleten</span><span class="sxs-lookup"><span data-stu-id="7ca27-111">Using the Update-DSCConfiguration cmdlet</span></span>

<span data-ttu-id="7ca27-112">Från och med PowerShell 5.0, den [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdleten tvingar en nod för att uppdatera konfigurationen från Pull-servern konfigurerats i LCM.</span><span class="sxs-lookup"><span data-stu-id="7ca27-112">Beginning in PowerShell 5.0, the [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdlet, forces a Node to update its configuration from the Pull Server configured in the LCM.</span></span>

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a><span data-ttu-id="7ca27-113">Med hjälp av Invoke-CIMMethod</span><span class="sxs-lookup"><span data-stu-id="7ca27-113">Using Invoke-CIMMethod</span></span>

<span data-ttu-id="7ca27-114">I PowerShell 4.0 kan du manuellt kan tvinga en Pull-klient för att uppdatera sin konfiguration med hjälp av [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span><span class="sxs-lookup"><span data-stu-id="7ca27-114">In PowerShell 4.0, you can still manually force a Pull Client to update its Configuration using [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod).</span></span> <span data-ttu-id="7ca27-115">I följande exempel skapar en CIM-session med angivna autentiseringsuppgifter, anropar metoden CIM och tar bort sessionen.</span><span class="sxs-lookup"><span data-stu-id="7ca27-115">The following example creates a CIM session with specified credentials, invokes the appropriate CIM method, and removes the session.</span></span>

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a><span data-ttu-id="7ca27-116">Se även</span><span class="sxs-lookup"><span data-stu-id="7ca27-116">See Also</span></span>

[<span data-ttu-id="7ca27-117">PerformRequiredConfigurationChecks</span><span class="sxs-lookup"><span data-stu-id="7ca27-117">PerformRequiredConfigurationChecks</span></span>](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
