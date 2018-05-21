---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsProcess resurs
ms.openlocfilehash: 72668136a3a51c17c52f762c6f94bec3ed4597b0
ms.sourcegitcommit: 54534635eedacf531d8d6344019dc16a50b8b441
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/16/2018
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