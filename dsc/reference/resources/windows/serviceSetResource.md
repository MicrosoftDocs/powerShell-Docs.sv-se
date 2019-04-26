---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC ServiceSet-resurs
ms.openlocfilehash: 5694c2abc5c0caf0098670b629af464b35125583
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62076845"
---
# <a name="dsc-serviceset-resource"></a>DSC ServiceSet-resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **ServiceSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera tjänster på målnoden. Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [tjänsten resource](serviceResource.md) för varje tjänst som anges i den `Name` egenskapen.

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
| Namn| Anger tjänstnamn. Observera att ibland Detta skiljer sig från namn som visas. Du kan hämta en lista över tjänsterna samt enheternas aktuella status med den [Get-Service](https://technet.microsoft.com/library/hh849804.aspx) cmdlet.|
| Startuptype för| Anger starttypen för tjänsten. De värden som tillåts för den här egenskapen är: **Automatisk**, **inaktiverad**, och **manuell**|
| BuiltInAccount| Anger kontot du använder för tjänsterna. De värden som tillåts för den här egenskapen är: **LocalService**, **LocalSystem**, och **NetworkService**.|
| Tillstånd| Visar status du vill säkerställa för tjänster: **Stoppad** eller **kör**.|
| Se till att| Anger om tjänsterna som finns på systemet. Den här egenskapen **frånvarande** att se till att tjänsterna inte finns. Ange värdet till **finns** (standardvärdet) säkerställer att mål-tjänster finns.|
| Autentiseringsuppgifter| Anger autentiseringsuppgifterna för kontot som tjänstresursen kommer att köras under. Den här egenskapen och **BuiltinAccount** egenskapen kan inte användas tillsammans.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är *ResourceName* och är av typen *ResourceType*, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|



## <a name="example"></a>Exempel

Följande konfiguration startar tjänsterna ”Windows ljud” och ”Remote Desktop Services”.

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
