---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxEnvironment-resurs
description: DSC för Linux nxEnvironment-resurs
ms.openlocfilehash: 86ed538732254967cb4a3bb55af4f6b179947e52
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92644681"
---
# <a name="dsc-for-linux-nxenvironment-resource"></a>DSC för Linux nxEnvironment-resurs

**NxEnvironment** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera systemmiljövariabler på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxEnvironment <string> #ResourceName
{
    Name = <string>
    [ Value = <string>
    [ Path = <bool> }
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den miljö variabel som du vill säkerställa ett speciellt tillstånd för. |
|Värde |Värdet som ska tilldelas miljövariabeln. |
|Sökväg |Definierar den miljö variabel som konfigureras. Ange den här egenskapen till `$true` om variabeln är **sökvägsvariabeln** . annars anger du den som `$false` . Standardvärdet är `$false`. Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om variabeln finns eller inte. Ange att den här egenskapen ska **användas** för att se till att variabeln finns. Ange det som **frånvarande** för att se till att variabeln inte finns. Standardvärdet finns **.** |

## <a name="additional-information"></a>Ytterligare information

- Om **sökvägen** saknas eller anges till `$false` hanteras miljövariabler i `/etc/environment` .
  Dina program eller skript kan behöva konfigureras för att käll `/etc/environment` filen ska kunna komma åt de hanterade miljövariablerna.
- Om **sökväg** är inställd på `$true` hanteras miljövariabeln i filen `/etc/profile.d/DSCenvironment.sh` . Den här filen kommer att skapas om den inte finns. Om alternativet för **att se** till att värdet **saknas** och **sökvägen** är inställt på `$true` , tas en befintlig miljö variabel bara bort från `/etc/profile.d/DSCenvironment.sh` och inte från andra filer.

## <a name="example"></a>Exempel

I följande exempel visas hur du använder **nxEnvironment** -resursen för att se till att **TestEnvironmentVariable** finns och har värdet "test-Value". Om **TestEnvironmentVariable** inte finns kommer den att skapas.

```powershell
Import-DSCResource -Module nx

nxEnvironment EnvironmentExample
{
    Ensure = "Present"
    Name = "TestEnvironmentVariable"
    Value = "TestValue"
}
```
