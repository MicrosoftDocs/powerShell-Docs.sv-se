---
title: Så här lägger du till retur värden i en cmdlet hjälp avsnitt | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: ad0fe5c63b145c681f14328d5ef5a8784a035e26
ms.sourcegitcommit: bc9a4904c2b1561386d748fc9ac242699d2f1694
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/04/2020
ms.locfileid: "76995938"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Lägga till returvärden i ett cmdlet-hjälpavsnitt

I det här avsnittet beskrivs hur du lägger till ett utmatnings avsnitt i hjälp avsnittet om Windows PowerShell® cmdlet. I avsnittet Utdata visas .NET-klasserna för objekt som cmdleten returnerar eller passerar pipelinen.

Det finns ingen gräns för antalet klasser som du kan lägga till i avsnittet utdata. Retur typerna för en cmdlet anges i ett \<kommando: returnValues >-noden, där varje klass omges av ett \<kommando: returnValue > element.

Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att visa att det inte finns några utdata. Till exempel, i stället för klass namnet, skriv "ingen" och ge en kort förklaring. Om cmdleten genererar utdata villkorligt använder du den här noden för att förklara villkoren och beskriva de villkorliga utdata.

Schemat innehåller två \<MAML: Description > element i varje \<kommando: returnValue > element. Men `Get-Help`-cmdlet: en visar bara innehållet i \<kommandot: returnValue >/\<MAML: Description > element.

Från och med Windows PowerShell 3,0 visar `Get-Help`-cmdlet innehållet i \<MAML: URI >-elementet. Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.

Följande XML visar noden \<MAML: returnValues >.

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

Följande XML visar ett exempel på hur du använder noden \<MAML: returnValues > för att dokumentera en utdatatyp.

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



