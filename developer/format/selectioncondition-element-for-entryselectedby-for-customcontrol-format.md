---
title: SelectionCondition Element för EntrySelectedBy för anpassad kontroll (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 231e9c6d-09ec-4e68-80ee-0c8f7fe1b9f5
caps.latest.revision: 7
ms.openlocfilehash: 49e2c0cf09dfa55b535effcd431e980daf12fac3
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075757"
---
# <a name="selectioncondition-element-for-entryselectedby-for-customcontrol-format"></a><span data-ttu-id="5ae7a-102">SelectionCondition-element för EntrySelectedBy för CustomControl (format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-102">SelectionCondition Element for EntrySelectedBy for CustomControl (Format)</span></span>

<span data-ttu-id="5ae7a-103">Definierar ett villkor som måste finnas en definition för kontrollen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-103">Defines a condition that must exist for a control definition to be used.</span></span> <span data-ttu-id="5ae7a-104">Det här elementet används när du definierar en anpassad kontroll vy.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-104">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="5ae7a-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) anpassad kontroll konfigurationselement för Visa (Format) CustomEntries elementet för anpassad kontroll för Visa (Format) CustomEntry elementet för CustomEntries för anpassad kontroll för Visa ( Format) CustomItem Element för CustomEntry för anpassad kontroll för Visa (Format) EntrySelectedBy elementet för CustomEntry för anpassad kontroll för Visa (Format) SelectionCondition elementet för EntrySelectedBy för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for CustomControl for View (Format) CustomItem Element for CustomEntry for CustomControl for View (Format) EntrySelectedBy Element for CustomEntry for CustomControl for View (Format) SelectionCondition Element for EntrySelectedBy for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ae7a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ae7a-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ae7a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5ae7a-107">Attributes and Elements</span></span>

<span data-ttu-id="5ae7a-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ae7a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ae7a-109">Attributes</span></span>

<span data-ttu-id="5ae7a-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ae7a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5ae7a-111">Child Elements</span></span>

|<span data-ttu-id="5ae7a-112">Element</span><span class="sxs-lookup"><span data-stu-id="5ae7a-112">Element</span></span>|<span data-ttu-id="5ae7a-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ae7a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ae7a-114">PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-114">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ae7a-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="5ae7a-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="5ae7a-117">ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-117">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ae7a-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-118">Optional element.</span></span><br /><br /> <span data-ttu-id="5ae7a-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="5ae7a-120">SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-120">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ae7a-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-121">Optional element.</span></span><br /><br /> <span data-ttu-id="5ae7a-122">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="5ae7a-123">TypeName-Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-123">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ae7a-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-124">Optional element.</span></span><br /><br /> <span data-ttu-id="5ae7a-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5ae7a-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5ae7a-126">Parent Elements</span></span>

|<span data-ttu-id="5ae7a-127">Element</span><span class="sxs-lookup"><span data-stu-id="5ae7a-127">Element</span></span>|<span data-ttu-id="5ae7a-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ae7a-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ae7a-129">EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-129">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)|<span data-ttu-id="5ae7a-130">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5ae7a-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5ae7a-131">Remarks</span></span>

<span data-ttu-id="5ae7a-132">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="5ae7a-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="5ae7a-133">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="5ae7a-134">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="5ae7a-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="5ae7a-135">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5ae7a-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5ae7a-136">Se även</span><span class="sxs-lookup"><span data-stu-id="5ae7a-136">See Also</span></span>

[<span data-ttu-id="5ae7a-137">PropertyName-Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-137">PropertyName Element for SelectionCondition for CustomControl for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ae7a-138">ScriptBlock Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-138">ScriptBlock Element for SelectionCondition for CustomControl for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ae7a-139">SelectionSetName Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-139">SelectionSetName Element for SelectionCondition for Custom Control for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ae7a-140">TypeName-Element för SelectionCondition för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-140">TypeName Element for SelectionCondition for CustomControl for View  (Format)</span></span>](./typename-element-for-selectioncondition-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ae7a-141">EntrySelectedBy Element för CustomEntry för anpassad kontroll för vy (Format)</span><span class="sxs-lookup"><span data-stu-id="5ae7a-141">EntrySelectedBy Element for CustomEntry for CustomControl for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-customcontrol-for-view-format.md)

[<span data-ttu-id="5ae7a-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="5ae7a-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
