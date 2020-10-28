---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för Controls för View (format)
description: SelectionCondition-element för EntrySelectedBy för Controls för View (format)
ms.openlocfilehash: 16b048e73195b3d6168724714ff223851dc1b20b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664847"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="b862f-103">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-103">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="b862f-104">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b862f-104">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="b862f-105">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="b862f-105">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="b862f-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b862f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b862f-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b862f-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b862f-108">Attributes and Elements</span></span>

<span data-ttu-id="b862f-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b862f-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b862f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="b862f-110">Attributes</span></span>

<span data-ttu-id="b862f-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="b862f-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b862f-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b862f-112">Child Elements</span></span>

|<span data-ttu-id="b862f-113">Element</span><span class="sxs-lookup"><span data-stu-id="b862f-113">Element</span></span>|<span data-ttu-id="b862f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b862f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b862f-115">PropertyName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-115">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b862f-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b862f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="b862f-117">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b862f-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b862f-118">ScriptBlock-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-118">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b862f-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b862f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="b862f-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b862f-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b862f-121">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-121">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b862f-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b862f-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b862f-123">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b862f-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="b862f-124">TypeName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-124">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="b862f-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b862f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="b862f-126">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b862f-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b862f-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b862f-127">Parent Elements</span></span>

|<span data-ttu-id="b862f-128">Element</span><span class="sxs-lookup"><span data-stu-id="b862f-128">Element</span></span>|<span data-ttu-id="b862f-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b862f-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b862f-130">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-130">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="b862f-131">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="b862f-131">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b862f-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b862f-132">Remarks</span></span>

<span data-ttu-id="b862f-133">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="b862f-133">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b862f-134">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b862f-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b862f-135">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b862f-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b862f-136">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b862f-136">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b862f-137">Se även</span><span class="sxs-lookup"><span data-stu-id="b862f-137">See Also</span></span>

[<span data-ttu-id="b862f-138">PropertyName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-138">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b862f-139">ScriptBlock-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-139">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b862f-140">SelectionSetName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-140">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b862f-141">TypeName-element för SelectionCondition för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-141">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="b862f-142">EntrySelectedBy-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="b862f-142">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="b862f-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b862f-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
