---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för WideEntry (format)
description: EntrySelectedBy-element för WideEntry (format)
ms.openlocfilehash: 246a1967300ab0551f376c4799deac275068308c
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92660244"
---
# <a name="entryselectedby-element-for-wideentry-format"></a><span data-ttu-id="47ea5-103">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-103">EntrySelectedBy Element for WideEntry (Format)</span></span>

<span data-ttu-id="47ea5-104">Definierar de .NET-typer som använder den här definitionen för wide View eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="47ea5-104">Defines the .NET types that use this definition of the wide view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="47ea5-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="47ea5-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="47ea5-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="47ea5-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="47ea5-107">Attributes and Elements</span></span>

<span data-ttu-id="47ea5-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="47ea5-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="47ea5-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="47ea5-109">Attributes</span></span>

<span data-ttu-id="47ea5-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="47ea5-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="47ea5-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="47ea5-111">Child Elements</span></span>

|<span data-ttu-id="47ea5-112">Element</span><span class="sxs-lookup"><span data-stu-id="47ea5-112">Element</span></span>|<span data-ttu-id="47ea5-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47ea5-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47ea5-114">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-114">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="47ea5-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47ea5-115">Optional element.</span></span><br /><br /> <span data-ttu-id="47ea5-116">Definierar det villkor som måste finnas för att denna wide View-definition ska användas.</span><span class="sxs-lookup"><span data-stu-id="47ea5-116">Defines the condition that must exist for this wide view definition to be used.</span></span>|
|[<span data-ttu-id="47ea5-117">SelectionSetName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-117">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="47ea5-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47ea5-118">Optional element.</span></span><br /><br /> <span data-ttu-id="47ea5-119">Anger en uppsättning av .NET-typer som använder denna wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="47ea5-119">Specifies a set of .NET types that use this wide view definition.</span></span>|
|[<span data-ttu-id="47ea5-120">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-120">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="47ea5-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="47ea5-121">Optional element.</span></span><br /><br /> <span data-ttu-id="47ea5-122">Anger en .NET-typ som använder denna wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="47ea5-122">Specifies a .NET type that uses this wide view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="47ea5-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="47ea5-123">Parent Elements</span></span>

|<span data-ttu-id="47ea5-124">Element</span><span class="sxs-lookup"><span data-stu-id="47ea5-124">Element</span></span>|<span data-ttu-id="47ea5-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="47ea5-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="47ea5-126">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-126">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)|<span data-ttu-id="47ea5-127">Ger en definition av den breda vyn.</span><span class="sxs-lookup"><span data-stu-id="47ea5-127">Provides a definition of the wide view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="47ea5-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="47ea5-128">Remarks</span></span>

<span data-ttu-id="47ea5-129">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en wide View-definition.</span><span class="sxs-lookup"><span data-stu-id="47ea5-129">You must specify at least one type, selection set, or selection condition for a wide view definition.</span></span> <span data-ttu-id="47ea5-130">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="47ea5-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="47ea5-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript värde utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="47ea5-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script value evaluates to `true`.</span></span> <span data-ttu-id="47ea5-132">Mer information om urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="47ea5-132">For more information about selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="47ea5-133">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="47ea5-133">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="47ea5-134">Se även</span><span class="sxs-lookup"><span data-stu-id="47ea5-134">See Also</span></span>

[<span data-ttu-id="47ea5-135">WideEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-135">WideEntry Element (Format)</span></span>](./wideentry-element-for-widecontrol-format.md)

[<span data-ttu-id="47ea5-136">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-136">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="47ea5-137">SelectionSetName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-137">SelectionSetName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="47ea5-138">TypeName-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="47ea5-138">TypeName Element for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="47ea5-139">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="47ea5-139">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="47ea5-140">Definiera villkor för datavisning</span><span class="sxs-lookup"><span data-stu-id="47ea5-140">Defining Conditions for Displaying Data</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="47ea5-141">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="47ea5-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
