---
ms.date: 07/16/2020
ms.topic: reference
title: DSC-gruppresurs
description: DSC-gruppresurs
ms.openlocfilehash: 9e8931fe1227f3ac258c46fb1aecf4586958de66
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92650515"
---
# <a name="dsc-group-resource"></a>DSC-gruppresurs

> Gäller för: Windows PowerShell 4,0, Windows PowerShell 5. x

**Grupp** resursen i Windows PowerShell Desired State Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.

## <a name="syntax"></a>Syntax

```Syntax
Group [string] #ResourceName
{
    GroupName = [string]
    [ Credential = [PSCredential] ]
    [ Description = [string[]] ]
    [ Members = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ PsDscRunAsCredential = [PSCredential] ]
}
```

## <a name="properties"></a>Egenskaper

|Egenskap |Beskrivning |
|---|---|
|Namn |Namnet på den grupp som du vill säkerställa ett speciellt tillstånd för. |
|Autentiseringsuppgift |De autentiseringsuppgifter som krävs för att komma åt fjär resurser. Det här kontot måste ha rätt Active Directory behörighet för att lägga till alla icke-lokala konton i gruppen. annars inträffar ett fel när konfigurationen körs på målnoden.
|Beskrivning |Beskrivning av gruppen. |
|Medlemmar |Använd den här egenskapen för att ersätta det aktuella grupp medlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda någon av egenskaperna **MembersToExclude** eller **MembersToInclude** . Detta genererar ett fel. |
|MembersToExclude |Använd den här egenskapen för att ta bort medlemmar från det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** . Detta genererar ett fel. |
|MembersToInclude |Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formuläret `Domain\UserName` . Om du ställer in den här egenskapen i en konfiguration ska du inte använda egenskapen **medlemmar** . Om du gör det skapas ett fel. |

## <a name="common-properties"></a>Gemensamma egenskaper

|Egenskap |Beskrivning |
|---|---|
|DependsOn |Anger att konfigurationen av en annan resurs måste köras innan den här resursen har kon figurer ATS. Exempel: om ID: t för skript blocket för resurs konfigurationen som du vill köra först är ResourceName och dess typ är ResourceType, är syntaxen för att använda den här egenskapen `DependsOn = "[ResourceType]ResourceName"` . |
|Kontrol |Anger om gruppen finns. Ange den här egenskapen som **saknas** för att säkerställa att gruppen inte finns. Att ställa in det för att **Visa** garanterar att gruppen finns. Standardvärdet finns **.** |
|PsDscRunAsCredential |Anger autentiseringsuppgifter för att köra hela resursen som. |

> [!NOTE]
> Den gemensamma egenskapen **PsDscRunAsCredential** har lagts till i WMF 5,0 för att tillåta körning av DSC-resurser i kontexten för andra autentiseringsuppgifter. Mer information finns i [använda autentiseringsuppgifter med DSC-resurser](../../../configurations/runasuser.md).

## <a name="example-1-ensure-group-is-not-present"></a>Exempel 1: kontrol lera att gruppen inte finns

I följande exempel visas hur du ser till att en grupp med namnet "TestGroup" saknas.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present"
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2-add-domain-user-to-local-group"></a>Exempel 2: Lägg till domän användare i lokal grupp

I följande exempel visas hur du lägger till en Active Directory användare i den lokala gruppen Administratörer som en del av en labb version med flera datorer där du redan använder en PSCredential för det lokala administratörs kontot. Eftersom detta också används för domän administratörs kontot (efter domän befordran), måste du konvertera det befintliga PSCredential till en domän med egna autentiseringsuppgifter. Sedan kan vi lägga till en domän användare i den lokala gruppen Administratörer på medlems servern.

```powershell
@{
    AllNodes = @(
        @{
            NodeName = '*';
            DomainName = 'SubTest.contoso.com';
         }
        @{
            NodeName = 'Box2';
            AdminAccount = 'Admin-Dave_Alexanderson'
        }
    )
}

$domain = $node.DomainName.split('.')[0]
$DCredential = New-Object -TypeName System.Management.Automation.PSCredential -ArgumentList ("$domain\$($credential.Username)", $Credential.Password)

Group AddADUserToLocalAdminGroup {
    GroupName='Administrators'
    Ensure= 'Present'
    MembersToInclude= "$domain\$($Node.AdminAccount)"
    Credential = $dCredential
    PsDscRunAsCredential = $DCredential
}
```

## <a name="example-3"></a>Exempel 3

I följande exempel visas hur du ser till att en lokal grupp, TigerTeamAdmins, på Server TigerTeamSource.Contoso.Com inte innehåller ett visst domän konto, Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSource {
    Import-DscResource -ModuleName 'PSDesiredStateConfiguration'

    Node TigerTeamSource.Contoso.Com {
        Group TigerTeamAdmins {
            GroupName        = 'TigerTeamAdmins'
            Ensure           = 'Present'
            MembersToExclude = "Contoso\JerryG"
        }
    }
}
```
