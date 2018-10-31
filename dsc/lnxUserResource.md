---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC för Linux nxUser-resurs
ms.openlocfilehash: 1b02be1559957585a2a1733630cb93440e8182f9
ms.sourcegitcommit: e76665315fd928bf85210778f1fea2be15264fea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/30/2018
ms.locfileid: "50226040"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC för Linux nxUser-resurs

Den **nxUser** resursen i PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala användare på en Linux-nod.

## <a name="syntax"></a>Syntax

```
nxUser <string> #ResourceName
{
    UserName = <string>
    [ Ensure = <string> { Absent | Present }  ]
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]

}
```

## <a name="properties"></a>Egenskaper

|  Egenskap |  Anger namnet på kontot som du vill se till att ett visst tillstånd. |
|---|---|
| UserName| Anger den plats där du vill kontrollera status för en fil eller katalog.|
| Se till att| Anger om kontot finns. Ange den här egenskapen ”aktuella” så att konton som finns och ange den till ”” så att kontot inte finns.|
| FullName| En sträng som innehåller det fullständiga namnet för användarkontot.|
| Beskrivning| Beskrivning för användarkontot.|
| Lösenord| Hash för användarnas lösenord på sätt som passar för Linux-dator. Detta är vanligtvis en saltat SHA-256 eller SHA-512 hash. Det här värdet kan genereras med kommandot mkpasswd på Debian och Ubuntu Linux. För andra Linux-distributioner kan metoden crypt i Python's Crypt biblioteket användas för att generera en hash.|
| Inaktiverad| Anger om kontot har aktiverats. Den här egenskapen **$true** så att det här kontot är inaktiverat och ange den till **$false** så att den är aktiverad.|
| PasswordChangeRequired| Anger om användaren kan ändra lösenordet. Den här egenskapen **$true** så att användaren inte kan ändra lösenordet och ange den till **$false** att tillåta användare att ändra lösenordet. Standardvärdet är **$false**. Den här egenskapen utvärderas bara om användarkontot inte fanns tidigare och håller på att skapas.|
| Arbetskatalog| Arbetskatalog för användaren.|
| Grupp-ID| Primär grupp-ID för användaren.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resursen configuration skriptblocket som du vill köra först är ”ResourceName” och ”ResourceType” är av typen, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|

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