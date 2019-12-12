---
title: EntrySelectedBy-element för ListEntry för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f7a74e9-764d-46ce-ab8e-8b9314ce1659
caps.latest.revision: 12
ms.openlocfilehash: 442565d25f60ae8e04501f3f9ffba35d486fbc8a
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355106"
---
# <a name="entryselectedby-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="8e2cd-102">EntrySelectedBy-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-102">EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="8e2cd-103">Definierar de .NET-typer som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-103">Defines the .NET types that use this list view definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="8e2cd-104">I de flesta fall behövs bara en definition för en listvy.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-104">In most cases only one definition is needed for a list view.</span></span> <span data-ttu-id="8e2cd-105">Du kan dock ange flera definitioner för listvyn om du vill använda samma listvy för att visa olika data för olika objekt.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-105">However, you can provide multiple definitions for the list view if you want to use the same list view to display different data for different objects.</span></span>

<span data-ttu-id="8e2cd-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntry för ListControl (format) EntrySelectedBy-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntry for ListControl (Format) EntrySelectedBy Element for ListEntry for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e2cd-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e2cd-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e2cd-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8e2cd-108">Attributes and Elements</span></span>

<span data-ttu-id="8e2cd-109">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-109">The following sections describe the attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e2cd-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8e2cd-110">Attributes</span></span>

<span data-ttu-id="8e2cd-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e2cd-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8e2cd-112">Child Elements</span></span>

|<span data-ttu-id="8e2cd-113">Element</span><span class="sxs-lookup"><span data-stu-id="8e2cd-113">Element</span></span>|<span data-ttu-id="8e2cd-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e2cd-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e2cd-115">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-115">SelectionCondition Element for EntrySelectedBy for ListControl  (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e2cd-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8e2cd-117">Definierar det villkor som måste finnas för att den här List visnings definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-117">Defines the condition that must exist for this list view definition to be used.</span></span>|
|[<span data-ttu-id="8e2cd-118">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-118">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e2cd-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8e2cd-120">Anger en uppsättning av .NET-typer som använder den här List vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-120">Specifies a set of .NET types that use this list view definition.</span></span>|
|[<span data-ttu-id="8e2cd-121">Elementet TypeName för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-121">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="8e2cd-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-122">Optional element.</span></span><br /><br /> <span data-ttu-id="8e2cd-123">Anger en .NET-typ som använder den här List vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-123">Specifies a .NET type that uses this list view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e2cd-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8e2cd-124">Parent Elements</span></span>

|<span data-ttu-id="8e2cd-125">Element</span><span class="sxs-lookup"><span data-stu-id="8e2cd-125">Element</span></span>|<span data-ttu-id="8e2cd-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e2cd-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e2cd-127">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-127">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="8e2cd-128">Definierar hur rader i listan visas.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-128">Defines how the rows of the list are displayed.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e2cd-129">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8e2cd-129">Remarks</span></span>

<span data-ttu-id="8e2cd-130">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en lista med en listvy.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-130">You must specify at least one type, selection set, or selection condition for a list view definition.</span></span> <span data-ttu-id="8e2cd-131">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-131">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="8e2cd-132">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="8e2cd-133">Mer information om urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="8e2cd-133">For more information about selection conditions, see [Defining Conditions for when Data is displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="8e2cd-134">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8e2cd-134">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8e2cd-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="8e2cd-135">Example</span></span>

<span data-ttu-id="8e2cd-136">I följande exempel visas hur du definierar objekten för en listvy med deras .NET-typnamn.</span><span class="sxs-lookup"><span data-stu-id="8e2cd-136">The following example shows how to define the objects for a list view using their .NET type name.</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>
    <TypeName>NameofDotNetType</TypeName>>
  </EntrySelectedBy>
</ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="8e2cd-137">Se även</span><span class="sxs-lookup"><span data-stu-id="8e2cd-137">See Also</span></span>

[<span data-ttu-id="8e2cd-138">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-138">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8e2cd-139">SelectionCondition-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-139">SelectionCondition Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8e2cd-140">SelectionSetName-element för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-140">SelectionSetName Element for EntrySelectedBy for ListControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8e2cd-141">Elementet TypeName för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8e2cd-141">TypeName Element for EntrySelectedBy for ListControl (Format)</span></span>](./typename-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="8e2cd-142">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="8e2cd-142">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8e2cd-143">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="8e2cd-143">Defining Conditions for when Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="8e2cd-144">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="8e2cd-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
