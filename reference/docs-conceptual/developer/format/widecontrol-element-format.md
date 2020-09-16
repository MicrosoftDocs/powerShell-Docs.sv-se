---
title: WideControl-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b6f19cf94dcb440eeaf53547db407287e5462520
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87784987"
---
# <a name="widecontrol-element-format"></a><span data-ttu-id="7f4fd-102">WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-102">WideControl Element (Format)</span></span>

<span data-ttu-id="7f4fd-103">Definierar ett brett List format (enskilt värde) för vyn.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-103">Defines a wide (single value) list format for the view.</span></span> <span data-ttu-id="7f4fd-104">I den här vyn visas ett enskilt egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-104">This view displays a single property value or script value for each object.</span></span>

<span data-ttu-id="7f4fd-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7f4fd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7f4fd-106">Syntax</span></span>

```xml
<WideControl>
  <AutoSize/>
  <ColumnNumber>PositiveInteger</ColumnNumber>
  <WideEntries>...</WideEntries>
</WideControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7f4fd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7f4fd-107">Attributes and Elements</span></span>

<span data-ttu-id="7f4fd-108">I följande avsnitt beskrivs attributen, underordnade element och `WideControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-108">The following sections describe the attributes, child elements, and parent element of the `WideControl` element.</span></span> <span data-ttu-id="7f4fd-109">Du kan inte ange `AutoSize` `ColumnNumber` elementen och på samma tidpunkt.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-109">You cannot specify the `AutoSize` and `ColumnNumber` elements at the same time.</span></span>

### <a name="attributes"></a><span data-ttu-id="7f4fd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7f4fd-110">Attributes</span></span>

<span data-ttu-id="7f4fd-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7f4fd-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7f4fd-112">Child Elements</span></span>

|<span data-ttu-id="7f4fd-113">Element</span><span class="sxs-lookup"><span data-stu-id="7f4fd-113">Element</span></span>|<span data-ttu-id="7f4fd-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7f4fd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f4fd-115">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-115">AutoSize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)|<span data-ttu-id="7f4fd-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="7f4fd-117">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="7f4fd-118">ColumnNumber-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-118">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)|<span data-ttu-id="7f4fd-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="7f4fd-120">Anger antalet kolumner som visas i den bred vyn.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-120">Specifies the number of columns displayed in the wide view.</span></span>|
|[<span data-ttu-id="7f4fd-121">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-121">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="7f4fd-122">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-122">Required element.</span></span><br /><br /> <span data-ttu-id="7f4fd-123">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-123">Provides the definitions of the wide view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7f4fd-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7f4fd-124">Parent Elements</span></span>

|<span data-ttu-id="7f4fd-125">Element</span><span class="sxs-lookup"><span data-stu-id="7f4fd-125">Element</span></span>|<span data-ttu-id="7f4fd-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7f4fd-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7f4fd-127">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-127">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="7f4fd-128">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-128">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7f4fd-129">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7f4fd-129">Remarks</span></span>

<span data-ttu-id="7f4fd-130">När du definierar en bred vy kan du lägga till `AutoSize` elementet eller, `ColumnNumber` men du kan inte lägga till båda.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-130">When defining a wide view, you can add the `AutoSize` element or the `ColumnNumber` but you cannot add both.</span></span>

<span data-ttu-id="7f4fd-131">I de flesta fall krävs bara en definition för varje bred vy, men det är möjligt att ha flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-131">In most cases, only one definition is required for each wide view, but it is possible to have multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="7f4fd-132">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="7f4fd-132">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

<span data-ttu-id="7f4fd-133">Mer information om komponenterna i en bred vy finns i [wide View-komponenter](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7f4fd-133">For more information about the components of a wide view, see [Wide View Components](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7f4fd-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="7f4fd-134">Example</span></span>

<span data-ttu-id="7f4fd-135">I följande exempel visas ett- `WideControl` element som används för att visa en egenskap för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="7f4fd-135">The following example shows a `WideControl` element that is used to display a property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

<span data-ttu-id="7f4fd-136">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="7f4fd-136">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7f4fd-137">Se även</span><span class="sxs-lookup"><span data-stu-id="7f4fd-137">See Also</span></span>

[<span data-ttu-id="7f4fd-138">AutoSize-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-138">Autosize Element for WideControl (Format)</span></span>](./autosize-element-for-widecontrol-format.md)

[<span data-ttu-id="7f4fd-139">ColumnNumber-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-139">ColumnNumber Element for WideControl (Format)</span></span>](./columnnumber-element-for-widecontrol-format.md)

[<span data-ttu-id="7f4fd-140">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-140">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="7f4fd-141">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-141">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="7f4fd-142">Bred vy (grundläggande)</span><span class="sxs-lookup"><span data-stu-id="7f4fd-142">Wide View (Basic)</span></span>](./wide-view-basic.md)

[<span data-ttu-id="7f4fd-143">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="7f4fd-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="7f4fd-144">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7f4fd-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
