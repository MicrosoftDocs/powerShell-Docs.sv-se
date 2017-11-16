---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet resurs
ms.openlocfilehash: 3bf6a993d0ec9ce71c1e9222ddaa3bb429accb15
ms.sourcegitcommit: 79e8f03afb8d0b0bb0a167e56464929b27f51990
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/26/2017
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet resurs

> Gäller för: Windows PowerShell 5.0

Den **WindowsOptionalFeatureSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden. Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsOptionalFeature resurs](windowsOptionalFeatureResource.md) för varje funktion som anges i den `Name` egenskapen.

Använd den här resursen när du vill konfigurera ett antal Windows valfria funktioner till samma tillstånd.

## <a name="syntax"></a>Syntax

```
WindowsOptionalFeature [string] #ResourceName
{
    Name = [string[]]
    [ Ensure = [string] { Enable | Disable }  ]
    [ Source = [string] ] 
    [ RemoveFilesOnDisable = [bool] ]  
    [ LogPath = [string] ]
    [ NoWindowsUpdateCheck = [bool] ]
    [ LogLevel = [string] { ErrorsOnly | ErrorsAndWarning | ErrorsAndWarningAndInformation }  ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på de funktioner som du vill kontrollera är aktiverade eller inaktiverade.| 
| Se till att| Anger om funktionerna är aktiverade. För att säkerställa att funktionerna är aktiverade, ange den här egenskapen till ”aktivera” för att säkerställa att funktionerna är inaktiverade, egenskapen till ”inaktivera”.|
| Källa| Inte implementerat.|
| NoWindowsUpdateCheck| Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera funktioner. Om $true DISM inte kontaktar WU.|
| RemoveFilesOnDisable| Värdet **$true** att ta bort alla filer som är associerat med funktioner när de är inaktiverade (det vill säga när **Kontrollera** anges till ”saknas”).|
| Loggnivå| Den maximala utdatanivån som visas i loggarna. De giltiga värdena är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).|
| LogPath| Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.| 
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 
 



