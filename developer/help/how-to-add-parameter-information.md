---
title: Hur du lägger till parameterinformation | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: cf6c1442-60aa-477a-8f30-ab02b1b11039
caps.latest.revision: 7
ms.openlocfilehash: d4a5fc934a41b00f89862674e44e4540680674f7
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083373"
---
# <a name="how-to-add-parameter-information"></a>Lägga till parameterinformation

Det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet parametrar i cmdlet-hjälpavsnittet. Parameteravsnittet i hjälpavsnittet visar var och en av parametrarna för cmdleten och innehåller en detaljerad beskrivning av varje parameter.

Innehållet i avsnittet parametrar ska stämma överens med innehållet i avsnittet SYNTAX i hjälpavsnittet. Det är ansvar i hjälpfilen för att se till att både Syntax och parametrar noden innehåller liknande XML-element.

> [!NOTE]
> För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell. Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.

### <a name="to-add-parameters"></a>Lägga till parametrar

1. Öppna cmdlet-hjälpfilen och leta rätt på kommando-noden för cmdleten du dokumenterar. Om du lägger till en ny cmdlet behöver du skapa en ny nod i kommandot. Hjälp-filen innehåller en kommando-nod för varje cmdlet som du tillhandahåller hjälpinnehållet för. Här är ett exempel på en tom kommando-nod.

    ```xml
    <command:command>
    </command:command>
    ```

2. Leta upp noden beskrivning i noden kommando och lägger till en nod för parametrar som visas nedan. Endast en nod för parametrar tillåts och det omedelbart ska följa noden Syntax.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

3. I noden parametrar lägger du till en Parameter-nod för varje parameter för cmdlet: en som visas nedan.

   I det här exemplet läggs en Parameter-nod för tre parametrar.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Eftersom dessa är de samma XML-taggar som används i noden Syntax och eftersom parametrarna som anges här måste matcha parametrarna som anges av noden Syntax, kan du kopiera parametern-noder från noden Syntax och klistrar in den i noden parametrar. Dock måste du kopiera endast en instans av en Parameter-nod, även om parametern har angetts i flera parameteruppsättningar i syntax.

4. Ange de attributvärden som definierar egenskaperna för varje parameter för varje Parameter-nod. Dessa attribut inkluderar följande: krävdes globbing, pipelineinput och position.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named">
      </command:parameter>
      <command:parameter required="false" globbing="false"
               pipelineInput="false" position="named" ></command:parameter>
    </command:Parameters>
    ```

5. Lägg till namnet på parametern för varje Parameter-nod. Här är ett exempel på parameternamnet läggs till parametern-nod.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

6. Lägg till beskrivning av parametern för varje Parameter-nod. Här är ett exempel på Parameterbeskrivning som lagts till i parametern-nod.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
      </command:parameter>
    </command:parameters>
    ```

7. Lägg till .NET Framework-typen för parametern för varje Parameter-nod. Parametertypen visas tillsammans med parameternamnet.

   Här är ett exempel på .NET Framework parametertypen läggs till parametern-nod.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
      </command:parameter>
    </command:parameters>
    ```

8. Lägg till standardvärdet för parametern för varje Parameter-nod. Följande mening läggs till i Parameterbeskrivning när innehållet visas: Standardvärdet är ”DefaultValue”.

   Här är ett exempel på standardvärdet för parametern har lagts till i parametern-nod.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
        <maml:description>
          <maml:para> Add parameter description... </maml:para>
        </maml:description>
        <dev:type> Add .NET Framework type... </dev:type>
        <dev:defaultvalue> Add default value...</dev:defaultvalue>
      </command:parameter>
    </command:parameters>
    ```

9. Lägg till en nod för möjliga värden för varje Parameter som har flera värden.

   Här är ett exempel på den för en nod för möjliga värden som definierar två möjliga värden för parametern

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      /dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Här följer några saker att komma ihåg när du lägger till parametrar.

- Attribut för parametern visas inte i alla vyer i cmdlet-hjälpavsnittet. Men de visas i en tabell efter Parameterbeskrivning när användaren ombeds att ange fullständiga (Get-Help \<cmdletname > – fullständig) eller Parameter (Get-Help \<cmdletname >-parametern) vy av avsnittet.

- Beskrivning av parameter är en av de viktigaste delarna av en cmdlet-hjälpavsnittet. Beskrivningen bör vara kort, samt omfattande. Tänk också på att om Parameterbeskrivning blir för lång, till exempel när två parametrar interagerar med varandra, du kan lägga till mer innehåll i avsnittet information i cmdlet-hjälpavsnittet.

  Parametern-beskrivningen innehåller två typer av information.

- Vad cmdleten gör när parametern används.

- Det är ett giltigt värde för parametern.

- Eftersom parametervärdena som är uttryckt i .NET Framework-objekt, måste användarna mer information om dessa värden än de skulle göra i en traditionell hjälpen. Meddela användaren vilken typ av data som parametern har utformats för att acceptera och innehåller exempel.

Standardvärdet för parametern är det värde som används om parametern inte anges på kommandoraden. Observera att standardvärdet är valfritt och krävs inte för vissa parametrar, till exempel obligatoriska parametrar. Dock bör du ange ett standardvärde för de flesta valfria parametrar.

Standardvärdet hjälper användare att förstå effekten av att inte använda parametern. Beskriv standardvärdet särskilt, till exempel ”den aktuella katalogen” eller ”Windows PowerShell installationskatalogen ($pshome)” för en valfri sökväg. Du kan också skriva en mening som beskriver standard, till exempel följande mening som används för den `PassThru` parameter: ”Om PassThru anges cmdlet: en skickar inte objekt av pipelinen”.  Dessutom eftersom värdet visas motsatt fältnamnet ”**standardvärde**”, du behöver inte inkludera termen ”standardvärdet” i posten.

Standardvärdet för parametern visas inte i alla vyer i cmdlet-hjälpavsnittet. Men den visas i en tabell (tillsammans med parameterattribut) efter Parameterbeskrivning när användaren ombeds att ange fullständiga (Get-Help \<cmdletname > – fullständig) eller Parameter (Get-Help \<cmdletname >-parametern) visa i avsnittet.

Följande XML visar ett par `<dev:defaultValue>` taggar som lagts till i den `<command:parameter>` noden. Observera att standardvärdet följer direkt efter avslutande `</command:parameterValue>` tagg (när värdet för parametern har angetts) eller avslutande `</maml:description>` taggen för Parameterbeskrivning. Namn.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
  </command:parameter>
</command:parameters>
```

Lägg till värdena för uppräknade typer

Om parametern har flera värden eller värdena för en uppräknade typ, kan du använda en valfri \<dev:possibleValues > noden. Den här noden kan du ange ett namn och beskrivning för flera värden.

Tänk på att beskrivningarna för uppräknade värden inte visas i någon av standard hjälp vyer som visas i den `Get-Help` cmdleten, men andra hjälp användarna kan visa det här innehållet i sina synpunkter.

I följande XML-visas en `<dev:possibleValues>` nod med två värden anges.

```xml
<command:parameters>
  <command:parameter required="true" globbing="true"
           pipelineInput="false" position="named">
    <maml:name> Parameter name </maml:name>
    <maml:description>
      <maml:para> Parameter Description </maml:para>
    </maml:description>
    <command:parameterValue required="true">
      Value
    </command:parameterValue>
    <dev:defaultValue> Default parameter value </dev:defaultValue>
    <dev:possibleValues>
      <dev:possibleValue>
        <dev:value> Value 1 </dev:value>
        <maml:description>
          <maml:para> Description 1 </maml:para>
        </maml:description>
      <dev:possibleValue>
      <dev:possibleValue>
        <dev:value> Value 2 </dev:value>
        <maml:description>
          <maml:para> Description 2 </maml:para>
        </maml:description>
      <dev:possibleValue>
    </dev:possibleValues>
  </command:parameter>
</command:parameters>
```