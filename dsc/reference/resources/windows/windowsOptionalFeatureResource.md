---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-WindowsOptionalFeature-resurs
ms.openlocfilehash: 390caefd2ad190afc651b22ed1beb5cf1d604527
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076766"
---
# <a name="dsc-windowsoptionalfeature-resource"></a>DSC-WindowsOptionalFeature-resurs

> Gäller för: Windows PowerShell 5.0

Den **WindowsOptionalFeature** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att säkerställa att valfria funktioner är aktiverade på målnoden.

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
| Namn| Anger namnet på den funktion som du vill se till att är aktiverat eller inaktiverat.|
| Se till att| Anger om funktionen är aktiverad. För att säkerställa att funktionen är aktiverad, Ställ in den här egenskapen till ”aktivera” för att säkerställa att funktionen är inaktiverad, egenskapen till ”inaktivera”.|
| Källa| Inte implementerat.|
| NoWindowsUpdateCheck| Anger om DISM kontaktar Windows Update (WU) när du söker efter källfilerna för att aktivera en funktion. Om $true DISM inte kontaktar WU.|
| RemoveFilesOnDisable| Inställd **$true** att ta bort alla filer som är associerade med funktionen när den är inaktiverad (det vill säga när **Kontrollera** anges till ””).|
| Loggnivå| Den maximala utdatanivån som visas i loggarna. Godkända värden är: ”ErrorsOnly” (endast fel loggas), ”ErrorsAndWarning” (fel och varningar loggas), och ”ErrorsAndWarningAndInformation” (fel, varningar och felsökningsinformation loggas).|
| LogPath| Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|