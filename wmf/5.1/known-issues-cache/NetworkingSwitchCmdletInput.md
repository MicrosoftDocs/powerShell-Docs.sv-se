---
ms.date: 06/12/2017
author: JKeithB
ms.topic: reference
keywords: WMF, powershell, inställning
contributor: vaibch
title: Nätverksväxelhanterare cmdlets fel
ms.openlocfilehash: 626809513e7a8f1aa2c47a48c74e69ca4077f598
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
<span data-ttu-id="d95f3-103">Nätverksväxelhanterare-cmdlets kan användas för att hantera nätverksväxlar via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="d95f3-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="d95f3-104">Några cmdlets i den här modulen finns möjlighet att acceptera värden från pipelines.</span><span class="sxs-lookup"><span data-stu-id="d95f3-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="d95f3-105">WMF 5.1 Förhandsgranska de cmdlets som kan acceptera värde från pipeline inte köras när värden inte har skickats via pipelines.</span><span class="sxs-lookup"><span data-stu-id="d95f3-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="d95f3-106">Om ”InputObject”-parametern inte används, bör cmdlet fortsätta att köras utan fel.</span><span class="sxs-lookup"><span data-stu-id="d95f3-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="d95f3-107">Här är listan över berörda cmdletar d.v.s. dessa cmdlets kan acceptera värde för parametern ”InputObject” från pipeline.</span><span class="sxs-lookup"><span data-stu-id="d95f3-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="d95f3-108">Körningen av cmdlet misslyckas om det här värdet inte har överförts från pipeline.</span><span class="sxs-lookup"><span data-stu-id="d95f3-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="d95f3-109">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="d95f3-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="d95f3-110">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="d95f3-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="d95f3-111">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="d95f3-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="d95f3-112">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="d95f3-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="d95f3-113">Set-NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="d95f3-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="d95f3-114">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="d95f3-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="d95f3-115">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="d95f3-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="d95f3-116">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="d95f3-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="d95f3-117">Remove-NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="d95f3-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="d95f3-118">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="d95f3-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="d95f3-119">Lösning</span><span class="sxs-lookup"><span data-stu-id="d95f3-119">Resolution</span></span>
<span data-ttu-id="d95f3-120">Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline.</span><span class="sxs-lookup"><span data-stu-id="d95f3-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="d95f3-121">Några exempel som fungerar för ovan-cmdlets är:</span><span class="sxs-lookup"><span data-stu-id="d95f3-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="d95f3-122">Disable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="d95f3-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="d95f3-123">Enable-NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="d95f3-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="d95f3-124">Remove-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="d95f3-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="d95f3-125">Set-NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="d95f3-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="d95f3-126">Set-NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="d95f3-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="d95f3-127">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="d95f3-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="d95f3-128">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="d95f3-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="d95f3-129">Set-NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="d95f3-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```