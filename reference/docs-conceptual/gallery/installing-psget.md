---
ms.date: 09/19/2019
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 69dc851c54089b47fb19e5b32990d579d26effb9
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71328982"
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

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>För datorer som kör PowerShell 3,0 eller PowerShell 4,0

Dessa anvisningar gäller för datorer där **PackageManagement Preview** är installerat eller inte har någon version av **PowerShellGet** installerad.

`Save-Module` Cmdleten används i båda uppsättningarna med instruktioner. `Save-Module`hämtar och sparar en modul och eventuella beroenden från en registrerad lagrings plats. Modulens senaste version sparas till en angiven sökväg på den lokala datorn, men är inte installerad. Mer information finns i [Save-module](/powershell/module/PowershellGet/Save-Module).

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Datorer med PackageManagement-förhands granskning installerad

1. Använd `Save-Module` för att spara modulerna till en lokal katalog från en PowerShell-session.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.
1. Ta bort innehållet i mapparna: `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\`.
1. Öppna PowerShell-konsolen med förhöjd behörighet och kör följande kommandon.

   ```powershell
   Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
   Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force
   ```

#### <a name="computers-without-powershellget"></a>Datorer utan PowerShellGet

För datorer utan någon version av **PowerShellGet** installerat krävs en dator med **PowerShellGet** installerat för att ladda ned modulerna.

1. Använd `Save-Module` för att hämta den aktuella versionen av **PowerShellGet**från den dator som har installerat **PowerShellGet** . Två mappar hämtas: **PowerShellGet** och **PackageManagement**. Varje mapp innehåller en undermapp med ett versions nummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Kopiera mapparna **PowerShellGet** och **PackageManagement** till datorn som inte har **PowerShellGet** installerat.

   Mål katalogen är:`$env:ProgramFiles\WindowsPowerShell\Modules`
