---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxService-resurs
ms.openlocfilehash: fe8043995205649378725f2ab0a78e19313739c9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684250"
---
# <a name="dsc-for-linux-nxservice-resource"></a>DSC för Linux nxService-resurs

Den **nxService** resurs i PowerShell Desired State Configuration (DSC) är en mekanism för att hantera tjänster på en Linux-nod.

## <a name="syntax"></a>Syntax

```
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

| Egenskap | Beskrivning |
|---|---|
| Namn| Namnet på tjänsten/daemon för att konfigurera.|
| Domänkontrollant| Typ av tjänsthanteraren för att använda när du konfigurerar tjänsten.|
| Aktiverad| Anger om tjänsten startar vid start.|
| Tillstånd| Anger om tjänsten körs. Ange den här egenskapen till ”Stoppad” för att säkerställa att tjänsten inte körs. Ange den till ”körs” för att säkerställa att tjänsten inte körs.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="additional-information"></a>Ytterligare information

Den **nxService** resurs skapar inte en tjänstdefinition eller ett skript för tjänsten om den inte finns. Du kan använda PowerShell Desired State Configuration **nxFile** resursen att hantera förekomsten eller innehållet i tjänstdefinitionsfilen eller skript.

## <a name="example"></a>Exempel

I följande exempel visas konfigurationen för tjänsten ”httpd” (för Apache HTTP Server), som registrerats med den **SystemD** tjänsthanteraren.

```powershell
Import-DSCResource -Module nx

Node $node {
    #Apache Service
    nxService ApacheService {
        Name = 'httpd'
        State = 'running'
        Enabled = $true
        Controller = 'systemd'
    }
}
```