---
title: Så här lägger du till indatatyper i ett hjälp avsnitt för cmdleten | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: 58b908be3149376547b075320b021421351b881e
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83557079"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Lägga till indatatyper i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till ett indata-avsnitt i ett hjälp avsnitt om Windows PowerShell® cmdlet. I avsnittet indata visas de .NET-klasser av objekt som cmdleten accepterar som indata från pipelinen, antingen med värde eller efter egenskaps namn.

Det finns ingen gräns för antalet klasser som du kan lägga till i ett indata-avsnitt. Indatatyperna omges av ett \< kommando: inputTypes>-noden, med varje klass omsluten i ett \< kommando: inputType> element.

Schemat innehåller två \< MAML: description> element i varje \< kommando: inputType> element. Men `Get-Help` cmdleten visar bara innehållet i \< kommandot: inputType>/ \< maml: Description>).

Från och med Windows PowerShell 3,0 `Get-Help` visar cmdleten innehållet i \< MAML: URI>-elementet. Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.

Följande XML visar>- \< noden MAML: inputTypes.

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

Följande XML visar ett exempel på hur du använder \< noden MAML: inputTypes> för att dokumentera en indatatyp.

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
