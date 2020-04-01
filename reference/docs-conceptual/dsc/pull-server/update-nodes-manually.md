---
ms.date: 06/12/2017
keywords: DSC, PowerShell, konfiguration, installation
title: Uppdatera noder från en hämtningsserver
ms.openlocfilehash: fa59a2f6574db2dbc96621be4326f1d5a55e5de9
ms.sourcegitcommit: 30ccbbb32915b551c4cd4c91ef1df96b5b7514c4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/01/2020
ms.locfileid: "80500663"
---
# <a name="update-nodes-from-a-pull-server"></a>Uppdatera noder från en hämtningsserver

I avsnitten nedan förutsätts att du redan har konfigurerat en hämtnings Server. Om du inte har konfigurerat din pull-server kan du använda följande guider:

- [Konfigurera en DSC SMB-pull-server](pullServerSmb.md)
- [Konfigurera en DSC HTTP-pull-server](pullServer.md)

Varje målnod kan konfigureras för att ladda ned konfigurationer, resurser och till och med rapportera dess status. Den här artikeln visar hur du laddar upp resurser så att de kan laddas ned och konfigurera klienterna att ladda ned resurser automatiskt. När noden tar emot en tilldelad konfiguration via **pull** eller **push** (V5) laddar den automatiskt ned eventuella resurser som krävs av konfigurationen från den plats som anges i LCM.

## <a name="using-the-update-dscconfiguration-cmdlet"></a>Använda cmdleten Update-DSCConfiguration

Med början i PowerShell 5,0 är cmdleten [Update-DSCConfiguration](/powershell/module/psdesiredstateconfiguration/update-dscconfiguration) en nod för att uppdatera konfigurationen från den hämtnings server som kon figurer ATS i LCM.

```powershell
Update-DSCConfiguration -ComputerName "Server01"
```

## <a name="using-invoke-cimmethod"></a>Använda Invoke-CIMMethod

I PowerShell 4,0 kan du fortfarande manuellt framtvinga en pull-klient för att uppdatera konfigurationen med [Invoke-CIMMethod](/powershell/module/cimcmdlets/invoke-cimmethod). I följande exempel skapas en CIM-session med angivna autentiseringsuppgifter, en lämplig CIM-metod anropas och sessionen tas bort.

```powershell
$cimSession = New-CimSession -ComputerName "Server01" -Credential $(Get-Credential)
Invoke-CimMethod -CimSession $cimSession -Namespace 'root/microsoft/windows/desiredstateconfiguration' -Class 'MSFT_DscLocalConfigurationManager' -MethodName 'PerformRequiredConfigurationChecks' -Arguments @{ 'Flags' = [uint32]1 } -Verbose
$cimSession | Remove-CimSession
```

## <a name="see-also"></a>Se även

[PerformRequiredConfigurationChecks](../reference/mof-classes/msft-dsclocalconfigurationmanager-performrequiredconfigurationchecks.md)
