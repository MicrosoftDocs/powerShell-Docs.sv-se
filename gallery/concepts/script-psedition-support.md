---
ms.date: 06/12/2017
contributor: manikb
keywords: galleriet, powershell, cmdlet, psget
title: Skriptet med kompatibla PowerShell-utgåvor
ms.openlocfilehash: 0ab655ff1c5dd0f48ec41a16ad394251b6c70748
ms.sourcegitcommit: c3f1a83b59484651119630f3089aa51b6e7d4c3c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/26/2018
ms.locfileid: "39267821"
---
# <a name="script-with-compatible-powershell-editions"></a>Skriptet med kompatibla PowerShell-utgåvor

Från och med version 5.1 finns PowerShell i olika utgåvor som anger olika funktionsuppsättningar och plattformskompatibilitet.

- **Desktop Edition:** bygger på .NET Framework och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på fullständiga utgåvor av Windows, till exempel Server Core och Windows Desktop.

- **Core Edition:** bygger på .NET Core och ger kompatibilitet med skript och moduler för versioner av PowerShell som körs på begränsade utgåvor av Windows som Nano Server och Windows IoT.

Vilken utgåva av PowerShell som körs visas i PSEdition-egenskapen i $PSVersionTable.

```powershell
$PSVersionTable

Name                           Value
----                           -----
PSVersion                      5.1.14300.1000
PSEdition                      Desktop
PSCompatibleVersions           {1.0, 2.0, 3.0, 4.0...}
CLRVersion                     4.0.30319.42000
BuildVersion                   10.0.14300.1000
WSManStackVersion              3.0
PSRemotingProtocolVersion      2.3
SerializationVersion           1.1.0.1
```

Skriptskribenter kan förhindra att ett skript körs om den körs på en kompatibel version av PowerShell med hjälp av parametern PSEdition på ett `#requires` instruktionen.

```powershell
Set-Content C:\script.ps1 -Value "#requires -PSEdition Core
Get-Process -Name PowerShell"
Get-Content C:\script.ps1
#requires -PSEdition Core
Get-Process -Name PowerShell

C:\script.ps1
C:\script.ps1 : The script 'script.ps1' cannot be run because it contained a "#requires" statement for PowerShell Core edition. The edition of PowerShell that is required by the script does not match the currently running PowerShell Desktop edition.
At line:1 char:1
+ C:\script.ps1
+ ~~~~~~~~~~~~~
    + CategoryInfo          : NotSpecified: (script.ps1:String) [], RuntimeException
    + FullyQualifiedErrorId : ScriptRequiresUnmatchedPSEdition
```

PowerShell-galleriet användare kan hitta listan stöds på en viss version av PowerShell-skript.
Skript utan PSEdition_Desktop och PSEditon_Core anses fungera på PowerShell Desktop-versioner.

```powershell
# Find scripts supported on PowerShell Desktop edition
Find-Script -Tag PSEditon_Desktop

# Find scripts supported on PowerShell Core editions
Find-Script -Tag PSEditon_Core
```

## <a name="more-details"></a>Mer information

- [Moduler med PSEditions](module-psedition-support.md)
- [Stöd för PSEditions på PowerShellGallery](../how-to/finding-items/searching-by-psedition.md)