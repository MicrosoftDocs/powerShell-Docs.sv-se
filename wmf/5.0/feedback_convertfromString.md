---
ms.date: 06/12/2017
keywords: WMF, powershell, inställning
ms.openlocfilehash: fcf2adf67f36edb534df3e2a849459fb20e1c2de
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62085362"
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extrahera och parsa strukturerade objekt från sträng

Det skapar också ytterligare några funktioner för den `ConvertFrom-String` cmdlet:

- Tar bort egenskapen utsträckning text som standard. Du kan inkludera den med parametern - IncludeExtent.

- Många learning algoritmen felkorrigeringar från MVP och community-feedback.

- En ny parameter - UpdateTemplate att spara resultatet av Inlärningsalgoritmen till en kommentar i mallfilen. Detta gör learning bearbeta (långsammaste scenen) en engångskostnad. Kör Convert-sträng med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbart.

## <a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extrahera och parsa strukturerade objekt från sträng innehåll

I samarbete med [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F), en ny `ConvertFrom-String` cmdlet har lagts till.

Den här cmdleten stöder två lägen: basic avgränsade parsning och automatiskt genererad exempel-drivna parsning.

Avgränsad parsning, som standard delar upp inmatningen vid blanksteg och tilldelar egenskapsnamn till grupperna. Du kan anpassa avgränsaren:

```powershell
"Hello World" | ConvertFrom-String | Format-Table -Auto
```

```output
P1     P2
--     --
Hello  World
```

Cmdleten stöder också automatiskt genererade exempel-drivna parsning baserat på den [FlashExtract](https://www.microsoft.com/en-us/research/publication/flashextract-framework-data-extraction-examples/?from=http%3A%2F%2Fresearch.microsoft.com%2Fen-us%2Fum%2Fpeople%2Fsumitg%2Fflashextract.html) undersöka arbete i [Microsoft Research](https://www.microsoft.com/en-us/research/?from=http%3A%2F%2Fresearch.microsoft.com%2F).

Överväg ett textbaserat adressboken för att komma igång:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

    Thomas Hardy

    Seattle, WA

    Christina Berglund

    Redmond, WA

    Hanna Moos

    Puyallup, WA
```

Kopiera några exempel till en fil som du vill använda som din mall:

```
    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA
```

Placera klammerparenteser-data som du vill extrahera, ger den ett namn som du gör. Eftersom den **namn** egenskapen (och dess associerade andra egenskaper) kan visas flera gånger, använda en asterisk (\*) att indikera att detta resulterar i flera poster (i stället för att extrahera en mängd egenskaper till en post):

```
    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}
```

Från den här uppsättningen med exempel `ConvertFrom-String` nu automatiskt extrahera objektbaserad utdata från indatafilerna med liknande struktur.

```powershell
Get-Content .\addresses.output.txt | ConvertFrom-String -TemplateFile .\addresses.template.txt | Format-Table -Auto
```

```output
ExtentText                     Name               City     State
----------                     ----               ----     -----
Ana Trujillo...                Ana Trujillo       Redmond  WA
Antonio Moreno...              Antonio Moreno     Renton   WA
Thomas Hardy...                Thomas Hardy       Seattle  WA
Christina Berglund...          Christina Berglund Redmond  WA
Hanna Moos...                  Hanna Moos         Puyallup WA
```

Att göra ytterligare datamanipulering extraherad text i **ExtentText** egenskapen fångar rå text från vilket posten extraheras. Lämna feedback om den här funktionen eller för att dela innehåll som du har problem med skriva exempel, e-postmeddelande <psdmfb@microsoft.com>.