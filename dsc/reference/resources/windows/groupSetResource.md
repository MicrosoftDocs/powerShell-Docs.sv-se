---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
description: Är en mekanism för att hantera lokala grupper på målnoden.
title: DSC GroupSet-resurs
ms.openlocfilehash: afe4c4d33ac5620c411481e93d76a1f90c26deb9
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077185"
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet-resurs

> Gäller för: Windows PowerShell 5.0

Den **GroupSet** resursen i Windows PowerShell Desired State Configuration (DSC) ger dig möjlighet att hantera lokala grupper på målnoden. Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [gruppen resource](groupResource.md) för varje grupp som anges i den `GroupName` parametern.

Använd den här resursen när du vill lägga till och/eller ta bort samma listan över medlemmar i mer än en grupp, ta bort mer än en grupp eller lägga till mer än en grupp med samma lista över medlemmar.

## <a name="syntax"></a>Syntax

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
| MembersToExclude| Använd den här egenskapen att ta bort medlemmar från det befintliga medlemskapet i grupperna. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen. Detta genererar ett fel.|
| Autentiseringsuppgifter| De autentiseringsuppgifter som krävs för att få åtkomst till fjärranslutna resurser. **Obs**: Det här kontot måste ha behörighet som Active Directory så att lägga till alla icke-lokala konton i gruppen. Annars uppstår ett fel.
| Se till att| Anger om det finns grupperna. Ange den här egenskapen till ”” så att grupperna som inte finns. Ange värdet till ”Visa” (standardvärdet) säkerställer att grupperna som finns.|
| Medlemmar| Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan inte använda antingen den **MembersToExclude** eller **MembersToInclude** egenskapen. Detta genererar ett fel.|
| MembersToInclude| Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen. Detta genererar ett fel.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.|

## <a name="example-1-ensuring-groups-are-present"></a>Exempel 1: Säkerställa grupper finns

I följande exempel visar hur du se till att det finns två grupper som kallas ”myGroup” och ”myOtherGroup”.

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

> [!NOTE]
> Det här exemplet använder autentiseringsuppgifter i klartext för enkelhetens skull. Information om hur du krypterar autentiseringsuppgifterna i MOF-konfigurationsfilen finns i [skydda MOF-filen](../../../pull-server/secureMOF.md).
