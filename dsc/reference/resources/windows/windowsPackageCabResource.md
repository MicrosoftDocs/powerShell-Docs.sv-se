---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsPackageCab-resurs
ms.openlocfilehash: 035944e7ca5c7469250c48a19b79f2f2d5d38e9a
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048654"
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab-resurs

> Gäller för: Windows PowerShell 5.1 och senare

Den **WindowsPackageCab** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att installera eller avinstallera Windows CAB-paket på målnoden.

Målnoden måste ha installerat DISM PowerShell-modulen. Mer information finns i [Använd DISM i Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14).


## <a name="syntax"></a>Syntax

```
{
    Name = [string]
    Ensure = [string] { Absent | Present }
    SourcePath = [string]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Namn| Anger namnet på paketet för du vill se till att ett visst tillstånd.|
| Se till att| Anger om paketet har installerats. Ange den här egenskapen till ”inte” för att kontrollera att paketet inte har installerats (eller avinstallera paketet om det är installerat). Ange den till ”Visa” (standardvärdet) för att säkerställa att paketet har installerats.|
| Sökväg| Anger sökvägen där paketet finns.|
| LogPath| Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.|

## <a name="example"></a>Exempel

Följande exempelkonfiguration tar indataparametrar och säkerställer att CAB-filen som anges av den `$Name` parametern är installerad.

```powershell
Configuration Sample_WindowsPackageCab
{
    param
    (
        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $Name,

        [Parameter (Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $SourcePath,

        [Parameter(Mandatory = $true)]
        [ValidateNotNullOrEmpty()]
        [String]
        $LogPath
    )

    Import-DscResource -ModuleName 'PSDscResources'

    WindowsPackageCab WindowsPackageCab1
    {
        Name = $Name
        Ensure = 'Present'
        SourcePath = $SourcePath
        LogPath = $LogPath
    }
}
```