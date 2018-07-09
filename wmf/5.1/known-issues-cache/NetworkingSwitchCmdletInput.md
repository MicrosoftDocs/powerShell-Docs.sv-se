---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.topic: conceptual
contributor: vaibch
title: Växeln Nätverkshanteraren cmdletar fel
ms.openlocfilehash: a0f84c35974b6674faba4b0f19a28bd6e2490a96
ms.sourcegitcommit: 8b076ebde7ef971d7465bab834a3c2a32471ef6f
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/06/2018
ms.locfileid: "37893162"
---
# <a name="network-switch-manager-cmdlets-failure"></a>Växeln Nätverkshanteraren cmdletar fel

Nätverkshanteraren växeln-cmdletar kan användas för att hantera nätverksväxlar via WSMAN.
Några cmdlets för den här modulen finns kan acceptera värdena från pipelines.
WMF 5.1 förhandsversion de cmdletar som kan acceptera värdet från pipelinen gick inte att köra när värdena inte skickas pipelines.

Om inte ”InputObject”-parametern används bör cmdleten fortsätta att köra utan fel.

Här är listan över berörda cmdletar dvs. dessa cmdletar kan acceptera värde för parametern ”InputObject” från pipeline.
Körningen av cmdlet misslyckas om det här värdet inte överförs från pipeline.

- Inaktivera NetworkSwitchEthernetPort
- Aktivera NetworkSwitchEthernetPort
- Ta bort NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchEthernetPortIPAddress
- Set-NetworkSwitchPortMode
- Set-NetworkSwitchPortProperty
- Inaktivera NetworkSwitchFeature
- Aktivera NetworkSwitchFeature
- Ta bort NetworkSwitchVlan
- Set-NetworkSwitchVlanProperty

## <a name="resolution"></a>Lösning

Cmdlets fungerar bra när värdet för parametern InputObject skickas till den via pipeline. Några exempel som fungerar för ovanstående cmdletar är:

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