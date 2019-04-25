---
title: Så här skapar du filen Cmdlet-hjälpavsnitten | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 4a88dd89-6beb-494f-9e2a-6b10baed1a8d
caps.latest.revision: 17
ms.openlocfilehash: 08e05939f8aee42f2cd502a3da7a528d8460dec1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62083254"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="98ee7-102">Skapa cmdlet-hjälpfilen</span><span class="sxs-lookup"><span data-stu-id="98ee7-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="98ee7-103">Det här avsnittet beskriver hur du skapar en giltig XML-fil som innehåller innehållet för hjälpavsnitt för Windows PowerShell-cmdlet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="98ee7-104">Det här avsnittet beskrivs hur du namnger hjälpfilen, hur du lägger till rätt XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten hjälpinnehållet-cmdlet: ens.</span><span class="sxs-lookup"><span data-stu-id="98ee7-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="98ee7-105">För en fullständig överblick över en hjälpfilen, öppna en av dll-Help.xml-filerna finns i installationskatalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="98ee7-105">For a complete view of a Help file, open one of the dll-Help.xml files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="98ee7-106">Till exempel innehåller filen Microsoft.PowerShell.Commands.Management.dll Help.xml innehåll för flera av Windows PowerShell-cmdlets.</span><span class="sxs-lookup"><span data-stu-id="98ee7-106">For example, the Microsoft.PowerShell.Commands.Management.dll-Help.xml file contains content for several of the Windows PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="98ee7-107">Så här skapar du en Cmdlet-hjälpavsnitten-fil</span><span class="sxs-lookup"><span data-stu-id="98ee7-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="98ee7-108">Skapa en textfil och spara den UTF8-kodning används.</span><span class="sxs-lookup"><span data-stu-id="98ee7-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="98ee7-109">Filnamnet måste ha följande format så att Windows PowerShell kan identifiera den som en cmdlet-hjälpfilen.</span><span class="sxs-lookup"><span data-stu-id="98ee7-109">The file name must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

2. <span data-ttu-id="98ee7-110">Lägg till följande XML-huvuden i textfilen.</span><span class="sxs-lookup"><span data-stu-id="98ee7-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="98ee7-111">Tänk på att filen kommer att valideras mot flera agenten modellering språk (MAML)-schemat.</span><span class="sxs-lookup"><span data-stu-id="98ee7-111">Be aware that the file will be validated against the Multi-Agent Modeling Language (MAML) schema.</span></span> <span data-ttu-id="98ee7-112">Windows PowerShell ger för närvarande inte några verktyg för att verifiera filen.</span><span class="sxs-lookup"><span data-stu-id="98ee7-112">Currently, Windows PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

3. <span data-ttu-id="98ee7-113">Lägga till en kommando-nod i hjälpfilen för cmdlet: en för varje cmdlet i sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="98ee7-113">Add a Command node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="98ee7-114">Varje nod under noden kommandot relaterar till de olika avsnitten i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-114">Each node within the Command node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="98ee7-115">I följande tabell visas de XML-elementet för varje nod, följt av en beskrivningar för varje nod.</span><span class="sxs-lookup"><span data-stu-id="98ee7-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |<span data-ttu-id="98ee7-116">Nod</span><span class="sxs-lookup"><span data-stu-id="98ee7-116">Node</span></span>|<span data-ttu-id="98ee7-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98ee7-117">Description</span></span>|
   |----------|-----------------|
   |`<details>`|<span data-ttu-id="98ee7-118">Lägger till innehåll för avsnitten namn och en sammanfattning av cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-119">Mer information finns i [hur du lägger till Cmdlet-namn och sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:description>`|<span data-ttu-id="98ee7-120">Lägger till innehåll för avsnittet beskrivning i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-121">Mer information finns i [hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>|
   |`<command:syntax>`|<span data-ttu-id="98ee7-122">Lägger till innehåll för avsnittet SYNTAX i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-123">Mer information finns i [hur du lägger till Syntax för en Cmdlet-hjälpavsnittet](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:parameters>`|<span data-ttu-id="98ee7-124">Lägger till innehåll för avsnittet parametrar i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-125">Mer information finns i [hur du lägger till parametrar till en Cmdlet-hjälpavsnittet](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>|
   |`<command:inputTypes>`|<span data-ttu-id="98ee7-126">Lägger till innehåll för avsnittet indata i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-127">Mer information finns i [hur du lägger till indata-typer till en Cmdlet-hjälpavsnittet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:returnValues>`|<span data-ttu-id="98ee7-128">Lägger till innehåll för OUTPUTS-avsnittet i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-129">Mer information finns i [hur du lägger till returnera värden till en Cmdlet-hjälpavsnittet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:alertset>`|<span data-ttu-id="98ee7-130">Lägger till innehåll i avsnittet ANTECKNINGAR i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-130">Adds content to the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-131">Mer information finns i [hur du lägger till information till en Cmdlet-hjälpavsnittet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>|
   |`<command:examples>`|<span data-ttu-id="98ee7-132">Lägger till innehåll för avsnittet exempel i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-133">Mer information finns i [så här lägger du till exempel att en Cmdlet-hjälpavsnittet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>|
   |`<maml:relatedLinks>`|<span data-ttu-id="98ee7-134">Lägger till innehåll för avsnittet med länkar i cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="98ee7-135">Mer information finns i [så här lägger du till relaterade länkar till en Cmdlet-hjälpavsnittet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="98ee7-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>|

## <a name="example"></a><span data-ttu-id="98ee7-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="98ee7-136">Example</span></span>

 <span data-ttu-id="98ee7-137">Här är ett exempel på en kommando-nod som innehåller noder för de olika delarna av cmdlet-hjälpavsnittet.</span><span class="sxs-lookup"><span data-stu-id="98ee7-137">Here is an example of a Command node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

```xml
<command:command
  xmlns:maml="http://schemas.microsoft.com/maml/2004/10"
  xmlns:command="http://schemas.microsoft.com/maml/dev/command/2004/10"
  xmlns:dev="http://schemas.microsoft.com/maml/dev/2004/10">
  <command:details>
    <!--Add name an synopsis here-->
  </command:details>
  <maml:description>
    <!--Add detailed description here-->
  </maml:description>
  <command:syntax>
    <!--Add syntax information here-->
  </command:syntax>
  <command:parameters>
    <!--Add parameter information here-->
  </command:parameters>
  <command:inputTypes>
    <!--Add input type information here-->
  </command:inputTypes>
  <command:returnValues>
    <!--Add return value information here-->
  </command:returnValues>
  <maml:alertSet>
    <!--Add Note information here-->
  </maml:alertSet>
  <command:examples>
    <!--Add cmdlet examples here-->
  </command:examples>
  <maml:relatedLinks>
    <!--Add links to related content here-->
  </maml:relatedLinks>
</command:command>
```

## <a name="see-also"></a><span data-ttu-id="98ee7-138">Se även</span><span class="sxs-lookup"><span data-stu-id="98ee7-138">See Also</span></span>

 [<span data-ttu-id="98ee7-139">Hur du lägger till Cmdlet-namn och sammanfattning</span><span class="sxs-lookup"><span data-stu-id="98ee7-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-140">Hur du lägger till den detaljerade beskrivningen för en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="98ee7-141">Lägga till Syntax i en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-142">Lägga till parametrar i en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="98ee7-143">Hur du lägger till Indatatyper en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-144">Hur du lägger till returvärden för en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-145">Hur du lägger till information till en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-146">Hur du lägger till exempel att en Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-147">Lägga till länkarna till Cmdlet-hjälpavsnittet</span><span class="sxs-lookup"><span data-stu-id="98ee7-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="98ee7-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="98ee7-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)