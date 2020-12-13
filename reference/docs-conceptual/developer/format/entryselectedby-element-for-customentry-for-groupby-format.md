---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för CustomEntry för GroupBy (format)
description: EntrySelectedBy-element för CustomEntry för GroupBy (format)
ms.openlocfilehash: 5af4abe081ca268699d281a1b586a584107b9a83
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92652366"
---
# <a name="entryselectedby-element-for-customentry-for-groupby-format"></a><span data-ttu-id="74229-103">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-103">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="74229-104">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="74229-104">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="74229-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="74229-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="74229-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry element for CustomControl for GroupBy (format) EntrySelectedBy-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="74229-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="74229-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="74229-107">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="74229-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="74229-108">Attributes and Elements</span></span>

<span data-ttu-id="74229-109">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="74229-109">The following sections describe attributes, child elements, and parent element of the `EntrySelectedBy` element.</span></span> <span data-ttu-id="74229-110">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en definition.</span><span class="sxs-lookup"><span data-stu-id="74229-110">You must specify at least one type, selection set, or selection condition for a definition.</span></span> <span data-ttu-id="74229-111">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="74229-111">There is no maximum limit to the number of child elements that you can use.</span></span>

### <a name="attributes"></a><span data-ttu-id="74229-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="74229-112">Attributes</span></span>

<span data-ttu-id="74229-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="74229-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="74229-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="74229-114">Child Elements</span></span>

|<span data-ttu-id="74229-115">Element</span><span class="sxs-lookup"><span data-stu-id="74229-115">Element</span></span>|<span data-ttu-id="74229-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74229-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74229-117">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-117">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="74229-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="74229-118">Optional element.</span></span><br /><br /> <span data-ttu-id="74229-119">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="74229-119">Defines the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="74229-120">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-120">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="74229-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="74229-121">Optional element.</span></span><br /><br /> <span data-ttu-id="74229-122">Anger en uppsättning av .NET-typer som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="74229-122">Specifies a set of .NET types that use this definition of the control.</span></span>|
|[<span data-ttu-id="74229-123">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-123">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="74229-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="74229-124">Optional element.</span></span><br /><br /> <span data-ttu-id="74229-125">Anger en .NET-typ som använder den här definitionen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="74229-125">Specifies a .NET type that uses this definition of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="74229-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="74229-126">Parent Elements</span></span>

|<span data-ttu-id="74229-127">Element</span><span class="sxs-lookup"><span data-stu-id="74229-127">Element</span></span>|<span data-ttu-id="74229-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="74229-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="74229-129">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-129">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="74229-130">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="74229-130">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="74229-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="74229-131">Remarks</span></span>

<span data-ttu-id="74229-132">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller när ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="74229-132">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or when a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="74229-133">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="74229-133">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="74229-134">Se även</span><span class="sxs-lookup"><span data-stu-id="74229-134">See Also</span></span>

[<span data-ttu-id="74229-135">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-135">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="74229-136">SelectionSetName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-136">SelectionSetName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="74229-137">TypeName-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="74229-137">TypeName Element for EntrySelectedBy for GroupBy (Format)</span></span>](./typename-element-for-entryselectedby-for-groupby-format.md)

[<span data-ttu-id="74229-138">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="74229-138">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)

[<span data-ttu-id="74229-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="74229-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
