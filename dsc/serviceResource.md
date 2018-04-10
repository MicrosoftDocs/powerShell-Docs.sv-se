---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-tjänstresurs
ms.openlocfilehash: 59d7c0c7147bf28b92d64a25c0d67c277e0bb210
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-service-resource"></a>DSC-tjänstresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0


Den **Service** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på målnoden.

## <a name="syntax"></a>Syntax

```
Service [string] #ResourceName
{
    Name = [string]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Description = [string] ]
    [ DisplayName = [string] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Path = [string] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Namn| Anger namnet på tjänsten. Observera att ibland Detta skiljer sig från namnet. Du kan hämta en lista över tjänster och det aktuella tillståndet med cmdleten Get-Service.|
| BuiltInAccount| Anger kontot du använder för tjänsten. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.|
| autentiseringsuppgifter| Anger autentiseringsuppgifterna för kontot som tjänsten ska köras under. Den här egenskapen och __BuiltinAccount__ egenskapen kan inte användas tillsammans.|
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| StartupType| Anger starttypen för tjänsten. De värden som tillåts för den här egenskapen är: **automatisk**, **inaktiverad**, och **manuell**|
| Läge| Visar du vill säkerställa för tjänsten.|
| Beskrivning | Anger beskrivningen av Måltjänsten.|
| Visningsnamn | Anger visningsnamnet för Måltjänsten.|
| Se till att | Anger om Måltjänsten finns på systemet. Den här egenskapen **saknas** så att Måltjänsten inte finns. Ange värdet till **finns** (standardvärdet) säkerställer att Måltjänsten finns.|
| Sökväg | Anger sökvägen till den binära fil för en ny tjänst.|

## <a name="example"></a>Exempel

```powershell
configuration ServiceTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        Service ServiceExample
        {
            Name        = "TermService"
            StartupType = "Manual"
            State       = "Running"
        }
    }
}
```