---
title: SelectionCondition-element för EntrySelectedBy för CustomControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 52858dba5c7a5222b5410835f3374546ce8b88a2
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785361"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="076ae-102">SelectionCondition-element för EntrySelectedBy för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="076ae-103">Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="076ae-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="076ae-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="076ae-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="076ae-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för CustomControl för View (format) CustomItem-element för CustomEntry för CustomControl för View (format) EntrySelectedBy-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="076ae-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="076ae-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="076ae-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="076ae-107">Attributes and Elements</span></span>

<span data-ttu-id="076ae-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="076ae-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="076ae-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="076ae-109">Attributes</span></span>

<span data-ttu-id="076ae-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="076ae-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="076ae-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="076ae-111">Child Elements</span></span>

|<span data-ttu-id="076ae-112">Element</span><span class="sxs-lookup"><span data-stu-id="076ae-112">Element</span></span>|<span data-ttu-id="076ae-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="076ae-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="076ae-114">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="076ae-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="076ae-115">Optional element.</span></span><br /><br /> <span data-ttu-id="076ae-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="076ae-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="076ae-117">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="076ae-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="076ae-118">Optional element.</span></span><br /><br /> <span data-ttu-id="076ae-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="076ae-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="076ae-120">SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="076ae-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="076ae-121">Optional element.</span></span><br /><br /> <span data-ttu-id="076ae-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="076ae-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="076ae-123">TypeName-element för SelectionCondition för CustomControl för View  (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="076ae-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="076ae-124">Optional element.</span></span><br /><br /> <span data-ttu-id="076ae-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="076ae-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="076ae-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="076ae-126">Parent Elements</span></span>

|<span data-ttu-id="076ae-127">Element</span><span class="sxs-lookup"><span data-stu-id="076ae-127">Element</span></span>|<span data-ttu-id="076ae-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="076ae-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="076ae-129">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="076ae-130">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="076ae-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="076ae-131">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="076ae-131">Remarks</span></span>

<span data-ttu-id="076ae-132">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="076ae-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="076ae-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="076ae-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="076ae-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="076ae-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="076ae-135">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="076ae-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="076ae-136">Se även</span><span class="sxs-lookup"><span data-stu-id="076ae-136">See Also</span></span>

[<span data-ttu-id="076ae-137">PropertyName-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="076ae-138">ScriptBlock-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="076ae-139">SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="076ae-140">TypeName-element för SelectionCondition för CustomControl för View  (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="076ae-141">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="076ae-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="076ae-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="076ae-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
