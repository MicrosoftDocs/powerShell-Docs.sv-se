---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxGroup-resurs
ms.openlocfilehash: 098ae2e8ab183934ec3c185c0fd237731b1353dc
ms.sourcegitcommit: 18985d07ef024378c8590dc7a983099ff9225672
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/04/2019
ms.locfileid: "71941427"
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

## <a name="properties"></a>properties

|Egenskap |Beskrivning |
|---|---|
|Namn |Anger namnet på den grupp som du vill säkerställa ett speciellt tillstånd för. |
|Members |Anger de medlemmar som utgör gruppen. |
|MembersToInclude |Anger de användare som du vill ska vara medlemmar i gruppen. |
|MembersToExclude |Anger de användare som du vill säkerställa inte är medlemmar i gruppen. |
|PreferredGroupID |Anger grupp-ID till det angivna värdet om det är möjligt. Om grupp-ID: t används för närvarande används nästa tillgängliga grupp-ID. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är `DependsOn = "[ResourceType]ResourceName"`syntaxen för att använda den här egenskapen. |
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