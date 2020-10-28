---
ms.date: 07/17/2020
ms.topic: reference
title: DSC för Linux nxUser-resurs
description: DSC för Linux nxUser-resurs
ms.openlocfilehash: 298caa8f5ea6d4587f9782a02d0544147ee33e84
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667393"
---
# <a name="dsc-for-linux-nxuser-resource"></a>DSC för Linux nxUser-resurs

**NxUser** -resursen i PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala användare på en Linux-nod.

## <a name="syntax"></a>Syntax

```Syntax
nxUser <string> #ResourceName
{
    UserName = <string>
    [ FullName = <string> ]
    [ Description = <string> ]
    [ Password = <string> ]
    [ Disabled = <bool> ]
    [ PasswordChangeRequired = <bool> ]
    [ HomeDirectory = <string> ]
    [ GroupID = <string> ]
    [ DependsOn = <string[]> ]
    [ Ensure = <string> { Absent | Present }  ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Anger det konto namn som du vill säkerställa ett speciellt tillstånd för. |
|---|---|
|Användarnamn |Anger den plats där du vill kontrol lera statusen för en fil eller katalog. |
|FullName |En sträng som innehåller det fullständiga namnet som ska användas för användar kontot. |
|Beskrivning |Beskrivning av användar kontot. |
|Lösenord |Hash för användarens lösen ord i rätt format för Linux-datorn. Detta är vanligt vis en saltad SHA-256-eller SHA-512-Hash. I Debian och Ubuntu Linux kan det här värdet genereras med `mkpasswd` kommandot. För andra Linux-distributioner kan du använda metoden cryption för python: s krypterings bibliotek för att generera hashen. |
|Inaktiverad |Anger om kontot är aktiverat. Ange den här egenskapen till `$true` för att säkerställa att det här kontot är inaktiverat och ange det för att `$false` säkerställa att det är aktiverat. |
|PasswordChangeRequired |Anger om användaren kan ändra lösen ordet. Ange den här egenskapen till `$true` om du vill se till att användaren inte kan ändra lösen ordet och ange det som `$false` tillåter användaren att ändra lösen ordet. Standardvärdet är `$false`. Den här egenskapen utvärderas bara om användar kontot inte fanns tidigare och skapas. |
|HomeDirectory |Användarens Hem Katalog. |
|GroupID |Användarens primära grupp-ID. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om kontot finns. Ange att den här egenskapen **finns för att** se till att kontot finns och att det inte finns **något att se** till att kontot inte finns. |

## <a name="example"></a>Exempel

I följande exempel ser du till att användaren "monuser" finns och är medlem i gruppen "DBusers".

```powershell
Import-DSCResource -Module nx

Node $node
{
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
