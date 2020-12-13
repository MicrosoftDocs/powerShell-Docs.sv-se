---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)
description: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 3ecf7fde99b9ee66a153eea416792f351ff62af3
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92647917"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="f6362-103">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-103">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="f6362-104">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="f6362-104">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="f6362-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f6362-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f6362-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f6362-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f6362-107">Attributes and Elements</span></span>

<span data-ttu-id="f6362-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f6362-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="f6362-109">Du måste ange ett enskilt `PropertyName` eller- `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="f6362-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="f6362-110">`SelectionSetName` `TypeName` Elementen och är valfria.</span><span class="sxs-lookup"><span data-stu-id="f6362-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="f6362-111">Du kan ange ett av båda elementen.</span><span class="sxs-lookup"><span data-stu-id="f6362-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f6362-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="f6362-112">Attributes</span></span>

<span data-ttu-id="f6362-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="f6362-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f6362-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f6362-114">Child Elements</span></span>

|<span data-ttu-id="f6362-115">Element</span><span class="sxs-lookup"><span data-stu-id="f6362-115">Element</span></span>|<span data-ttu-id="f6362-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f6362-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6362-117">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-117">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f6362-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6362-118">Optional element.</span></span><br /><br /> <span data-ttu-id="f6362-119">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f6362-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="f6362-120">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f6362-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6362-121">Optional element.</span></span><br /><br /> <span data-ttu-id="f6362-122">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f6362-122">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="f6362-123">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f6362-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6362-124">Optional element.</span></span><br /><br /> <span data-ttu-id="f6362-125">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f6362-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="f6362-126">TypeName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-126">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="f6362-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f6362-127">Optional element.</span></span><br /><br /> <span data-ttu-id="f6362-128">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="f6362-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f6362-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f6362-129">Parent Elements</span></span>

|<span data-ttu-id="f6362-130">Element</span><span class="sxs-lookup"><span data-stu-id="f6362-130">Element</span></span>|<span data-ttu-id="f6362-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f6362-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f6362-132">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="f6362-132">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="f6362-133">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="f6362-133">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f6362-134">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f6362-134">Remarks</span></span>

<span data-ttu-id="f6362-135">Varje definition måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="f6362-135">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="f6362-136">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="f6362-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="f6362-137">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f6362-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="f6362-138">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="f6362-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="f6362-139">Mer information om hur du använder urvals villkor finns i [definiera villkor för Diplaying-data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="f6362-139">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="f6362-140">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="f6362-140">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f6362-141">Se även</span><span class="sxs-lookup"><span data-stu-id="f6362-141">See Also</span></span>

[<span data-ttu-id="f6362-142">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="f6362-142">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="f6362-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f6362-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
