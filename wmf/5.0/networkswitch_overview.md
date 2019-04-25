---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: 61c5df1b64cb9c54f9c7372a56e77abf319658dd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085161"
---
# <a name="network-switch-management-with-powershell"></a><span data-ttu-id="ed507-102">Hantering av nätverksväxling med PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed507-102">Network Switch Management with PowerShell</span></span>

<span data-ttu-id="ed507-103">Den **Get-NetworkSwitchEthernetPort** cmdlet returnerar nu följande ytterligare information med instanser:</span><span class="sxs-lookup"><span data-stu-id="ed507-103">The **Get-NetworkSwitchEthernetPort** cmdlet now returns the following additional information with instances:</span></span>

- <span data-ttu-id="ed507-104">IP-adress – IP-adressen som är associerade med porten</span><span class="sxs-lookup"><span data-stu-id="ed507-104">IPAddress – the IP address associated with the port</span></span>
- <span data-ttu-id="ed507-105">PortMode – portläge: åtkomst, flöde eller segment</span><span class="sxs-lookup"><span data-stu-id="ed507-105">PortMode – the port mode: access, route, or trunk</span></span>
- <span data-ttu-id="ed507-106">AccessVLAN – ID för VLAN som är associerade med den här porten i åtkomstläge</span><span class="sxs-lookup"><span data-stu-id="ed507-106">AccessVLAN – the ID of the VLAN associated with this port in access mode</span></span>
- <span data-ttu-id="ed507-107">TrunkedVLANList – en lista med ID: N för virtuella lokala nätverk som är associerade med den här porten i segmentläge</span><span class="sxs-lookup"><span data-stu-id="ed507-107">TrunkedVLANList – a list of IDs of VLANs associated with this port in trunk mode</span></span>

## <a name="fundamental-network-switch-management-with-windows-powershell"></a><span data-ttu-id="ed507-108">Grundläggande hantering av nätverksswitchar med Windows PowerShell</span><span class="sxs-lookup"><span data-stu-id="ed507-108">Fundamental network switch management with Windows PowerShell</span></span>

<span data-ttu-id="ed507-109">Nätverksswitch-cmdlets med WMF 5.0, kan du använda växeln, virtuellt LAN (VLAN) och grundläggande nivå 2-portkonfiguration av nätverksväxel för Windows Server 2012 R2-logotyp-certifierade nätverksväxlar.</span><span class="sxs-lookup"><span data-stu-id="ed507-109">The Network Switch cmdlets, introduced in WMF 5.0, enable you to apply switch, virtual LAN (VLAN), and basic Layer 2 network switch port configuration to Windows Server 2012 R2 logo-certified network switches.</span></span> <span data-ttu-id="ed507-110">Microsoft förblir förbinder sig att stödja den [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, och för att visa värdet för våra kunder och partner inom detta område.</span><span class="sxs-lookup"><span data-stu-id="ed507-110">Microsoft remains committed to supporting the [Datacenter Abstraction](http://technet.microsoft.com/cloud/dal.aspx) Layer (DAL) vision, and to show value for our customers and partners in this space.</span></span> <span data-ttu-id="ed507-111">Med dessa cmdletar kan du utföra:</span><span class="sxs-lookup"><span data-stu-id="ed507-111">Using these cmdlets you can perform:</span></span>

- <span data-ttu-id="ed507-112">Global växla konfiguration, till exempel:</span><span class="sxs-lookup"><span data-stu-id="ed507-112">Global switch configuration, such as:</span></span>
    - <span data-ttu-id="ed507-113">Set-värdnamn</span><span class="sxs-lookup"><span data-stu-id="ed507-113">Set host name</span></span>
    - <span data-ttu-id="ed507-114">Ange växeln banderoll</span><span class="sxs-lookup"><span data-stu-id="ed507-114">Set switch banner</span></span>
    - <span data-ttu-id="ed507-115">Spara konfigurationen</span><span class="sxs-lookup"><span data-stu-id="ed507-115">Persist configuration</span></span>
    - <span data-ttu-id="ed507-116">Aktivera eller inaktivera funktionen</span><span class="sxs-lookup"><span data-stu-id="ed507-116">Enable or disable feature</span></span>

- <span data-ttu-id="ed507-117">VLAN-konfiguration:</span><span class="sxs-lookup"><span data-stu-id="ed507-117">VLAN configuration:</span></span>
    - <span data-ttu-id="ed507-118">Skapa eller ta bort VLAN</span><span class="sxs-lookup"><span data-stu-id="ed507-118">Create or remove VLAN</span></span>
    - <span data-ttu-id="ed507-119">Aktivera eller inaktivera VLAN</span><span class="sxs-lookup"><span data-stu-id="ed507-119">Enable or disable VLAN</span></span>
    - <span data-ttu-id="ed507-120">Räkna upp VLAN</span><span class="sxs-lookup"><span data-stu-id="ed507-120">Enumerate VLAN</span></span>
    - <span data-ttu-id="ed507-121">Ange eget namn som ett VLAN</span><span class="sxs-lookup"><span data-stu-id="ed507-121">Set friendly name to a VLAN</span></span>

- <span data-ttu-id="ed507-122">Portkonfiguration för Layer 2:</span><span class="sxs-lookup"><span data-stu-id="ed507-122">Layer 2 port configuration:</span></span>
    - <span data-ttu-id="ed507-123">Räkna upp portar</span><span class="sxs-lookup"><span data-stu-id="ed507-123">Enumerate ports</span></span>
    - <span data-ttu-id="ed507-124">Aktivera eller inaktivera portar</span><span class="sxs-lookup"><span data-stu-id="ed507-124">Enable or disable ports</span></span>
    - <span data-ttu-id="ed507-125">Ange port lägen och egenskaper</span><span class="sxs-lookup"><span data-stu-id="ed507-125">Set port modes and properties</span></span>
    - <span data-ttu-id="ed507-126">Lägga till eller associera VLAN till segment eller åtkomst på port</span><span class="sxs-lookup"><span data-stu-id="ed507-126">Add or associate VLAN to Trunk or Access on the port</span></span>

<span data-ttu-id="ed507-127">Börja utforska genom att söka efter alla NetworkSwitch-cmdlet: ar!</span><span class="sxs-lookup"><span data-stu-id="ed507-127">Start exploring by looking for all of the NetworkSwitch cmdlets!</span></span>

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

<span data-ttu-id="ed507-128">Mer information finns i blogginlägget för Jeffrey Snover WMF 5.0 förhandsversion meddelande: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span><span class="sxs-lookup"><span data-stu-id="ed507-128">More information is available in Jeffrey Snover’s WMF 5.0 Preview announcement blog post: <http://blogs.technet.com/b/windowsserver/archive/2014/04/03/windows-management-framework-v5-preview.aspx></span></span>
