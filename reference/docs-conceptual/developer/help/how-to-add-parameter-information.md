---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till parameterinformation
description: Lägga till parameterinformation
ms.openlocfilehash: 8f4fc46ef256a77b058df4ba506124f80732cb39
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92663055"
---
# <a name="how-to-add-parameter-information"></a>Lägga till parameterinformation

I det här avsnittet beskrivs hur du lägger till innehåll som visas i avsnittet **parametrar** i hjälp avsnittet för cmdlet. I avsnittet **parametrar** i hjälp avsnittet visas var och en av parametrarna för cmdleten och en detaljerad beskrivning av varje parameter.

Innehållet i **parameter** avsnittet ska överensstämma med innehållet i **syntax** -avsnittet i hjälp avsnittet. Det åligger hjälp författaren att se till att både noden **syntax** och **parametrar** innehåller liknande XML-element.

> [!NOTE]
> Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för PowerShell. Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.

### <a name="to-add-parameters"></a>Lägga till parametrar

1. Öppna cmdlet-hjälpen och leta upp kommando-noden för den cmdlet som du dokumenterar. Om du lägger till en ny cmdlet måste du skapa en ny kommando-nod. Hjälp filen innehåller en kommando-nod för varje cmdlet som du tillhandahåller hjälp innehåll för. Här är ett exempel på en tom kommando-nod.

    ```xml
    <command:command>
    </command:command>
    ```

1. Leta upp noden beskrivning i noden kommando och Lägg till noden parametrar enligt nedan.
   Endast en parameter-nod tillåts och den ska omedelbart följa noden syntax.

    ```xml
    <command:command>
      <command:details></command:details>
      <maml:description></maml:description>
      <command:syntax></command:syntax>
      <command:parameters>
      </command:Parameters>
    </command:command>
    ```

1. I noden parametrar lägger du till en **parameter** -nod för varje parameter i cmdleten enligt vad som visas nedan.

   I det här exemplet läggs en **parametriserad** nod till för tre parametrar.

    ```xml
    <command:parameters>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
      <command:parameter></command:parameter>
    </command:Parameters>
    ```

   Eftersom dessa är samma XML-taggar som används i noden syntax, och eftersom parametrarna som anges här måste matcha de parametrar som anges av noden syntax, kan du kopiera parametervärdena från noden syntax och klistra in dem i noden parametrar. Men var noga med att bara kopiera en instans av en parameter-nod, även om parametern anges i flera parameter uppsättningar i syntaxen.

1. Ange attributvärden som definierar egenskaperna för varje parameter för varje parameter-nod. Dessa attribut innehåller följande: required, globbing, pipelineinput och position.

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

1. Lägg till namnet på parametern för varje parameter-nod. Här är ett exempel på parameter namnet som har lagts till i noden parameter.

    ```xml
    <command:parameters>
      <command:parameter required="true" globbing="true"
               pipelineInput="false" position="named">
        <maml:name> Add parameter name...  </maml:name>
      </command:parameter>
    </command:Parameters>
    ```

1. Lägg till en beskrivning av parametern för varje **parameter** -nod. Här är ett exempel på parameter beskrivningen som läggs till i noden **parameter** .

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

1. Lägg till parameterns .NET-typ för varje **parameter** -nod. Parameter typen visas tillsammans med parameter namnet.

   Här är ett exempel på den parameter-.NET-typ som har lagts till i noden **parameter** .

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

1. Lägg till standardvärdet för parametern för varje **parameter** -nod. Följande mening läggs till i parameter beskrivningen när innehållet visas: **Standardvärde** är standardvärdet.

   Här är ett exempel på standardvärdet för parametern läggs till i noden **parameter** .

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

1. Lägg till en nod för möjliga värden för varje parameter som har flera värden.

   Här är ett exempel på en nod med möjliga värden som definierar två möjliga värden för parametern

    ```xml
    <dev:possiblevalues>
      <dev:possiblevalue>
        <dev:value>Unknown</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possiblevalue>
      <dev:possiblevalue>
        <dev:value>String</dev:value>
        <maml:description>
          <maml:para></maml:para>
        </maml:description>
      </dev:possibleValue>
    </dev:possiblevalues>
    ```

Här är några saker att komma ihåg när du lägger till parametrar.

- Attributen för parametern visas inte i alla vyer i hjälp avsnittet för cmdleten. De visas dock i en tabell som följer parameter beskrivningen när användaren ombeds använda vyn **fullständig** ( `Get-Help <cmdletname> -full` ) eller **parameter** ( `Get-Help <cmdletname> -parameter` ) för ämnet.

- Parameter beskrivningen är en av de viktigaste delarna i ett cmdlet-hjälp ämne. Beskrivningen måste vara kortfattad, samt grundlig. Kom också ihåg att om parameter beskrivningen blir för lång, t. ex. När två parametrar interagerar med varandra, kan du lägga till mer innehåll i avsnittet anteckningar i hjälp avsnittet för cmdleten.

  Parameter beskrivningen innehåller två typer av information.

- Vad cmdleten gör när parametern används.

- Det juridiska värdet för parametern.

- Eftersom parametervärdena uttrycks som .NET-objekt, behöver användarna mer information om dessa värden än de skulle ha i en traditionell kommando rads hjälp. Berätta för användaren vilken typ av data som parametern är avsedd att godkänna och inkludera exempel.

Standardvärdet för parametern är det värde som används om parametern inte anges på kommando raden. Observera att standardvärdet är valfritt och att det inte behövs för vissa parametrar, till exempel obligatoriska parametrar. Du bör dock ange ett standardvärde för de flesta valfria parametrar.

Standardvärdet hjälper användaren att förstå effekterna av att inte använda-parametern. Beskriv standardvärdet särskilt, till exempel "aktuell katalog" eller "PowerShell installations katalog ( `$PSHOME` )" för en valfri sökväg. Du kan också skriva en mening som beskriver standard, till exempel följande mening som används för parametern **Passthru** : "om Passthru inte har angetts, skickar inte cmdleten objekt nedåt i pipelinen." Eftersom värdet visas mittemot **standardvärdet** för fält namn, behöver du inte heller ta med termen "standardvärde" i posten.

Standardvärdet för parametern visas inte i alla vyer i hjälp avsnittet för cmdleten. Den visas dock i en tabell (tillsammans med parametervärdena) efter parameter beskrivningen när användaren ställer en **fullständig** ( `Get-Help <cmdletname> -full` ) eller **parameter** ( `Get-Help
<cmdletname> -parameter` ) vy av ämnet.

Följande XML visar ett par med `<dev:defaultValue>` taggar som har lagts till i `<command:parameter>` noden.
Observera att standardvärdet följer omedelbart efter den avslutande `</command:parameterValue>` taggen (när parametervärdet har angetts) eller den avslutande `</maml:description>` taggen för parameter beskrivningen. Namn.

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

Lägg till värden för uppräknade typer

Om parametern har flera värden eller värden för en uppräknings typ kan du använda en valfri \<dev:possibleValues> nod. Med den här noden kan du ange ett namn och en beskrivning för flera värden.

Observera att beskrivningarna av de uppräknade värdena inte visas i någon av de standard visnings lägen som visas av `Get-Help` cmdleten, men andra hjälp visnings program kan visa det här innehållet i sina vyer.

Följande XML visar en `<dev:possibleValues>` nod med två angivna värden.

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
