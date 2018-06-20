---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
contributor: vaibch
title: Nätverksväxelhanterare cmdlets fel
ms.openlocfilehash: 197a25411a82e5d256a9420706535d5411991f1b
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
ms.locfileid: "34188691"
---
<span data-ttu-id="3872a-103">Nätverksväxelhanterare-cmdlets kan användas för att hantera nätverksväxlar via WSMAN.</span><span class="sxs-lookup"><span data-stu-id="3872a-103">The Network Switch Manager cmdlets can be used to manage network switches over WSMAN.</span></span>
<span data-ttu-id="3872a-104">Några cmdlets i den här modulen finns möjlighet att acceptera värden från pipelines.</span><span class="sxs-lookup"><span data-stu-id="3872a-104">A few cmdlets of this module are capable of accepting values from pipelines.</span></span>
<span data-ttu-id="3872a-105">WMF 5.1 Förhandsgranska de cmdlets som kan acceptera värde från pipeline inte köras när värden inte har skickats via pipelines.</span><span class="sxs-lookup"><span data-stu-id="3872a-105">In WMF 5.1 Preview, the cmdlets that can accept value from pipeline fail to execute when the values are not passed through pipelines.</span></span>

<span data-ttu-id="3872a-106">Om ”InputObject”-parametern inte används, bör cmdlet fortsätta att köras utan fel.</span><span class="sxs-lookup"><span data-stu-id="3872a-106">If "InputObject" parameter is not used, the cmdlet should continue to execute without failures.</span></span>

<span data-ttu-id="3872a-107">Här är listan över berörda cmdletar d.v.s. dessa cmdlets kan acceptera värde för parametern ”InputObject” från pipeline.</span><span class="sxs-lookup"><span data-stu-id="3872a-107">Here is the list of affected cmdlets i.e. these cmdlets can accept value for "InputObject" parameter from pipeline.</span></span>
<span data-ttu-id="3872a-108">Körningen av cmdlet misslyckas om det här värdet inte har överförts från pipeline.</span><span class="sxs-lookup"><span data-stu-id="3872a-108">If this value is not passed from pipeline the execution of cmdlet will fail.</span></span>

- <span data-ttu-id="3872a-109">Inaktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3872a-109">Disable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3872a-110">Aktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3872a-110">Enable-NetworkSwitchEthernetPort</span></span>
- <span data-ttu-id="3872a-111">Ta bort NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3872a-111">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3872a-112">Ange NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3872a-112">Set-NetworkSwitchEthernetPortIPAddress</span></span>
- <span data-ttu-id="3872a-113">Ange NetworkSwitchPortMode</span><span class="sxs-lookup"><span data-stu-id="3872a-113">Set-NetworkSwitchPortMode</span></span>
- <span data-ttu-id="3872a-114">Ange NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3872a-114">Set-NetworkSwitchPortProperty</span></span>
- <span data-ttu-id="3872a-115">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3872a-115">Disable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3872a-116">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3872a-116">Enable-NetworkSwitchFeature</span></span>
- <span data-ttu-id="3872a-117">Ta bort NetworkSwitchVlan</span><span class="sxs-lookup"><span data-stu-id="3872a-117">Remove-NetworkSwitchVlan</span></span>
- <span data-ttu-id="3872a-118">Ange NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3872a-118">Set-NetworkSwitchVlanProperty</span></span>

### <a name="resolution"></a><span data-ttu-id="3872a-119">Lösning</span><span class="sxs-lookup"><span data-stu-id="3872a-119">Resolution</span></span>
<span data-ttu-id="3872a-120">Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline.</span><span class="sxs-lookup"><span data-stu-id="3872a-120">The cmdlets work fine when the value of InputObject parameter are passed into it through pipeline.</span></span> <span data-ttu-id="3872a-121">Några exempel som fungerar för ovan-cmdlets är:</span><span class="sxs-lookup"><span data-stu-id="3872a-121">A few examples that work for the above cmdlets are:</span></span>

- <span data-ttu-id="3872a-122">Inaktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3872a-122">Disable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3872a-123">Aktivera NetworkSwitchEthernetPort</span><span class="sxs-lookup"><span data-stu-id="3872a-123">Enable-NetworkSwitchEthernetPort</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- <span data-ttu-id="3872a-124">Ta bort NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3872a-124">Remove-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- <span data-ttu-id="3872a-125">Ange NetworkSwitchEthernetPortIPAddress</span><span class="sxs-lookup"><span data-stu-id="3872a-125">Set-NetworkSwitchEthernetPortIPAddress</span></span>
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- <span data-ttu-id="3872a-126">Ange NetworkSwitchPortProperty</span><span class="sxs-lookup"><span data-stu-id="3872a-126">Set-NetworkSwitchPortProperty</span></span>
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- <span data-ttu-id="3872a-127">Inaktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3872a-127">Disable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3872a-128">Aktivera NetworkSwitchFeature</span><span class="sxs-lookup"><span data-stu-id="3872a-128">Enable-NetworkSwitchFeature</span></span>
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- <span data-ttu-id="3872a-129">Ange NetworkSwitchVlanProperty</span><span class="sxs-lookup"><span data-stu-id="3872a-129">Set-NetworkSwitchVlanProperty</span></span>
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
