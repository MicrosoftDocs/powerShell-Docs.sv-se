---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsPackageCab resurs
ms.openlocfilehash: 9b1bf3cb95abcbe46976ae0fd328280a3a8d7f28
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowspackagecab-resource"></a>DSC WindowsPackageCab resurs

> Gäller för: Windows PowerShell 5.1 och senare

Den **WindowsPackageCab** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att installera eller avinstallera Windows CAB-paket på målnoden.

Målnoden måste ha installerat PowerShell DISM-modulen. Mer information finns i [Använd DISM i Windows PowerShell](https://msdn.microsoft.com/en-us/windows/hardware/commercialize/manufacture/desktop/use-dism-in-windows-powershell-s14). 


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
| Se till att| Anger om paketet har installerats. Ange den här egenskapen till ”saknas” för att se till att paketet inte är installerat (eller avinstallera paketet om det är installerat). Ange att ”finns” (standardvärdet) för att säkerställa att paketet har installerats.|
| Sökväg| Anger sökvägen där paketet finns.| 
| LogPath| Anger den fullständiga sökvägen där du vill att providern ska spara en loggfil för att installera eller avinstallera paketet.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **ResourceType**, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.| 

## <a name="example"></a>Exempel

Följande exempelkonfiguration tar indataparametrar och säkerställer att CAB-filen som anges av den `$Name` parameter är installerad.

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
