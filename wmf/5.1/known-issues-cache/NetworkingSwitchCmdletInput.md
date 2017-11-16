---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
contributor: vaibch
title: "Nätverksväxelhanterare cmdlets fel"
ms.openlocfilehash: d9fcdedbfc7d0c3f68624ed1db6259e04c3d06d1
ms.sourcegitcommit: fee03bb9802222078c8d5f6c8efb0698024406ed
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/27/2017
---
<span data-ttu-id="caeea-103">Nätverksväxelhanterare-cmdlets kan användas för att hantera nätverksväxlar via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="caeea-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span> <span data-ttu-id="caeea-104">Några cmdlets i den här modulen finns möjlighet att acceptera värden från pipelines.</span><span class="sxs-lookup"><span data-stu-id="caeea-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span> <span data-ttu-id="caeea-105">WMF 5.1 Förhandsgranska de cmdlets som kan acceptera värde från pipeline inte köras när värden inte har skickats via pipelines.</span><span class="sxs-lookup"><span data-stu-id="caeea-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="caeea-106">Om ”InputObject”-parametern inte används, bör cmdlet fortsätta att köras utan fel.</span><span class="sxs-lookup"><span data-stu-id="caeea-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="caeea-107">Här är listan över berörda cmdletar d.v.s. dessa cmdlets kan acceptera värde för parametern ”InputObject” från pipeline.</span><span class="sxs-lookup"><span data-stu-id="caeea-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span> <span data-ttu-id="caeea-108">Körningen av cmdlet misslyckas om det här värdet inte har överförts från pipeline.</span><span class="sxs-lookup"><span data-stu-id="caeea-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="caeea-109">Inaktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="caeea-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="caeea-110">Aktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="caeea-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="caeea-111">Ta bort NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="caeea-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="caeea-112">Ange NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="caeea-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="caeea-113">Ange NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="caeea-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="caeea-114">Ange NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="caeea-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="caeea-115">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="caeea-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="caeea-116">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="caeea-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="caeea-117">Ta bort NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="caeea-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="caeea-118">Ange NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="caeea-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="caeea-119">Lösning</span><span class="sxs-lookup"><span data-stu-id="caeea-119">Resolution</span></span>
<span data-ttu-id="caeea-120">Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline.</span><span class="sxs-lookup"><span data-stu-id="caeea-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="caeea-121">Några exempel som fungerar för ovan-cmdlets är:</span><span class="sxs-lookup"><span data-stu-id="caeea-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="caeea-122">Inaktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="caeea-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="caeea-123">Aktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="caeea-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="caeea-124">Ta bort NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="caeea-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="caeea-125">Ange NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="caeea-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="caeea-126">Ange NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="caeea-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="caeea-127">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="caeea-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="caeea-128">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="caeea-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="caeea-129">Ange NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="caeea-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```

