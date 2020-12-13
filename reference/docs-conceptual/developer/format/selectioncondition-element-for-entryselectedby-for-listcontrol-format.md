---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för ListControl (format)
description: SelectionCondition-element för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: e93499691dd0046265e43abd26497b2974546083
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655100"
---
# <a name="selectioncondition-element-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="2a8e2-103">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-103">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="2a8e2-104">Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-104">Defines the condition that must exist to use this definition of the list view.</span></span> <span data-ttu-id="2a8e2-105">Det finns ingen gräns för antalet urvals villkor som kan anges för en List definition.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-105">There is no limit to the number of selection conditions that can be specified for a list definition.</span></span>

<span data-ttu-id="2a8e2-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a8e2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a8e2-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a8e2-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2a8e2-108">Attributes and Elements</span></span>

<span data-ttu-id="2a8e2-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a8e2-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a8e2-110">Attributes</span></span>

<span data-ttu-id="2a8e2-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a8e2-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2a8e2-112">Child Elements</span></span>

|<span data-ttu-id="2a8e2-113">Element</span><span class="sxs-lookup"><span data-stu-id="2a8e2-113">Element</span></span>|<span data-ttu-id="2a8e2-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2a8e2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a8e2-115">PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-115">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2a8e2-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="2a8e2-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="2a8e2-118">Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2a8e2-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="2a8e2-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="2a8e2-121">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format.md)|<span data-ttu-id="2a8e2-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="2a8e2-123">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="2a8e2-124">Elementet TypeName för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-124">TypeName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="2a8e2-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-125">Optional element.</span></span><br /><br /> <span data-ttu-id="2a8e2-126">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2a8e2-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2a8e2-127">Parent Elements</span></span>

|<span data-ttu-id="2a8e2-128">Element</span><span class="sxs-lookup"><span data-stu-id="2a8e2-128">Element</span></span>|<span data-ttu-id="2a8e2-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2a8e2-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a8e2-130">EntrySelectedBy-element för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2a8e2-131">Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2a8e2-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2a8e2-132">Remarks</span></span>

<span data-ttu-id="2a8e2-133">lWhen du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="2a8e2-133">lWhen you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="2a8e2-134">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="2a8e2-135">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="2a8e2-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="2a8e2-136">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="2a8e2-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="2a8e2-137">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="2a8e2-137">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a8e2-138">Se även</span><span class="sxs-lookup"><span data-stu-id="2a8e2-138">See Also</span></span>

[<span data-ttu-id="2a8e2-139">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="2a8e2-139">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2a8e2-140">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="2a8e2-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="2a8e2-141">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-141">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="2a8e2-142">SelectionSetName-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-142">SelectionSetName Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="2a8e2-143">Elementet TypeName för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="2a8e2-143">TypeName Element for EntrySelectedBy for ListEntry (Format)</span></span>](/powershell/scripting/developer/format/typename-element-for-entryselectedby-for-listcontrol-format)

[<span data-ttu-id="2a8e2-144">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2a8e2-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
