---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för WideControl (format)
description: SelectionCondition-element för EntrySelectedBy för WideControl (format)
ms.openlocfilehash: 8c51ca72edc6ad174dc289c61a8987e8f9495d19
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655111"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="d081b-103">SelectionCondition-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-103">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="d081b-104">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d081b-104">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="d081b-105">Det finns ingen gräns för hur många urvals villkor som kan anges för en bred post definition.</span><span class="sxs-lookup"><span data-stu-id="d081b-105">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="d081b-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d081b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d081b-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d081b-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d081b-108">Attributes and Elements</span></span>

<span data-ttu-id="d081b-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d081b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="d081b-110">Du måste ange ett enskilt `PropertyName` eller- `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="d081b-110">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="d081b-111">`SelectionSetName` `TypeName` Elementen och är valfria.</span><span class="sxs-lookup"><span data-stu-id="d081b-111">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="d081b-112">Du kan ange ett av båda elementen.</span><span class="sxs-lookup"><span data-stu-id="d081b-112">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d081b-113">Attribut</span><span class="sxs-lookup"><span data-stu-id="d081b-113">Attributes</span></span>

<span data-ttu-id="d081b-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="d081b-114">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d081b-115">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d081b-115">Child Elements</span></span>

|<span data-ttu-id="d081b-116">Element</span><span class="sxs-lookup"><span data-stu-id="d081b-116">Element</span></span>|<span data-ttu-id="d081b-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d081b-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d081b-118">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-118">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="d081b-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d081b-119">Optional element.</span></span><br /><br /> <span data-ttu-id="d081b-120">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d081b-120">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="d081b-121">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-121">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d081b-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d081b-122">Optional element.</span></span><br /><br /> <span data-ttu-id="d081b-123">Anger det skript block som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d081b-123">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="d081b-124">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-124">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="d081b-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d081b-125">Optional element.</span></span><br /><br /> <span data-ttu-id="d081b-126">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d081b-126">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="d081b-127">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-127">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="d081b-128">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="d081b-128">Optional element.</span></span><br /><br /> <span data-ttu-id="d081b-129">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d081b-129">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d081b-130">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d081b-130">Parent Elements</span></span>

|<span data-ttu-id="d081b-131">Element</span><span class="sxs-lookup"><span data-stu-id="d081b-131">Element</span></span>|<span data-ttu-id="d081b-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d081b-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d081b-133">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-133">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="d081b-134">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d081b-134">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d081b-135">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d081b-135">Remarks</span></span>

<span data-ttu-id="d081b-136">Varje bred post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="d081b-136">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="d081b-137">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="d081b-137">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="d081b-138">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d081b-138">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="d081b-139">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d081b-139">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="d081b-140">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d081b-140">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d081b-141">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="d081b-141">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d081b-142">Se även</span><span class="sxs-lookup"><span data-stu-id="d081b-142">See Also</span></span>

[<span data-ttu-id="d081b-143">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="d081b-143">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="d081b-144">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="d081b-144">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d081b-145">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-145">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="d081b-146">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-146">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d081b-147">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-147">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d081b-148">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-148">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="d081b-149">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d081b-149">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="d081b-150">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d081b-150">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
