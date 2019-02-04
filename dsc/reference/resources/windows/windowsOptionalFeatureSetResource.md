---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsOptionalFeatureSet-resurs
ms.openlocfilehash: c27d026e01bbb443a82112e37f1d199fb3482e49
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55683949"
---
# <a name="dsc-windowsoptionalfeatureset-resource"></a>DSC WindowsOptionalFeatureSet-resurs

> Gäller för: Windows PowerShell 5.0

Den **WindowsOptionalFeatureSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.
Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [WindowsOptionalFeature-resurs](windowsOptionalFeatureResource.md) för varje funktion som anges i den `Name` egenskapen.

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
| Namn| Anger namnet på de funktioner som du vill se till att är aktiverade eller inaktiverade.|
| Se till att| Anger om funktionerna är aktiverade. För att säkerställa att funktionerna är aktiverade, ange den här egenskapen till ”aktivera” för att säkerställa att funktionerna är inaktiverade, egenskapen till ”inaktivera”.|
| Källa| Inte implementerat.|
| NoWindowsUpdateCheck| Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera funktioner. Om $true DISM inte kontaktar WU.|
| RemoveFilesOnDisable| Inställd **$true** att ta bort alla filer som är associerade med funktioner när de är inaktiverade (det vill säga när **Kontrollera** anges till ””).|
| Loggnivå| Den maximala utdatanivån som visas i loggarna. Godkända värden är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).|
| LogPath| Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
