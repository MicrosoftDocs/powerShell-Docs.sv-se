---
ms.date: 06/12/2017
ms.topic: conceptual
title: Kända problem i WMF 5.1
description: Kända problem i WMF 5.1
ms.openlocfilehash: 7d27bc570108a0ae1470ae06f5bdf5fcd7849d16
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92663322"
---
# <a name="known-issues-in-wmf-51"></a>Kända problem i WMF 5.1

## <a name="starting-powershell-shortcut-as-administrator"></a>Startar PowerShell-genväg som administratör

Vid installation av WMF, om du försöker starta PowerShell som administratör från genvägen, kan det hända att meddelandet "Ospecificerat fel" visas. Öppna genvägen igen som icke-administratör och genvägen fungerar nu även som administratör.

## <a name="pester"></a>Pester

I den här versionen finns det två problem som du bör känna till när du använder pester på Nano Server:

- Att köra tester mot pester kan leda till problem på grund av skillnader mellan fullständig CLR och CORE CLR. I synnerhet är **validate** -metoden inte tillgänglig för typen **XMLDocument** . Sex tester som försöker validera schemat för NUnit-utgående loggar är kända för att Miss lyckas.
- Ett kod täcknings test Miss lyckas eftersom **WindowsFeature** DSC-resursen inte finns i Nano Server. Dessa problem är dock i allmänhet ofarliga och kan ignoreras på ett säkert sätt.

## <a name="operation-validation"></a>Åtgärds validering

- `Update-Help` Det går inte att utföra Microsoft. PowerShell. operation. Validation-modulen på grund av en icke fungerande hjälp-URI

## <a name="dsc-after-uninstall-wmf"></a>DSC efter avinstallation av WMF

- Om du avinstallerar WMF raderas inte DSC MOF-dokument från mappen konfiguration. DSC fungerar inte korrekt om MOF-dokumenten innehåller nyare egenskaper som inte är tillgängliga på äldre system. I det här fallet kör du följande skript från upphöjd PowerShell-konsolen för att rensa DSC-tillstånd.

  ```powershell
  $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
    "$env:windir\system32\configuration\*.mof.checksum",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof",
    "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
  )
  $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>Virtuella JEA-konton

JEA-slutpunkter och sessionsinställningar som kon figurer ATS för att använda virtuella konton i WMF 5,0 kommer inte att konfigureras att använda ett virtuellt konto efter uppgraderingen till WMF 5,1. Det innebär att kommandon som körs i JEA-sessioner körs under den anslutna användarens identitet i stället för ett tillfälligt administratörs konto, vilket kan hindra användaren från att köra kommandon som kräver förhöjd behörighet. Om du vill återställa de virtuella kontona måste du avregistrera och registrera om alla användarsessioner som använder virtuella konton.

```powershell
# Find the JEA endpoint by its name
$jea = Get-PSSessionConfiguration -Name MyJeaEndpoint

# Copy the cached PSSC file so it can be re-registered
$pssc = Copy-Item $jea.ConfigFilePath $env:temp -PassThru

# Unregister the current PSSC
Unregister-PSSessionConfiguration -Name $jea.Name

# Re-register the PSSC
Register-PSSessionConfiguration -Name $jea.Name -Path $pssc.FullName -Force

# Ensure the access policies remain the same
Set-PSSessionConfiguration -Name $newjea.Name -SecurityDescriptorSddl $jea.SecurityDescriptorSddl
```
