---
ms.date: 2017-06-12
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsFeatureSet resurs
ms.openlocfilehash: a2bb008852ccfdc04998a57d3e64e08bf05e6433
ms.sourcegitcommit: a444406120e5af4e746cbbc0558fe89a7e78aef6
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/17/2018
---
# <a name="dsc-windowsfeatureset-resource"></a>DSC WindowsFeatureSet resurs

> Gäller för: Windows PowerShell 5.0

Den **WindowsFeatureSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.
Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsFeature resurs](windowsfeatureResource.md) för varje funktion som anges i den `Name` egenskapen.

Använd den här resursen när du vill konfigurera ett antal Windows-funktioner till samma tillstånd.

## <a name="syntax"></a>Syntax

```
WindowsFeatureSet [string] #ResourceName
{
    Name = [string[]] 
    [ Ensure = [string] { Absent | Present }  ]
    [ Source = [string] ]
    [ IncludeAllSubFeature = [bool] ]
    [ Credential = [PSCredential] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   | 
|---|---| 
| Namn| Namnen på de roller eller funktioner som du vill kontrollera läggs till eller tas bort. Det här är samma som den **namn** -egenskapen för den [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, och inte visningsnamnet för roller eller funktioner.| 
| autentiseringsuppgifter| Autentiseringsuppgifter som ska användas för att lägga till eller ta bort roller och funktioner.| 
| Se till att| Anger om roller och funktioner har lagts till. För att säkerställa att de roller eller funktioner är tillagt, Ställ in den här egenskapen till ”finns” för att säkerställa att bort roller eller funktioner, egenskapen till ”saknas”.| 
| IncludeAllSubFeature| Den här egenskapen **$true** att inkludera alla nödvändiga underfunktioner med funktioner som du anger med den **namn** egenskapen.| 
| LogPath| Sökvägen till en loggfil där du vill att resursprovidern att logga in igen.| 
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 
| Källa| Anger platsen för källfilen för installationen, om det behövs.| 

## <a name="example"></a>Exempel

Följande konfiguration ser till att den **Web Server** (IIS) och **SMTP-servern** funktioner och dess underfunktioner vardera, installeras.

```powershell
configuration FeatureSetTest
{
    Import-DscResource -ModuleName PSDesiredStateConfiguration
    Node localhost
    {

        WindowsFeatureSet WindowsFeatureSetExample
        {
            Name                    = @("SMTP-Server", "Web-Server")
            Ensure                  = 'Present'
            IncludeAllSubFeature    = $true
        } 
    }
}
```

