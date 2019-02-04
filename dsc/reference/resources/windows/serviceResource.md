---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-tjänstresurs
ms.openlocfilehash: 09571bd0eaa428e7d0bb7a533d6ad1c0c936e2cf
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55688303"
---
# <a name="dsc-service-resource"></a>DSC-tjänstresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0


Den **Service** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera tjänster på målnoden.

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
| Namn| Anger namnet på tjänsten. Observera att ibland Detta skiljer sig från visningsnamnet. Du kan hämta en lista över tjänsterna samt enheternas aktuella status med cmdleten Get-Service.|
| BuiltInAccount| Anger kontot du använder för tjänsten. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.|
| Autentiseringsuppgifter| Anger autentiseringsuppgifterna för kontot som tjänsten ska köras under. Den här egenskapen och __BuiltinAccount__ egenskapen kan inte användas tillsammans.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Startuptype för| Anger starttypen för tjänsten. De värden som tillåts för den här egenskapen är: **Automatisk**, **inaktiverad**, och **manuell**|
| Tillstånd| Anger det tillstånd som du vill säkerställa för tjänsten.|
| Beskrivning | Anger beskrivningen av Måltjänsten.|
| Visningsnamn | Anger visningsnamnet för Måltjänsten.|
| Se till att | Anger om Måltjänsten finns i systemet. Den här egenskapen **frånvarande** så inte finns target-tjänsten. Ange värdet till **finns** (standardvärdet) säkerställer att Måltjänsten finns.|
| Sökväg | Anger sökvägen till den binära filen för en ny tjänst.|

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