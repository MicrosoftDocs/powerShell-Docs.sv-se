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
ms.openlocfilehash: a5618b72827d8ef70201437c4a99ea8bf68cdfd3
ms.sourcegitcommit: 173556307d45d88de31086ce776770547eece64c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 05/19/2020
ms.locfileid: "83565551"
---
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="1f721-102">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="1f721-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="1f721-103">I det här avsnittet beskrivs hur du lägger till ett utmatnings avsnitt i hjälp avsnittet om Windows PowerShell® cmdlet.</span><span class="sxs-lookup"><span data-stu-id="1f721-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="1f721-104">I avsnittet Utdata visas .NET-klasserna för objekt som cmdleten returnerar eller passerar pipelinen.</span><span class="sxs-lookup"><span data-stu-id="1f721-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="1f721-105">Det finns ingen gräns för antalet klasser som du kan lägga till i avsnittet utdata.</span><span class="sxs-lookup"><span data-stu-id="1f721-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="1f721-106">Retur typerna för en cmdlet omges av ett \< kommando: returnValues>-noden, där varje klass omges av ett \< kommando: returnValue>-element.</span><span class="sxs-lookup"><span data-stu-id="1f721-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="1f721-107">Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att visa att det inte finns några utdata.</span><span class="sxs-lookup"><span data-stu-id="1f721-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="1f721-108">Till exempel, i stället för klass namnet, skriv "ingen" och ge en kort förklaring.</span><span class="sxs-lookup"><span data-stu-id="1f721-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="1f721-109">Om cmdleten genererar utdata villkorligt använder du den här noden för att förklara villkoren och beskriva de villkorliga utdata.</span><span class="sxs-lookup"><span data-stu-id="1f721-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="1f721-110">Schemat innehåller två \< MAML: description> element i varje \< kommando: returnValue>-element.</span><span class="sxs-lookup"><span data-stu-id="1f721-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="1f721-111">Men `Get-Help` cmdleten visar bara innehållet i \< kommandot: returnValue>/ \< maml: Description> element.</span><span class="sxs-lookup"><span data-stu-id="1f721-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="1f721-112">Från och med Windows PowerShell 3,0 `Get-Help` visar cmdleten innehållet i \< MAML: URI>-elementet.</span><span class="sxs-lookup"><span data-stu-id="1f721-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="1f721-113">Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.</span><span class="sxs-lookup"><span data-stu-id="1f721-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="1f721-114">Följande XML visar>- \< noden MAML: returnValues.</span><span class="sxs-lookup"><span data-stu-id="1f721-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="1f721-115">Följande XML visar ett exempel på hur du använder \< noden MAML: returnValues> för att dokumentera en utdatatyp.</span><span class="sxs-lookup"><span data-stu-id="1f721-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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
