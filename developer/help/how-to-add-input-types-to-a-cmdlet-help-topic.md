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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56850178"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="5571c-102">Lägga till indatatyper i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="5571c-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="5571c-103">Det här avsnittet beskriver hur du lägger till ett indata-avsnitt i en Windows PowerShell® cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="5571c-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="5571c-104">INDATA-avsnittet listas de .NET-klasserna av objekt som cmdleten indata av typen från pipelinen, antingen med värde eller egenskapsnamn.</span><span class="sxs-lookup"><span data-stu-id="5571c-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="5571c-105">Det finns ingen gräns för hur många klasser som du kan lägga till ett indata-avsnitt.</span><span class="sxs-lookup"><span data-stu-id="5571c-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="5571c-106">Indatatyperna är inom en \<kommandot: inputTypes > nod, där varje klass inom en \<kommandot: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="5571c-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="5571c-107">Schemat innehåller två \<maml:description > element i varje \<kommandot: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="5571c-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="5571c-108">Men den `Get-Help` cmdlet visar endast innehållet i den \<kommandot: inputType > /\<maml:description >) element.</span><span class="sxs-lookup"><span data-stu-id="5571c-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="5571c-109">Från och med Windows PowerShell 3.0, den `Get-Help` cmdlet visar innehållet i den \<maml:uri > element.</span><span class="sxs-lookup"><span data-stu-id="5571c-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="5571c-110">Det här elementet kan du dirigera användare till avsnitt som beskriver .NET-klass.</span><span class="sxs-lookup"><span data-stu-id="5571c-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="5571c-111">I följande XML-visas den \<maml:inputTypes > noden.</span><span class="sxs-lookup"><span data-stu-id="5571c-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="5571c-112">Följande XML visar ett exempel på hur du använder den \<maml:inputTypes > noden dokumenterar du en Indatatyp.</span><span class="sxs-lookup"><span data-stu-id="5571c-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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