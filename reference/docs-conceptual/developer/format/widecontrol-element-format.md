---
ms.date: 09/13/2016
ms.topic: reference
title: WideControl-element (format)
description: WideControl-element (format)
ms.openlocfilehash: f88e1ce18f87e5e47de473298b3ecf070b71c192
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651274"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="3c27a-103">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-103">WideControl Element (Format)</span></span>

<span data-ttu-id="3c27a-104">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="3c27a-104">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="3c27a-105">I den här vyn visas ett enskilt egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="3c27a-105">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="3c27a-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3c27a-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3c27a-107">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3c27a-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3c27a-108">Attributes and Elements</span></span>

<span data-ttu-id="3c27a-109">I följande avsnitt beskrivs attributen, underordnade element och `WideControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="3c27a-109">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="3c27a-110">Du kan inte ange `AutoSize` `ColumnNumber` elementen och på samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="3c27a-110">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="3c27a-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="3c27a-111">Attributes</span></span>

<span data-ttu-id="3c27a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="3c27a-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3c27a-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3c27a-113">Child Elements</span></span>

|<span data-ttu-id="3c27a-114">Element</span><span class="sxs-lookup"><span data-stu-id="3c27a-114">Element</span></span>|<span data-ttu-id="3c27a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3c27a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c27a-116">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-116">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="3c27a-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c27a-117">Optional element.</span></span><br /><br /> <span data-ttu-id="3c27a-118">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="3c27a-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="3c27a-119">ColumnNumber-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-119">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="3c27a-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3c27a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="3c27a-121">Anger antalet kolumner som visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="3c27a-121">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="3c27a-122">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-122">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="3c27a-123">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="3c27a-123">Required element.</span></span><br /><br /> <span data-ttu-id="3c27a-124">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="3c27a-124">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3c27a-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3c27a-125">Parent Elements</span></span>

|<span data-ttu-id="3c27a-126">Element</span><span class="sxs-lookup"><span data-stu-id="3c27a-126">Element</span></span>|<span data-ttu-id="3c27a-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3c27a-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3c27a-128">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-128">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="3c27a-129">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="3c27a-129">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3c27a-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3c27a-130">Remarks</span></span>

<span data-ttu-id="3c27a-131">När du definierar en bred vy kan du lägga till `AutoSize` elementet eller, `ColumnNumber` men du kan inte lägga till båda.</span><span class="sxs-lookup"><span data-stu-id="3c27a-131">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="3c27a-132">I de flesta fall krävs bara en definition för varje bred vy, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="3c27a-132">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="3c27a-133">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="3c27a-133">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="3c27a-134">Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="3c27a-134">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3c27a-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="3c27a-135">Example</span></span>

<span data-ttu-id="3c27a-136">I följande exempel visas ett- `WideControl` element som används för att visa en egenskap för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="3c27a-136">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="3c27a-137">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="3c27a-137">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3c27a-138">Se även</span><span class="sxs-lookup"><span data-stu-id="3c27a-138">See Also</span></span>

[<span data-ttu-id="3c27a-139">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-139">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="3c27a-140">ColumnNumber-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-140">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="3c27a-141">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-141">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="3c27a-142">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="3c27a-142">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="3c27a-143">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="3c27a-143">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="3c27a-144">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="3c27a-144">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="3c27a-145">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="3c27a-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
