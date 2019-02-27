---
title: Hur du lägger till returnera värden till en Cmdlet-hjälpavsnittet | Microsoft Docs
ms.custom: ''
ms.date: 09/12/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: a52ab737-753c-4d04-8af7-758d5c805e18
caps.latest.revision: 7
ms.openlocfilehash: b21811e5a5a819c3d5c4a55fcbe685a84819b71d
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849219"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a>Lägga till returvärden i ett cmdlet-hjälpavsnitt

Det här avsnittet beskriver hur du lägger till en OUTPUTS-avsnittet i en Windows PowerShell® cmdlet-hjälpavsnittet. OUTPUTS-avsnittet listar de .NET-klasserna av objekt som cmdleten Returnerar eller skickar av pipelinen.

Det finns ingen gräns för hur många klasser som du kan lägga till OUTPUTS-avsnittet. Returtyper för en cmdlet: en är inom en \<kommandot: returnValues > nod, där varje klass inom en \<kommandot: returnValue > element.

Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att indikera att det finns inga utdata. I stället för namnet på klassen till exempel skriva ”None” och ges en kort förklaring. Om cmdleten genererar utdata villkorligt, Använd den här noden för att förklara villkoren och beskriva villkorlig utdata.

Schemat innehåller två \<maml:description > element i varje \<kommandot: returnValue > element. Men den `Get-Help` cmdlet visar endast innehållet i den \<kommandot: returnValue > /\<maml:description > element.

Från och med Windows PowerShell 3.0, den `Get-Help` cmdlet visar innehållet i den \<maml:uri > element. Det här elementet kan du dirigera användare till avsnitt som beskriver .NET-klass.

I följande XML-visas den \<maml:returnValues > noden.

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

Följande XML visar ett exempel på hur du använder den \<maml:returnValues > noden dokumenterar du en Utdatatyp.

```xml
<command:returnValues>
  <command:returnValue>
    <dev:type>
      <maml:name> System.DateTime </maml:name>
      <maml:uri>  http://msdn.microsoft.com/library/system.datetime.aspx </maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> Get-Date returns a DateTime object. <maml:para>
    </maml:description>
  </command: returnValue>
</command: returnValues>
```



