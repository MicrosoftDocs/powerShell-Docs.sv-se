---
ms.date: 2017-06-12
author: JKeithB
ms.topic: reference
keywords: "WMF, powershell, inställning"
ms.openlocfilehash: 3413672e73705252225300a853c10a514500baa2
ms.sourcegitcommit: 99227f62dcf827354770eb2c3e95c5cf6a3118b4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/15/2018
---
# <a name="extract-and-parse-structured-objects-out-of-string"></a>Extrahera och parsa strukturerade objekt utanför sträng
Det skapar också några ytterligare funktioner för ConvertFrom-String-cmdlet:

-   Tar bort egenskapen text omfattning som standard. Du kan inkludera den med parametern - IncludeExtent.

-   Många learning algoritmen felkorrigeringar från MVP och community-feedback.

-   En ny parameter - UpdateTemplate spara resultaten av Inlärningsalgoritmen till en kommentar i mallfilen. Detta gör learning bearbeta (den långsammaste delen) en enstaka kostnad. Kör konvertera strängen med en mall som innehåller kodade Inlärningsalgoritmen är nu nästan omedelbar.


<a name="extract-and-parse-structured-objects-out-of-string-content"></a>Extrahera och parsa strukturerade objekt från strängen innehåll
----------------------------------------------------------

I samarbete med [Microsoft Research](http://research.microsoft.com/), en ny **ConvertFrom sträng** cmdlet har lagts till.

Denna cmdlet har stöd för två lägen: basic avgränsade parsning och exempel-driven parsning av genereras automatiskt.

Avgränsad parsning som standard delar inmatningen vid blanksteg och tilldelar grupperna egenskapsnamn. Du kan anpassa avgränsaren:

> 1 \[C:\\temp\] &gt; &gt; ”Hello World” | ConvertFrom sträng | Format-Table-automatiskt

P1    P2
--    --

Cmdleten stöder också automatiskt genererade exempel datadrivna parsning baserat på de [FlashExtract](http://research.microsoft.com/en-us/um/people/sumitg/flashextract.html) forskning arbete i [Microsoft Research](http://research.microsoft.com).

Överväg att en textbaserad adressbok för att komma igång:

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

Kopiera några exempel till en fil som du vill använda som mallen:

    Ana Trujillo

    Redmond, WA

    Antonio Moreno

    Renton, WA

   

Placera klammerparenteser runt data som du vill extrahera, ger den ett namn som du gör. Eftersom den **namn** egenskapen (och dess associerade andra egenskaper) kan visas flera gånger, Använd en asterisk (\*) att indikera att detta resulterar i flera poster (i stället för att extrahera en massa egenskaper till en post):

    {Name\*:Ana Trujillo}

    {City:Redmond}, {State:WA}

    {Name\*:Antonio Moreno}

    {City:Renton}, {State:WA}

Från den här uppsättningen exempel **ConvertFrom sträng** kan nu automatiskt extrahera objektbaserad utdata från indatafiler med liknande struktur.

> 2 \[C:\\temp\]
>
> &gt;&gt; Get-innehåll. \\addresses.output.txt | ConvertFrom-String - TemplateFile. \\addresses.template.txt | &gt; &gt; &gt; Format-Table-automatiskt
>
> ExtentText namn stad tillstånd
> ----------                     ----               ----     -----
> ANA Trujillo...                ANA Trujillo Redmond, WA Antonio Moreno...              Antonio Moreno Renton WA Thomas Hardy...                Thomas Hardy Seattle WA Christina Berglund...          Christina Berglund Redmond  WA Hanna Moos...                  Hanna Moos Puyallup WA

Att göra ytterligare datamanipulering på extraherade text i **ExtentText** egenskapen fångar oformaterade texten som posten extraherades. Ge feedback om den här funktionen eller dela innehåll som du har problem med skrivning till exempel e-postmeddelande till <psdmfb@microsoft.com>.

