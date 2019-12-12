---
ms.date: 09/20/2019
keywords: DSC, PowerShell, konfiguration, installation
title: DSC för Linux nxUser-resurs
ms.openlocfilehash: 6d7b52809741813af7fa80b1c6372b267aff4777
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "71942540"
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
|UserName |Anger den plats där du vill kontrol lera statusen för en fil eller katalog. |
|FullName |En sträng som innehåller det fullständiga namnet som ska användas för användar kontot. |
|Beskrivning |Beskrivning av användar kontot. |
|Lösenord |Hash för användarens lösen ord i rätt format för Linux-datorn. Detta är vanligt vis en saltad SHA-256-eller SHA-512-Hash. I Debian och Ubuntu Linux kan det här värdet genereras med kommandot `mkpasswd`. För andra Linux-distributioner kan du använda metoden cryption för python: s krypterings bibliotek för att generera hashen. |
|Inaktiverat |Anger om kontot är aktiverat. Ange den här egenskapen till `$true` för att säkerställa att det här kontot är inaktiverat och ange det som `$false` för att säkerställa att det är aktiverat. |
|PasswordChangeRequired |Anger om användaren kan ändra lösen ordet. Ange den här egenskapen till `$true` för att se till att användaren inte kan ändra lösen ordet och ange det som `$false` för att tillåta att användaren ändrar lösen ordet. Standardvärdet är `$false`. Den här egenskapen utvärderas bara om användar kontot inte fanns tidigare och skapas. |
|HomeDirectory |Användarens Hem Katalog. |
|GroupID |Användarens primära grupp-ID. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"`. |
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