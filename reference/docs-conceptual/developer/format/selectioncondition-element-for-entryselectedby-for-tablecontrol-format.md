---
title: SelectionCondition-element för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 4a829f9daef22c4b3fd6b21dfb3af2f8539bdeb3
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780295"
---
# <a name="selectioncondition-element-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="e2204-102">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-102">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="e2204-103">Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="e2204-103">Defines the condition that must exist to use for this definition of the table view.</span></span> <span data-ttu-id="e2204-104">Det finns ingen gräns för antalet urvals villkor som kan anges för en tabell definition.</span><span class="sxs-lookup"><span data-stu-id="e2204-104">There is no limit to the number of selection conditions that can be specified for a table definition.</span></span>

<span data-ttu-id="e2204-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e2204-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e2204-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e2204-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e2204-107">Attributes and Elements</span></span>

<span data-ttu-id="e2204-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i SelectionCondition-elementet.</span><span class="sxs-lookup"><span data-stu-id="e2204-108">The following sections describe attributes, child elements, and the parent element of the SelectionCondition element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e2204-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e2204-109">Attributes</span></span>

<span data-ttu-id="e2204-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e2204-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e2204-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e2204-111">Child Elements</span></span>

|<span data-ttu-id="e2204-112">Element</span><span class="sxs-lookup"><span data-stu-id="e2204-112">Element</span></span>|<span data-ttu-id="e2204-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e2204-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2204-114">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-114">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)|<span data-ttu-id="e2204-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2204-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e2204-116">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e2204-116">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e2204-117">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-117">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e2204-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2204-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e2204-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e2204-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e2204-120">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-120">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e2204-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2204-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e2204-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e2204-122">Specifies the set of .NET types that trigger the condition.</span></span>|
|[<span data-ttu-id="e2204-123">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-123">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="e2204-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e2204-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e2204-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e2204-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e2204-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e2204-126">Parent Elements</span></span>

|<span data-ttu-id="e2204-127">Element</span><span class="sxs-lookup"><span data-stu-id="e2204-127">Element</span></span>|<span data-ttu-id="e2204-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e2204-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e2204-129">EntrySelectedBy-element för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-129">EntrySelectedBy Element for TableRowEntry (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="e2204-130">Definierar de .NET-typer som använder den här tabell posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e2204-130">Defines the .NET types that use this table entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e2204-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e2204-131">Remarks</span></span>

<span data-ttu-id="e2204-132">Varje List post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="e2204-132">Each list entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="e2204-133">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="e2204-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="e2204-134">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e2204-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e2204-135">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e2204-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e2204-136">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e2204-136">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="e2204-137">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e2204-137">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e2204-138">Se även</span><span class="sxs-lookup"><span data-stu-id="e2204-138">See Also</span></span>

[<span data-ttu-id="e2204-139">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="e2204-139">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e2204-140">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="e2204-140">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="e2204-141">EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-141">EntrySelectedBy Element (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="e2204-142">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-142">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format.md)

[<span data-ttu-id="e2204-143">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-143">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e2204-144">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-144">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e2204-145">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="e2204-145">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="e2204-146">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="e2204-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
