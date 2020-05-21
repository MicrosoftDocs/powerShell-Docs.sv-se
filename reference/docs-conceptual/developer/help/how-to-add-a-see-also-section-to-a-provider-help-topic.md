---
title: Så här lägger du till ett Se även-avsnitt i ett hjälp avsnitt om leverantörer | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: b6561120d1bbe848ab4ebcdec7de92c6cad96314
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83564831"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers

I det här avsnittet beskrivs hur du fyller i avsnittet **Se även** i en providers hjälp avsnitt.

Avsnittet **Se även** består av en lista med ämnen som är relaterade till leverantören eller kan hjälpa användaren att förstå och använda providern. Ämnes listan kan innehålla hjälp avsnitten om cmdlet-hjälpen, providerns hjälp och konceptuellhet ("om") i Windows PowerShell. Det kan även innehålla referenser till böcker, papper och online-ämnen, inklusive en online-version av hjälp avsnittet aktuell Provider.

När du refererar till online-ämnen ska du ange URI: n eller en sökterm som oformaterad text. `Get-Help`Cmdlet: en länkar eller omdirigerar inte till något av ämnena i listan. `Online`Parametern för `Get-Help` cmdleten fungerar inte heller med leverantörs hjälpen.

Avsnittet Se även skapas från `RelatedLinks` elementet och de taggar som det innehåller. Följande XML visar hur du lägger till taggarna.

### <a name="to-add-see-also-topics"></a>Så här lägger du till "Se även"-ämnen

1. I filen *AssemblyName*. dll-Help. xml i- `providerHelp` elementet lägger du till ett- `RelatedLinks` element. `RelatedLinks`Elementet ska vara det sista elementet i `providerHelp` elementet. Endast ett- `RelatedLinks` element tillåts i varje leverantörs hjälp avsnitt.

   Till exempel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. För varje ämne i avsnittet **Se även** , `RelatedLinks` Lägg till ett-element i elementet `navigationLink` . `navigationLink`Lägg sedan till ett- `linkText` element och ett-element inom varje element `uri` . Om du inte använder `uri` -elementet kan du lägga till det som ett tomt element ( \< uri/>).

   Till exempel:

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

3. Skriv ämnes namnet mellan `linkText` taggarna. Om du tillhandahåller en URI, anger du den mellan `uri` taggarna. Om du vill ange onlineversionen av hjälp avsnittet för aktuell Provider, mellan `linkText` taggarna, skriver du "online version:" i stället för ämnes namnet. Normalt är länken "online version:" den första artikeln i listan se även.

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
