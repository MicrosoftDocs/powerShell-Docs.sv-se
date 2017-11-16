---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: "Resurs för DSC-WindowsFeature"
ms.openlocfilehash: a3433577a122f6c7e31360e094a089f6ceef77c2
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsfeature-resource"></a>Resurs för DSC-WindowsFeature

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **WindowsFeature** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att säkerställa att roller och funktioner läggs till eller tas bort på målnoden.

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
| Namn| Anger namnet på rollen eller funktionen som du vill kontrollera läggs till eller tas bort. Det här är samma som den __namn__ egenskap från den [Get-WindowsFeature](https://technet.microsoft.com/en-us/library/jj205469.aspx) cmdlet, och inte visningsnamnet för rollen eller funktionen.| 
| autentiseringsuppgifter| Anger autentiseringsuppgifter som ska användas för att lägga till eller ta bort roll eller funktion.| 
| Se till att| Anger om rollen eller funktionen har lagts till. Se till att rollen eller funktionen lagts till, Ställ in den här egenskapen till ”finns” för att se till att rollen eller funktionen bort, egenskapen till ”saknas”.| 
| IncludeAllSubFeature| Den här egenskapen __$true__ att kontrollera tillståndet för alla obligatoriska underfunktioner med tillståndet för funktionen som anges med den __namn__ egenskapen.| 
| LogPath| Anger sökvägen till en loggfil där du vill att resursprovidern att logga in igen.| 
| dependsOn| Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.| 
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

