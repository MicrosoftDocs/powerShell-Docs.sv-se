---
title: SelectionCondition-element för EntrySelectedBy för kontroller för vy (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353860"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="88b76-102">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="88b76-103">Definierar ett villkor som måste finnas för att den kontroll definition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="88b76-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="88b76-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="88b76-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="88b76-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) styr element (format) styr element (format) styr element för Controls (format) CustomControl-element för kontroll för Control for View (format) CustomEntries-element för CustomControl for Controls for View (format) CustomEntry-elementet för CustomEntries for Controls for View (format) EntrySelectedBy-elementet for CustomEntry for Controls for View (format) SelectionCondition element for EntrySelectedBy for Controls for View ( Formatering</span><span class="sxs-lookup"><span data-stu-id="88b76-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="88b76-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="88b76-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="88b76-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="88b76-107">Attributes and Elements</span></span>

<span data-ttu-id="88b76-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionCondition`-elementet.</span><span class="sxs-lookup"><span data-stu-id="88b76-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="88b76-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="88b76-109">Attributes</span></span>

<span data-ttu-id="88b76-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="88b76-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="88b76-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="88b76-111">Child Elements</span></span>

|<span data-ttu-id="88b76-112">Element</span><span class="sxs-lookup"><span data-stu-id="88b76-112">Element</span></span>|<span data-ttu-id="88b76-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88b76-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88b76-114">PropertyName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="88b76-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88b76-115">Optional element.</span></span><br /><br /> <span data-ttu-id="88b76-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="88b76-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="88b76-117">Script block-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="88b76-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88b76-118">Optional element.</span></span><br /><br /> <span data-ttu-id="88b76-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="88b76-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="88b76-120">SelectionSetName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="88b76-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88b76-121">Optional element.</span></span><br /><br /> <span data-ttu-id="88b76-122">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="88b76-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="88b76-123">Elementet TypeName för SelectionCondition för kontroller för vyn (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="88b76-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="88b76-124">Optional element.</span></span><br /><br /> <span data-ttu-id="88b76-125">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="88b76-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="88b76-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="88b76-126">Parent Elements</span></span>

|<span data-ttu-id="88b76-127">Element</span><span class="sxs-lookup"><span data-stu-id="88b76-127">Element</span></span>|<span data-ttu-id="88b76-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="88b76-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="88b76-129">EntrySelectedBy-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="88b76-130">Definierar de .NET-typer som använder den här kontroll definitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="88b76-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="88b76-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="88b76-131">Remarks</span></span>

<span data-ttu-id="88b76-132">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="88b76-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="88b76-133">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="88b76-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="88b76-134">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="88b76-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="88b76-135">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="88b76-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="88b76-136">Se även</span><span class="sxs-lookup"><span data-stu-id="88b76-136">See Also</span></span>

[<span data-ttu-id="88b76-137">PropertyName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="88b76-138">Script block-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="88b76-139">SelectionSetName-element för SelectionCondition för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="88b76-140">Elementet TypeName för SelectionCondition för kontroller för vyn (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="88b76-141">EntrySelectedBy-element för CustomEntry för kontroller för vy (format)</span><span class="sxs-lookup"><span data-stu-id="88b76-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="88b76-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="88b76-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
