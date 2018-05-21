---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
description: Tillhandahåller en mekanism för att hantera lokala grupper på målnoden.
title: DSC GroupSet resurs
ms.openlocfilehash: 3d6fdcaef6053964d3fb3b709a5263d291a7c840
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet resurs

> Gäller för: Windows Windows PowerShell 5.0

Den **GroupSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera lokala grupper på målnoden. Resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [gruppen resurs](groupResource.md) för varje grupp som anges i den `GroupName` parameter.

Använd den här resursen när du vill lägga till och/eller ta bort samma lista över medlemmar i mer än en grupp, ta bort mer än en grupp eller Lägg till mer än en grupp med samma lista över medlemmar.

##<a name="syntax"></a>Syntaxen ##
```
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ Ensure = [string] { Absent | Present }  ]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Gruppnamn| Namnen på de grupper som du vill se till att ett visst tillstånd.|
| MembersToExclude| Använd den här egenskapen för att ta bort medlemmar från det befintliga medlemskapet i grupperna. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen. Detta genererar ett fel.|
| autentiseringsuppgifter| De autentiseringsuppgifter som krävs för att komma åt fjärresurser. **Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel.
| Se till att| Anger om det finns grupperna. Ange den här egenskapen till ”saknas” för att se till att grupperna inte finns. Ange värdet ”finns” (standardvärdet) ser du till att grupperna finns.|
| Medlemmar| Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration, bör inte använda någon av **MembersToExclude** eller **MembersToInclude** egenskapen. Detta genererar ett fel.|
| MembersToInclude| Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen. Detta genererar ett fel.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.|

## <a name="example-1"></a>Exempel 1

I följande exempel visas hur du kontrollerar att det finns två grupper som kallas ”myGroup” och ”myOtherGroup”.

```powershell
configuration GroupSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {
        GroupSet GroupSetTest
        {
            GroupName        = @("myGroup", "myOtherGroup")
            Ensure           = "Present"
            MembersToInclude = @("contoso\alice", "contoso\bob")
            MembersToExclude = $("contoso\john")
            Credential       = Get-Credential
        }
    }
}
$cd = @{
    AllNodes = @(
        @{
            NodeName                    = 'localhost'
            PSDscAllowPlainTextPassword = $true
            PSDscAllowDomainUser        = $true
        }
    )
}


GroupSetTest -ConfigurationData $cd
```

>**Obs:** det här exemplet använder autentiseringsuppgifter i klartext för enkelhetens skull. Information om hur du krypterar autentiseringsuppgifter i MOF-konfigurationsfilen finns [skydda MOF-filen](secureMOF.md).