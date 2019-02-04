---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Miljöresurs
ms.openlocfilehash: 2bc1600a9df32538d59efa712569b12fa9e3beee
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685986"
---
# <a name="dsc-environment-resource"></a>DSC-Miljöresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den __miljö__ resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera systemets miljövariabler.

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
| Se till att| Anger om det finns en variabel. Den här egenskapen __finns__ att skapa miljövariabeln om det inte finns eller se till att värdet matchar vad som är tillgängligt via den __värdet__ egenskapen om variabeln redan finns. Ange den till __frånvarande__ att ta bort variabeln om den finns.|
| Sökväg| Definierar miljövariabeln som konfigureras. Den här egenskapen __$true__ om variabeln är den __sökväg__ variabeln, i annat fall väljer __$false__. Standardvärdet är __$false__. Om variabeln som konfigureras är den __sökväg__ variabeln, värdet tillhandahålls via de __värdet__ egenskapen kommer att läggas till det befintliga värdet.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Värde| Värdet som tilldelas miljövariabeln.|

## <a name="example"></a>Exempel

I följande exempel ser till att __TestEnvironmentVariable__ finns och har värdet __Provvärde__. Om det inte finns skapas den.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```