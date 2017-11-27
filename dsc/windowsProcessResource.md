---
ms.date: 2017-06-12
author: eslesar
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsProcess resurs
ms.openlocfilehash: c34d3cb1d4d9b899b45fba7b4b148a7c977f5365
ms.sourcegitcommit: 75f70c7df01eea5e7a2c16f9a3ab1dd437a1f8fd
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 06/12/2017
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Den **WindowsProcess** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att konfigurera processer på målnoden.

## <a name="syntax"></a>Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ DependsOn = [string[]] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ StandardOutputPath = [string] ]
    [ WorkingDirectory = [string] ]
}
```

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   | 
|---|---| 
| Argument| Anger en sträng med argument som ska skickas till processen som-är. Om du behöver ange flera argument placeras i den här strängen.| 
| Sökväg| Sökvägen till den körbara filen processen. Om det här namnet på den körbara filen (inte fullständigt kvalificerade sökvägen) DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) att hitta den körbara filen. Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, DSC kommer inte att använda den **sökväg** miljövariabeln för att hitta filen, och ett fel genereras om sökvägen inte finns. Relativa sökvägar tillåts inte.| 
| autentiseringsuppgifter| Anger autentiseringsuppgifterna för att starta processen.| 
| Se till att| Anger om processen finns. Ange egenskapen ”aktuella” så att processen finns. Ange annars det till ”saknas”. Standardvärdet är ”saknas”.| 
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är ”DependsOn =” [ResourceType] ResourceName ”''.| 
| StandardErrorPath| Anger sökvägen till om du vill skriva standardfelet. Alla befintliga filen skrivs över.| 
| StandardInputPath| Anger den inkommande standardplatsen.| 
| StandardOutputPath| Indikerar platsen om du vill skriva standardutdata. Alla befintliga filen skrivs över.| 
| WorkingDirectory| Anger den plats som ska användas som den aktuella arbetskatalogen för processen.| 

