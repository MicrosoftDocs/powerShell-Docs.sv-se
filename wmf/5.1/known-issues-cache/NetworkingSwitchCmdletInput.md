---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
contributor: vaibch
title: Växeln Nätverkshanteraren cmdletar fel
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62084988"
---
# <a name="network-switch-manager-cmdlets-failure"></a><span data-ttu-id="32052-103">Växeln Nätverkshanteraren cmdletar fel</span><span class="sxs-lookup"><span data-stu-id="32052-103">Network Switch Manager Cmdlets Failure</span></span>

<span data-ttu-id="32052-104">Nätverkshanteraren växeln-cmdletar kan användas för att hantera nätverksväxlar via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="32052-104">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="32052-105">Några cmdlets för den här modulen finns kan acceptera värdena från pipelines.</span><span class="sxs-lookup"><span data-stu-id="32052-105">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="32052-106">WMF 5.1 förhandsversion de cmdletar som kan acceptera värdet från pipelinen gick inte att köra när värdena inte skickas pipelines.</span><span class="sxs-lookup"><span data-stu-id="32052-106">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="32052-107">Om inte ”InputObject”-parametern används bör cmdleten fortsätta att köra utan fel.</span><span class="sxs-lookup"><span data-stu-id="32052-107">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="32052-108">Här är listan över berörda cmdletar dvs. dessa cmdletar kan acceptera värde för parametern ”InputObject” från pipeline.</span><span class="sxs-lookup"><span data-stu-id="32052-108">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="32052-109">Körningen av cmdlet misslyckas om det här värdet inte överförs från pipeline.</span><span class="sxs-lookup"><span data-stu-id="32052-109">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="32052-110">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="32052-110">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="32052-111">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="32052-111">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="32052-112">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="32052-112">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="32052-113">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="32052-113">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="32052-114">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="32052-114">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="32052-115">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="32052-115">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="32052-116">Disable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="32052-116">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="32052-117">Enable-NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="32052-117">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="32052-118">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="32052-118">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="32052-119">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="32052-119">Set-NetworkSwitchVlanProperty</span></span>

## <a name="resolution"></a><span data-ttu-id="32052-120">Lösning</span><span class="sxs-lookup"><span data-stu-id="32052-120">Resolution</span></span>

<span data-ttu-id="32052-121">Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline.</span><span class="sxs-lookup"><span data-stu-id="32052-121">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="32052-122">Några exempel som fungerar för ovanstående cmdletar är:</span><span class="sxs-lookup"><span data-stu-id="32052-122">A few examples that work for the above cmdlets are:</span></span>

- `Disable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Enable-NetworkSwitchEthernetPort`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
  ```

- `Remove-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchEthernetPortIPAddress`

  ```powershell
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $ipAddress = "192.168.10.1"
  $subnetAddress = "255.255.255.0"
  $port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
  ```

- `Set-NetworkSwitchPortProperty`

  ```powershell
  $portProperties = @{Caption = "New Caption"}
  $port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
  $port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
  ```

- `Disable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Disable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Enable-NetworkSwitchFeature`

  ```powershell
  $feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
  $feature | Enable-NetworkSwitchFeature -CimSession $cimSession
  ```

- `Set-NetworkSwitchVlanProperty`

  ```powershell
  $properties = @{Caption = "New Caption"}
  $vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
  $vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
  ```