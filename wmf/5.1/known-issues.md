---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: WMF, powershell, inställning
title: Kända problem i WMF 5.1
ms.openlocfilehash: e59ea1b9a5282eb5727a37ce605c71724a219827
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50225853"
---
# <a name="known-issues-in-wmf-51"></a>Kända problem i WMF 5.1

> [!Note]
> Den här informationen kan komma att ändras.

## <a name="starting-powershell-shortcut-as-administrator"></a>Starta PowerShell-genväg som administratör

Om du försöker starta PowerShell som administratör från genvägen till vid installation av WMF, kan du få meddelandet ”okänt fel”.
Öppna genväg som icke-administratör och genvägen nu fungerar även som administratör.

## <a name="pester"></a>Lära

Det finns två problem som du bör känna till när du använder Pester på Nano Server i den här versionen:

- Kör tester mot Pester själva kan resultera i några fel på grund av skillnader mellan fullständig CLR- och CORE CLR. I synnerhet är verifiera-metoden inte tillgänglig på vilken XmlDocument. Sex tester som försöker verifiera schemat för utdataloggar NUnit är kända misslyckas.
- En kod täckning testet misslyckas just nu eftersom den *WindowsFeature* DSC-resursen finns inte i Nano Server. De här felen är vanligtvis ofarlig och på ett säkert sätt kan ignoreras.

## <a name="operation-validation"></a>Validering av

- `Update-Help` misslyckas för Microsoft.PowerShell.Operation.Validation modulen på grund av icke-fungerande hjälp URI

## <a name="dsc-after-uninstall-wmf"></a>DSC efter avinstallera WMF

- Avinstallera WMF tar inte bort DSC MOF-dokument från konfigurationsmappen. DSC fungerar inte korrekt om MOF-dokument innehåller nyare egenskaper som inte är tillgängliga på de äldre systemen. I det här fallet kör följande skript från en upphöjd PowerShell-konsol att rensa DSC-tillstånd.

  ```powershell
    $PreviousDSCStates = @("$env:windir\system32\configuration\*.mof",
            "$env:windir\system32\configuration\*.mof.checksum",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof",
            "$env:windir\system32\configuration\PartialConfiguration\*.mof.checksum"
           )
    $PreviousDSCStates | Remove-Item -ErrorAction SilentlyContinue -Verbose
  ```

## <a name="jea-virtual-accounts"></a>JEA virtuella konton

JEA-slutpunkter och sessionskonfigurationer som konfigurerats för att använda virtuella konton i WMF 5.0 ska inte konfigureras för att använda ett virtuellt konto när du har uppgraderat till WMF 5.1.
Det innebär att kommandon som körs i JEA-sessioner kommer att köras under den anslutande användarens identitet i stället för ett tillfälligt administratörskonto, potentiellt hindrar användaren från att köra kommandon som kräver utökade privilegier.
Om du vill återställa de virtuella kontona, måste du avregistrera och Omregistrera alla sessionskonfigurationer som använder virtuella konton.

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