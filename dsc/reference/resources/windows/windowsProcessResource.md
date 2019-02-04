---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC WindowsProcess-resurs
ms.openlocfilehash: cee93ab283ded407d6e032161125aa6d6ac98827
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "55684817"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-resurs

_Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0_

Den **WindowsProcess** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att konfigurera processer på målnoden.

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

| Egenskap | Beskrivning |
| --- | --- |
| Argument| Anger en sträng med argument som ska skickas till processen som – är. Om du vill ange flera argument kan du placera dem på den här strängen.|
| Sökväg| Sökvägen till den process körbara filen. Om det här namnet på den körbara filen (inte fullständigt kvalificerade sökvägen) DSC-resurs söker igenom miljön **sökväg** variabeln (`$env:Path`) att hitta den körbara filen. Om värdet för den här egenskapen är en fullständigt kvalificerad sökväg, DSC kommer inte att använda den **sökväg** miljövariabeln att hitta filen, och genererar ett fel om sökvägen inte finns. Relativa sökvägar är inte tillåtna.|
| Autentiseringsuppgifter| Anger autentiseringsuppgifterna för att starta processen.|
| Se till att| Anger om processen finns. Ange egenskapen ”aktuella” så att processen finns. Annars kan ange den till ””. Standardvärdet är ”tillgänglig”.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"` .|
| StandardErrorPath| Anger sökvägen till om du vill skriva standardfelet. Alla befintliga filer kommer att skrivas över.|
| StandardInputPath| Anger standardplats för indata.|
| StandardOutputPath| Anger platsen för att skriva standardutdata. Alla befintliga filer kommer att skrivas över.|
| WorkingDirectory| Anger den plats som ska användas som den aktuella arbetskatalogen för processen.|