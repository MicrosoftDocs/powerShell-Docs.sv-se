---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för ListEntry för ListControl (format)
description: EntrySelectedBy-element för ListEntry för ListControl (format)
ms.openlocfilehash: 1981c8fae65f494504d6cdd9f59337d555350b07
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652296"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="16d81-103">EntrySelectedBy-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-103">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="16d81-104">Definierar de .NET-typer som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="16d81-104">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="16d81-105">I de flesta fall behövs bara en definition för en listvy.</span><span class="sxs-lookup"><span data-stu-id="16d81-105">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="16d81-106">Du kan dock ange flera definitioner för listvyn om du vill använda samma listvy för att visa olika data för olika objekt.</span><span class="sxs-lookup"><span data-stu-id="16d81-106">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="16d81-107">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntry för ListControl (format) EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-107">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="16d81-108">Syntax</span><span class="sxs-lookup"><span data-stu-id="16d81-108">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="16d81-109">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="16d81-109">Attributes and Elements</span></span>

<span data-ttu-id="16d81-110">I följande avsnitt beskrivs attributen, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="16d81-110">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="16d81-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="16d81-111">Attributes</span></span>

<span data-ttu-id="16d81-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="16d81-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="16d81-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="16d81-113">Child Elements</span></span>

|<span data-ttu-id="16d81-114">Element</span><span class="sxs-lookup"><span data-stu-id="16d81-114">Element</span></span>|<span data-ttu-id="16d81-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="16d81-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16d81-116">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-116">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="16d81-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="16d81-117">Optional element.</span></span><br /><br /> <span data-ttu-id="16d81-118">Definierar det villkor som måste finnas för att den här List visnings definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="16d81-118">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="16d81-119">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-119">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="16d81-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="16d81-120">Optional element.</span></span><br /><br /> <span data-ttu-id="16d81-121">Anger en uppsättning av .NET-typer som använder den här List vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="16d81-121">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="16d81-122">TypeName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-122">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="16d81-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="16d81-123">Optional element.</span></span><br /><br /> <span data-ttu-id="16d81-124">Anger en .NET-typ som använder den här List vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="16d81-124">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="16d81-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="16d81-125">Parent Elements</span></span>

|<span data-ttu-id="16d81-126">Element</span><span class="sxs-lookup"><span data-stu-id="16d81-126">Element</span></span>|<span data-ttu-id="16d81-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="16d81-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="16d81-128">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="16d81-129">Definierar hur rader i listan visas.</span><span class="sxs-lookup"><span data-stu-id="16d81-129">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="16d81-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="16d81-130">Remarks</span></span>

<span data-ttu-id="16d81-131">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en lista med en listvy.</span><span class="sxs-lookup"><span data-stu-id="16d81-131">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="16d81-132">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="16d81-132">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="16d81-133">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="16d81-133">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="16d81-134">Mer information om urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="16d81-134">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="16d81-135">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="16d81-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="16d81-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="16d81-136">Example</span></span>

<span data-ttu-id="16d81-137">I följande exempel visas hur du definierar objekten för en listvy med deras .NET-typnamn.</span><span class="sxs-lookup"><span data-stu-id="16d81-137">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="16d81-138">Se även</span><span class="sxs-lookup"><span data-stu-id="16d81-138">See Also</span></span>

[<span data-ttu-id="16d81-139">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-139">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="16d81-140">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-140">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="16d81-141">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-141">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="16d81-142">TypeName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="16d81-142">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="16d81-143">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="16d81-143">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="16d81-144">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="16d81-144">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="16d81-145">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="16d81-145">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
