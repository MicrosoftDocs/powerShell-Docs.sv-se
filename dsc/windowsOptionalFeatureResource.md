---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Resurs för DSC-WindowsOptionalFeature"
ms.openlocfilehash: d9b8cc316255f06d2de71fedc47ce4472cc8b382
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsoptionalfeature-resource"></a>Resurs för DSC-WindowsOptionalFeature

> Gäller för: Windows PowerShell 5.0

Den **WindowsOptionalFeature** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.

## <a name="syntax"></a>Syntax

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ RemoveFilesOnDisable = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på funktionen som du vill kontrollera är aktiverat eller inaktiverat.| 
| Se till att| Anger om funktionen är aktiverad. För att säkerställa att funktionen är aktiverad, Ställ in den här egenskapen till ”aktivera” för att säkerställa att funktionen är inaktiverad, egenskapen till ”inaktivera”.|
| Källa| Inte implementerat.|
| NoWindowsUpdateCheck| Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera en funktion. Om $true DISM inte kontaktar WU.|
| RemoveFilesOnDisable| Värdet **$true** att ta bort alla filer som är associerade med funktionen när den är inaktiverad (det vill säga när **Kontrollera** anges till ”saknas”).|
| Loggnivå| Den maximala utdatanivån som visas i loggarna. De giltiga värdena är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).|
| LogPath| Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.| 
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 
 



