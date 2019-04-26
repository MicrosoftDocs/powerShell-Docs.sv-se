---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxPackage-resurs
ms.openlocfilehash: 64bb89a95bd6cbaea4e74b8a9979de52428fef3f
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077882"
---
# <a name="dsc-for-linux-nxpackage-resource"></a>DSC för Linux nxPackage-resurs

Den **nxPackage** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera paket på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxPackage <string> #ResourceName
{
    Name = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ PackageManager = <string> { Yum | Apt | Zypper } ]
    [ PackageGroup = <bool>]
    [ Arguments = <string> ]
    [ ReturnCode = <uint32> ]
    [ LogPath = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| Namn| Namnet på paketet som du vill se till att ett visst tillstånd.|
| Se till att| Anger om du vill kontrollera om paketet. Ange egenskapen ”aktuella” för att se till att paketet finns. Ange den till ”inte” för att se till att paketet inte finns. Standardvärdet är ”tillgänglig”.|
| PackageManager| Värden som stöds är ”yum”, ”apt” och ”zypper”. Anger package manager att använda när du installerar paket. Om **FilePath** anges, används den angivna sökvägen för att installera paketet. I annat fall används en pakethanterare att installera paketet från en förkonfigurerad lagringsplats. Om varken **PackageManager** eller **FilePath** har angetts, standard-Pakethanteraren för systemet används.|
| FilePath| Sökvägen där paketet finns|
| PackageGroup| Om **$true**, **namn** förväntas vara namnet på en paketeringsgrupp för användning med en **PackageManager**. **PacakgeGroup** är inte giltig när du anger en **FilePath**.|
| Argument| En sträng med argument som exakt så som kommer att skickas till paketet.|
| Returkod| Den förväntade returkod. Om den faktiska returkod matchar inte det förväntade värdet som anges här kan ett fel returneras i konfigurationen.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

## <a name="example"></a>Exempel

I följande exempel ser till att paket med namnet ”httpd” är installerad på en Linux-dator med ”Yum”-Pakethanteraren.

```
Import-DSCResource -Module nx

Node $node {
nxPackage httpd
{
    Name = "httpd"
    Ensure = "Present"
    PackageManager = "Yum"
}
}
```