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
ms.openlocfilehash: f213605dda0132051d983f8608515325e815c455
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353293"
---
# <a name="how-to-add-input-types-to-a-cmdlet-help-topic"></a><span data-ttu-id="dedaa-102">Lägga till indatatyper i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="dedaa-102">How to Add Input Types to a Cmdlet Help Topic</span></span>

<span data-ttu-id="dedaa-103">I det här avsnittet beskrivs hur du lägger till ett indata-avsnitt i ett hjälp avsnitt om Windows PowerShell® cmdlet.</span><span class="sxs-lookup"><span data-stu-id="dedaa-103">This section describes how to add an INPUTS section to a Windows PowerShell® cmdlet Help topic.</span></span> <span data-ttu-id="dedaa-104">I avsnittet indata visas de .NET-klasser av objekt som cmdleten accepterar som indata från pipelinen, antingen med värde eller efter egenskaps namn.</span><span class="sxs-lookup"><span data-stu-id="dedaa-104">The INPUTS section lists the .NET classes of objects that the cmdlet accepts as input from the pipeline, either by value or by property name.</span></span>

<span data-ttu-id="dedaa-105">Det finns ingen gräns för antalet klasser som du kan lägga till i ett indata-avsnitt.</span><span class="sxs-lookup"><span data-stu-id="dedaa-105">There is no limit to the number of classes that you can add to an INPUTS section.</span></span> <span data-ttu-id="dedaa-106">Indatatyperna anges i ett \<kommando: inputTypes >-noden, där varje klass omges av ett \<kommando: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="dedaa-106">The input types are enclosed in a \<command:inputTypes> node, with each class enclosed in a  \<command:inputType> element.</span></span>

<span data-ttu-id="dedaa-107">Schemat innehåller två \<MAML: Description > element i varje \<kommando: inputType > element.</span><span class="sxs-lookup"><span data-stu-id="dedaa-107">The schema includes two \<maml:description> elements in each \<command:inputType> element.</span></span> <span data-ttu-id="dedaa-108">Men `Get-Help`-cmdlet: en visar bara innehållet i \<kommandot: inputType >/\<MAML: Description >).</span><span class="sxs-lookup"><span data-stu-id="dedaa-108">However, the `Get-Help` cmdlet displays only the content of the \<command:inputType>/\<maml:description>) element.</span></span>

<span data-ttu-id="dedaa-109">Från och med Windows PowerShell 3,0 visar `Get-Help`-cmdlet innehållet i \<MAML: URI >-elementet.</span><span class="sxs-lookup"><span data-stu-id="dedaa-109">Beginning in Windows PowerShell 3.0, the `Get-Help` cmdlet displays the content of the \<maml:uri> element.</span></span> <span data-ttu-id="dedaa-110">Med det här elementet kan du dirigera användare till ämnen som beskriver .NET-klassen.</span><span class="sxs-lookup"><span data-stu-id="dedaa-110">This element lets you direct users to topics that describe the .NET class.</span></span>

<span data-ttu-id="dedaa-111">Följande XML visar noden \<MAML: inputTypes >.</span><span class="sxs-lookup"><span data-stu-id="dedaa-111">The following XML shows the \<maml:inputTypes> node.</span></span>

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

<span data-ttu-id="dedaa-112">Följande XML visar ett exempel på hur du använder noden \<MAML: inputTypes > för att dokumentera en indatatyp.</span><span class="sxs-lookup"><span data-stu-id="dedaa-112">The following XML shows an example of using the \<maml:inputTypes> node to document an input type.</span></span>

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