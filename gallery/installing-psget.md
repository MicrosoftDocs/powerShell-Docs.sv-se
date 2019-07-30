---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 2d3ba8c4d4d4c7ee023c7e6a948a29d8f47ea242
ms.sourcegitcommit: 8d47eb41445ffaf10fcd68874e397c9a1703d898
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/29/2019
ms.locfileid: "68601413"
---
# <a name="installing-powershellget"></a>Installera PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet är en modul i box i följande versioner

- [Windows 10](https://www.microsoft.com/windows) eller senare
- [Windows Server 2016](/windows-server/windows-server) eller senare
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Hämta PowerShellGet-modul för PowerShell-versionerna 3,0 och 4,0

- [PackageManagement-MSI](https://www.microsoft.com/download/details.aspx?id=51451)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Hämta den senaste versionen från PowerShell-galleriet

- Innan du uppdaterar PowerShellGet bör du alltid installera den senaste NuGet-providern. Det gör du genom att köra följande i en upphöjd PowerShell-session.

  ```powershell
  Install-PackageProvider Nuget -Force
  Exit
  ```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet

- Om du vill göra detta på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerade, eller ett system med PowerShell 6, kör du följande kommandon från en upphöjd PowerShell-session.

  ```powershell
  Install-Module -Name PowerShellGet -Force
  Exit
  ```

- Använd `Update-Module` för att hämta nyare versioner.

  ```powershell
  Update-Module -Name PowerShellGet
  Exit
  ```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpswwwmicrosoftcomdownloaddetailsaspxid51451"></a>För system som kör PowerShell 3 eller PowerShell 4, som har installerat [PACKAGEMANAGEMENT MSI](https://www.microsoft.com/download/details.aspx?id=51451)

- Använd nedanstående PowerShellGet-cmdlet från en upphöjd PowerShell-session för att spara modulerna i en lokal katalog

  ```powershell
  Save-Module PowerShellGet -Path C:\LocalFolder
  Exit
  ```

- Se till att PowerShellGet-och PackageManagement-modulerna inte har lästs in i någon annan process.
- Ta bort innehåll `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` i `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` och mappar.
- Öppna PS-konsolen igen med utökade behörigheter och kör sedan följande kommandon.

  ```powershell
  Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
  Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
  ```
