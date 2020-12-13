---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för ListControl (format)
description: SelectionSetName-element för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: 413a77f7ba06fe952e574061e58d0b5d80c5b3c4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651838"
---
# <a name="selectionsetname-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="feb91-103">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="feb91-103">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="feb91-104">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="feb91-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="feb91-105">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="feb91-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="feb91-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionSetName-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="feb91-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="feb91-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="feb91-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="feb91-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="feb91-108">Attributes and Elements</span></span>

<span data-ttu-id="feb91-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="feb91-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="feb91-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="feb91-110">Attributes</span></span>

<span data-ttu-id="feb91-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="feb91-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="feb91-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="feb91-112">Child Elements</span></span>

<span data-ttu-id="feb91-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="feb91-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="feb91-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="feb91-114">Parent Elements</span></span>

|<span data-ttu-id="feb91-115">Element</span><span class="sxs-lookup"><span data-stu-id="feb91-115">Element</span></span>|<span data-ttu-id="feb91-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="feb91-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="feb91-117">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="feb91-117">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="feb91-118">Definierar de .NET-typer som använder den här List posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="feb91-118">Defines the .NET types that use this list entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="feb91-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="feb91-119">Text Value</span></span>

<span data-ttu-id="feb91-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="feb91-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="feb91-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="feb91-121">Remarks</span></span>

<span data-ttu-id="feb91-122">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="feb91-122">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="feb91-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="feb91-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="feb91-124">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="feb91-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="feb91-125">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="feb91-125">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="feb91-126">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="feb91-126">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="feb91-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="feb91-127">Example</span></span>

<span data-ttu-id="feb91-128">I följande exempel visas hur du anger en markerings uppsättning för en post i en listvy.</span><span class="sxs-lookup"><span data-stu-id="feb91-128">The following example shows how to specify a selection set for an entry of a list view.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <SelectionSetName>NameofSelectionSet</SelectionSetName>
  </EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="feb91-129">Se även</span><span class="sxs-lookup"><span data-stu-id="feb91-129">See Also</span></span>

[<span data-ttu-id="feb91-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="feb91-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="feb91-131">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="feb91-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="feb91-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="feb91-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
