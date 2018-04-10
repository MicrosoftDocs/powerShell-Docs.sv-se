---
ms.date: 06/12/2017
ms.topic: conceptual
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: 7964eabe5f4585600ae80f3e5ff7439c0d954769
ms.sourcegitcommit: cf195b090b3223fa4917206dfec7f0b603873cdf
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/09/2018
---
# <a name="dsc-file-resource"></a>DSC-filresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

Filresurser i Windows PowerShell önskad tillstånd Configuration (DSC) tillhandahåller en mekanism för att hantera filer och mappar på målnoden.

>**Obs:** om den **MatchSource** egenskap är inställd på **$false** (vilket är standardvärdet), innehållet kopieras cachelagras första gången konfigurationen tillämpas.
>Efterföljande program av konfigurationen kommer inte att söka efter uppdaterade filer eller mappar i sökvägen som anges av **SourcePath**. Om du vill söka efter uppdateringar av filer eller mappar i **SourcePath** varje gång konfigurationen tillämpas ange **MatchSource** till **$true**.

## <a name="syntax"></a>Syntax
```
File [string] #ResourceName
{
    DestinationPath = [string]
    [ Attributes = [string[]] { Archive | Hidden | ReadOnly | System }]
    [ Checksum = [string] { CreatedDate | ModifiedDate | SHA-1 | SHA-256 | SHA-512 } ]
    [ Contents = [string] ]
    [ Credential = [PSCredential] ]
    [ Ensure = [string] { Absent | Present } ]
    [ Force = [bool] ]
    [ Recurse = [bool] ]
    [ DependsOn = [string[]] ]
    [ SourcePath = [string] ]
    [ Type = [string] { Directory | File } ]
    [ MatchSource = [bool] ]
}
```

## <a name="properties"></a>Egenskaper

|  Egenskap  |  Beskrivning   |
|---|---|
| Målsökväg| Anger den plats där du vill kontrollera tillståndet för en fil eller katalog.|
| Attribut| Anger tillståndet som attribut för filen eller katalogen.|
| Kontrollsumma| Anger kontrollsumma ska användas för att fastställa om de två filerna är samma typ. Om __kontrollsumma__ anges endast filen eller katalogen namn som används för jämförelse. Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifiedDate.|
| Innehåll| Anger innehållet i en fil, till exempel en viss sträng.|
| autentiseringsuppgifter| Anger de autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler, om sådan åtkomst krävs.|
| Se till att| Anger om filen eller katalogen finns. Ange den här egenskapen till ”saknas” för att se till att filen eller katalogen inte finns. Ange den till ”finns” för att se till att filen eller katalogen finns. Standardvärdet är ”saknas”.|
| Force| Vissa åtgärder (till exempel skriver över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av egenskapen Force åsidosätter sådana fel. Standardvärdet är __$false__.|
| Recurse| Anger om underkataloger ingår. Den här egenskapen __$true__ att ange att du vill underkataloger som ska inkluderas. Standardvärdet är __$false__. **Obs**: den här egenskapen är endast giltig när egenskapen Type har angetts till katalogen.|
| dependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Om ID för resurskonfigurationen skriptblock som du vill köra först är exempelvis __ResourceName__ och dess typ är __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Källsökväg| Anger sökvägen som du vill kopiera filen eller mappen resurs.|
| Typ| Anger om resursen som konfigureras är en katalog eller fil. Ange den här egenskapen till ”Directory” för att indikera att resursen är en katalog. Ange den till ”fil” för att indikera att resursen är en fil. Standardvärdet är ”fil”.|
| MatchSource| Om inställd på standardvärdet __$false__, och alla filer på källan (exempelvis filer A, B och C) kommer att läggas till målet första gången konfigurationen tillämpas. Om en ny fil (D) läggs till källan kommer den inte att lägga till målet trots att använda konfigurationen igen senare. Om värdet är __$true__, och varje gång konfigurationen tillämpas nya filerna senare på källan (till exempel fil D i det här exemplet) läggs till målet. Standardvärdet är **$false**.|

## <a name="example"></a>Exempel

I följande exempel visas hur du använder filresurs så att en katalog med sökvägen `C:\Users\Public\Documents\DSCDemo\DemoSource` på en dator (till exempel ”pull”-server) finns också (tillsammans med alla undermappar) på målnoden. Dessutom skriver ett bekräftande meddelande till loggfilen när du är klar och innehåller en instruktion för att säkerställa att filkontroll-åtgärden körs innan loggningsåtgärden.

```powershell
Configuration FileResourceDemo
{
    Node "localhost"
    {
        File DirectoryCopy
        {
            Ensure = "Present"  # You can also set Ensure to "Absent"
            Type = "Directory" # Default is "File".
            Recurse = $true # Ensure presence of subdirectories, too
            SourcePath = "C:\Users\Public\Documents\DSCDemo\DemoSource"
            DestinationPath = "C:\Users\Public\Documents\DSCDemo\DemoDestination"
        }

        Log AfterDirectoryCopy
        {
            # The message below gets written to the Microsoft-Windows-Desired State Configuration/Analytic log
            Message = "Finished running the file resource with ID DirectoryCopy"
            DependsOn = "[File]DirectoryCopy" # This means run "DirectoryCopy" first.
        }
    }
}
```