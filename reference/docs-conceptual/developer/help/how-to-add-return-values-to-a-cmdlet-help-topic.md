---
title: Lägga till returvärden i ett cmdlet-hjälpavsnitt
ms.date: 09/12/2016
ms.openlocfilehash: c164556cd06b332d04857987360c98f740a150b5
ms.sourcegitcommit: de59ff77c6535fc772c1e327b3c823295eaed6ea
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 07/22/2020
ms.locfileid: "86893364"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="61e0e-102">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="61e0e-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="61e0e-103">I det här avsnittet beskrivs hur du lägger till ett utmatnings avsnitt i hjälp avsnittet om PowerShell-cmdleten.</span><span class="sxs-lookup"><span data-stu-id="61e0e-103">This section describes how to add an OUTPUTS section to a PowerShell cmdlet Help topic.</span></span> <span data-ttu-id="61e0e-104">I avsnittet **utdata** visas .net-klasserna för objekt som cmdleten returnerar eller passerar pipelinen.</span><span class="sxs-lookup"><span data-stu-id="61e0e-104">The **OUTPUTS** section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="61e0e-105">Det finns ingen gräns för antalet klasser som du kan lägga till i avsnittet **utdata** .</span><span class="sxs-lookup"><span data-stu-id="61e0e-105">There is no limit to the number of classes that you can add to the **OUTPUTS** section.</span></span> <span data-ttu-id="61e0e-106">Retur typerna för en cmdlet omges av en `<command:returnValues>` nod, med varje klass omgiven av ett- `<command:returnValue>` element.</span><span class="sxs-lookup"><span data-stu-id="61e0e-106">The return types of a cmdlet are enclosed in a `<command:returnValues>` node, with each class enclosed in a `<command:returnValue>` element.</span></span>

<span data-ttu-id="61e0e-107">Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att visa att det inte finns några utdata.</span><span class="sxs-lookup"><span data-stu-id="61e0e-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="61e0e-108">I stället för klass namnet skriver du till exempel **ingen** och ger en kort förklaring.</span><span class="sxs-lookup"><span data-stu-id="61e0e-108">For example, in place of the class name, write **None** and provide a brief explanation.</span></span> <span data-ttu-id="61e0e-109">Om cmdleten genererar utdata villkorligt använder du den här noden för att förklara villkoren och beskriva de villkorliga utdata.</span><span class="sxs-lookup"><span data-stu-id="61e0e-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="61e0e-110">Schemat innehåller två `<maml:description>` element i varje `<command:returnValue>` element.</span><span class="sxs-lookup"><span data-stu-id="61e0e-110">The schema includes two `<maml:description>` elements in each `<command:returnValue>` element.</span></span>
<span data-ttu-id="61e0e-111">Men `Get-Help` cmdleten visar bara innehållet i `<command:returnValue>/<maml:description>` elementet.</span><span class="sxs-lookup"><span data-stu-id="61e0e-111">However, the `Get-Help` cmdlet displays only the content of the `<command:returnValue>/<maml:description>` element.</span></span>

<span data-ttu-id="61e0e-112">Från och med PowerShell 3,0 `Get-Help` visar cmdleten innehållet i- `<maml:uri>` elementet.</span><span class="sxs-lookup"><span data-stu-id="61e0e-112">Beginning in PowerShell 3.0, the `Get-Help` cmdlet displays the content of the `<maml:uri>` element.</span></span>
<span data-ttu-id="61e0e-113">Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.</span><span class="sxs-lookup"><span data-stu-id="61e0e-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="61e0e-114">Följande XML visar `<maml:returnValues>` noden.</span><span class="sxs-lookup"><span data-stu-id="61e0e-114">The following XML shows the `<maml:returnValues>` node.</span></span>

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

<span data-ttu-id="61e0e-115">Följande XML visar ett exempel på hur du använder `<maml:returnValues>` noden för att dokumentera en utdatatyp.</span><span class="sxs-lookup"><span data-stu-id="61e0e-115">The following XML shows an example of using the `<maml:returnValues>` node to document an output type.</span></span>

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
