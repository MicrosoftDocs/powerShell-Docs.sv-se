---
title: Lägga till en Se även avsnittet i ett hjälpavsnitt för providern | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 9c754ac3-cee3-4c13-9bad-e499c8a68a09
caps.latest.revision: 4
ms.openlocfilehash: f5c48fd04c620828a6e99c5c5424d11b31fd10e5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848456"
---
# <a name="how-to-add-a-see-also-section-to-a-provider-help-topic"></a>Lägga till ett ”Se även”-avsnitt i ett hjälpavsnitt för providers

Det här avsnittet beskrivs hur du fyller i **Se även** delen av ett hjälpavsnitt för providern.

Den **Se även** avsnittet består av en lista över ämnen som är relaterade till providern eller kan hjälpa dig att du bättre förstå och använda providern. Avsnittet listan kan innehålla cmdlet-hjälpen, provider hjälp och konceptuella (”information”) hjälpavsnitten i Windows PowerShell. Den kan även innehålla referenser till böcker, faktablad och online ämnen, t.ex. en onlineversionen av hjälpavsnittet för providern.

När du refererar till online ämnen, ange URI: N eller en sökterm i oformaterad text. Den `Get-Help` cmdlet inte länka eller omdirigera till något av ämnena i listan. Dessutom den `Online` -parametern för den `Get-Help` cmdlet fungerar inte med hjälp av providern.

Se även skapas från den `RelatedLinks` element och taggar som den innehåller. Följande XML-koden visar hur du lägger till taggar.

### <a name="to-add-see-also-topics"></a>Att lägga till ”Se även” ämnen

1. I den *AssemblyName*.dll-help.xml filen i den `providerHelp` element, lägga till en `RelatedLinks` element. Den `RelatedLinks` elementet ska vara det sista elementet i den `providerHelp` element. Endast en `RelatedLinks` element tillåts i varje hjälpavsnitt för providern.

   Till exempel:

    ```xml
    <providerHelp>
        <RelatedLinks>
        </RelatedLinks>
    </providerHelp>
    ```

2. För varje avsnitt i den **Se även** avsnittet i den `RelatedLinks` element, lägga till en `navigationLink` element. Sedan, i varje `navigationLink` element, lägga till en `linkText` element och en `uri` element. Om du inte använder den `uri` element, du kan lägga till det som ett tomt element (\<uri / >).

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

3. Skriv namnet på ämnet mellan den `linkText` taggar. Om du tillhandahåller en URI, skriver du det mellan den `uri` taggar. Att ange onlineversionen av hjälpavsnittet i providern mellan den `linkText` , skriver ”onlineversion”: i stället för namnet på ämnet. Normalt den ”onlineversion”: länk är det första avsnittet i avsnittet Se även listan.

   I följande exempel innehåller tre Se även avsnitt. Först avser online-versionen av det här avsnittet. Andra refererar till ett hjälpavsnitt för Windows PowerShell-cmdlet. Tredje refererar till en annan onlineavsnittet.

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
                <uri>http://go.microsoft.com/fwlink/?LinkID=89597<uri/>
            </navigationLink>
        </RelatedLinks>
    </providerHelp>
    ```