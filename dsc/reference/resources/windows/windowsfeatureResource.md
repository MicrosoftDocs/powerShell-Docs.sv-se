---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-WindowsFeature-resurs
ms.openlocfilehash: 7a57f4b2797ab3bb202aea8b2543d1e3f14074e9
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55685972"
---
# <a name="dsc-windowsfeature-resource"></a>DSC-WindowsFeature-resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **WindowsFeature** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.

## <a name="syntax"></a>Syntax

```
WindowsFeature [string] #ResourceName
{
    Name = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ IncludeAllSubFeature = [bool] ]
    [ LogPath = [string] ]
    [ DependsOn = [string[]] ]
    [ Source = [string] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Namn| Anger namnet på rollen eller funktionen som du vill kontrollera läggs till eller tas bort. Det här är samma som den __namn__ egenskap från den [Get-WindowsFeature](/powershell/module/servermanager/Get-WindowsFeature) cmdlet, och inte visningsnamnet för rollen eller funktionen.|
| Autentiseringsuppgifter| Anger autentiseringsuppgifterna som används för att lägga till eller ta bort roll eller funktion.|
| Se till att| Anger om rollen eller funktionen läggs till. Om du vill se till att rollen eller funktionen är har lagts till, ange den här egenskapen ”aktuella” för att se till att rollen eller funktionen tas bort, egenskapen till ””.|
| IncludeAllSubFeature| Den här egenskapen __$true__ att säkerställa att tillståndet för alla obligatoriska underfunktioner med tillståndet för funktionen som du anger med den __namn__ egenskapen.|
| LogPath| Anger sökvägen till en loggfil där du vill att resursprovidern att logga in igen.|
| DependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Källa| Anger platsen för källfilen för installationen, om det behövs.|

## <a name="example"></a>Exempel
```powershell
WindowsFeature RoleExample
{
    Ensure = "Present"
    # Alternatively, to ensure the role is uninstalled, set Ensure to "Absent"
    Name = "Web-Server" # Use the Name property from Get-WindowsFeature
}
```