---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxGroup-resurs
ms.openlocfilehash: c61b6ab4a8c56d085b5297dcfc7582187d54f946
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048784"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC för Linux nxGroup-resurs

Den **nxGroup** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala grupper på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present } ]
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning |
|---|---|
| Gruppnamn| Anger namnet på gruppen som du vill se till att ett visst tillstånd.|
| Se till att| Anger om du vill kontrollera om gruppen. Ange egenskapen ”aktuella” för att se till att gruppen finns. Ange den till ”inte” för att se till att gruppen inte finns. Standardvärdet är ”tillgänglig”.|
| Medlemmar| Anger de medlemmar som utgör gruppen.|
| MembersToInclude| Anger de användare som du vill se till att är medlemmar i gruppen.|
| MembersToExclude| Anger de användare som du vill se till att inte är medlemmar i gruppen.|
| PreferredGroupID| Anger om möjligt grupp-id till det angivna värdet. Om grupp-id används, används nästa tillgängliga grupp-id.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** för resursen configuration-skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = '[ResourceType]ResourceName'`.|

## <a name="example"></a>Exempel

I följande exempel säkerställer att användare monuser finns och är medlem i gruppen 'DBusers'.

```powershell
Import-DSCResource -Module nx

Node $node {
    nxUser UserExample {
       UserName = 'monuser'
       Description = 'Monitoring user'
       Password = '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
       Ensure = 'Present'
       HomeDirectory = '/home/monuser'
    }

    nxGroup GroupExample {
       GroupName = 'DBusers'
       Ensure = 'Present'
       MembersToInclude = 'monuser'
       DependsOn = '[nxUser]UserExample'
    }
}
```