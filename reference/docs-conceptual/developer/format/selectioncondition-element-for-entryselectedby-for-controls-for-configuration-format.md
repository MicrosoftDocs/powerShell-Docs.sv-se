---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)
description: SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)
ms.openlocfilehash: ce00cdf868a3075875043aeb59f2cb8a17d049a9
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92645780"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="950bb-103">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-103">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="950bb-104">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="950bb-104">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="950bb-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="950bb-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="950bb-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för Controls (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="950bb-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="950bb-107">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="950bb-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="950bb-108">Attributes and Elements</span></span>

<span data-ttu-id="950bb-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="950bb-109">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="950bb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="950bb-110">Attributes</span></span>

<span data-ttu-id="950bb-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="950bb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="950bb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="950bb-112">Child Elements</span></span>

|<span data-ttu-id="950bb-113">Element</span><span class="sxs-lookup"><span data-stu-id="950bb-113">Element</span></span>|<span data-ttu-id="950bb-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="950bb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="950bb-115">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-115">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="950bb-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="950bb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="950bb-117">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="950bb-117">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="950bb-118">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-118">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="950bb-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="950bb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="950bb-120">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="950bb-120">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="950bb-121">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-121">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="950bb-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="950bb-122">Optional element.</span></span><br /><br /> <span data-ttu-id="950bb-123">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="950bb-123">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="950bb-124">TypeName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-124">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="950bb-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="950bb-125">Optional element.</span></span><br /><br /> <span data-ttu-id="950bb-126">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="950bb-126">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="950bb-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="950bb-127">Parent Elements</span></span>

|<span data-ttu-id="950bb-128">Element</span><span class="sxs-lookup"><span data-stu-id="950bb-128">Element</span></span>|<span data-ttu-id="950bb-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="950bb-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="950bb-130">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-130">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="950bb-131">Definierar de .NET-typer som använder den här posten i common Control definition.</span><span class="sxs-lookup"><span data-stu-id="950bb-131">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="950bb-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="950bb-132">Remarks</span></span>

<span data-ttu-id="950bb-133">Följande rikt linjer måste följas när du definierar ett urvals villkor:</span><span class="sxs-lookup"><span data-stu-id="950bb-133">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="950bb-134">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="950bb-134">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="950bb-135">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="950bb-135">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="950bb-136">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="950bb-136">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="950bb-137">Se även</span><span class="sxs-lookup"><span data-stu-id="950bb-137">See Also</span></span>

[<span data-ttu-id="950bb-138">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-138">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="950bb-139">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-139">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="950bb-140">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-140">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="950bb-141">TypeName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-141">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="950bb-142">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="950bb-142">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="950bb-143">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="950bb-143">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
