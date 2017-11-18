---
ms.date: 2017-06-12
contributor: manikb
ms.topic: reference
keywords: galleriet, powershell, cmdlet, psget
title: "Hämta PowerShellGet-modul"
ms.openlocfilehash: a5a323b17709e519ec57623a9dd7499e591bbed5
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
<a name="get-powershellget-module"></a>Hämta PowerShellGet-modul
========================

### <a name="powershellget-is-an-in-box-module-in-the-following-releases"></a>PowerShellGet är en modul i rutan i följande versioner
- [Windows 10](https://www.microsoft.com/en-us/windows/get-windows-10) eller senare
- [Windows Server 2016](https://technet.microsoft.com/en-us/windows-server-docs/get-started/windows-server-2016) eller senare
- [Windows Management Framework (WMF) 5.0](https://www.microsoft.com/en-us/download/details.aspx?id=50395) eller senare
- [PowerShell 6](https://github.com/PowerShell/PowerShell/releases)

### <a name="get-powershellget-module-for-powershell-versions-30-and-40"></a>Hämta PowerShellGet modul för PowerShell version 3.0 och 4.0
- [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409) 

### <a name="get-the-latest-version-from-powershell-gallery"></a>Hämta den senaste versionen från PowerShell-galleriet

- Innan du uppdaterar PowerShellGet, bör du alltid installera den senaste Nuget-providern. Om du vill göra det kör du följande i en upphöjd PowerShell-session.
```powershell
Install-PackageProvider Nuget –Force
Exit
```

#### <a name="for-systems-with-powershell-50-or-newer-you-can-install-the-latest-powershellget"></a>Du kan installera den senaste PowerShellGet för system med PowerShell 5.0 (eller senare) 
- Om du vill göra detta på Windows 10, kör Windows Server 2016, alla system med WMF 5.0 eller 5.1 installerat eller alla system med PowerShell 6, du följande kommandon från en upphöjd PowerShell-session.
```powershell
Install-Module –Name PowerShellGet –Force
Exit
```

- Använda Update-modulen för att få nyare versioner.
```powershell
Update-Module -Name PowerShellGet
Exit
```

#### <a name="for-systems-running-powershell-3-or-powershell-4-that-have-installed-the-packagemanagement-msihttpgomicrosoftcomfwlinklinkid746217clcid0x409"></a>För datorer som kör PowerShell 3 eller 4 för PowerShell, som har installerat den [PackageManagement MSI](http://go.microsoft.com/fwlink/?LinkID=746217&clcid=0x409)

- Använd nedan PowerShellGet cmdlet från en upphöjd PowerShell-session för att spara modulerna till en lokal katalog

```powershell
Save-Module PowerShellGet -Path C:\LocalFolder
Exit
```

- Se till att PowerShellGet och PackageManagment-moduler inte har lästs in i andra processer.
- Ta bort innehållet i `$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\` och `$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\` mappar.
- Öppna igen PS-konsolen med förhöjd behörighet och kör sedan följande kommandon.

```powershell
Copy-Item "C:\LocalFolder\PowerShellGet\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PowerShellGet\" -Recurse -Force
Copy-Item "C:\LocalFolder\PackageManagement\*" "$env:ProgramFiles\WindowsPowerShell\Modules\PackageManagement\" -Recurse -Force