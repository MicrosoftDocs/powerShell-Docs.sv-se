---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxService resurs"
ms.openlocfilehash: 4273ad59f15eedd08b07888ebb6ee51d039b72b3
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC för Linux nxService resurs

Den **nxService** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxService <string> #ResourceName
{
    Name = <string>
    [ Controller = <string> { init | upstart | systemd }  ]
    [ Enabled = <bool> ]
    [ State = <string> { Running | Stopped } ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper
|  Egenskap |  Beskrivning | 
|---|---|
| Namn| Namnet på tjänsten/daemon för att konfigurera.| 
| Domänkontrollant| Typ av service controller ska använda när du konfigurerar tjänsten.| 
| Aktiverat| Anger om tjänsten startar vid start.| 
| Läge| Anger om tjänsten körs. Den här egenskapen till ”Stoppad” för att se till att tjänsten inte körs. Ange den till ”körs” för att se till att tjänsten inte körs.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 


## <a name="additional-information"></a>Ytterligare information

Den **nxService** resursen kommer inte att skapa en tjänstdefinitionen eller ett skript för tjänsten om den inte finns. Du kan använda PowerShell Desired State Configuration **nxFile** resurs resurs som ska hantera förekomsten eller innehållet i tjänstdefinitionsfilen eller skript.

## <a name="example"></a>Exempel

I följande exempel visas konfigurationen för tjänsten ”httpd” (för Apache http-Server) som registrerats med den **SystemD** tjänsthanteraren.

```
Import-DSCResource -Module nx 

Node $node {
#Apache Service
nxService ApacheService 
{
Name = "httpd"
State = "running"
Enabled = $true
Controller = "systemd"
}
}
```

