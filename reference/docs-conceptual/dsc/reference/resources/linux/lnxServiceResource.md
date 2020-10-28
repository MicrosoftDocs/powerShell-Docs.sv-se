---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxService-resurs
description: DSC för Linux nxService-resurs
ms.openlocfilehash: 4eefe491c491c9245732def1cc85260f368ef9e1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92648795"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC för Linux nxService-resurs

**NxService** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera tjänster på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd } ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Namnet på tjänsten/daemon som ska konfigureras. |
|Domänkontrollant |Typ av tjänst kontrollant som ska användas när tjänsten konfigureras. |
|Enabled |Anger om tjänsten startar vid start. |
|Tillstånd |Anger om tjänsten körs. Ange att den här egenskapen ska **stoppas** för att säkerställa att tjänsten inte körs. Ange att den ska **köras** för att säkerställa att tjänsten körs. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |

## <a name="additional-information"></a>Ytterligare information

**NxService** -resursen skapar inte någon tjänst definition eller ett skript för tjänsten om den inte finns. Du kan använda PowerShell- **nxFile** resurs resurs för att hantera förekomst eller innehåll i tjänst definitions filen eller skriptet.

## <a name="example"></a>Exempel

I följande exempel visas konfigurationen av tjänsten "httpd" (för Apache HTTP-server) som är registrerad hos **system** tjänst hanteraren.

```powershell
Import-DSCResource -Module nx

Node $node
{
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```
