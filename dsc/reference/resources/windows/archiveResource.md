---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-Arkivera resursen
ms.openlocfilehash: d5ccd242d000a0907c6768f30923764be6bf20a3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62077559"
---
# <a name="dsc-archive-resource"></a>DSC-Arkivera resursen

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Arkivera resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att packa upp arkivfiler (.zip) på en specifik sökväg.

## <a name="syntax"></a>Syntax
```MOF
Archive [string] #ResourceName
{
    Destination = [string]
    Path = [string]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ DependsOn = [string[]] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Validate = [bool] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Mål| Anger den plats där du vill kontrollera arkivinnehållet extraheras.|
| Sökväg| Anger källsökvägen för arkivfilen.|
| __Kontrollsumma__| Definierar den typ som ska användas när du bestämmer om två filer är lika. Om __kontrollsumma__ inte anges endast filen eller katalogen namnet används för jämförelse. Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde none (standard). Om du anger __kontrollsumma__ utan __verifiera__, konfigurationen misslyckas.|
| Se till att| Avgör om du vill kontrollera om innehållet i arkivet på den __mål__. Den här egenskapen __finns__ att säkerställa att innehållet finns. Ange den till __frånvarande__ att se till att de inte finns. Standardvärdet är __finns__.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resursen configuration skriptblocket som du vill köra först ResourceName och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Verifiera| Använder egenskapen kontrollsumma för att avgöra om arkivet matchar signaturen. Om du anger kontrollsumma utan att verifiera misslyckas konfigurationen. Om du anger verifiera utan kontrollsumma, används en SHA-256-kontrollsumma som standard.|
| Force| Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av egenskapen Force åsidosätter sådana fel. Standardvärdet är FALSKT.|

## <a name="example"></a>Exempel

I följande exempel visar hur du använder Arkivera resursen så att innehållet i en arkivfil kallas Test.zip finns och har extraherats vid ett givet mål.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```