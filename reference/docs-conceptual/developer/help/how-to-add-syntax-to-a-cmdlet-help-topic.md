---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till syntax till ett cmdlet-hjälpavsnitt
description: Lägga till syntax till ett cmdlet-hjälpavsnitt
ms.openlocfilehash: bcc037d22051c162cd0f70702da17afe7ed9c01a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659069"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Lägga till syntax till ett cmdlet-hjälpavsnitt

Innan du börjar koda XML för syntax-diagrammet i cmdlet-hjälpen läser du det här avsnittet för att få en tydlig bild av den typ av data som du behöver ange, till exempel parameter-attribut och hur dessa data visas i syntax diagrammet.

## <a name="parameter-attributes"></a>Parameter-attribut

- Krävs
  - Om värdet är true måste parametern visas i alla kommandon som använder parameter uppsättningen.
  - Om värdet är false är parametern valfri i alla kommandon som använder parameter uppsättningen.
- Position
  - Parameter namnet krävs om det har angetts.
  - Parameter namnet är valfritt om det är placerat. När den utelämnas måste parametervärdet vara i den angivna positionen i kommandot. Om värdet till exempel är position = "1" måste parametervärdet vara det första eller enda parameter värde som inte är namn i kommandot.
- Pipeline-inmatade
  - Om värdet är true (ByValue) kan du skicka pipe-information till-parametern. Indatamängden är associerad med ("bind till") parametern även om egenskaps namnet och objekt typen inte matchar den förväntade typen.
    Med PowerShell-parameterns bindnings komponenter försöker du konvertera inmatarna till rätt typ och växlar kommandot endast när typen inte kan konverteras. Endast en parameter i en parameter uppsättning kan associeras med värde.
  - Om värdet är true (ByPropertyName) kan du skicka pipe-information till-parametern. Inmatarna är dock bara kopplade till parametern när parameter namnet matchar namnet på en egenskap för objektet. Om parameter namnet t. ex. är `Path` , associeras objekt skickas till cmdleten endast när objektet har en egenskap med namnet Path.
  - Om det här värdet är sant (ByValue, ByPropertyName) kan du skicka pipe-värden till-parametern med egenskaps namn eller värde. Endast en parameter i en parameter uppsättning kan associeras med värde.
  - Om det här värdet är falskt kan du inte skicka vidare inmatade parametrar.
- Globbing
  - Om det här värdet är sant kan texten som användar typerna för parametervärdet innehålla jokertecken.
  - Om värdet är false får inte texten som användar typerna för parametervärdet innehålla jokertecken.

### <a name="parameter-value-attributes"></a>Attribut för parameter värde

- Krävs
  - Om värdet är true måste det angivna värdet användas när parametern i ett kommando används.
  - Om värdet är false är parametervärdet valfritt. Normalt är ett värde bara valfritt när det är ett av flera giltiga värden för en parameter, till exempel i en uppräknings typ.

Attributet som **krävs** för ett parameter värde skiljer sig från det **obligatoriska** attributet för en parameter.

Attributet som krävs för en parameter anger om parametern (och dess värde) måste tas med vid anrop av cmdlet: en. Däremot används det obligatoriska attributet för ett parameter värde bara när parametern ingår i kommandot. Det anger om detta specifika värde måste användas med parametern.

Vanligt vis krävs parameter värden som är plats hållare och parameter värden som är literala krävs inte, eftersom de är ett av flera värden som kan användas med parametern.

### <a name="gathering-syntax-information"></a>Samlar in Syntaxs information

1. Börja med cmdlet-namnet.

   ```
   SYNTAX
       Get-Tech
   ```

1. Visa en lista med alla parametrar för cmdleten. Skriv ett bindestreck ( `-` ) (ASCII 45) före varje parameter namn.
   Avgränsa parametrarna i parameter uppsättningar (vissa cmdletar får bara ha en parameter uppsättning). I det här exemplet har Get-Tech-cmdlet två parameter uppsättningar.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Starta varje parameter uppsättning med cmdlet-namnet.

   Visa en lista med standard parameter uppsättningen först. Standard parametern anges av cmdlet-klassen.

   För varje parameter uppsättning måste du först ange en unik parameter, såvida det inte finns några positions parametrar som måste visas först. I föregående exempel är namn-och ID-parametrarna unika parametrar för de två parameter uppsättningarna (varje parameter uppsättning måste ha en parameter som är unik för den parameter uppsättningen). Detta gör det enklare för användarna att identifiera vilken parameter de behöver ange för parameter uppsättningen.

   Visa en lista med parametrarna i den ordning som de ska visas i kommandot. Om ordningen inte spelar någon roll, visar en lista över relaterade parametrar tillsammans eller listar de mest använda parametrarna först.

   Se till att ange parametrarna WhatIf och Confirm om cmdleten stöder ShouldProcess.

   Visa inte vanliga parametrar (till exempel verbose, debug och ErrorAction) i ditt syntax-diagram. `Get-Help`Cmdleten lägger till den informationen åt dig när hjälp avsnittet visas.

1. Lägg till parameter värden. I PowerShell representeras parameter värden av deras .NET-typ.
   Typ namnet kan dock förkortas, till exempel "String" för system. String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Förkorta typer så länge deras innebörd är klar, till exempel **sträng** för **system. String** och **int** för **system. Int32** .

   Visa alla värden för uppräkningar, till exempel `-type` parametern i föregående exempel, som kan anges till **Basic** eller **Advanced** .

   Växla parametrar, t `-list` . ex. i föregående exempel, saknar värden.

1. Lägg till vinkelparenteser i parameter värden som är plats hållare, jämfört med parameter värden som är litteraler.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

1. Omge valfria parametrar och deras Vales inom hakparenteser.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Omge valfria parameter namn (för positions parametrar) inom hakparenteser. Namnet på parametrar som är placerat, till exempel parametern name i följande exempel, behöver inte inkluderas i kommandot.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

1. Om ett parameter värde kan innehålla flera värden, till exempel en lista med namn i parametern name, lägger du till ett par hakparenteser direkt efter parametervärdet.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

1. Om användaren kan välja bland parametrar eller parameter värden, t. ex. typ parameter, omger du valen i hakparenteser och avgränsar dem med den exklusiva eller symbolen (;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

1. Om parametervärdet måste använda en speciell formatering, t. ex. citat tecken eller parenteser, visar du formatet i syntaxen.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Koda XML för syntax diagram

Nodens syntax i XML-koden börjar omedelbart efter noden Description, som slutar med `</maml:description>` taggen. Information om hur du samlar in data som används i syntax-diagrammet finns i [samla in syntax information](#gathering-syntax-information).

### <a name="adding-a-syntax-node"></a>Lägga till en syntax-nod

Det syntax diagram som visas i hjälp avsnittet om cmdleten genereras från data i noden syntax i XML-koden. Noden syntax är innesluten i ett par om- `<command:syntax>` taggar. Med varje parameter uppsättning i cmdleten som anges i ett par med `<command:syntaxitem>` taggar. Det finns ingen gräns för antalet `<command:syntaxitem>` taggar som du kan lägga till.

I följande exempel visas en syntax-nod som innehåller noder för syntaxfel för två parameter uppsättningar.

```xml
<command:syntax>
  <command:syntaxItem>
    ...
    <!--Parameter Set 1 (default parameter set) parameters go here-->
    ...
  </command:syntaxItem>
  <command:syntaxItem>
    ...
    <!--Parameter Set 2 parameters go here-->
    ...
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Lägga till cmdlet-namnet i parameter uppsättnings data

Varje parameter uppsättning i cmdleten anges i en nod för ett syntax-objekt. Varje syntax-Artikelnod börjar med ett par `<maml:name>` taggar som innehåller namnet på cmdleten.

I följande exempel finns en syntax-nod som innehåller noder för kommandosyntaxen för två parameter uppsättningar.

```xml
<command:syntax>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
  <command:syntaxItem>
    <maml:name>Cmdlet-Name</maml:name>
  </command:syntaxItem>
</command:syntax>
```

### <a name="adding-parameters"></a>Parametrar läggs till

Varje parameter som läggs till i noden syntax anges i ett par med `<command:parameter>` taggar. Du behöver ett par med `<command:parameter>` taggar för varje parameter som ingår i parameter uppsättningen, med undantag för de gemensamma parametrar som tillhandahålls av PowerShell.

Attributen för den inledande `<command:parameter>` taggen avgör hur parametern visas i syntax-diagrammet. Information om parameter-attribut finns i [parameter-attribut](#parameter-attributes).

> [!NOTE]
> `<command:parameter>`Taggen stöder ett underordnat element `<maml:description>` vars innehåll aldrig visas. Parameter beskrivningar anges i noden parameter i XML-filen. Undvik inkonsekvenser mellan informationen i Bodes och noden parameter genom att utelämna ( `<maml:description>` eller lämna det tomt.

I följande exempel finns en nod för sökobjekt för en parameter uppsättning med två parametrar.

```xml
<command:syntaxItem>
  <maml:name>Cmdlet-Name</maml:name>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByValue)" position="1">
    <maml:name>ParameterName1</maml:name>
    <command:parameterValue required="true">
      string[]
    </command:parameterValue>
  </command:parameter>
  <command:parameter required="true" globbing="true"
    pipelineInput="true (ByPropertyName)">
    <maml:name>ParameterName2</maml:name>
    <command:parameterValue required="true">
      int32[]
    </command:parameterValue>
  </command:parameter>
</command:syntaxItem>
```
