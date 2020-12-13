---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för TableControl (format)
description: SelectionCondition-element för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: 22f304615c6433ffb67f3b4046b645d0c37be8a4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645763"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="162e2-103">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-103">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="162e2-104">Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="162e2-104">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="162e2-105">Det finns ingen gräns för antalet urvals villkor som kan anges för en tabell definition.</span><span class="sxs-lookup"><span data-stu-id="162e2-105">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="162e2-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="162e2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="162e2-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="162e2-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="162e2-108">Attributes and Elements</span></span>

<span data-ttu-id="162e2-109">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i SelectionCondition-elementet.</span><span class="sxs-lookup"><span data-stu-id="162e2-109">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="162e2-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="162e2-110">Attributes</span></span>

<span data-ttu-id="162e2-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="162e2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="162e2-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="162e2-112">Child Elements</span></span>

|<span data-ttu-id="162e2-113">Element</span><span class="sxs-lookup"><span data-stu-id="162e2-113">Element</span></span>|<span data-ttu-id="162e2-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="162e2-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="162e2-115">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-115">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="162e2-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="162e2-116">Optional element.</span></span><br /><br /> <span data-ttu-id="162e2-117">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="162e2-117">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="162e2-118">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-118">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="162e2-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="162e2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="162e2-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="162e2-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="162e2-121">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-121">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="162e2-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="162e2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="162e2-123">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="162e2-123">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="162e2-124">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-124">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="162e2-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="162e2-125">Optional element.</span></span><br /><br /> <span data-ttu-id="162e2-126">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="162e2-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="162e2-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="162e2-127">Parent Elements</span></span>

|<span data-ttu-id="162e2-128">Element</span><span class="sxs-lookup"><span data-stu-id="162e2-128">Element</span></span>|<span data-ttu-id="162e2-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="162e2-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="162e2-130">EntrySelectedBy-element för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-130">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="162e2-131">Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="162e2-131">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="162e2-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="162e2-132">Remarks</span></span>

<span data-ttu-id="162e2-133">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="162e2-133">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="162e2-134">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="162e2-134">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="162e2-135">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="162e2-135">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="162e2-136">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="162e2-136">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="162e2-137">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="162e2-137">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="162e2-138">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="162e2-138">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="162e2-139">Se även</span><span class="sxs-lookup"><span data-stu-id="162e2-139">See Also</span></span>

[<span data-ttu-id="162e2-140">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="162e2-140">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="162e2-141">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="162e2-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="162e2-142">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-142">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="162e2-143">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-143">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="162e2-144">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-144">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="162e2-145">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-145">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="162e2-146">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="162e2-146">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="162e2-147">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="162e2-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
