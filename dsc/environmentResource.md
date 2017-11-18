---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Resurs för DSC-miljö"
ms.openlocfilehash: 7c98798fa0e8fc865798ea30530e41ac87b2dadc
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-environment-resource"></a>Resurs för DSC-miljö

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den __miljö__ resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler.

## <a name="syntax"></a>Syntax
``` mof
Environment [string] #ResourceName
{
    Name = [string]
    [ Ensure = [string] { Absent | Present }  ]
    [ Path = [bool] ]
    [ DependsOn = [string[]] ]
    [ Value = [string] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger namnet på den miljövariabel som du vill se till att ett visst tillstånd.| 
| Se till att| Anger om det finns en variabel. Den här egenskapen __finns__ skapa miljövariabeln om det inte finns eller så att dess värde matchar vad som tillhandahålls via den __värdet__ egenskapen om variabeln redan finns. Ange det till __saknas__ ta bort variabeln om den finns.| 
| Sökväg| Definierar miljövariabeln som konfigureras. Den här egenskapen __$true__ om variabeln är den __sökväg__ variabeln, annars inställd på __$false__. Standardvärdet är __$false__. Om variabeln som konfigureras är den __sökväg__ variabel, värdet tillhandahålls via den __värdet__ egenskap läggs till det befintliga värdet.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 
| Värde| Värdet som tilldelas miljövariabeln.| 

## <a name="example"></a>Exempel

I följande exempel säkerställer att __TestEnvironmentVariable__ finns och har värdet __Provvärde__. Om det inte finns, skapas den.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
