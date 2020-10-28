---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)
description: SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)
ms.openlocfilehash: a158c5476fb3a168a146ce67565c0ed6f7859519
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651917"
---
# <a name="selectionsetname-element-for-entryselectedby-for-customcontrol-for-view-format"></a><span data-ttu-id="4aea9-103">SelectionSetName-element för EntrySelectedBy för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="4aea9-103">SelectionSetName Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

<span data-ttu-id="4aea9-104">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="4aea9-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="4aea9-105">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="4aea9-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span>

<span data-ttu-id="4aea9-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) EntrySelectedBy-element för CustomEntry för View (format) SelectionSetName-element för EntrySelectedBy för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="4aea9-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) EntrySelectedBy Element for CustomEntry for View (Format) SelectionSetName Element for EntrySelectedBy for CustomEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4aea9-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="4aea9-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4aea9-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4aea9-108">Attributes and Elements</span></span>

<span data-ttu-id="4aea9-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="4aea9-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4aea9-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4aea9-110">Attributes</span></span>

<span data-ttu-id="4aea9-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="4aea9-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4aea9-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4aea9-112">Child Elements</span></span>

<span data-ttu-id="4aea9-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="4aea9-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4aea9-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4aea9-114">Parent Elements</span></span>

|<span data-ttu-id="4aea9-115">Element</span><span class="sxs-lookup"><span data-stu-id="4aea9-115">Element</span></span>|<span data-ttu-id="4aea9-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4aea9-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4aea9-117">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="4aea9-117">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="4aea9-118">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="4aea9-118">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4aea9-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="4aea9-119">Text Value</span></span>

<span data-ttu-id="4aea9-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="4aea9-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="4aea9-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4aea9-121">Remarks</span></span>

<span data-ttu-id="4aea9-122">Varje anpassad kontroll post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="4aea9-122">Each custom control entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="4aea9-123">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="4aea9-123">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="4aea9-124">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="4aea9-124">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="4aea9-125">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="4aea9-125">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="4aea9-126">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="4aea9-126">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="4aea9-127">Se även</span><span class="sxs-lookup"><span data-stu-id="4aea9-127">See Also</span></span>

[<span data-ttu-id="4aea9-128">EntrySelectedBy-element för CustomEntry för vy (format)</span><span class="sxs-lookup"><span data-stu-id="4aea9-128">EntrySelectedBy Element for CustomEntry for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="4aea9-129">Vy för anpassad kontroll</span><span class="sxs-lookup"><span data-stu-id="4aea9-129">Custom Control View</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="4aea9-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="4aea9-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
