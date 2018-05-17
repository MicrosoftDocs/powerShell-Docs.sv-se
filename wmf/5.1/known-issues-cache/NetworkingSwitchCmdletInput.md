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
---
Nätverksväxelhanterare-cmdlets kan användas för att hantera nätverksväxlar via WSMAN.
Några cmdlets i den här modulen finns möjlighet att acceptera värden från pipelines.
WMF 5.1 Förhandsgranska de cmdlets som kan acceptera värde från pipeline inte köras när värden inte har skickats via pipelines.

Om ”InputObject”-parametern inte används, bör cmdlet fortsätta att köras utan fel.

Här är listan över berörda cmdletar d.v.s. dessa cmdlets kan acceptera värde för parametern ”InputObject” från pipeline.
Körningen av cmdlet misslyckas om det här värdet inte har överförts från pipeline.

- Inaktivera NetworkSwitchEthernetPort
- Aktivera NetworkSwitchEthernetPort
- Ta bort NetworkSwitchEthernetPortIPAddress
- Ange NetworkSwitchEthernetPortIPAddress
- Ange NetworkSwitchPortMode
- Ange NetworkSwitchPortProperty
- Inaktivera NetworkSwitchFeature
- Aktivera NetworkSwitchFeature
- Ta bort NetworkSwitchVlan
- Ange NetworkSwitchVlanProperty

### <a name="resolution"></a>Lösning
Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline. Några exempel som fungerar för ovan-cmdlets är:

- Inaktivera NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Disable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Aktivera NetworkSwitchEthernetPort
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Enable-NetworkSwitchEthernetPort -CimSession $cimSession
```

- Ta bort NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Remove-NetworkSwitchEthernetPortIPAddress -CimSession $cimSession
```

- Ange NetworkSwitchEthernetPortIPAddress
```powershell
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$ipAddress = "192.168.10.1"
$subnetAddress = "255.255.255.0"
$port | Set-NetworkSwitchEthernetPortIPAddress -IpAddress $ipAddress -SubnetAddress $subnetAddress -CimSession $cimSession
```

- Ange NetworkSwitchPortProperty
```powershell
$portProperties = @{Caption = "New Caption"}
$port = Get-CimInstance -Namespace root/interop -ClassName CIM_EthernetPort -CimSession $cimSession | Select-Object -First 1
$port | Set-NetworkSwitchPortProperty -Property $portProperties -CimSession $cimSession
```

- Inaktivera NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Disable-NetworkSwitchFeature -CimSession $cimSession
```

- Aktivera NetworkSwitchFeature
```powershell
$feature = Get-CimInstance -Namespace root/interop -ClassName MSFT_Feature -CimSession $cimSession | Select-Object -First 1
$feature | Enable-NetworkSwitchFeature -CimSession $cimSession
```

- Ange NetworkSwitchVlanProperty
```powershell
$properties = @{Caption = "New Caption"}
$vlan = Get-CimInstance -ClassName CIM_NetworkVlan -Namespace root/interop -CimSession $cimSession | Select-Object -First 1
$vlan | Set-NetworkSwitchVlanProperty -Property $properties -CimSession $cimSession
```
