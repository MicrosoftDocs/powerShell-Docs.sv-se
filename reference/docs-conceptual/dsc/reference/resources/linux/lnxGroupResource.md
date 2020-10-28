---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxGroup-resurs
description: DSC för Linux nxGroup-resurs
ms.openlocfilehash: 3544bee763c0a4456002f9a02fde38de5d4fb65c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664252"
---
# <a name="dsc-for-linux-nxgroup-resource"></a>DSC för Linux nxGroup-resurs

**NxGroup** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxGroup <string> #ResourceName
{
    GroupName = <string>
    [ Members = <string[]> ]
    [ MembersToInclude = <string[]> ]
    [ MembersToExclude = <string[]> ]
    [ PreferredGroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present } ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den grupp som du vill säkerställa ett speciellt tillstånd för. |
|Medlemmar |Anger de medlemmar som utgör gruppen. |
|MembersToInclude |Anger de användare som du vill ska vara medlemmar i gruppen. |
|MembersToExclude |Anger de användare som du vill säkerställa inte är medlemmar i gruppen. |
|PreferredGroupID |Anger grupp-ID till det angivna värdet om det är möjligt. Om grupp-ID: t används för närvarande används nästa tillgängliga grupp-ID. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om gruppen finns eller inte. Ange att den här egenskapen **finns för att** säkerställa att gruppen finns. Ange det som **frånvarande** för att se till att gruppen inte finns. Standardvärdet finns **.** |

## <a name="example"></a>Exempel

I följande exempel ser du till att användaren ' monuser ' finns och är medlem i gruppen ' DBusers '.

```powershell
Import-DSCResource -Module nx

Node $node
{
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
