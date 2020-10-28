---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för EnumerableExpansion (format)
description: EntrySelectedBy-element för EnumerableExpansion (format)
ms.openlocfilehash: 8b2fff2d0b14d0622d0be2c5af3a95194c733a73
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92652331"
---
# <a name="entryselectedby-element-for-enumerableexpansion-format"></a><span data-ttu-id="e2dfd-103">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-103">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="e2dfd-104">Definierar de .NET-typer som använder den här definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-104">Defines the .NET types that use this definition or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="e2dfd-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2dfd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2dfd-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2dfd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e2dfd-107">Attributes and Elements</span></span>

<span data-ttu-id="e2dfd-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2dfd-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e2dfd-109">Attributes</span></span>

<span data-ttu-id="e2dfd-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2dfd-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e2dfd-111">Child Elements</span></span>

|<span data-ttu-id="e2dfd-112">Element</span><span class="sxs-lookup"><span data-stu-id="e2dfd-112">Element</span></span>|<span data-ttu-id="e2dfd-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e2dfd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2dfd-114">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-114">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e2dfd-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e2dfd-116">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-116">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|
|[<span data-ttu-id="e2dfd-117">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-117">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e2dfd-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e2dfd-119">Anger en uppsättning .NET-typer som använder den här definitionen av hur samlings objekt expanderas.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-119">Specifies a set of .NET types that use this definition of how collection objects are expanded.</span></span>|
|[<span data-ttu-id="e2dfd-120">TypeName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-120">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="e2dfd-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e2dfd-122">Anger en .NET-typ som använder den här definitionen av hur samlings objekt expanderas.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-122">Specifies a .NET type that uses this definition of how collection objects are expanded.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2dfd-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e2dfd-123">Parent Elements</span></span>

|<span data-ttu-id="e2dfd-124">Element</span><span class="sxs-lookup"><span data-stu-id="e2dfd-124">Element</span></span>|<span data-ttu-id="e2dfd-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e2dfd-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2dfd-126">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-126">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)|<span data-ttu-id="e2dfd-127">Definierar hur vissa .NET Collection-objekt expanderas när de visas i en vy.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-127">Defines how specific .NET collection objects are expanded when they are displayed in a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2dfd-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e2dfd-128">Remarks</span></span>

<span data-ttu-id="e2dfd-129">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definitions post.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-129">You must specify at least one type, selection set, or selection condition for a definition entry.</span></span> <span data-ttu-id="e2dfd-130">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="e2dfd-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="e2dfd-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="e2dfd-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="e2dfd-132">Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e2dfd-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2dfd-133">Se även</span><span class="sxs-lookup"><span data-stu-id="e2dfd-133">See Also</span></span>

[<span data-ttu-id="e2dfd-134">Definiera villkor för datavisning</span><span class="sxs-lookup"><span data-stu-id="e2dfd-134">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e2dfd-135">EnumerableExpansion-element (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-135">EnumerableExpansion Element (Format)</span></span>](./enumerableexpansion-element-format.md)

[<span data-ttu-id="e2dfd-136">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-136">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e2dfd-137">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-137">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e2dfd-138">TypeName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="e2dfd-138">TypeName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="e2dfd-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e2dfd-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
