---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxGroup resurs"
ms.openlocfilehash: bc01f6ae5ed61aff63958fe55f30d82f9b81b2b9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC för Linux nxGroup resurs

Den **nxGroup** resurs i PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera lokala grupper på en Linux-nod.

## <a name="syntax"></a>Syntax

```powershell
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ Members = <string[]> ]
    [ MebersToInclude = <string[]>]
    [ MembersToExclude = <string[]> ]
    [ DependsOn = <string[]> ]
}

```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Beskrivning | 
|---|---|
| Gruppnamn| Anger namnet på gruppen som du vill se till att ett visst tillstånd.| 
| Se till att| Anger om du vill kontrollera att gruppen finns. Ange egenskapen ”aktuella” för att se till att gruppen finns. Ange den till ”saknas” för att se till att gruppen inte finns. Standardvärdet är ”saknas”.| 
| Medlemmar| Anger de medlemmar som utgör gruppen.| 
| MembersToInclude| Anger de användare som du vill kontrollera är medlemmar i gruppen.| 
| MembersToExclude| Anger de användare som du vill se till att inte är medlemmar i gruppen.| 
| PreferredGroupID| Anger om möjligt grupp-id till det angivna värdet. Om grupp-id är för närvarande används, används nästa tillgängliga grupp-id.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om den **ID** resursens configuration skriptblock som du vill köra först är **ResourceName** och dess typ är **ResourceType**, syntaxen för detta Egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

## <a name="example"></a>Exempel

I följande exempel säkerställer att användare ”monuser” finns och är medlem i gruppen ”DBusers”.

```
Import-DSCResource -Module nx 

Node $node {

nxUser UserExample{
   UserName = "monuser"
   Description = "Monitoring user"
   Password  =    '$6$fZAne/Qc$MZejMrOxDK0ogv9SLiBP5J5qZFBvXLnDu8HY1Oy7ycX.Y3C7mGPUfeQy3A82ev3zIabhDQnj2ayeuGn02CqE/0'
   Ensure = "Present"
   HomeDirectory = "/home/monuser"
}
 
nxGroup GroupExample{
   GroupName = "DBusers"
   Ensure = "Present"
   MembersToInclude = "monuser"
   DependsOn = "[nxUser]UserExample"            
}
}
```

