---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för GroupBy (format)
description: SelectionSetName-element för EntrySelectedBy för GroupBy (format)
ms.openlocfilehash: 7ebe5d884061243c8b4af196788187d84c15a92e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651855"
---
# <a name="selectionsetname-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="7e4c9-103">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7e4c9-103">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="7e4c9-104">Anger en uppsättning .NET-objekt för List posten.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-104">Specifies a set of .NET objects for the list entry.</span></span> <span data-ttu-id="7e4c9-105">Det finns ingen gräns för antalet markerings uppsättningar som kan anges för en post.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-105">There is no limit to the number of selection sets that can be specified for an entry.</span></span> <span data-ttu-id="7e4c9-106">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-106">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="7e4c9-107">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="7e4c9-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e4c9-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e4c9-108">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e4c9-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7e4c9-109">Attributes and Elements</span></span>

<span data-ttu-id="7e4c9-110">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-110">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e4c9-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e4c9-111">Attributes</span></span>

<span data-ttu-id="7e4c9-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e4c9-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7e4c9-113">Child Elements</span></span>

<span data-ttu-id="7e4c9-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7e4c9-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7e4c9-115">Parent Elements</span></span>

|<span data-ttu-id="7e4c9-116">Element</span><span class="sxs-lookup"><span data-stu-id="7e4c9-116">Element</span></span>|<span data-ttu-id="7e4c9-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e4c9-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e4c9-118">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7e4c9-118">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="7e4c9-119">Definierar de .NET-typer som använder den här anpassade posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-119">Defines the .NET types that use this custom entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7e4c9-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7e4c9-120">Text Value</span></span>

<span data-ttu-id="7e4c9-121">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-121">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7e4c9-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7e4c9-122">Remarks</span></span>

<span data-ttu-id="7e4c9-123">Varje definition av anpassad kontroll måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-123">Each custom control definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7e4c9-124">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-124">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="7e4c9-125">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="7e4c9-125">For example, you may want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="7e4c9-126">Mer information om hur du definierar urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7e4c9-126">For more information about defining selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

<span data-ttu-id="7e4c9-127">Mer information om komponenterna i en anpassad kontroll vy finns i [skapa anpassade kontroller](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="7e4c9-127">For more information about the components of a custom control view, see [Creating Custom Controls](./creating-custom-controls.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e4c9-128">Se även</span><span class="sxs-lookup"><span data-stu-id="7e4c9-128">See Also</span></span>

[<span data-ttu-id="7e4c9-129">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="7e4c9-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="7e4c9-130">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="7e4c9-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="7e4c9-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7e4c9-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
