---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.1
ms.openlocfilehash: d53031bea978087c68fcb22989c7cd2e2cf2d9fa
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="known-issues-in-wmf-51"></a>Kända problem i WMF 5.1 #

> Obs: Den här informationen kan ändras.

## <a name="starting-powershell-shortcut-as-administrator"></a>Startar genvägen PowerShell som administratör
Om du försöker starta PowerShell som administratör från genvägen när installeras WMF kan du få ett ”okänt fel”-meddelande.
Öppna en genväg som icke-administratör och genvägen nu fungerar även som administratör.

## <a name="pester"></a>Lära
Det finns två saker du bör vara medveten om när du använder Pester på Nano Server i den här versionen:

* Kör tester mot Pester själva kan resultera i några fel på grund av skillnader mellan fullständig CLR och CORE CLR. I synnerhet är Validate-metoden inte tillgänglig i XmlDocument-typen. Sex tester som försöker verifiera schemat NUnit utdata loggar är känt att misslyckas.
* En kod täckning testet misslyckas för tillfället eftersom den *WindowsFeature* DSC-resursen finns inte i Nano Server. Dessa fel är vanligtvis ofarlig och ignoreras.

## <a name="operation-validation"></a>Validering av Distributionsåtgärden

* Update-Help misslyckas för Microsoft.PowerShell.Operation.Validation modulen på grund av icke-fungerande hjälp URI

## <a name="dsc-after-uninstall-wmf"></a>DSC efter avinstallera WMF
* Avinstallera WMF tar inte bort DSC MOF dokument från konfigurationsmappen. DSC fungerar inte korrekt om MOF-dokument innehåller nyare egenskaper som inte är tillgängliga på äldre system. Kör följande skript i det här fallet från upphöjd PowerShell-konsolen för att rensa DSC-tillstånd.
 ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )

    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
 ```

## <a name="jea-virtual-accounts"></a>JEA virtuella konton
JEA slutpunkter och sessionskonfigurationer som konfigurerats för att använda virtuella konton i WMF 5.0 konfigureras inte för att använda ett virtuellt konto när du har uppgraderat till WMF 5.1.
Det innebär att kommandon som körs i JEA sessioner kommer att köras under den anslutande användarens identitet i stället för ett tillfälligt administratörskonto potentiellt hindrar användaren från att köra kommandon som kräver utökade privilegier.
Om du vill återställa de virtuella kontona, måste du avregistrera och registrera alla sessionskonfigurationer som använder virtuella konton.

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
