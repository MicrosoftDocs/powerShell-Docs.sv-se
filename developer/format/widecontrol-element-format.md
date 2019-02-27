---
title: WideControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 715ea055-037b-46ad-b70f-87b3f5134403
caps.latest.revision: 14
ms.openlocfilehash: 2742be0389a1bf04af100a490a59c0d938165811
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849492"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="87035-102">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="87035-102">WideControl Element (Format)</span></span>

<span data-ttu-id="87035-103">Definierar en bred (enstaka värde) listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="87035-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="87035-104">Den här vyn visar ett enda egenskapsvärdet eller skriptvärde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="87035-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="87035-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="87035-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="87035-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="87035-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="87035-107">Attributes and Elements</span></span>

<span data-ttu-id="87035-108">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `WideControl` element.</span><span class="sxs-lookup"><span data-stu-id="87035-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="87035-109">Du kan inte ange den `AutoSize` och `ColumnNumber` element på samma gång.</span><span class="sxs-lookup"><span data-stu-id="87035-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="87035-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="87035-110">Attributes</span></span>

<span data-ttu-id="87035-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="87035-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="87035-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="87035-112">Child Elements</span></span>

|<span data-ttu-id="87035-113">Element</span><span class="sxs-lookup"><span data-stu-id="87035-113">Element</span></span>|<span data-ttu-id="87035-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87035-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87035-115">AutoSize-Element för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="87035-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="87035-116">Optional element.</span></span><br /><br /> <span data-ttu-id="87035-117">Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.</span><span class="sxs-lookup"><span data-stu-id="87035-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="87035-118">Antal_kolumner anger Element för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="87035-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="87035-119">Optional element.</span></span><br /><br /> <span data-ttu-id="87035-120">Anger antalet kolumner som visas i bred vy.</span><span class="sxs-lookup"><span data-stu-id="87035-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="87035-121">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="87035-122">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="87035-122">Required element.</span></span><br /><br /> <span data-ttu-id="87035-123">Innehåller definitioner av bred vy.</span><span class="sxs-lookup"><span data-stu-id="87035-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="87035-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="87035-124">Parent Elements</span></span>

|<span data-ttu-id="87035-125">Element</span><span class="sxs-lookup"><span data-stu-id="87035-125">Element</span></span>|<span data-ttu-id="87035-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="87035-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="87035-127">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="87035-128">Definierar en vy som används för att visa en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="87035-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="87035-129">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="87035-129">Remarks</span></span>

<span data-ttu-id="87035-130">När du definierar en bred vy, kan du lägga till den `AutoSize` element eller `ColumnNumber` men du kan inte lägga till båda.</span><span class="sxs-lookup"><span data-stu-id="87035-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="87035-131">Endast en definition som krävs för varje bred vy i de flesta fall, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="87035-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="87035-132">I sådana fall kan ange du en definition av separat för varje objekt eller en uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="87035-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="87035-133">Mer information om komponenter för en bred vy finns i [bred vy komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="87035-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="87035-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="87035-134">Example</span></span>

<span data-ttu-id="87035-135">I följande exempel visas en `WideControl` element som används för att visa en egenskap för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="87035-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<View>
  <Name>process</Name>
  <ViewSelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </ViewSelectedBy>
  <WideControl>
    <WideEntries>...</WideEntries>
  </WideControl>
</View>
```

<span data-ttu-id="87035-136">Exempel på en bred vy, se [bred vy (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="87035-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="87035-137">Se även</span><span class="sxs-lookup"><span data-stu-id="87035-137">See Also</span></span>

[<span data-ttu-id="87035-138">AutoSize-Element för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="87035-139">Antal_kolumner anger Element för WideControl (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="87035-140">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="87035-141">WideEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="87035-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="87035-142">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="87035-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="87035-143">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="87035-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="87035-144">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="87035-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
