---
ms.date: 07/17/2020
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxFileLine-resurs
ms.openlocfilehash: c87054ec7039923bcb5e7c5c5d58f9221a12c9ca
ms.sourcegitcommit: 41e1acbd9ce0f49a23c6eb99facd2c280d836836
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/18/2020
ms.locfileid: "86463677"
---
# <a name="dsc-for-linux-nxfileline-resource"></a>DSC för Linux nxFileLine-resurs

**NxFileLine** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera rader i en konfigurations fil på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxFileLine <string> #ResourceName
{
    FilePath = <string>
    ContainsLine = <string>
    [ DoesNotContainPattern = <string> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|FilePath |Den fullständiga sökvägen till filen som hanterar rader i på målnoden. |
|ContainsLine |En rad för att se till att den finns i filen. Den här raden läggs till i filen om den inte finns i filen. **ContainsLine** är obligatoriskt, men kan anges till en tom sträng ( `ContainsLine = ""` ) om det inte behövs. |
|DoesNotContainPattern |Ett mönster för reguljära uttryck för rader som inte ska finnas i filen. För rader som finns i den fil som matchar det här reguljära uttrycket tas raden bort från filen. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |

## <a name="example"></a>Exempel

Det här exemplet visar hur du konfigurerar filen genom att använda **nxFileLine** `/etc/sudoers` -resursen och se till att användaren: monuser är konfigurerad till inte requiretty.

```powershell
Import-DscResource -Module nx

nxFileLine DoNotRequireTTY
{
   FilePath = "/etc/sudoers"
   ContainsLine = 'Defaults:monuser !requiretty'
   DoesNotContainPattern = "Defaults:monuser[ ]+requiretty"
}
```
