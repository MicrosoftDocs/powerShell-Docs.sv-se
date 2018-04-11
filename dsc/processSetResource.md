---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC ProcessSet resurs
ms.openlocfilehash: d3c7383da5fd10580612527465ab621004ee7269
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess resurs

> Gäller för: Windows PowerShell 5.0

Den **ProcessSet** resurs i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att konfigurera processer på målnoden. Den här resursen är en [sammansatta resurs](authoringResourceComposite.md) som anropar den [WindowsProcess resurs](windowsProcessResource.md) för varje grupp som anges i den `GroupName` parametern.

## <a name="syntax"></a>Syntax

```
WindowsProcess [string] #ResourceName
{
    Arguments = [string]
    Path = [string]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present }  ]
    [ StandardOutputPath = [string] ]
    [ StandardErrorPath = [string] ]
    [ StandardInputPath = [string] ]
    [ WorkingDirectory = [string] ]
    [ DependsOn = [string[]] ]
}
```

## <a name="properties"></a>Egenskaper
|  Egenskap  |  Beskrivning   |
|---|---|
| Argument| En sträng som innehåller argument som ska skickas till processen som-är. Om du behöver ange flera argument placeras i den här strängen.|
| Sökväg| Sökvägar till processen körbara filer. Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar) DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) att hitta filerna. Om du värdena för den här egenskapen är fullständigt kvalificerade sökvägar, DSC kommer inte att använda den **sökväg** miljövariabeln kan hitta filerna och genereras ett fel om någon av sökvägarna som inte finns. Relativa sökvägar tillåts inte.|
| autentiseringsuppgifter| Anger autentiseringsuppgifterna för att starta processen.|
| Se till att| Anger om det finns processer. Ange egenskapen ”aktuella” så att processen finns. Ange annars det till ”saknas”. Standardvärdet är ”saknas”.|
| StandardErrorPath| Sökvägen som standard fel vid skrivning av processer. Alla befintliga filen skrivs över.|
| StandardInputPath| Dataströmmen som processen tar emot standardindata.|
| StandardOutputPath| Sökvägen till filen som processerna skriva standardutdata. Alla befintliga filen skrivs över.|
| WorkingDirectory| Den plats som används som den aktuella arbetskatalogen för processer.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis **ResourceName** och dess typ är **_ResourceType**, syntaxen för den här egenskapen är ”DependsOn =”[ResourceType] ResourceName ”''.|