---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Gruppresurs
ms.openlocfilehash: 9894150f6f749fc23efd4ce2b155b18788557d1d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55687512"
---
# <a name="dsc-group-resource"></a>DSC-Gruppresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Gruppresurs i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera lokala grupper på målnoden.

## <a name="syntax"></a>Syntax

```
Group [string] #ResourceName
{
    GroupName          = [string]
    [ Credential       = [PSCredential] ]
    [ Description      = [string[]] ]
    [ Ensure           = [string] { Absent | Present }  ]
    [ Members          = [string[]] ]
    [ MembersToExclude = [string[]] ]
    [ MembersToInclude = [string[]] ]
    [ DependsOn        = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Gruppnamn| Namnet på gruppen som du vill se till att ett visst tillstånd.|
| Autentiseringsuppgifter| De autentiseringsuppgifter som krävs för att få åtkomst till fjärranslutna resurser. **Obs**: Det här kontot måste ha behörighet som Active Directory så att lägga till alla icke-lokala konton i gruppen. Annars uppstår ett fel när konfigurationen körs på målnoden.
| Beskrivning| Beskrivning av gruppen.|
| Se till att| Anger om gruppen finns. Ange den här egenskapen till ”” så att gruppen inte finns. Ange värdet till ”Visa” (standardvärdet) säkerställer att gruppen finns.|
| Medlemmar| Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan inte använda antingen den **MembersToExclude** eller **MembersToInclude** egenskapen. Detta genererar ett fel.|
| MembersToExclude| Ta bort medlemmar från det befintliga medlemskapet i gruppen med hjälp av den här egenskapen. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen. Detta genererar ett fel.|
| MembersToInclude| Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formatet *domän*\\*användarnamn*. Om du ställer in den här egenskapen i en konfiguration, Använd inte den **medlemmar** egenskapen. Detta genererar ett fel.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ ResourceType] ResourceName ”''.|

## <a name="example-1"></a>Exempel 1

I följande exempel visas hur du säkerställer att en grupp med namnet ”TestGroup” inte finns.

```powershell
Group GroupExample
{
    # This removes TestGroup, if present
    # To create a new group, set Ensure to "Present“
    Ensure = "Absent"
    GroupName = "TestGroup"
}
```

## <a name="example-2"></a>Exempel 2

I följande exempel visas hur du lägger till en Active Directory-användare i gruppen lokala administratörer som en del av en flera Machine labb där du redan använder en PSCredential för kontot som lokal administratör.
Eftersom den används också för administratörskontot för domänen (efter befordran av domän), behöver vi sedan konvertera den här befintliga PSCredential till en domän eget autentiseringsuppgift.
Vi kan sedan lägga till en domänanvändare i gruppen lokala administratörer på medlemsservern.

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

I följande exempel visas hur du säkerställer en lokal grupp, TigerTeamAdmins, på servern TigerTeamSource.Contoso.Com innehåller inte ett visst domänkonto Contoso\JerryG.

```powershell
Configuration SecureTigerTeamSrouce {
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