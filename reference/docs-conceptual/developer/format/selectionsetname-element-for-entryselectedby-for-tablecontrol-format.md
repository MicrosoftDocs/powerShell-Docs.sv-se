---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för TableControl (format)
description: SelectionSetName-element för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: a5a395f718d0e1a2d7f33d120ce4fd2ff787cc34
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651778"
---
# <a name="selectionsetname-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="d4cbb-103">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d4cbb-103">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="d4cbb-104">Anger en uppsättning .NET-typer. Använd den här posten i vyn tabell.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-104">Specifies a set of .NET types the use this entry of the table view.</span></span> <span data-ttu-id="d4cbb-105">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="d4cbb-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy element (format) SelectionSetName-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d4cbb-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format) SelectionSetName Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d4cbb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d4cbb-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d4cbb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d4cbb-108">Attributes and Elements</span></span>

<span data-ttu-id="d4cbb-109">I följande avsnitt beskrivs attribut, underordnade element och överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-109">The following sections describe attributes, child elements, and parent elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="d4cbb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d4cbb-110">Attributes</span></span>

<span data-ttu-id="d4cbb-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d4cbb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d4cbb-112">Child Elements</span></span>

<span data-ttu-id="d4cbb-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d4cbb-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d4cbb-114">Parent Elements</span></span>

|<span data-ttu-id="d4cbb-115">Element</span><span class="sxs-lookup"><span data-stu-id="d4cbb-115">Element</span></span>|<span data-ttu-id="d4cbb-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d4cbb-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d4cbb-117">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4cbb-117">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="d4cbb-118">Definierar de .NET-typer som använder den här posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-118">Defines the .NET types that use this entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d4cbb-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d4cbb-119">Text Value</span></span>

<span data-ttu-id="d4cbb-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="d4cbb-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d4cbb-121">Remarks</span></span>

<span data-ttu-id="d4cbb-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="d4cbb-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="d4cbb-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="d4cbb-124">For more information about defining selection sets, see [Defining Sets of objects for a View](./defining-selection-sets.md).</span></span>

<span data-ttu-id="d4cbb-125">Om du anger en markerings uppsättning för en post kan du inte ange ett typnamn.</span><span class="sxs-lookup"><span data-stu-id="d4cbb-125">If you specify a selection set for an entry, you cannot specify a type name.</span></span> <span data-ttu-id="d4cbb-126">Mer information om hur du anger en .NET-typ finns i [elementet TypeName för EntrySelectedBy för TableRowEntry (format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span><span class="sxs-lookup"><span data-stu-id="d4cbb-126">For more information about how to specify a .NET type, see [TypeName Element for EntrySelectedBy for TableRowEntry (Format)](./typename-element-for-entryselectedby-for-tablecontrol-format.md).</span></span>

<span data-ttu-id="d4cbb-127">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d4cbb-127">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d4cbb-128">Se även</span><span class="sxs-lookup"><span data-stu-id="d4cbb-128">See Also</span></span>

[<span data-ttu-id="d4cbb-129">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="d4cbb-129">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="d4cbb-130">Definiera uppsättningar av objekt för en vy</span><span class="sxs-lookup"><span data-stu-id="d4cbb-130">Defining Sets of objects for a View</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="d4cbb-131">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="d4cbb-131">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d4cbb-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d4cbb-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
