---
ms.date: 09/19/2019
contributor: manikb
keywords: Galleri, PowerShell, cmdlet, psget
title: Installera PowerShellGet
ms.openlocfilehash: 4a10699be9ff2b64e5848c6749bdd3dedf55e3c7
ms.sourcegitcommit: f05f18154913d346012527c23020d48d87ccac74
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/13/2020
ms.locfileid: "88162519"
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
```

### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>För system med PowerShell 5,0 (eller senare) kan du installera den senaste PowerShellGet

Kör följande kommandon från en upphöjd PowerShell-session för att installera PowerShellGet på Windows 10, Windows Server 2016, alla system med WMF 5,0 eller 5,1 installerat, eller ett system med PowerShell 6.

```powershell
Install-Module -Name PowerShellGet -Force
```

Använd `Update-Module` för att hämta nyare versioner.

```powershell
Update-Module -Name PowerShellGet
Exit
```

### <a name="for-computers-running-powershell-30-or-powershell-40"></a>För datorer som kör PowerShell 3,0 eller PowerShell 4,0

Dessa anvisningar gäller för datorer där **PackageManagement Preview** är installerat eller inte har någon version av **PowerShellGet** installerad.

`Save-Module`Cmdleten används i båda uppsättningarna med instruktioner. `Save-Module` hämtar och sparar en modul och eventuella beroenden från en registrerad lagrings plats. Modulens senaste version sparas till en angiven sökväg på den lokala datorn, men är inte installerad. Om du vill installera modulerna i PowerShell 3,0 eller 4,0 kopierar du modulen sparade mappar till `$env:ProgramFiles\WindowsPowerShell\Modules` .

Mer information finns i [Save-module](/powershell/module/PowershellGet/Save-Module).

> [!NOTE]
> PowerShell 3,0 och PowerShell 4,0 har endast stöd för en version av en modul. Moduler som börjar i PowerShell 5,0 installeras i `<modulename>\<version>` . På så sätt kan du installera flera versioner sida vid sida. När du har laddat ned modulen med `Save-Module` måste du kopiera filerna från `<modulename>\<version>` till `<modulename>` -mappen på mål datorn, som du ser i anvisningarna nedan.

#### <a name="preparatory-step-on-computers-running-powershell-30"></a>Förberedelse steg för datorer som kör PowerShell 3,0

Anvisningarna i avsnitten nedan installerar modulerna i katalogen `$env:ProgramFiles\WindowsPowerShell\Modules` .
I PowerShell 3,0 visas den här katalogen inte i som `$env:PSModulePath` standard, så du måste lägga till den för att modulerna ska kunna läsas in automatiskt. 

Öppna en upphöjd PowerShell-session och kör följande kommando (som börjar gälla i framtida sessioner):

```powershell
[Environment]::SetEnvironmentVariable(
  'PSModulePath',
  ((([Environment]::GetEnvironmentVariable('PSModulePath', 'Machine') -split ';') + "$env:ProgramFiles\WindowsPowerShell\Modules") -join ';'),
  'Machine'
)
```

#### <a name="computers-with-the-packagemanagement-preview-installed"></a>Datorer med PackageManagement-förhands granskning installerad

> [!NOTE] 
> PackageManagement Preview var en nedladdnings bar komponent som gjorde PowerShellGet tillgänglig för PowerShell-versionerna 3 och 4, men den är inte längre tillgänglig.
> Kör om du vill testa om den har installerats på en specifik dator `Get-Module -ListAvailable PowerShellGet` .

1. Från en PowerShell-session använder `Save-Module` du för att hämta den aktuella versionen av **PowerShellGet**. Två mappar hämtas: **PowerShellGet** och **PackageManagement**. Varje mapp innehåller en undermapp med ett versions nummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Se till att modulerna **PowerShellGet** och **PackageManagement** inte har lästs in i någon annan process.

1. Öppna PowerShell-konsolen igen med utökade behörigheter och kör följande kommando.

   ```powershell
   'PowerShellGet', 'PackageManagement' | % { 
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     Remove-Item $targetDir\* -Recurse -Force
     Copy-Item C:\LocalFolder\$_\*\* $targetDir\ -Recurse -Force
   }
   ```

#### <a name="computers-without-powershellget"></a>Datorer utan PowerShellGet

För datorer utan någon version av **PowerShellGet** installerat (test med `Get-Module -ListAvailable PowerShellGet` ) krävs en dator med **PowerShellGet** installerat för att hämta modulerna.

1. Använd **PowerShellGet** `Save-Module` för att hämta den aktuella versionen av **PowerShellGet**från den dator som har installerat PowerShellGet. Två mappar hämtas: **PowerShellGet** och **PackageManagement**. Varje mapp innehåller en undermapp med ett versions nummer.

   ```powershell
   Save-Module -Name PowerShellGet -Path C:\LocalFolder -Repository PSGallery
   ```

1. Kopiera respektive `<version>` undermapp i mapparna **PowerShellGet** och **PackageManagement** till datorn som inte har **PowerShellGet** installerad, i mappar `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` som kräver en upphöjd session.
   
1. Om du till exempel har åtkomst till download-mappen på den andra datorn, t. ex `ws1` . från mål datorn via en UNC-sökväg, så `\\ws1\C$\LocalFolder` öppnar du en PowerShell-konsol med förhöjd behörighet och kör följande kommando:

   ```powershell
   'PowerShellGet', 'PackageManagement' | % {
     $targetDir = "$env:ProgramFiles\WindowsPowerShell\Modules\$_"
     $null = New-Item -Type Directory -Force $targetDir
     $fromComputer = 'ws1'  # Specify the name of the other computer here.
     Copy-Item \\$fromComputer\C$\LocalFolder\$_\*\* $targetDir -Recurse -Force
     if (-not (Get-ChildItem $targetDir)) { Throw "Copying failed." }
   }
   ```
