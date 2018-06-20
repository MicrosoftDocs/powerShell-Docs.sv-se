---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: Tillgänglighetsgruppsresursen DSC
ms.openlocfilehash: 68e0840eaeb116b92260ca697acd5796460a2909
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/17/2018
ms.locfileid: "34222079"
---
# <a name="dsc-group-resource"></a>Tillgänglighetsgruppsresursen DSC

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Grupp-resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera lokala grupper på målnoden.

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
| autentiseringsuppgifter| De autentiseringsuppgifter som krävs för att komma åt fjärresurser. **Obs**: det här kontot måste ha behörighet att lägga till alla icke-lokala konton i gruppen Active Directory, annars uppstår ett fel när konfigurationen körs på målnoden.
| Beskrivning| Beskrivning av gruppen.|
| Se till att| Anger om gruppen finns. Ange den här egenskapen till ”saknas” så att gruppen inte finns. Ange värdet ”finns” (standardvärdet) säkerställer att gruppen finns.|
| Medlemmar| Använd den här egenskapen för att ersätta det aktuella gruppmedlemskapet med de angivna medlemmarna. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration, bör inte använda någon av **MembersToExclude** eller **MembersToInclude** egenskapen. Detta genererar ett fel.|
| MembersToExclude| Ta bort medlemmar från det befintliga medlemskapet i gruppen med hjälp av den här egenskapen. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen. Detta genererar ett fel.|
| MembersToInclude| Använd den här egenskapen för att lägga till medlemmar i det befintliga medlemskapet i gruppen. Värdet för den här egenskapen är en matris med strängar i formuläret *domän*\\*användarnamn*. Om du anger den här egenskapen i en konfiguration kan du inte använda den **medlemmar** egenskapen. Detta genererar ett fel.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.|

## <a name="example-1"></a>Exempel 1

I följande exempel visas hur du kontrollerar att en grupp med namnet ”TestGroup” saknas.

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

I följande exempel visas hur du lägger till en Active Directory-användare i gruppen lokala administratörer som en del av en flera datorn Lab version om du redan använder en PSCredential för kontot lokal administratör.
Eftersom den används också för domänens administratörskonto (efter befordran), behöver vi sedan konvertera den här befintliga PSCredential till en domän egna autentiseringsuppgifter.
Vi kan sedan lägga till en domänanvändare i den lokala gruppen Administratörer på medlemsservern.

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

I följande exempel visas hur du ser du till en lokal grupp TigerTeamAdmins, på servern TigerTeamSource.Contoso.Com innehåller inte ett visst domänkonto Contoso\JerryG.

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