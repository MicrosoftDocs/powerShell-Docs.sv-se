---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till indatatyper i ett cmdlet-hjälpavsnitt
description: Lägga till indatatyper i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: 1a8f04832ddfdf796596da2367a5c599aa0f245e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92647745"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Lägga till indatatyper i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till ett **indata** -avsnitt i hjälp avsnittet om PowerShell-cmdleten. I avsnittet **indata** visas de .NET-klasser av objekt som cmdleten accepterar som indata från pipelinen, antingen med värde eller efter egenskaps namn.

Det finns ingen gräns för antalet klasser som du kan lägga till i ett **indata** -avsnitt. Indatatyperna omges av en `<command:inputTypes>` nod, med varje klass som omges av ett- `<command:inputType>` element.

Schemat innehåller två `<maml:description>` element i varje `<command:inputType>` element.
Men `Get-Help` cmdleten visar bara innehållet i `<command:inputType>/<maml:description>` elementet.

Från och med PowerShell 3,0 `Get-Help` visar cmdleten innehållet i- `<maml:uri>` elementet.
Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.

Följande XML visar `<maml:inputTypes>` noden.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> Class name </maml:name>
      <maml:uri>  URI of a topic that describes the class </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Brief description </maml:para>
    </maml:description>
  </command:inputType>
</command:inputTypes>
```

Följande XML visar ett exempel på hur du använder `<maml:inputTypes>` noden för att dokumentera en indatatyp.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  https://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
