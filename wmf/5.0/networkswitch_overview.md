---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683767"
---
# <a name="network-switch-management-with-powershell"></a>Hantering av nätverksväxling med PowerShell

Den **Get-NetworkSwitchEthernetPort** cmdlet returnerar nu följande ytterligare information med instanser:

- IP-adress – IP-adressen som är associerade med porten
- PortMode – portläge: åtkomst, flöde eller segment
- AccessVLAN – ID för VLAN som är associerade med den här porten i åtkomstläge
- TrunkedVLANList – en lista med ID: N för virtuella lokala nätverk som är associerade med den här porten i segmentläge

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Grundläggande hantering av nätverksswitchar med Windows PowerShell

Nätverksswitch-cmdlets med WMF 5.0, kan du använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-portkonfiguration av nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar. Microsoft förblir förbinder sig att stödja den [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, och för att visa värdet för våra kunder och partner inom detta område. Med dessa cmdletar kan du utföra:

- Global växla konfiguration, till exempel:
    - Set-värdnamn
    - Ange växeln banderoll
    - Spara konfigurationen
    - Aktivera eller inaktivera funktionen

- VLAN-konfiguration:
    - Skapa eller ta bort VLAN
    - Aktivera eller inaktivera VLAN
    - Räkna upp VLAN
    - Ange eget namn som ett VLAN

- Portkonfiguration för Layer 2:
    - Räkna upp portar
    - Aktivera eller inaktivera portar
    - Ange port lägen och egenskaper
    - Lägga till eller associera VLAN till segment eller åtkomst på port

Börja utforska genom att söka efter alla NetworkSwitch-cmdlet: ar!

```powershell
PS> Get-Command *-NetworkSwitch*

| CommandType | Name                                      | Source        |
|-------------|-------------------------------------------|---------------|
|             |                                           |               |
| Function    | Disable-NetworkSwitchEthernetPort         | NetworkSwitch |
| Function    | Disable-NetworkSwitchFeature              | NetworkSwitch |
| Function    | Disable-NetworkSwitchVlan                 | NetworkSwitch |
| Function    | Enable-NetworkSwitchEthernetPort          | NetworkSwitch |
| Function    | Enable-NetworkSwitchFeature               | NetworkSwitch |
| Function    | Enable-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Get-NetworkSwitchEthernetPort             | NetworkSwitch |
| Function    | Get-NetworkSwitchFeature                  | NetworkSwitch |
| Function    | Get-NetworkSwitchGlobalData               | NetworkSwitch |
| Function    | Get-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | New-NetworkSwitchVlan                     | NetworkSwitch |
| Function    | Remove-NetworkSwitchEthernetPortIPAddress | NetworkSwitch |
| Function    | Remove-NetworkSwitchVlan                  | NetworkSwitch |
| Function    | Restore-NetworkSwitchConfiguration        | NetworkSwitch |
| Function    | Save-NetworkSwitchConfiguration           | NetworkSwitch |
| Function    | Set-NetworkSwitchEthernetPortIPAddress    | NetworkSwitch |
| Function    | Set-NetworkSwitchPortMode                 | NetworkSwitch |
| Function    | Set-NetworkSwitchPortProperty             | NetworkSwitch |
| Function    | Set-NetworkSwitchVlanProperty             | NetworkSwitch |
```

Mer information finns i blogginlägget för Jeffrey Snover WMF 5.0 förhandsversion meddelande: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>
