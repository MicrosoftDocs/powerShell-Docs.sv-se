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
# <a name="how-to-add-return-values-to-a-cmdlet-help-topic"></a><span data-ttu-id="0fcb3-102">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="0fcb3-102">How to Add Return Values to a Cmdlet Help Topic</span></span>

<span data-ttu-id="0fcb3-103">Det här avsnittet beskriver hur du lägger till en OUTPUTS-avsnittet i en Windows PowerShell® cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-103">This section describes how to add an OUTPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="0fcb3-104">OUTPUTS-avsnittet listar de .NET-klasserna av objekt som cmdleten Returnerar eller skickar av pipelinen.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-104">The OUTPUTS section lists the .NET classes of objects that the cmdlet returns or passes down the pipeline.</span></span>

<span data-ttu-id="0fcb3-105">Det finns ingen gräns för hur många klasser som du kan lägga till OUTPUTS-avsnittet.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-105">There is no limit to the number of classes that you can add to the OUTPUTS section.</span></span> <span data-ttu-id="0fcb3-106">Returtyper för en cmdlet: en är inom en \<kommandot: returnValues > nod, där varje klass inom en \<kommandot: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-106">The return types of a cmdlet are enclosed in a \<command:returnValues> node, with each class enclosed in a \<command:returnValue> element.</span></span>

<span data-ttu-id="0fcb3-107">Om en cmdlet inte genererar några utdata kan du använda det här avsnittet för att indikera att det finns inga utdata.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-107">If a cmdlet does not generate any output, use this section to indicate that there is no output.</span></span> <span data-ttu-id="0fcb3-108">I stället för namnet på klassen till exempel skriva ”None” och ges en kort förklaring.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-108">For example, in place of the class name, write "None" and provide a brief explanation.</span></span> <span data-ttu-id="0fcb3-109">Om cmdleten genererar utdata villkorligt, Använd den här noden för att förklara villkoren och beskriva villkorlig utdata.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-109">If the cmdlet generates output conditionally, use this node to explain the conditions and describe the conditional output.</span></span>

<span data-ttu-id="0fcb3-110">Schemat innehåller två \<maml:description > element i varje \<kommandot: returnValue > element.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-110">The schema includes two \<maml:description> elements in each \<command:returnValue> element.</span></span> <span data-ttu-id="0fcb3-111">Men den `Get-Help` cmdlet visar endast innehållet i den \<kommandot: returnValue > /\<maml:description > element.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-111">However, the `Get-Help` cmdlet displays only the content of the \<command:returnValue>/\<maml:description> element.</span></span>

<span data-ttu-id="0fcb3-112">Från och med Windows PowerShell 3.0, den `Get-Help` cmdlet visar innehållet i den \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-112">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="0fcb3-113">Det här elementet kan du dirigera användare till avsnitt som beskriver .NET-klass.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-113">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="0fcb3-114">I följande XML-visas den \<maml:returnValues > noden.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-114">The following XML shows the \<maml:returnValues> node.</span></span>

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

<span data-ttu-id="0fcb3-115">Följande XML visar ett exempel på hur du använder den \<maml:returnValues > noden dokumenterar du en Utdatatyp.</span><span class="sxs-lookup"><span data-stu-id="0fcb3-115">The following XML shows an example of using the \<maml:returnValues> node to document an output type.</span></span>

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



