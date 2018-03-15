---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 4868cf657f678ee43a6c92d5ee286e9ddb490964
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="network-switch-management-with-powershell"></a>Växeln nätverkshantering med PowerShell

Den **Get-NetworkSwitchEthernetPort** cmdlet returnerar nu följande information med instanser:

- IP-adress – IP-adress kopplad till porten
- PortMode – portläge: åtkomst, flöde eller trunk
- AccessVLAN – ID för VLAN som associeras med den här porten för åtkomstläge
- TrunkedVLANList – en lista över ID: N för virtuella lokala nätverk som associeras med den här porten i segmentläge

## <a name="fundamental-network-switch-management-with-windows-powershell"></a>Grundläggande växeln nätverkshantering med Windows PowerShell

Nätverksswitch-cmdlets med WMF 5.0 gör att du kan använda växel, virtuellt LAN (VLAN) och grundläggande nivå 2-port nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar. Microsoft förblir förbinder sig att stödja den [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, och du vill visa värdet för våra kunder och partner här. Med hjälp av dessa cmdletar kan du utföra:

- Global växel konfiguration, exempelvis:
    - Namnet på värden
    - Ange växeln banderoll
    - Beständig konfiguration
    - Aktivera eller inaktivera funktionen

- VLAN-konfiguration:
    - Skapa eller ta bort VLAN
    - Aktivera eller inaktivera VLAN
    - Räkna upp VLAN
    - Ange eget namn till ett virtuellt lokalt nätverk

- Portkonfiguration för nivå 2:
    - Räkna upp portar
    - Aktivera eller inaktivera portar
    - Egenskaper och ange port lägen
    - Lägg till eller associera VLAN till Trunk eller åtkomst på port

Börja utforska genom att söka efter alla cmdlets NetworkSwitch!

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

Mer information finns i blogginlägget för Jeffrey Snover WMF 5.0 Preview meddelande: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx>

