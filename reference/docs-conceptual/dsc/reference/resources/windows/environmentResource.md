---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC-miljö-resurs
ms.openlocfilehash: d6d3b4a2086be28fbfa2bf200acef9b13b7b7825
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942484"
---
# <a name="dsc-environment-resource"></a>DSC-miljö-resurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Miljö** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler.

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
|Sökväg |Definierar den miljö variabel som konfigureras. Ange den här egenskapen som `$true` om variabeln är variabeln **Path** ; Annars anger du det till `$false`. Standardvärdet är `$false`. Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet. |
|Värde |Värdet som ska tilldelas miljövariabeln. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |
|Kontrol |Anger om en variabel finns. Ange att den här egenskapen ska **användas** för att skapa miljövariabeln om den inte finns eller för att säkerställa att dess värde matchar det som tillhandahålls via egenskapen **Value** om variabeln redan finns. Ange det som **frånvarande** för att ta bort variabeln om den finns. |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example"></a>Exempel

I följande exempel ser du att TestEnvironmentVariable finns och att det har värdet _TestValue_. Om den inte finns skapas den av.

```powershell
Environment EnvironmentExample
{
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```