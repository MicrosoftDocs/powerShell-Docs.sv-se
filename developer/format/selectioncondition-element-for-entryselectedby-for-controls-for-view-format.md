---
title: SelectionCondition Element för EntrySelectedBy för kontroller för att visa (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 2623407e-fa10-4d27-a804-204f6d50ef22
caps.latest.revision: 6
ms.openlocfilehash: ea15e647a9dd7a7064718a0c536c4a3178d62d95
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848225"
---
# <a name="selectioncondition-element-for-entryselectedby-for-controls-for-view-format"></a><span data-ttu-id="28145-102">SelectionCondition-element för EntrySelectedBy för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="28145-102">SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

<span data-ttu-id="28145-103">Definierar ett villkor som måste finnas för kontrolldefinition som ska användas.</span><span class="sxs-lookup"><span data-stu-id="28145-103">Defines a condition that must exist for the control definition to be used.</span></span> <span data-ttu-id="28145-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="28145-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="28145-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) kontroller Element (Format) kontroll konfigurationselement för kontroller för att visa (Format) anpassad kontroll Element för kontroll för kontroller för att visa (Format) CustomEntries Element för Anpassad kontroll för kontroller för att visa (Format) CustomEntry Element för CustomEntries för kontroller för att visa (Format) EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format) SelectionCondition Element för EntrySelectedBy för kontroller för att visa ( Format)</span><span class="sxs-lookup"><span data-stu-id="28145-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for Controls for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) EntrySelectedBy Element for CustomEntry for Controls for View (Format) SelectionCondition Element for EntrySelectedBy for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28145-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="28145-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="28145-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="28145-107">Attributes and Elements</span></span>

<span data-ttu-id="28145-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="28145-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="28145-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="28145-109">Attributes</span></span>

<span data-ttu-id="28145-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="28145-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28145-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="28145-111">Child Elements</span></span>

|<span data-ttu-id="28145-112">Element</span><span class="sxs-lookup"><span data-stu-id="28145-112">Element</span></span>|<span data-ttu-id="28145-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28145-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28145-114">PropertyName-Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-114">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="28145-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28145-115">Optional element.</span></span><br /><br /> <span data-ttu-id="28145-116">Anger en .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="28145-116">Specifies a .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="28145-117">ScriptBlock Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-117">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="28145-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28145-118">Optional element.</span></span><br /><br /> <span data-ttu-id="28145-119">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="28145-119">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="28145-120">SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-120">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="28145-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28145-121">Optional element.</span></span><br /><br /> <span data-ttu-id="28145-122">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="28145-122">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="28145-123">TypeName-Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-123">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)|<span data-ttu-id="28145-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28145-124">Optional element.</span></span><br /><br /> <span data-ttu-id="28145-125">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="28145-125">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="28145-126">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="28145-126">Parent Elements</span></span>

|<span data-ttu-id="28145-127">Element</span><span class="sxs-lookup"><span data-stu-id="28145-127">Element</span></span>|<span data-ttu-id="28145-128">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28145-128">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28145-129">EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-129">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)|<span data-ttu-id="28145-130">Definierar vilka typer av .NET som använder den här kontrollen definitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="28145-130">Defines the .NET types that use this control definition or the condition that must exist for this definition to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28145-131">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="28145-131">Remarks</span></span>

<span data-ttu-id="28145-132">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="28145-132">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="28145-133">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="28145-133">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="28145-134">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="28145-134">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="28145-135">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="28145-135">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="28145-136">Se även</span><span class="sxs-lookup"><span data-stu-id="28145-136">See Also</span></span>

[<span data-ttu-id="28145-137">PropertyName-Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-137">PropertyName Element for SelectionCondition for Controls for View (Format)</span></span>](./propertyname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="28145-138">ScriptBlock Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-138">ScriptBlock Element for SelectionCondition for Controls for View (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="28145-139">SelectionSetName Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-139">SelectionSetName Element for SelectionCondition for Controls for View (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="28145-140">TypeName-Element för SelectionCondition för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-140">TypeName Element for SelectionCondition for Controls for View (Format)</span></span>](./typename-element-for-selectioncondition-for-controls-for-view-format.md)

[<span data-ttu-id="28145-141">EntrySelectedBy Element för CustomEntry för kontroller för att visa (Format)</span><span class="sxs-lookup"><span data-stu-id="28145-141">EntrySelectedBy Element for CustomEntry for Controls for View (Format)</span></span>](./entryselectedby-element-for-customentry-for-controls-for-view-format.md)

[<span data-ttu-id="28145-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="28145-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
