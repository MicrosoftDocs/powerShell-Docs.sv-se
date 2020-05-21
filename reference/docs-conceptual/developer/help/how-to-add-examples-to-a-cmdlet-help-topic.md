---
title: Så här lägger du till exempel i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 82bee7b7bb0ef49203636f2a293075f3db924ce4
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557098"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Lägga till exempel i ett cmdlet-hjälpavsnitt

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Saker att veta om exempel i cmdlet-hjälpen

- Lista alla parameter namn i kommandot, även om parameter namnen är valfria. Detta hjälper användaren att tolka kommandot enkelt.

- Undvik alias och del parameter namn, även om de fungerar i Windows PowerShell®.

- I exempel beskrivningen förklarar du rationellt för kommandots konstruktion. Förklara varför du har valt särskilda parametrar och värden och hur du använder variabler.

- Om kommandot använder uttryck förklarar du dem i detalj.

- Om kommandot använder egenskaper och metoder för objekt, särskilt egenskaper som inte visas i standard visningen, använder du exemplet som en affärs möjlighet för att berätta för användaren om objektet.

## <a name="help-views-that-display-examples"></a>Hjälp vyer som visar exempel

Exempel visas bara i de detaljerade och fullständiga vyerna för cmdlet-hjälpen.

## <a name="adding-an-examples-node"></a>Lägga till en exempel nod

Följande XML visar hur du lägger till en exempel-nod som innehåller en enda exempel-nod. Lägg till ytterligare exempel-noder för varje exempel som du vill inkludera i avsnittet.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Lägga till en rubrik för exempel

Följande XML visar hur du lägger till en rubrik för exemplet. Rubriken används för att ställa in exemplet från andra exempel. Windows PowerShell® använder ett standard huvud som innehåller ett sekventiellt exempel nummer.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Lägga till föregående tecken

Följande XML visar hur du lägger till tecken, t. ex. Windows PowerShell-prompten, som visas omedelbart före kommandot example (utan några mellanliggande blank steg). Windows PowerShell® använder Windows PowerShell-prompten: C:\PS>.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
</command:example>
</command:examples>
```

## <a name="adding-the-command"></a>Kommandot läggs till

Följande XML visar hur du lägger till det faktiska kommandot i exemplet. När du lägger till kommandot skriver du hela namnet (Använd inte alias) för cmdlets och parametrar. Använd också gemener när det är möjligt.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
</command:example>
</command:examples>
```

## <a name="adding-a-description"></a>Lägga till en beskrivning

Följande XML visar hur du lägger till en beskrivning av exemplet. I Windows PowerShell® används en enda uppsättning \< MAML: stycke> taggar för beskrivningen, även om flera \< maml-> taggar kan användas.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
    </dev:remarks>
</command:example>
</command:examples>
```

## <a name="adding-example-output"></a>Lägger till exempel utdata

Följande XML visar hur du lägger till kommandots utdata. Kommando resultat informationen är valfri, men i vissa fall är det bra att demonstrera effekterna av att använda vissa parametrar. Windows PowerShell® använder två uppsättningar av tomma \< MAML: stycke> taggar för att separera kommandoutdata från kommandot.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
    <maml:Introduction>
      <maml:paragraph>C:\PS></maml:paragraph>
    </maml:Introduction>
    <dev:code> command </dev:code>
    <dev:remarks>
      <maml:para> command description </maml:para>
      <maml:para></maml:para>
      <maml:para></maml:para>
      <maml:para> command output </maml:para>
</dev:remarks>
</command:example>
</command:examples>
```
