---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC ProcessSet-resurs
ms.openlocfilehash: 91a2d5b562864addcb8e11062916d291448bbf57
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048630"
---
# <a name="dsc-windowsprocess-resource"></a>DSC WindowsProcess-resurs

_Gäller för: Windows PowerShell 5.0_

Den **ProcessSet** resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att konfigurera processer på målnoden. Den här resursen är en [sammansatta resource](../../../resources/authoringResourceComposite.md) som anropar den [WindowsProcess-resurs](windowsProcessResource.md) för varje grupp som anges i den `GroupName` parametern.

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

| Egenskap | Beskrivning |
| --- | --- |
| Argument| En sträng som innehåller argument ska skickas till processen som – är. Om du vill ange flera argument kan du placera dem på den här strängen.|
| Sökväg| Sökvägar till processen körbara filer. Om dessa är namnen på de körbara filerna (inte fullständigt kvalificerade sökvägar), DSC-resurs söker miljön **sökväg** variabeln (`$env:Path`) och hitta filerna. Om värdena för den här egenskapen är fullständigt kvalificerade sökvägar, DSC kommer inte att använda den **sökväg** miljövariabeln och hitta filerna och genererar ett fel om någon av sökvägarna som inte finns. Relativa sökvägar är inte tillåtna.|
| Autentiseringsuppgifter| Anger autentiseringsuppgifterna för att starta processen.|
| Se till att| Anger om processerna som finns. Ange egenskapen ”aktuella” så att processen finns. Annars kan ange den till ””. Standardvärdet är ”tillgänglig”.|
| StandardErrorPath| Sökvägen som processerna skriva standardfel. Alla befintliga filer kommer att skrivas över.|
| StandardInputPath| Dataströmmen som processen tar emot standardindata.|
| StandardOutputPath| Sökvägen till filen som processerna skriva standardutdata. Alla befintliga filer kommer att skrivas över.|
| WorkingDirectory| Den plats som används som den aktuella arbetskatalogen för processer.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är **ResourceName** och är av typen **_ResourceType**, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"` .|
