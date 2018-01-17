---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "DSC för Linux nxUser resurs"
ms.openlocfilehash: 93e2b12af076fce687e045e3043c94fa82d61861
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC för Linux nxUser resurs

Den **nxUser** resurs i PowerShell önskad tillstånd Configuration (DSC) ger möjlighet till att hantera lokala användare på en Linux-nod.

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
| UserName| Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.| 
| Se till att| Anger om kontot finns. Ange egenskapen ”aktuella” för att säkerställa att finns ett konto och ange den till ”saknas” så att kontot inte finns.| 
| Fullständigt namn| En sträng som innehåller det fullständiga namnet för användarkontot.| 
| Beskrivning| Beskrivning för användarkontot.| 
| Lösenord| Hash för lösenordet användare på sätt som passar för Linux-datorn. Detta är vanligtvis en saltat SHA-256 eller SHA-512 hash. Det här värdet kan skapas med kommandot mkpasswd på Debian och Ubuntu Linux. För andra Linux-distributioner kan metoden crypt i Python's Crypt biblioteket användas för att generera hash-algoritmen.| 
| Inaktiverad| Anger om kontot är aktiverat. Den här egenskapen **$true** så att det här kontot är inaktiverad och inställd på **$false** så att den är aktiverad.| 
| PasswordChangeRequired| Anger om användaren kan ändra lösenordet. Den här egenskapen **$true** så att användaren inte kan ändra lösenordet och Ställ in den på **$false** att tillåta användaren att ändra lösenordet. Standardvärdet är **$false**. Den här egenskapen utvärderas endast om användarkontot inte fanns tidigare och håller på att skapas.| 
| Arbetskatalog| Arbetskatalog för användaren.| 
| Grupp-ID| Primär grupp-ID för användaren.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resursen configuration skriptblock som du vill köra först är ”ResourceName” och ”ResourceType” är av typen syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 

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

