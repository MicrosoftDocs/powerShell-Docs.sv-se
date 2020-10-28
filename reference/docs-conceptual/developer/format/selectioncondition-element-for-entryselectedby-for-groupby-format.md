---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för GroupBy (format)
description: SelectionCondition-element för EntrySelectedBy för GroupBy (format)
ms.openlocfilehash: 14c293b6bc6d6accc201de35be9219349079801d
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664757"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="6f5fa-103">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-103">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="6f5fa-104">Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-104">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="6f5fa-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="6f5fa-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for GroupBy (format) CustomEntry-element for CustomControl for groupby (format) EntrySelectedBy-element för CustomEntry (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6f5fa-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6f5fa-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6f5fa-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6f5fa-108">Attributes and Elements</span></span>

<span data-ttu-id="6f5fa-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="6f5fa-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="6f5fa-110">Attributes</span></span>

<span data-ttu-id="6f5fa-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6f5fa-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6f5fa-112">Child Elements</span></span>

|<span data-ttu-id="6f5fa-113">Element</span><span class="sxs-lookup"><span data-stu-id="6f5fa-113">Element</span></span>|<span data-ttu-id="6f5fa-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6f5fa-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f5fa-115">PropertyName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-115">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="6f5fa-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-116">Optional element.</span></span><br /><br /> <span data-ttu-id="6f5fa-117">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="6f5fa-118">Script block-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-118">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="6f5fa-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-119">Optional element.</span></span><br /><br /> <span data-ttu-id="6f5fa-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="6f5fa-121">SelectionSetName-element för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-121">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="6f5fa-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-122">Optional element.</span></span><br /><br /> <span data-ttu-id="6f5fa-123">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="6f5fa-124">Elementet TypeName för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-124">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="6f5fa-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-125">Optional element.</span></span><br /><br /> <span data-ttu-id="6f5fa-126">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6f5fa-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6f5fa-127">Parent Elements</span></span>

|<span data-ttu-id="6f5fa-128">Element</span><span class="sxs-lookup"><span data-stu-id="6f5fa-128">Element</span></span>|<span data-ttu-id="6f5fa-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6f5fa-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6f5fa-130">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-130">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="6f5fa-131">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6f5fa-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6f5fa-132">Remarks</span></span>

<span data-ttu-id="6f5fa-133">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="6f5fa-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="6f5fa-134">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="6f5fa-135">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="6f5fa-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="6f5fa-136">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="6f5fa-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="6f5fa-137">Se även</span><span class="sxs-lookup"><span data-stu-id="6f5fa-137">See Also</span></span>

[<span data-ttu-id="6f5fa-138">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-138">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6f5fa-139">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-139">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6f5fa-140">SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-140">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="6f5fa-141">Elementet TypeName för SelectionCondition för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-141">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="6f5fa-142">EntrySelectedBy-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="6f5fa-142">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="6f5fa-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6f5fa-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
