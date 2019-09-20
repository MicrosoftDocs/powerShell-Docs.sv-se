---
ms.date: 06/12/2017
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: a0ef46a9ee4bbf668a58067256d098967bde48c5
ms.sourcegitcommit: 0a6b562a497860caadba754c75a83215315d37a1
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 09/19/2019
ms.locfileid: "71143600"
---
# <a name="installing-powershellget"></a>Installera PowerShellGet

## <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet är en modul i box i följande versioner

- [Windows 10](https://www.microsoft.com/windows) eller senare
- [Windows Server 2016](/windows-server/windows-server) eller senare
- [Windows Management Framework (WMF) 5,0](https://www.microsoft.com/download/details.aspx?id=50395) eller senare
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

## <a name="get-the-latest-version-from-powershell-gallery"></a>Hämta den senaste versionen från PowerShell-galleriet

Innan du uppdaterar **PowerShellGet**bör du alltid installera den senaste **NuGet** -providern. Kör följande kommando från en upphöjd PowerShell-session.

```powershell
Install-PackageProvider -Name NuGet -Force
Exit
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet

Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.

```powershell
Install-Module -Name PowerShellGet -Force
Exit
```

Använd `Update-Module` för att hämta nyare versioner.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-preview"></a>För system som kör PowerShell 3 eller PowerShell 4, som har installerat PackageManagement Preview

1. Använd `Save-Module` för att spara modulerna till en lokal katalog från en upphöjd PowerShell-session.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder
   Exit
   ```

1. Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.
1. Ta bort innehållet i mapparna: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Öppna PowerShell-konsolen med förhöjd behörighet och kör följande kommandon.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```
