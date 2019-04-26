---
title: Hur du lägger till exempel att en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8f723b21-8f95-4981-8b6e-4f07c22d601a
caps.latest.revision: 5
ms.openlocfilehash: 5e8d1df6b423bfd2cd6b0a64a8875dea9c3fb4ef
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083475"
---
# <a name="how-to-add-examples-to-a-cmdlet-help-topic"></a>Lägga till exempel i ett cmdlet-hjälpavsnitt

- [Att känna till om exemplen i Cmdlet-hjälpen](#Things-to-Know-about-Examples-in-Cmdlet-Help)

- [Hjälp-vyer som visar exempel](#Help-Views-that-Display-Examples)

- [Lägga till en exempel-nod](#Adding-an-Examples-Node)

- [Att lägga till föregående tecken](#Adding-Preceding-Characters)

- [Att lägga till kommandot](#Adding-the-Command)

- [Att lägga till en beskrivning](#Adding-a-Description)

- [Att lägga till exempel på utdata](#Adding-Example-Output)

## <a name="things-to-know-about-examples-in-cmdlet-help"></a>Att känna till om exemplen i Cmdlet-hjälpen

- Lista över alla parameternamn i kommandot, även om parameternamn är valfria. Detta hjälper användare att tolka kommandot enkelt.

- Undvik att alias och partiella parameternamn, även om de fungerar med Windows PowerShell®.

- I exempel-beskrivning, förklara rationella för kommandot. Förklara varför du har valt viss parametrar och värden och hur du använder variabler.

- Om kommandot använder uttryck, förklarar du dem i detalj.

- Om kommandot använder egenskaper och metoder för objekt, särskilt de egenskaper som inte visas i standardvisningen, Använd exemplet som en möjlighet att meddela användaren om objektet.

## <a name="help-views-that-display-examples"></a>Hjälp-vyer som visar exempel

Exempel visas bara i detaljerat och fullständig vyer i cmdlet-hjälpen.

## <a name="adding-an-examples-node"></a>Lägga till en exempel-nod

Följande XML-koden visar hur du lägger till en exempel-nod som innehåller en exempel-nod. Lägga till ytterligare exempel noder för varje exempel som du vill ska ingå i avsnittet.

```xml
<command:examples>
  <command:example>
  </command:example>
</command:examples>
```

## <a name="adding-an-example-title"></a>Att lägga till en exempel-rubrik

Följande XML-koden visar hur du lägger till en rubrik för det här exemplet. Rubriken används för att ange exemplet förutom andra exempel. Windows PowerShell® använder ett standard-huvud som innehåller en rad för sekventiella exempel.

```xml
<command:examples>
  <command:example>
    <maml:title>----------  EXAMPLE 1  ----------</maml:title>
  </command:example>
</command:examples>
```

## <a name="adding-preceding-characters"></a>Att lägga till föregående tecken

Följande XML-koden visar hur du lägger till tecken, till exempel Windows PowerShell-Kommandotolken som visas omedelbart före detta kommando (utan blanksteg mellanliggande). Windows PowerShell® använder Windows PowerShell-Kommandotolken: C:\PS>.

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

## <a name="adding-the-command"></a>Att lägga till kommandot

Följande XML-koden visar hur du lägger till kommandot faktiska för till exempel. När du lägger till kommandot, skriver du namnet (Använd inte alias) av cmdlets och parametrar. Kan också använda gemener när det är möjligt.

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

## <a name="adding-a-description"></a>Att lägga till en beskrivning

Följande XML-koden visar hur du lägger till en beskrivning för det här exemplet. Windows PowerShell® använder en enda uppsättning \<maml:para > taggar för beskrivning, även om flera \<maml:para > taggar kan användas.

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

## <a name="adding-example-output"></a>Att lägga till exempel på utdata

Följande XML-koden visar hur du lägger till kommandots utdata. Kommandot resultat information är valfri, men i vissa fall är det bra att demonstrera effekten av att använda specifika parametrar. Windows PowerShell® använder två uppsättningar av tom \<maml:para > taggar om du vill separera kommandoutdata från kommandot.

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