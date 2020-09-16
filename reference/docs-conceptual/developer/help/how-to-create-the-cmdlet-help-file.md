---
title: Så här skapar du cmdlet-hjälp filen | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 7ab0404e5d0122a64483883e6e2d4760dfa5038d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87779836"
---
# <a name="how-to-create-the-cmdlet-help-file"></a><span data-ttu-id="c2f3c-102">Skapa cmdlet-hjälpfilen</span><span class="sxs-lookup"><span data-stu-id="c2f3c-102">How to Create the Cmdlet Help File</span></span>

<span data-ttu-id="c2f3c-103">I det här avsnittet beskrivs hur du skapar en giltig XML-fil som innehåller innehåll för Windows PowerShell-cmdlet hjälp avsnitt.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-103">This section describes how to create a valid XML file that contains content for Windows PowerShell cmdlet Help topics.</span></span> <span data-ttu-id="c2f3c-104">I det här avsnittet beskrivs hur du namnger hjälp filen, hur du lägger till lämpliga XML-huvuden och hur du lägger till noder som innehåller de olika avsnitten i hjälp innehållet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-104">This section discusses how to name the Help file, how to add the appropriate XML headers, and how to add nodes that will contain the different sections of the cmdlet Help content.</span></span>

> [!NOTE]
> <span data-ttu-id="c2f3c-105">Om du vill se en fullständig vy över en hjälpfil öppnar du en av `dll-Help.xml` filerna som finns i installations katalogen för Windows PowerShell.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-105">For a complete view of a Help file, open one of the `dll-Help.xml` files located in the Windows PowerShell installation directory.</span></span> <span data-ttu-id="c2f3c-106">Filen innehåller till exempel `Microsoft.PowerShell.Commands.Management.dll-Help.xml` innehåll för flera av PowerShell-cmdletarna.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-106">For example, the `Microsoft.PowerShell.Commands.Management.dll-Help.xml` file contains content for several of the PowerShell cmdlets.</span></span>

### <a name="how-to-create-a-cmdlet-help-file"></a><span data-ttu-id="c2f3c-107">Så här skapar du en cmdlet-hjälpfil</span><span class="sxs-lookup"><span data-stu-id="c2f3c-107">How to Create a Cmdlet Help File</span></span>

1. <span data-ttu-id="c2f3c-108">Skapa en textfil och spara den med hjälp av UTF8-kodning.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-108">Create a text file and save it using UTF8 encoding.</span></span> <span data-ttu-id="c2f3c-109">Fil namnet måste ha följande format så att Windows PowerShell kan identifiera det som en hjälp fil för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-109">The filename must have the following format so that Windows PowerShell can detect it as a cmdlet Help file.</span></span>

   `<PSSnapInAssemblyName>.dll-Help.xml`

1. <span data-ttu-id="c2f3c-110">Lägg till följande XML-rubriker i text filen.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-110">Add the following XML headers to the text file.</span></span> <span data-ttu-id="c2f3c-111">Tänk på att filen kommer att verifieras mot MAML-schemat (Microsoft Assistance Markup Language).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-111">Be aware that the file will be validated against the Microsoft Assistance Markup Language (MAML) schema.</span></span> <span data-ttu-id="c2f3c-112">För närvarande tillhandahåller PowerShell inga verktyg för att validera filen.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-112">Currently, PowerShell does not provide any tools to validate the file.</span></span>

   `<?xml version="1.0" encoding="utf-8" ?> <helpItems xmlns="http://msh" schema="maml">`

1. <span data-ttu-id="c2f3c-113">Lägg till en **kommando** nod i cmdlet-hjälpen för varje cmdlet i sammansättningen.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-113">Add a **Command** node to the cmdlet Help file for each cmdlet in the assembly.</span></span> <span data-ttu-id="c2f3c-114">Varje nod i **kommando** -noden relaterar till de olika avsnitten i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-114">Each node within the **Command** node relates to the different sections of the cmdlet Help topic.</span></span>

   <span data-ttu-id="c2f3c-115">I följande tabell visas XML-elementet för varje nod, följt av en beskrivning av varje nod.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-115">The following table lists the XML element for each node, followed by a descriptions of each node.</span></span>

   |           <span data-ttu-id="c2f3c-116">Node</span><span class="sxs-lookup"><span data-stu-id="c2f3c-116">Node</span></span>           |                                                                                                     <span data-ttu-id="c2f3c-117">Description</span><span class="sxs-lookup"><span data-stu-id="c2f3c-117">Description</span></span>                                                                                                     |
   | ------------------------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
   | `<details>`              | <span data-ttu-id="c2f3c-118">Lägger till innehåll för avsnittet namn och sammanfattning i hjälpen för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-118">Adds content for the NAME and SYNOPSIS sections of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-119">Mer information finns i [så här lägger du till cmdlet-namn och-sammanfattning](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-119">For more information, see [How to Add the Cmdlet Name and Synopsis](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md).</span></span> |
   | `<maml:description>`     | <span data-ttu-id="c2f3c-120">Lägger till innehåll i BESKRIVNINGs avsnittet i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-120">Adds content for the DESCRIPTION section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-121">Mer information finns i [avsnittet så här lägger du till den detaljerade beskrivningen i en cmdlet-hjälpfil](./how-to-add-a-cmdlet-description.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-121">For more information, see [How to Add the Detailed Description to a Cmdlet Help Topic](./how-to-add-a-cmdlet-description.md).</span></span>                    |
   | `<command:syntax>`       | <span data-ttu-id="c2f3c-122">Lägger till innehåll i avsnittet SYNTAX i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-122">Adds content for the SYNTAX section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-123">Mer information finns i [avsnittet så här lägger du till syntax i en cmdlet-hjälpfil](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-123">For more information, see [How to Add Syntax to a Cmdlet Help Topic](./how-to-add-syntax-to-a-cmdlet-help-topic.md).</span></span>                                  |
   | `<command:parameters>`   | <span data-ttu-id="c2f3c-124">Lägger till innehåll för avsnittet parametrar i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-124">Adds content for the PARAMETERS section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-125">Mer information finns i [avsnittet How to Add Parameters to a cmdlet Help](./how-to-add-parameter-information.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-125">For more information, see [How to Add Parameters to a Cmdlet Help Topic](./how-to-add-parameter-information.md).</span></span>                                  |
   | `<command:inputTypes>`   | <span data-ttu-id="c2f3c-126">Lägger till innehåll för indata-avsnittet i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-126">Adds content for the INPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-127">Mer information finns i [så här lägger du till indatatyper i ett hjälp avsnitt om cmdlet](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-127">For more information, see [How to Add Input Types to a Cmdlet Help Topic](./how-to-add-input-types-to-a-cmdlet-help-topic.md).</span></span>                        |
   | `<command:returnValues>` | <span data-ttu-id="c2f3c-128">Lägger till innehåll för avsnittet utdata i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-128">Adds content for the OUTPUTS section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-129">Mer information finns i [Hjälp avsnittet så här lägger du till retur värden i en cmdlet](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-129">For more information, see [How to Add Return Values to a Cmdlet Help Topic](./how-to-add-return-values-to-a-cmdlet-help-topic.md).</span></span>                   |
   | `<maml:alertset>`        | <span data-ttu-id="c2f3c-130">Lägger till innehåll i avsnittet anteckningar i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-130">Adds content for the NOTES section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-131">Mer information finns i [så här lägger du till anteckningar i ett hjälp avsnitt för cmdlet](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-131">For more information, see [How to add Notes to a Cmdlet Help Topic](./how-to-add-notes-to-a-cmdlet-help-topic.md).</span></span>                                      |
   | `<command:examples>`     | <span data-ttu-id="c2f3c-132">Lägger till innehåll i avsnittet exempel i hjälp avsnittet för cmdlet.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-132">Adds content for the EXAMPLES section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-133">Mer information finns i [så här lägger du till exempel i ett hjälp avsnitt om cmdlet](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-133">For more information, see [How to Add Examples to a Cmdlet Help Topic](./how-to-add-examples-to-a-cmdlet-help-topic.md).</span></span>                            |
   | `<maml:relatedLinks>`    | <span data-ttu-id="c2f3c-134">Lägger till innehåll i avsnittet relaterade länkar i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-134">Adds content for the RELATED LINKS section of the cmdlet Help topic.</span></span> <span data-ttu-id="c2f3c-135">Mer information finns i [så här lägger du till relaterade länkar i ett hjälp avsnitt för cmdlet](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span><span class="sxs-lookup"><span data-stu-id="c2f3c-135">For more information, see [How to Add Related Links to a Cmdlet Help Topic](./how-to-add-related-links-to-a-cmdlet-help-topic.md).</span></span>             |

## <a name="example"></a><span data-ttu-id="c2f3c-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="c2f3c-136">Example</span></span>

 <span data-ttu-id="c2f3c-137">Här är ett exempel på en **kommando** nod som innehåller noderna för de olika avsnitten i hjälp avsnittet för cmdleten.</span><span class="sxs-lookup"><span data-stu-id="c2f3c-137">Here is an example of a **Command** node that includes the nodes for the various sections of the cmdlet Help topic.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c2f3c-138">Se även</span><span class="sxs-lookup"><span data-stu-id="c2f3c-138">See Also</span></span>

 [<span data-ttu-id="c2f3c-139">Så här lägger du till cmdlet-namn och-sammanfattning</span><span class="sxs-lookup"><span data-stu-id="c2f3c-139">How to Add the Cmdlet Name and Synopsis</span></span>](./how-to-add-the-cmdlet-name-and-synopsis-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-140">Så här lägger du till den detaljerade beskrivningen i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="c2f3c-140">How to Add the Detailed Description to a Cmdlet Help Topic</span></span>](./how-to-add-a-cmdlet-description.md)

 [<span data-ttu-id="c2f3c-141">Lägga till syntax till ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="c2f3c-141">How to Add Syntax to a Cmdlet Help Topic</span></span>](./how-to-add-syntax-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-142">Så här lägger du till parametrar i ett hjälp avsnitt för cmdlet</span><span class="sxs-lookup"><span data-stu-id="c2f3c-142">How to Add Parameters to a Cmdlet Help Topic</span></span>](./how-to-add-parameter-information.md)

 [<span data-ttu-id="c2f3c-143">Lägga till indatatyper i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="c2f3c-143">How to Add Input Types to a Cmdlet Help Topic</span></span>](./how-to-add-input-types-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-144">Lägga till returvärden i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="c2f3c-144">How to Add Return Values to a Cmdlet Help Topic</span></span>](./how-to-add-return-values-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-145">Så här lägger du till anteckningar i hjälp avsnittet om cmdlet</span><span class="sxs-lookup"><span data-stu-id="c2f3c-145">How to add Notes to a Cmdlet Help Topic</span></span>](./how-to-add-notes-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-146">Lägga till exempel i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="c2f3c-146">How to Add Examples to a Cmdlet Help Topic</span></span>](./how-to-add-examples-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-147">Lägga till relaterade länkar i ett cmdlet-hjälpavsnitt</span><span class="sxs-lookup"><span data-stu-id="c2f3c-147">How to Add Related Links to a Cmdlet Help Topic</span></span>](./how-to-add-related-links-to-a-cmdlet-help-topic.md)

 [<span data-ttu-id="c2f3c-148">Windows PowerShell SDK</span><span class="sxs-lookup"><span data-stu-id="c2f3c-148">Windows PowerShell SDK</span></span>](../windows-powershell-reference.md)
