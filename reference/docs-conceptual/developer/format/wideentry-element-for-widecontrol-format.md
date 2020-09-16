---
title: WideEntry-element för WideControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 13dd1f6ad7ac1e9d8d0524f0a0f18fe80ffaf8e2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780023"
---
# <a name="wideentry-element-for-widecontrol-format"></a><span data-ttu-id="1a7b3-102">WideEntry-element för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-102">WideEntry Element for WideControl (Format)</span></span>

<span data-ttu-id="1a7b3-103">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-103">Provides a definition of the wide view.</span></span>

<span data-ttu-id="1a7b3-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="1a7b3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="1a7b3-105">Syntax</span></span>

```xml
<WideEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <WideItem>...</WideItem>
</WideEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="1a7b3-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="1a7b3-106">Attributes and Elements</span></span>

<span data-ttu-id="1a7b3-107">I följande avsnitt beskrivs attributen, underordnade element och `WideEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-107">The following sections describe the attributes, child elements, and the parent element of the `WideEntry` element.</span></span> <span data-ttu-id="1a7b3-108">Du måste ange ett enda `WideItem` underordnat element.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-108">You must specify a single `WideItem` child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="1a7b3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="1a7b3-109">Attributes</span></span>

<span data-ttu-id="1a7b3-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="1a7b3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="1a7b3-111">Child Elements</span></span>

|<span data-ttu-id="1a7b3-112">Element</span><span class="sxs-lookup"><span data-stu-id="1a7b3-112">Element</span></span>|<span data-ttu-id="1a7b3-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1a7b3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a7b3-114">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-114">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="1a7b3-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="1a7b3-116">Definierar de .NET-typer som använder den här breda post definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-116">Defines the .NET types that use this wide entry definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="1a7b3-117">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-117">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)|<span data-ttu-id="1a7b3-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-118">Required element.</span></span><br /><br /> <span data-ttu-id="1a7b3-119">Definierar egenskapen eller skriptet vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-119">Defines the property or script whose value is displayed.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="1a7b3-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="1a7b3-120">Parent Elements</span></span>

|<span data-ttu-id="1a7b3-121">Element</span><span class="sxs-lookup"><span data-stu-id="1a7b3-121">Element</span></span>|<span data-ttu-id="1a7b3-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="1a7b3-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="1a7b3-123">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-123">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)|<span data-ttu-id="1a7b3-124">Innehåller definitionerna för den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-124">Provides the definitions of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="1a7b3-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="1a7b3-125">Remarks</span></span>

<span data-ttu-id="1a7b3-126">En bred vy är ett List format som visar ett enda egenskaps värde eller skript värde för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-126">A wide view is a list format that displays a single property value or script value for each object.</span></span> <span data-ttu-id="1a7b3-127">Till skillnad från andra typer av vyer kan du bara ange ett objekt element för varje vydefinition.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-127">Unlike other types of views, you can specify only one item element for each view definition.</span></span> <span data-ttu-id="1a7b3-128">Mer information om de andra komponenterna i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="1a7b3-128">For more information about the other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="1a7b3-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="1a7b3-129">Example</span></span>

<span data-ttu-id="1a7b3-130">I följande exempel visas ett `WideEntry` element som definierar ett enda `WideItem` element.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-130">The following example shows a `WideEntry` element that defines a single `WideItem` element.</span></span> <span data-ttu-id="1a7b3-131">`WideItem`Elementet definierar den egenskap vars värde visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="1a7b3-131">The `WideItem` element defines the property whose value is displayed in the view.</span></span>

```xml
<WideEntries>
  <WideEntry>
    <WideItem>
      <PropertyName>ProcessName</PropertyName>
    </WideItem>
  </WideEntry>
</WideEntries>

```

<span data-ttu-id="1a7b3-132">Ett fullständigt exempel på en bred vy finns i [wide View (grundläggande)](./wide-view-basic.md).</span><span class="sxs-lookup"><span data-stu-id="1a7b3-132">For a complete example of a wide view, see [Wide View (Basic)](./wide-view-basic.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="1a7b3-133">Se även</span><span class="sxs-lookup"><span data-stu-id="1a7b3-133">See Also</span></span>

[<span data-ttu-id="1a7b3-134">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="1a7b3-134">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="1a7b3-135">SelectionCondition-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-135">SelectionCondition Element for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1a7b3-136">SelectionSetName-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-136">SelectionSetName Element for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="1a7b3-137">Elementet TypeName för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-137">TypeName Element for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="1a7b3-138">WideEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-138">WideEntries Element (Format)</span></span>](./wideentries-element-for-widecontrol-format.md)

[<span data-ttu-id="1a7b3-139">WideItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="1a7b3-139">WideItem Element (Format)</span></span>](./wideitem-element-for-widecontrol-format.md)

[<span data-ttu-id="1a7b3-140">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="1a7b3-140">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
