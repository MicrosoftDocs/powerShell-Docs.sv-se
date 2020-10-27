---
ms.date: 09/20/2019
ms.topic: reference
title: DSC GroupSet-resurs
description: DSC GroupSet-resurs
ms.openlocfilehash: f0e10409b0c80658ee05358c506b32da4b9deca7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650474"
---
# <a name="dsc-groupset-resource"></a>DSC GroupSet-resurs

> Gäller för: Windows PowerShell 5. x

**GroupSet** -resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden. Den här resursen är en [sammansatt resurs](../../../resources/authoringResourceComposite.md) som anropar [grupp resursen](groupResource.md) för varje grupp som anges i `GroupName` parametern.

Använd den här resursen när du vill lägga till och/eller ta bort samma lista med medlemmar till mer än en grupp, ta bort mer än en grupp eller lägga till mer än en grupp med samma lista med medlemmar.

## <a name="syntax"></a>Syntax

```Syntax
Group [string] #ResourceName
{
    GroupName = [string[]]
    [ MembersToInclude = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Namnen på de grupper som du vill säkerställa ett enskilt tillstånd för. |
|Medlemmar |Använd den här egenskapen för att ersätta det aktuella grupp medlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda någon av egenskaperna **MembersToExclude** eller **MembersToInclude** . Om du gör det skapas ett fel. |
|MembersToInclude |Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** . Om du gör det skapas ett fel. |
|MembersToExclude |Använd den här egenskapen för att ta bort medlemmar från de befintliga medlemskapet i grupperna. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** . Om du gör det skapas ett fel. |
|Autentiseringsuppgift |De autentiseringsuppgifter som krävs för att komma åt fjär resurser. Det här kontot måste ha rätt Active Directory behörighet för att lägga till alla icke-lokala konton i gruppen. annars sker ett fel. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om grupperna finns. Ange den här egenskapen som **saknas** för att se till att grupperna inte finns. Att ställa in det för att **Visa** ser till att grupperna finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example-1-ensuring-groups-are-present"></a>Exempel 1: se till att grupper finns

I följande exempel visas hur du ser till att två grupper som kallas "min grupp" och "myOtherGroup" finns.

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
> I det här exemplet används autentiseringsuppgifter för oformaterad text för enkelhet. Information om hur du krypterar autentiseringsuppgifter i MOF-konfigurationsfilen finns i [skydda MOF-filen](../../../pull-server/secureMOF.md).
