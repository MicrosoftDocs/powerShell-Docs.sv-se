---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till returvärden i ett cmdlet-hjälpavsnitt
description: Lägga till returvärden i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: f66e642d65c3f679ec3262736f4eff558265ab8f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92649601"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Lägga till returvärden i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till ett utmatnings avsnitt i hjälp avsnittet om PowerShell-cmdleten. I avsnittet **utdata** visas .net-klasserna för objekt som cmdleten returnerar eller passerar pipelinen.

Det finns ingen gräns för antalet klasser som du kan lägga till i avsnittet **utdata** . Retur typerna för en cmdlet omges av en `<command:returnValues>` nod, med varje klass omgiven av ett- `<command:returnValue>` element.

Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att visa att det inte finns några utdata. I stället för klass namnet skriver du till exempel **ingen** och ger en kort förklaring. Om cmdleten genererar utdata villkorligt använder du den här noden för att förklara villkoren och beskriva de villkorliga utdata.

Schemat innehåller två `<maml:description>` element i varje `<command:returnValue>` element.
Men `Get-Help` cmdleten visar bara innehållet i `<command:returnValue>/<maml:description>` elementet.

Från och med PowerShell 3,0 `Get-Help` visar cmdleten innehållet i- `<maml:uri>` elementet.
Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.

Följande XML visar `<maml:returnValues>` noden.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> Class Name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
       <maml:para> Brief description <maml:para>

</maml:description>
  </command: returnValue>
</command: returnValues>
```

Följande XML visar ett exempel på hur du använder `<maml:returnValues>` noden för att dokumentera en utdatatyp.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```
