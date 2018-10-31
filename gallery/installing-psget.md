---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 5c51cb1c7ea2538cc5f8503ce6c5d80edda70e15
ms.sourcegitcommit: 98b7cfd8ad5718efa8e320526ca76c3cc4141d78
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/25/2018
ms.locfileid: "50002231"
---
# <a name="installing-powershellget"></a>Installera PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet är en nyckelfärdig modul i följande versioner

- [Windows 10](https://www.microsoft.com/windows) eller senare
- [Windows Server 2016](/windows-server/windows-server) eller senare
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Hämta PowerShellGet-modul för PowerShell version 3.0 och 4.0

- [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Hämta den senaste versionen från PowerShell-galleriet

- Innan du uppdaterar PowerShellGet, bör du alltid installera den senaste Nuget-providern. Om du vill göra det, kör du följande i en upphöjd PowerShell-session.

  ```powershell
  Install-PackageProvider Nuget –Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Du kan installera den senaste PowerShellGet för system med PowerShell 5.0 (eller senare)

- Om du vill göra detta på Windows 10, kör Windows Server 2016, alla system med WMF 5.0 eller 5.1 installerad eller ett system med PowerShell 6, du följande kommandon från en upphöjd PowerShell-session.

  ```powershell
  Install-Module –Name PowerShellGet –Force
  Exit
  ```

- Använd `Update-Module` att hämta nyare versioner.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>För system som kör PowerShell 3 eller PowerShell 4, som har installerat den [PackageManagement MSI](https://www.microsoft.com/download/details.aspx?id=51451)

- Använda PowerShellGet cmdleten från en upphöjd PowerShell-session nedan för att spara modulerna till en lokal katalog

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Se till att PowerShellGet och PackageManagment moduler inte har lästs in i andra processer.
- Ta bort innehållet i `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappar.
- Öppnar PS-konsolen med förhöjd behörighet och kör sedan följande kommandon.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
