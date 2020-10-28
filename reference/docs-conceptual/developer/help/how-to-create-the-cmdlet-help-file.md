---
ms.date: 09/13/2016
ms.topic: reference
title: Skapa cmdlet-hjälpfilen
description: Skapa cmdlet-hjälpfilen
ms.openlocfilehash: 40259c8f9496b10380805a78f3711aed6f1bf2e5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659099"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="b84ac-103">Skapa cmdlet-hjälpfilen</span><span class="sxs-lookup"><span data-stu-id="b84ac-103">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="b84ac-104">I det här avsnittet beskrivs hur du skapar en giltig XML-fil som innehåller innehåll för Windows PowerShell-cmdlet hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="b84ac-104">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="b84ac-105">I det här avsnittet beskrivs hur du namnger hjälp filen, hur du lägger till lämpliga XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten i hjälp innehållet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b84ac-105">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="b84ac-106">Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="b84ac-106">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="b84ac-107">Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="b84ac-107">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="b84ac-108">Så här skapar du en cmdlet-hjälpfil</span><span class="sxs-lookup"><span data-stu-id="b84ac-108">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="b84ac-109">Skapa en textfil och spara den med hjälp av UTF8-kodning.</span><span class="sxs-lookup"><span data-stu-id="b84ac-109">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="b84ac-110">Fil namnet måste ha följande format så att Windows PowerShell kan identifiera det som en hjälp fil för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-110">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="b84ac-111">Lägg till följande XML-rubriker i text filen.</span><span class="sxs-lookup"><span data-stu-id="b84ac-111">Add the following XML headers to the text file.</span></span> <span data-ttu-id="b84ac-112">Tänk på att filen kommer att verifieras mot MAML-schemat (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="b84ac-112">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="b84ac-113">För närvarande tillhandahåller PowerShell inga verktyg för att validera filen.</span><span class="sxs-lookup"><span data-stu-id="b84ac-113">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="b84ac-114">Lägg till en **kommando** nod i cmdlet-hjälpen för varje cmdlet i sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="b84ac-114">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="b84ac-115">Varje nod i **kommando** -noden relaterar till de olika avsnitten i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b84ac-115">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="b84ac-116">I följande tabell visas XML-elementet för varje nod, följt av en beskrivning av varje nod.</span><span class="sxs-lookup"><span data-stu-id="b84ac-116">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="b84ac-117">Node</span><span class="sxs-lookup"><span data-stu-id="b84ac-117">Node</span></span>           |                                                                                                     <span data-ttu-id="b84ac-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b84ac-118">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="b84ac-119">Lägger till innehåll för avsnittet namn och sammanfattning i hjälpen för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-119">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-120">Mer information finns i [så här lägger du till cmdlet-namn och-sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-120">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="b84ac-121">Lägger till innehåll i BESKRIVNINGs avsnittet i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b84ac-121">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-122">Mer information finns i [avsnittet så här lägger du till den detaljerade beskrivningen i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-122">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="b84ac-123">Lägger till innehåll i avsnittet SYNTAX i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-123">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-124">Mer information finns i [avsnittet så här lägger du till syntax i en cmdlet-hjälpfil](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-124">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="b84ac-125">Lägger till innehåll för avsnittet parametrar i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-125">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-126">Mer information finns i [avsnittet How to Add Parameters to a cmdlet Help](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-126">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="b84ac-127">Lägger till innehåll för indata-avsnittet i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-127">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-128">Mer information finns i [så här lägger du till indatatyper i ett hjälp avsnitt om cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-128">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="b84ac-129">Lägger till innehåll för avsnittet utdata i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-129">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-130">Mer information finns i [Hjälp avsnittet så här lägger du till retur värden i en cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-130">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="b84ac-131">Lägger till innehåll i avsnittet anteckningar i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-131">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-132">Mer information finns i [så här lägger du till anteckningar i ett hjälp avsnitt för cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-132">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="b84ac-133">Lägger till innehåll i avsnittet exempel i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="b84ac-133">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-134">Mer information finns i [så här lägger du till exempel i ett hjälp avsnitt om cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-134">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="b84ac-135">Lägger till innehåll i avsnittet relaterade länkar i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b84ac-135">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="b84ac-136">Mer information finns i [så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="b84ac-136">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="b84ac-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="b84ac-137">Example</span></span>

 <span data-ttu-id="b84ac-138">Här är ett exempel på en **kommando** nod som innehåller noderna för de olika avsnitten i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="b84ac-138">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b84ac-139">Se även</span><span class="sxs-lookup"><span data-stu-id="b84ac-139">See Also</span></span>

 [<span data-ttu-id="b84ac-140">Så här lägger du till cmdlet-namn och-sammanfattning</span><span class="sxs-lookup"><span data-stu-id="b84ac-140">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-141">Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="b84ac-141">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="b84ac-142">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b84ac-142">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-143">Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="b84ac-143">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="b84ac-144">Lägga till indatatyper i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b84ac-144">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-145">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b84ac-145">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-146">Så här lägger du till anteckningar i hjälp avsnittet om cmdlet</span><span class="sxs-lookup"><span data-stu-id="b84ac-146">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-147">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b84ac-147">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-148">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="b84ac-148">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="b84ac-149">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="b84ac-149">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
