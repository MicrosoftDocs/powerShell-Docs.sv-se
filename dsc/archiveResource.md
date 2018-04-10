---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-Arkiv resurs
ms.openlocfilehash: 1accd48f3862ee09b88d2792f9b7e5a7324bcf17
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-archive-resource"></a>DSC-Arkiv resurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Arkiv-resurs i Windows PowerShell önskad tillstånd Configuration (DSC) ger dig möjlighet att packa upp arkivfiler (.zip) på en angiven sökväg.

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
| Mål| Anger den plats där du vill se till att arkivera innehåll extraheras.|
| Sökväg| Anger källsökvägen för arkivfilen.|
| __Kontrollsumma__| Definierar den typ som används när du fastställer om två filerna är samma. Om __kontrollsumma__ anges endast filen eller katalogen namn som används för jämförelse. Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate ingen (standard). Om du anger __kontrollsumma__ utan __verifiera__, konfigurationen misslyckas.|
| Se till att| Anger om du vill kontrollera om det finns innehåll till arkivet på den __mål__. Den här egenskapen __finns__ så innehållet finns. Ange det till __saknas__ så de inte finns. Standardvärdet är __finns__.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resursen configuration skriptblock som du vill köra först ResourceName och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Validera| Använder egenskapen kontrollsumma för att avgöra om arkivet matchar signaturen. Om du anger kontrollsumma utan att verifiera misslyckas konfigurationen. Om du anger verifiera utan kontrollsumma, används en SHA-256-kontrollsumma som standard.|
| Force| Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av egenskapen Force åsidosätter sådana fel. Standardvärdet är False.|

## <a name="example"></a>Exempel

I följande exempel visas hur du använder Arkiv-resurs så att innehållet i en fil kallad Test.zip finns och har extraherats vid ett givet mål.

```
Archive ArchiveExample {
    Ensure = "Present"  # You can also set Ensure to "Absent"
    Path = "C:\Users\Public\Documents\Test.zip"
    Destination = "C:\Users\Public\Documents\ExtractionPath"
}
```