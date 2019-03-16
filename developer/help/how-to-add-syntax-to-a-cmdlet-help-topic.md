---
title: Lägga till Syntax i en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d0c6d03f-1c1a-43d8-928e-e3290e90e0bc
caps.latest.revision: 5
ms.openlocfilehash: 2e9dbc9ff8f9507f2008cd6e114ba6fec36b10bf
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054619"
---
# <a name="how-to-add-syntax-to-a-cmdlet-help-topic"></a>Lägga till syntax till ett cmdlet-hjälpavsnitt

- [Parameterattribut](#Parameter-Attributes)

- [Parameterattribut värde](#Parameter-Value-Attributes)

- [Samla Information om Syntax](#Gathering-Syntax-Information)

- [Koda Syntaxdiagrammet XML](#Coding-the-Syntax-Diagram-XML)

## <a name="things-to-know-about-the-syntax-diagram-in-cmdlet-help"></a>Att känna till om Syntaxdiagrammet i Cmdlet-hjälpen

Innan du börjar koda XML för syntaxdiagrammet i hjälpfilen cmdlet Läs det här avsnittet för att få en tydlig bild av typ av data som du måste ange, till exempel parameterattribut och hur dessa data visas i syntaxdiagrammet...

### <a name="parameter-attributes"></a>Parameterattribut

- Obligatorisk

  - Om värdet är true måste parametern visas i alla kommandon som använder parameteruppsättningen.

  - Parametern är valfri i alla kommandon som använder parameteruppsättningen om värdet är false.

- Position

  - Om namnet, krävs parameternamnet.

  - Om det namngivna, är parameternamnet valfritt. Om det utelämnas måste parametervärdet vara i den angivna positionen i kommandot. Till exempel om värdet är position = ”1”, parametervärdet måste vara den första eller enda icke namngivna parametervärdet i kommandot.

- Pipeline-indata

  - Om värdet är true (ByValue), du kan skicka vidare indata till parametern. Indata är associerad med (”gränsvärde till”) parametern även om egenskapsnamnet och typen av objekt som inte matchar den förväntade typen. Windows PowerShell? Parametern bindning komponenter försök att konvertera indata till rätt typ och misslyckas kommandot endast när den inte kan konverteras. Endast en parameter i en parameteruppsättning kan associeras med värde.

  - Om värdet är true (ByPropertyName), du kan skicka vidare indata till parametern. Indata är associerade med parametern endast när Parameternamnet matchar namnet på en egenskap för indataobjektet. Exempel: om parameternamnet är `Path`, objekt som skickas till cmdleten är associerade med parametern endast när objektet har en egenskap med namnet sökväg.

  - Om SANT (ByValue, ByPropertyName), som du kan skicka vidare indata till parametern av egenskapsnamn eller av värde. Endast en parameter i en parameteruppsättning kan associeras med värde.

  - Du kan inte skicka vidare indata till denna parameter om värdet är false.

- Globbing

  - Om värdet är true kan texten som en användare anger för parametervärdet innehålla jokertecken.

  - Om värdet är false får inte texten som en användare anger för parametervärdet innehålla jokertecken.

### <a name="parameter-value-attributes"></a>Parameterattribut värde

- Obligatorisk

  - Om värdet är true, måste det angivna värdet användas när du använder parametern i ett kommando.

  - Om värdet är FALSKT, är värdet för parametern valfri. Ett värde är vanligtvis valfritt endast när det är en av flera giltiga värden för en parameter, till exempel i en uppräknade typen.

Det obligatoriska attributet för ett parametervärde skiljer sig från det obligatoriska attributet för en parameter.

Det obligatoriska attributet på en parameter anges om parametern (och dess värde) måste tas med vid cmdlet: en. Det obligatoriska attributet för ett parametervärde används däremot endast när parametern ingår i kommandot. Anger om motsvarande värde måste användas med parametern.

Normalt parametervärden som fungerar som platshållare krävs och literal parametervärden krävs inte, eftersom de är en av flera värden som kan användas med parametern.

### <a name="gathering-syntax-information"></a>Samla Information om Syntax

1. Börja med cmdlet-namn.

   ```
   SYNTAX
       Get-Tech
   ```

2. Lista alla parametrar för cmdleten. Skriv ett bindestreck (även kallat ”dash” eller ”minustecken” (ASCII 45) före varje parameternamn. Avgränsa parametrarna i parameteruppsättningar (vissa cmdlets kan ha bara en parameteruppsättning). I det här exemplet Get-Tech-cmdlet har två parameteruppsättningar.

   ```
   SYNTAX
       Get-Tech -name -type
       Get-Tech -ID -list -type
   ```

   Starta varje parameter med cmdlet-namn.

   Lista över standardparameter Ange först. Standardparametern har angetts av cmdlet-klassen.

   För varje parameter, en lista över dess unika parameter först om det inte finns namngivna parametrar som måste visas först. I exemplet ovan är de namn och ID-parametrarna unika parametrar för två parameteruppsättningar (varje parameteruppsättningen måste ha en parameter som är unik för den parameteruppsättningen). Detta gör det enklare för användarna att identifiera vilka de måste du ange för parametern parameteruppsättning.

   Lista över parametrarna i den ordning som de ska synas i kommandot. Om ordningen ingen spelar roll, visa relaterade parametrar tillsammans eller lista över de mest använda parametrarna först.

   Se till att parametrarna WhatIf och bekräfta om cmdleten stöder ShouldProcess.

   Du får inte ange parametrarna (t.ex utförlig, felsökning och ErrorAction) i syntaxdiagrammet. Den `Get-Help` cmdlet lägger till den informationen du när den visas i hjälpavsnittet.

3. Lägg till parametervärden. I Windows PowerShell?, parametervärden representeras av sina .NET-typen. Men kan namnet på förkortas, till exempel ”string” för System.String.

   ```
   SYNTAX
       Get-Tech -name string -type basic advanced
       Get-Tech -ID int -list -type basic advanced
   ```

   Förkorta typer så länge som deras innebörd är tydligt, till exempel ”string” för System.String och ”int” för System.Int32.

   Lista över alla värden i uppräkningar, till exempel-typparametern i föregående exempel, som kan anges till ”grundläggande” eller ”avancerad”.

   Växla parametrar, till exempel - lista i föregående exempel, har inte värden.

4. Lägg till vinkelparenteser i parametervärdena som är platshållare, jämfört med parametervärden litteraler.

   ```
   SYNTAX
       Get-Tech -name <string> -type basic advanced
       Get-Tech -ID <int> -list -type basic advanced
   ```

5. Ange valfria parametrar och deras värdena inom hakparenteser.

   ```
   SYNTAX
       Get-Tech -name <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

6. Valfria parametrar namn (för namngivna parametrar) omges av hakparenteser. Namn för parametrar som är namngivna, till exempel Name-parametern i exemplet nedan har inte ska ingå i kommandot.

   ```
   SYNTAX
       Get-Tech [-name] <string> [-type basic advanced]
       Get-Tech -ID <int> [-list] [-type basic advanced]
   ```

7. Om ett parametervärde kan innehålla flera värden, till exempel en lista med namn i Name-parametern lägger du till ett par med hakparenteser direkt efter värdet för parametern.

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type basic advanced]
       Get-Tech -ID <int[]> [-list] [-type basic advanced]
   ```

8. Om användaren kan välja mellan parametrar och parametervärden, till exempel parametern Type valen omges av klammerparenteser och avgränsa dem med exklusiv eller symbol(;).

   ```
   SYNTAX
       Get-Tech [-name] <string[]> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

9. Om värdet för parametern måste använda specifika formatering, till exempel citattecken eller parenteserna visa formatet i syntax.

   ```
   SYNTAX
       Get-Tech [-name] <"string[]"> [-type {basic | advanced}]
       Get-Tech -ID <int[]> [-list] [-type {basic | advanced}]
   ```

## <a name="coding-the-syntax-diagram-xml"></a>Koda Syntaxdiagrammet XML

Noden syntax i XML-filen börjar omedelbart efter att noden beskrivning som slutar med den \</maml:description > taggen. Läs om hur insamlingen av data som används i syntaxdiagrammet [samla in Syntaxinformationen](#Gathering-Syntax-Information).

### <a name="adding-a-syntax-node"></a>Lägger till en Syntax-nod

Syntaxdiagrammet visas i cmdlet-hjälpavsnittet genereras från data i noden syntax i XML-filen. Noden syntax är inom ett par om \<Kommandosyntax: > taggar. Med varje parameter för cmdlet: ar inom ett par \<kommandot: syntaxitem > taggar. Det finns ingen gräns för hur många \<kommandot: syntaxitem >-taggar som du kan lägga till.

I följande exempel visas en syntax-nod som har syntax objekt noder för två parameteruppsättningar.

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

### <a name="adding-the-cmdlet-name-to-the-parameter-set-data"></a>Lägger till Cmdlet-namn till parametern ange Data

Varje parameteruppsättning cmdlet: en har angetts i en syntax objekt nod. Varje nod för syntax-objekt som börjar med ett par \<maml:name > taggar som innehåller namnet på cmdleten.

I följande exempel innehåller ett syntax-noden som har syntax objekt noder för två parameteruppsättningar.

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

### <a name="adding-parameters"></a>Att lägga till parametrar

Varje parameter som lagts till i noden syntax objekt har angetts i ett par \<kommandoparameter: > taggar. Du behöver ett par \<kommandoparameter: >-taggar för varje parameter som ingår i parameteruppsättningen, med undantag för de gemensamma parametrarna som tillhandahålls av Windows PowerShell?

Attribut för att öppna \<kommandoparameter: > taggen avgöra hur parametern visas i syntaxdiagrammet. Information om parameterattribut finns [Parameterattribut](#Parameter-Attributes).

> [!NOTE]
> Den \<kommandoparameter: > taggen har stöd för ett underordnat element \<maml:description > vars innehåll aldrig visas. Beskrivningar av parametern har angetts i Parameternoden i XML-filen. Att undvika inkonsekvenser mellan informationen i objektet syntax bodes och Parameternoden utelämna den (\<maml:description > eller lämna det tomt.

I följande exempel innehåller en nod för objekt av syntax för en parameter med två parametrar.

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
