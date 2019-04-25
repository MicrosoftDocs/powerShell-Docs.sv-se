---
title: Hur du lägger till Indatatyper en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 432798e4-5d69-46b1-9517-ff09bffaa4be
caps.latest.revision: 7
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083441"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a>Lägga till indatatyper i ett cmdlet-hjälpavsnitt

Det här avsnittet beskriver hur du lägger till ett indata-avsnitt i en Windows PowerShell® cmdlet-hjälpavsnittet. INDATA-avsnittet listas de .NET-klasserna av objekt som cmdleten indata av typen från pipelinen, antingen med värde eller egenskapsnamn.

Det finns ingen gräns för hur många klasser som du kan lägga till ett indata-avsnitt. Indatatyperna är inom en \<kommandot: inputTypes > nod, där varje klass inom en \<kommandot: inputType > element.

Schemat innehåller två \<maml:description > element i varje \<kommandot: inputType > element. Men den `Get-Help` cmdlet visar endast innehållet i den \<kommandot: inputType > /\<maml:description >) element.

Från och med Windows PowerShell 3.0, den `Get-Help` cmdlet visar innehållet i den \<maml:uri > element. Det här elementet kan du dirigera användare till avsnitt som beskriver .NET-klass.

I följande XML-visas den \<maml:inputTypes > noden.

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

Följande XML visar ett exempel på hur du använder den \<maml:inputTypes > noden dokumenterar du en Indatatyp.

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```