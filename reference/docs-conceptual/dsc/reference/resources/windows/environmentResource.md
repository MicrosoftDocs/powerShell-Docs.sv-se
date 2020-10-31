---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-miljö-resurs
description: DSC-miljö-resurs
ms.openlocfilehash: c7995fc5e7efdfb9a1dbae3da9f824d33c67085c
ms.sourcegitcommit: 196c7f8cd24560cac70c88acc89909f17a86aea9
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/31/2020
ms.locfileid: "93142590"
---
# <a name="dsc-environment-resource"></a>DSC-miljö-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Miljö** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler.

[!INCLUDE [Updated DSC Resources](../../../../../includes/dsc-resources.md)]

## <a name="syntax"></a>Syntax

```Syntax
Environment [string] #ResourceName
{
    Name = [string]
    [ Path = [bool] ]
    [ Value = [string] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den miljö variabel som du vill säkerställa ett speciellt tillstånd för. |
|Sökväg |Definierar den miljö variabel som konfigureras. Ange den här egenskapen till `$true` om variabeln är **sökvägsvariabeln** . annars anger du den som `$false` . Standardvärdet är `$false`. Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet. |
|Värde |Värdet som ska tilldelas miljövariabeln. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om en variabel finns. Ange att den här egenskapen ska **användas** för att skapa miljövariabeln om den inte finns eller för att säkerställa att dess värde matchar det som tillhandahålls via egenskapen **Value** om variabeln redan finns. Ange det som **frånvarande** för att ta bort variabeln om den finns. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I följande exempel ser du att TestEnvironmentVariable finns och att det har värdet _TestValue_ . Om den inte finns skapas den av.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
