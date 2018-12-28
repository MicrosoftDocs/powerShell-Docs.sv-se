---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Uppdatera noder från en Pull-Server
ms.openlocfilehash: 4333a5bf82ef45f22a062942ebe93409433623f5
ms.sourcegitcommit: 00ff76d7d9414fe585c04740b739b9cf14d711e1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/14/2018
ms.locfileid: "53404648"
---
# <a name="update-nodes-from-a-pull-server"></a>Uppdatera noder från en Pull-Server

I avsnitten nedan förutsätter att du har ställt in en Pull-servern. Om du inte har konfigurerat din Pull-servern kan du använda följande guider:

- [Konfigurera en DSC SMB-Hämtningsserver](pullServerSmb.md)
- [Konfigurera en DSC HTTP-Hämtningsserver](pullServer.md)

Varje målnoden kan konfigureras för att hämta konfigurationer, resurser, och även rapportera statusen. Den här artikeln visar hur du laddar upp resurser så att de blir tillgängliga för att hämta och konfigurera klienter för att hämta resurser automatiskt. När nod som tar emot en tilldelade konfiguration via **hämta** eller **Push** (v5) hämtas automatiskt alla resurser som krävs av konfigurationen från den plats som anges i LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Med hjälp av Update-DSCConfiguration-cmdleten

Från och med PowerShell 5.0, den [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) cmdleten tvingar en nod för att uppdatera konfigurationen från Pull-servern konfigurerats i LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Med hjälp av Invoke-CIMMethod

I PowerShell 4.0 kan du manuellt kan tvinga en Pull-klient för att uppdatera sin konfiguration med hjälp av [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). I följande exempel skapar en CIM-session med angivna autentiseringsuppgifter, anropar metoden CIM och tar bort sessionen.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Se även

[PerformRequiredConfigurationChecks](/powershell/dsc/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks)
