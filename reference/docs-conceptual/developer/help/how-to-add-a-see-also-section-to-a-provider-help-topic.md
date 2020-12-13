---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers
description: Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers
ms.openlocfilehash: df0b14ba84e04baf404081944ef62ef6745d74b2
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667665"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers

I det här avsnittet beskrivs hur du fyller i avsnittet **Se även** i en providers hjälp avsnitt.

Avsnittet **Se även** består av en lista med ämnen som är relaterade till leverantören eller kan hjälpa användaren att förstå och använda providern. Ämnes listan kan innehålla hjälp avsnitten om cmdlet-hjälpen, providerns hjälp och konceptuellhet ("om") i Windows PowerShell. Det kan även innehålla referenser till böcker, papper och online-ämnen, inklusive en online-version av hjälp avsnittet aktuell Provider.

När du refererar till online-ämnen ska du ange URI: n eller en sökterm som oformaterad text. `Get-Help`Cmdlet: en länkar eller omdirigerar inte till något av ämnena i listan. `Online`Parametern för `Get-Help` cmdleten fungerar inte heller med leverantörs hjälpen.

Avsnittet **Se även** skapas från `RelatedLinks` elementet och de taggar som det innehåller.
Följande XML visar hur du lägger till taggarna.

### <a name="to-add-see-also-topics"></a>För att lägga till se även ämnen

1. `<AssemblyName>.dll-help.xml` `providerHelp` Lägg till ett-element i-filen i-elementet `RelatedLinks` . `RelatedLinks`Elementet ska vara det sista elementet i `providerHelp` elementet. Endast ett- `RelatedLinks` element tillåts i varje leverantörs hjälp avsnitt.

   Exempel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

1. För varje ämne i avsnittet **Se även** , `RelatedLinks` Lägg till ett-element i elementet `navigationLink` . `navigationLink`Lägg sedan till ett- `linkText` element och ett-element inom varje element `uri` . Om du inte använder `uri` -elementet kan du lägga till det som ett tomt element ( \<uri/> ).

   Exempel:

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> </linkText>
                <uri> </uri>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```

1. Skriv ämnes namnet mellan `linkText` taggarna. Om du tillhandahåller en URI, anger du den mellan `uri` taggarna. Om du vill ange onlineversionen av hjälp avsnittet för aktuell Provider, mellan `linkText` taggarna, skriver du "online version:" i stället för ämnes namnet. Normalt är länken "online version:" den första artikeln i listan se även.

   I följande exempel ingår tre Se även ämnen. Det första refererar till online-versionen av det aktuella avsnittet. Den andra hänvisar till ett hjälp avsnitt för Windows PowerShell-cmdlet. Den tredje refererar till ett annat online-ämne.

    ```xml
    <providerHelp>
        <RelatedLinks>
            <navigationLink>
                <linkText> Online version: </linkText>
                <uri>http://www.fabrikam.com/help/myFunction.htm</uri>
            </navigationLink>
            <navigationLink>
                <linkText> about_functions </linkText>
                <uri/>
            </navigationLink>
            <navigationLink>
                <linkText> Windows PowerShell Getting Started Guide </linkText>
                <uri>https://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```
