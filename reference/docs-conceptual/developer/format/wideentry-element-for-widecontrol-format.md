---
ms.date: 09/13/2016
ms.topic: reference
title: WideEntry-element för WideControl (format)
description: WideEntry-element för WideControl (format)
ms.openlocfilehash: 3faaf767d11914792effd6765beed956a502c642
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664545"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="67ed2-103">WideEntry-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-103">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="67ed2-104">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="67ed2-104">Provides a definition of the wide view.</span></span>

<span data-ttu-id="67ed2-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67ed2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67ed2-106">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67ed2-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="67ed2-107">Attributes and Elements</span></span>

<span data-ttu-id="67ed2-108">I följande avsnitt beskrivs attributen, underordnade element och `WideEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="67ed2-108">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="67ed2-109">Du måste ange ett enda `WideItem` underordnat element.</span><span class="sxs-lookup"><span data-stu-id="67ed2-109">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67ed2-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="67ed2-110">Attributes</span></span>

<span data-ttu-id="67ed2-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="67ed2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67ed2-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="67ed2-112">Child Elements</span></span>

|<span data-ttu-id="67ed2-113">Element</span><span class="sxs-lookup"><span data-stu-id="67ed2-113">Element</span></span>|<span data-ttu-id="67ed2-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67ed2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67ed2-115">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-115">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="67ed2-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67ed2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="67ed2-117">Definierar de .NET-typer som använder den här breda post definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="67ed2-117">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="67ed2-118">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-118">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="67ed2-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="67ed2-119">Required element.</span></span><br /><br /> <span data-ttu-id="67ed2-120">Definierar egenskapen eller skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="67ed2-120">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67ed2-121">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="67ed2-121">Parent Elements</span></span>

|<span data-ttu-id="67ed2-122">Element</span><span class="sxs-lookup"><span data-stu-id="67ed2-122">Element</span></span>|<span data-ttu-id="67ed2-123">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67ed2-123">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67ed2-124">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-124">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="67ed2-125">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="67ed2-125">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67ed2-126">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="67ed2-126">Remarks</span></span>

<span data-ttu-id="67ed2-127">En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="67ed2-127">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="67ed2-128">Till skillnad från andra typer av vyer kan du bara ange ett objekt element för varje vydefinition.</span><span class="sxs-lookup"><span data-stu-id="67ed2-128">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="67ed2-129">Mer information om de andra komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="67ed2-129">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67ed2-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="67ed2-130">Example</span></span>

<span data-ttu-id="67ed2-131">I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="67ed2-131">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="67ed2-132">`WideItem`Elementet definierar den egenskap vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="67ed2-132">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="67ed2-133">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="67ed2-133">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="67ed2-134">Se även</span><span class="sxs-lookup"><span data-stu-id="67ed2-134">See Also</span></span>

[<span data-ttu-id="67ed2-135">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="67ed2-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="67ed2-136">SelectionCondition-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-136">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="67ed2-137">SelectionSetName-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-137">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="67ed2-138">Elementet TypeName för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-138">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="67ed2-139">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-139">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="67ed2-140">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="67ed2-140">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="67ed2-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="67ed2-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
