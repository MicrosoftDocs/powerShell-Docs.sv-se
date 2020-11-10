---
ms.date: 09/12/2016
ms.topic: reference
title: Lägga till indatatyper i ett cmdlet-hjälpavsnitt
description: Lägga till indatatyper i ett cmdlet-hjälpavsnitt
ms.openlocfilehash: f2ad87c54230bcdd7e0ea708e9a1869daef7495f
ms.sourcegitcommit: 2c311274ce721cd1072dcf2dc077226789e21868
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 11/10/2020
ms.locfileid: "94391110"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="07c2e-103">Lägga till indatatyper i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="07c2e-103">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="07c2e-104">I det här avsnittet beskrivs hur du lägger till ett **indata** -avsnitt i hjälp avsnittet om PowerShell-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="07c2e-104">This section describes how to add an **INPUTS** section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="07c2e-105">I avsnittet **indata** visas de .NET-klasser av objekt som cmdleten accepterar som indata från pipelinen, antingen med värde eller efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="07c2e-105">The **INPUTS** section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="07c2e-106">Det finns ingen gräns för antalet klasser som du kan lägga till i ett **indata** -avsnitt.</span><span class="sxs-lookup"><span data-stu-id="07c2e-106">There is no limit to the number of classes that you can add to an **INPUTS** section.</span></span> <span data-ttu-id="07c2e-107">Indatatyperna omges av en `<command:inputTypes>` nod, med varje klass som omges av ett- `<command:inputType>` element.</span><span class="sxs-lookup"><span data-stu-id="07c2e-107">The input types are enclosed in a `<command:inputTypes>` node, with each class enclosed in a `<command:inputType>` element.</span></span>

<span data-ttu-id="07c2e-108">Schemat innehåller två `<maml:description>` element i varje `<command:inputType>` element.</span><span class="sxs-lookup"><span data-stu-id="07c2e-108">The schema includes two `<maml:description>` elements in each `<command:inputType>` element.</span></span>
<span data-ttu-id="07c2e-109">Men `Get-Help` cmdleten visar bara innehållet i `<command:inputType>/<maml:description>` elementet.</span><span class="sxs-lookup"><span data-stu-id="07c2e-109">However, the `Get-Help` cmdlet displays only the content of the `<command:inputType>/<maml:description>` element.</span></span>

<span data-ttu-id="07c2e-110">Från och med PowerShell 3,0 `Get-Help` visar cmdleten innehållet i- `<maml:uri>` elementet.</span><span class="sxs-lookup"><span data-stu-id="07c2e-110">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="07c2e-111">Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.</span><span class="sxs-lookup"><span data-stu-id="07c2e-111">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="07c2e-112">Följande XML visar `<maml:inputTypes>` noden.</span><span class="sxs-lookup"><span data-stu-id="07c2e-112">The following XML shows the `<maml:inputTypes>` node.</span></span>

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

<span data-ttu-id="07c2e-113">Följande XML visar ett exempel på hur du använder `<maml:inputTypes>` noden för att dokumentera en indatatyp.</span><span class="sxs-lookup"><span data-stu-id="07c2e-113">The following XML shows an example of using the `<maml:inputTypes>` node to document an input type.</span></span>

```xml
<command:inputTypes>
  <command:inputType>
    <dev:type>
      <maml:name>System.DateTime</maml:name>
      <maml:uri>https://docs.microsoft.com/dotnet/api/system.datetime</maml:uri>
      <maml:description/>
    </dev:type>
    <maml:description>
      <maml:para> You can pipe a date to the Set-Date cmdlet. <maml:para>
    <maml:description>
  </command:inputType>
</command:inputTypes>
```
