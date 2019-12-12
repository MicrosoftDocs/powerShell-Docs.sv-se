---
title: SelectionCondition-element för EntrySelectedBy för CustomControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358888"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="3d308-102">SelectionCondition-element för EntrySelectedBy för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="3d308-103">Definierar ett villkor som måste finnas för att en kontroll definition ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3d308-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="3d308-104">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="3d308-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="3d308-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element för View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View Format) CustomItem-element för CustomEntry för CustomControl för View (format) EntrySelectedBy-element för CustomEntry för CustomControl för View (format) SelectionCondition-element för EntrySelectedBy för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3d308-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="3d308-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3d308-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3d308-107">Attributes and Elements</span></span>

<span data-ttu-id="3d308-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="3d308-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3d308-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="3d308-109">Attributes</span></span>

<span data-ttu-id="3d308-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3d308-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3d308-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3d308-111">Child Elements</span></span>

|<span data-ttu-id="3d308-112">Element</span><span class="sxs-lookup"><span data-stu-id="3d308-112">Element</span></span>|<span data-ttu-id="3d308-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3d308-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d308-114">PropertyName-element för SelectionCondition för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3d308-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3d308-115">Optional element.</span></span><br /><br /> <span data-ttu-id="3d308-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3d308-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="3d308-117">Script block-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3d308-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3d308-118">Optional element.</span></span><br /><br /> <span data-ttu-id="3d308-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3d308-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="3d308-120">SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3d308-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3d308-121">Optional element.</span></span><br /><br /> <span data-ttu-id="3d308-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3d308-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="3d308-123">Elementet TypeName för SelectionCondition för CustomControl för vyn (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="3d308-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3d308-124">Optional element.</span></span><br /><br /> <span data-ttu-id="3d308-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="3d308-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3d308-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3d308-126">Parent Elements</span></span>

|<span data-ttu-id="3d308-127">Element</span><span class="sxs-lookup"><span data-stu-id="3d308-127">Element</span></span>|<span data-ttu-id="3d308-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3d308-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3d308-129">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="3d308-130">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3d308-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3d308-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3d308-131">Remarks</span></span>

<span data-ttu-id="3d308-132">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="3d308-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="3d308-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3d308-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="3d308-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="3d308-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="3d308-135">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="3d308-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="3d308-136">Se även</span><span class="sxs-lookup"><span data-stu-id="3d308-136">See Also</span></span>

[<span data-ttu-id="3d308-137">PropertyName-element för SelectionCondition för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3d308-138">Script block-element för SelectionCondition för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3d308-139">SelectionSetName-element för SelectionCondition för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3d308-140">Elementet TypeName för SelectionCondition för CustomControl för vyn (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3d308-141">EntrySelectedBy-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="3d308-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="3d308-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="3d308-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
