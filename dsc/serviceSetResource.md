---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC ServiceSet resurs
ms.openlocfilehash: 9556a1d513c3819a36c1161e3b35388ca1eb66f9
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0


Den **ServiceSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att hantera tjänster på målnoden. Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [tjänsten resurs](serviceResource.md) för varje tjänst som anges i den `Name` egenskapen.

Använd den här resursen när du vill konfigurera ett antal tjänster till samma tillstånd.

## <a name="syntax"></a>Syntax

```
Service [string] #ResourceName
{
    Name = [string[]]
    [ StartupType = [string] { Automatic | Disabled | Manual }  ]
    [ BuiltInAccount = [string] { LocalService | LocalSystem | NetworkService }  ]
    [ State = [string] { Running | Stopped }  ]
    [ Ensure = [string] { Absent | Present }  ]
    [ Credential = [PSCredential] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Anger tjänstnamn. Observera att ibland Detta skiljer sig från visningsnamnen. Du kan hämta en lista över tjänster och deras aktuella tillstånd med den [Get-Service](https://technet.microsoft.com/en-us/library/hh849804.aspx) cmdlet.|
| StartupType| Anger starttypen för tjänsten. De värden som tillåts för den här egenskapen är: **automatisk**, **inaktiverad**, och **manuell**|  
| BuiltInAccount| Anger kontot du använder för tjänsterna. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.| 
| Läge| Visar du vill säkerställa för tjänsterna: **stoppad** eller **kör**.| 
| Se till att| Anger om tjänsterna som finns på systemet. Den här egenskapen **saknas** så att tjänsten inte finns. Ange värdet till **finns** (standardvärdet) säkerställer att mål-tjänster finns.|
| autentiseringsuppgifter| Anger autentiseringsuppgifterna för kontot som tjänsten resursen kommer att köras under. Den här egenskapen och **BuiltinAccount** egenskapen kan inte användas tillsammans.| 
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis *ResourceName* och dess typ är *ResourceType*, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 



## <a name="example"></a>Exempel

Följande konfiguration startar tjänsterna ”Windows Audio” och ”Remote Desktop Services”.

```powershell
configuration ServiceSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        ServiceSet ServiceSetExample
        {
            Name        = @("TermService", "Audiosrv")
            StartupType = "Manual"
            State       = "Running"
        } 
    }
}
```

