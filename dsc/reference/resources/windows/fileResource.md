---
ms.date: 06/12/2017
keywords: DSC, powershell, konfiguration, installation
title: DSC-filresurs
ms.openlocfilehash: e5f7a91e5f19c8c7bbada090804d8f29a7cfedd5
ms.sourcegitcommit: e04292a9c10de9a8391d529b7f7aa3753b362dbe
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 01/04/2019
ms.locfileid: "54048748"
---
# <a name="dsc-file-resource"></a>DSC-filresurs

> Gäller för: Windows PowerShell 4.0, Windows PowerShell 5.0

File-resursen i Windows PowerShell Desired State Configuration (DSC) är en mekanism för att hantera filer och mappar på målnoden.

>**Obs:** Om den **MatchSource** är inställd på **$false** (vilket är standardvärdet), kopieras innehållet cachelagras första gången konfigurationen används.
>Efterföljande program av konfigurationen inte att söka efter uppdaterade filer och/eller mappar i sökvägen som angetts av **SourcePath**. Om du vill söka efter uppdateringar till filer och/eller mappar i **SourcePath** varje gång konfigurationen används, ange **MatchSource** till **$true**.

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
| Målsökväg| Anger den plats där du vill kontrollera status för en fil eller katalog.|
| Attribut| Anger det önskade tillståndet för attribut för den aktuella filen eller katalogen.|
| Kontrollsumma| Anger kontrollsumma ska användas för att avgöra om de två filerna är samma typ. Om __kontrollsumma__ inte anges endast filen eller katalogen namnet används för jämförelse. Giltiga värden är: SHA-1, SHA-256, SHA-512, createdDate, modifieddate kunde.|
| Innehåll| Anger innehållet i en fil, till exempel en viss sträng.|
| Autentiseringsuppgifter| Anger de autentiseringsuppgifter som krävs för att komma åt resurser, till exempel källfiler, om sådan åtkomst krävs.|
| Se till att| Anger om filen eller katalogen finns. Ange den här egenskapen till ”” så att filen eller katalogen inte finns. Ange den ”aktuella” för att se till att filen eller katalogen finns. Standardvärdet är ”tillgänglig”.|
| Force| Vissa åtgärder för sammansättningsfiler (till exempel att skriva över en fil eller ta bort en katalog som inte är tom) resulterar i ett fel. Med hjälp av egenskapen Force åsidosätter sådana fel. Standardvärdet är __$false__.|
| Recurse| Anger om underkataloger ingår. Den här egenskapen __$true__ att indikera att du vill att underkataloger som ska tas med. Standardvärdet är __$false__. **Obs**: Den här egenskapen gäller endast när egenskapen Type har angetts till katalogen.|
| DependsOn | Anger att konfigurationen av en annan resurs måste köras innan den här resursen har konfigurerats. Till exempel om ID för resurskonfigurationen skriptblock som du vill köra först är __ResourceName__ och är av typen __ResourceType__, syntaxen för den här egenskapen är `DependsOn = "[ResourceType]ResourceName"`.|
| Källsökväg| Anger sökvägen som du vill kopiera filen eller mappen resursen från.|
| Typ| Anger om resursen som konfigureras är en katalog eller en fil. Ange egenskapen till ”Directory” för att indikera att resursen är en katalog. Ange den till ”fil” för att indikera att resursen är en fil. Standardvärdet är ”fil”.|
| MatchSource| Om inställd på standardvärdet __$false__, och sedan alla filer på källan (t.ex, filer A, B och C) kommer att läggas till målet första gången konfigurationen används. Om en ny fil (D) läggs till i källan, läggs det inte till mål, även när konfigurationen används igen senare. Om värdet är __$true__, och sedan varje gång konfigurationen används nya filerna senare finns på källan (t.ex filer D i det här exemplet) läggs till målet. Standardvärdet är **$false**.|

## <a name="example"></a>Exempel

I följande exempel visas hur du använder File-resursen för att säkerställa att en katalog med sökvägen `C:\Users\Public\Documents\DSCDemo\DemoSource` på en källa datorn (till exempel ”pull”-server) finns också (tillsammans med alla underkataloger) på målnoden. Den skriver en bekräftande meddelande till loggen när du är klar och innehåller en instruktion för att se till att åtgärden filkontroll körs innan loggningsåtgärden.

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