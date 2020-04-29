---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxEnvironment-resurs
ms.openlocfilehash: 55c1b2402e23c1042ed48b40c1084aa63c515b36
ms.sourcegitcommit: 6545c60578f7745be015111052fd7769f8289296
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/22/2020
ms.locfileid: "71941441"
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
|Name |Anger namnet på den miljö variabel som du vill säkerställa ett speciellt tillstånd för. |
|Värde |Värdet som ska tilldelas miljövariabeln. |
|Sökväg |Definierar den miljö variabel som konfigureras. Ställ in den här `$true` egenskapen till om variabeln **är sökvägsvariabeln;** annars ställer du in den `$false`på. Standardvärdet är `$false`. Om variabeln som konfigureras är **sökvägsvariabeln,** läggs värdet som anges via egenskapen **Value** till i det befintliga värdet. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
|Kontrol |Anger om variabeln finns eller inte. Ange att den här egenskapen ska **användas** för att se till att variabeln finns. Ange det som **frånvarande** för att se till att variabeln inte finns. Standardvärdet finns **.** |

## <a name="additional-information"></a>Ytterligare information

- Om **sökvägen** saknas eller anges till `$false`hanteras miljövariabler i. `/etc/environment`
  Dina program eller skript kan behöva konfigureras för att `/etc/environment` käll filen ska kunna komma åt de hanterade miljövariablerna.
- Om **sökväg** är inställd på `$true`hanteras miljövariabeln i filen `/etc/profile.d/DSCenvironment.sh`. Den här filen kommer att skapas om den inte finns. Om alternativet för **att se** till att **Path** värdet **saknas** och sökvägen `$true`är inställt på, tas en befintlig miljö `/etc/profile.d/DSCenvironment.sh` variabel bara bort från och inte från andra filer.

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