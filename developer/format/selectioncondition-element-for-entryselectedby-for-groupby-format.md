---
title: SelectionCondition Element för EntrySelectedBy för GroupBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6dc2093a-dc54-42c4-ada3-c8d089ba1e8e
caps.latest.revision: 6
ms.openlocfilehash: a6738a7c4c934b2d6a16695a711f7c6c80afdd2d
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075723"
---
# <a name="selectioncondition-element-for-entryselectedby-for-groupby-format"></a><span data-ttu-id="788a3-102">SelectionCondition-element för EntrySelectedBy för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="788a3-102">SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

<span data-ttu-id="788a3-103">Definierar ett villkor som måste finnas en definition för kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="788a3-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="788a3-104">Det här elementet används när du definierar hur en ny grupp med objekt visas.</span><span class="sxs-lookup"><span data-stu-id="788a3-104">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="788a3-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) GroupBy konfigurationselement för Visa (Format) anpassad kontroll elementet för GroupBy (Format) CustomEntries Element för anpassad kontroll för GroupBy (Format) CustomEntry elementet för Anpassad kontroll för GroupBy (Format) EntrySelectedBy elementet för CustomEntry för GroupBy (Format) SelectionCondition elementet för EntrySelectedBy för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomEntry Element for CustomControl for GroupBy (Format) EntrySelectedBy Element for CustomEntry for GroupBy (Format) SelectionCondition Element for EntrySelectedBy for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="788a3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="788a3-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="788a3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="788a3-107">Attributes and Elements</span></span>

<span data-ttu-id="788a3-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="788a3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="788a3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="788a3-109">Attributes</span></span>

<span data-ttu-id="788a3-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="788a3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="788a3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="788a3-111">Child Elements</span></span>

|<span data-ttu-id="788a3-112">Element</span><span class="sxs-lookup"><span data-stu-id="788a3-112">Element</span></span>|<span data-ttu-id="788a3-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="788a3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="788a3-114">PropertyName-Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-114">PropertyName Element for SelectionCondition for GroupBy (Format)</span></span>](./propertyname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="788a3-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="788a3-115">Optional element.</span></span><br /><br /> <span data-ttu-id="788a3-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="788a3-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="788a3-117">ScriptBlock Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-117">ScriptBlock Element for SelectionCondition for GroupBy (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-groupby-format.md)|<span data-ttu-id="788a3-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="788a3-118">Optional element.</span></span><br /><br /> <span data-ttu-id="788a3-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="788a3-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="788a3-120">SelectionSetName Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-120">SelectionSetName Element for SelectionCondition for GroupBy (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="788a3-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="788a3-121">Optional element.</span></span><br /><br /> <span data-ttu-id="788a3-122">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="788a3-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="788a3-123">TypeName-Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-123">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)|<span data-ttu-id="788a3-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="788a3-124">Optional element.</span></span><br /><br /> <span data-ttu-id="788a3-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="788a3-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="788a3-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="788a3-126">Parent Elements</span></span>

|<span data-ttu-id="788a3-127">Element</span><span class="sxs-lookup"><span data-stu-id="788a3-127">Element</span></span>|<span data-ttu-id="788a3-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="788a3-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="788a3-129">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-129">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)|<span data-ttu-id="788a3-130">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="788a3-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="788a3-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="788a3-131">Remarks</span></span>

<span data-ttu-id="788a3-132">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="788a3-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="788a3-133">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="788a3-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="788a3-134">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="788a3-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="788a3-135">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="788a3-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="788a3-136">Se även</span><span class="sxs-lookup"><span data-stu-id="788a3-136">See Also</span></span>

[<span data-ttu-id="788a3-137">PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="788a3-138">ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="788a3-139">SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="788a3-140">TypeName-Element för SelectionCondition för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-140">TypeName Element for SelectionCondition for GroupBy  (Format)</span></span>](./typename-element-for-selectioncondition-for-groupby-format.md)

[<span data-ttu-id="788a3-141">EntrySelectedBy Element för CustomEntry för GroupBy (Format)</span><span class="sxs-lookup"><span data-stu-id="788a3-141">EntrySelectedBy Element for CustomEntry for GroupBy (Format)</span></span>](./entryselectedby-element-for-customentry-for-groupby-format.md)

[<span data-ttu-id="788a3-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="788a3-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
