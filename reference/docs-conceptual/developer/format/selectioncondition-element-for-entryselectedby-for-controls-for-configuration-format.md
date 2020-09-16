---
title: SelectionCondition-element för EntrySelectedBy för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 748aa1aa0ba603a44334d9401e9e2c0e68f14e03
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783423"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-configuration-format"></a><span data-ttu-id="e5669-102">SelectionCondition-element för EntrySelectedBy för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-102">SelectionCondition Element for EntrySelectedBy for Controls for Configuration (Format)</span></span>

<span data-ttu-id="e5669-103">Definierar ett villkor som måste finnas för att en gemensam kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="e5669-103">Defines a condition that must exist for a common control definition to be used.</span></span> <span data-ttu-id="e5669-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="e5669-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="e5669-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Controls (format) CustomEntry-element för CustomControl för Controls (format) EntrySelectedBy-element för CustomEntry för Controls (format) SelectionCondition-element för EntrySelectedBy för CustomEntry för konfiguration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Controls for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format) SelectionCondition Element for EntrySelectedBy for CustomEntry for Configuration (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5669-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5669-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5669-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e5669-107">Attributes and Elements</span></span>

<span data-ttu-id="e5669-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e5669-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5669-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5669-109">Attributes</span></span>

<span data-ttu-id="e5669-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e5669-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5669-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e5669-111">Child Elements</span></span>

|<span data-ttu-id="e5669-112">Element</span><span class="sxs-lookup"><span data-stu-id="e5669-112">Element</span></span>|<span data-ttu-id="e5669-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5669-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5669-114">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-114">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e5669-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5669-115">Optional element.</span></span><br /><br /> <span data-ttu-id="e5669-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5669-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="e5669-117">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-117">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e5669-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5669-118">Optional element.</span></span><br /><br /> <span data-ttu-id="e5669-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5669-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="e5669-120">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-120">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e5669-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5669-121">Optional element.</span></span><br /><br /> <span data-ttu-id="e5669-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5669-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="e5669-123">TypeName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-123">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)|<span data-ttu-id="e5669-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e5669-124">Optional element.</span></span><br /><br /> <span data-ttu-id="e5669-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="e5669-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e5669-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e5669-126">Parent Elements</span></span>

|<span data-ttu-id="e5669-127">Element</span><span class="sxs-lookup"><span data-stu-id="e5669-127">Element</span></span>|<span data-ttu-id="e5669-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5669-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5669-129">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-129">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)|<span data-ttu-id="e5669-130">Definierar de .NET-typer som använder den här posten i common Control definition.</span><span class="sxs-lookup"><span data-stu-id="e5669-130">Defines the .NET types that use this entry of the common control definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e5669-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e5669-131">Remarks</span></span>

<span data-ttu-id="e5669-132">Följande rikt linjer måste följas när du definierar ett urvals villkor:</span><span class="sxs-lookup"><span data-stu-id="e5669-132">The following guidelines must be followed when defining a selection condition:</span></span>

- <span data-ttu-id="e5669-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e5669-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="e5669-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="e5669-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="e5669-135">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="e5669-135">For more information about how selection conditions can be used, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="e5669-136">Se även</span><span class="sxs-lookup"><span data-stu-id="e5669-136">See Also</span></span>

[<span data-ttu-id="e5669-137">PropertyName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-137">PropertyName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5669-138">ScriptBlock-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-138">ScriptBlock Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5669-139">SelectionSetName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-139">SelectionSetName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5669-140">TypeName-element för SelectionCondition för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-140">TypeName Element for SelectionCondition for Controls for Configuration (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5669-141">EntrySelectedBy-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="e5669-141">EntrySelectedBy Element for CustomEntry for Controls for Configuration (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-configuration-format.md)

[<span data-ttu-id="e5669-142">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="e5669-142">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
