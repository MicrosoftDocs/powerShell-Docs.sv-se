---
title: SelectionCondition Element för EntrySelectedBy för WideControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845495"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="21554-102">SelectionCondition-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="21554-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="21554-103">Definierar de villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="21554-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="21554-104">Det finns ingen gräns för hur många val av villkor som kan anges för en bred post-definition.</span><span class="sxs-lookup"><span data-stu-id="21554-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="21554-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy konfigurationselement för WideEntry (Format) SelectionCondition elementet för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21554-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="21554-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21554-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="21554-107">Attributes and Elements</span></span>

<span data-ttu-id="21554-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionCondition` element.</span><span class="sxs-lookup"><span data-stu-id="21554-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="21554-109">Du måste ange en enda `PropertyName` eller `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="21554-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="21554-110">Den `SelectionSetName` och `TypeName` element är valfria.</span><span class="sxs-lookup"><span data-stu-id="21554-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="21554-111">Du kan ange en av antingen element.</span><span class="sxs-lookup"><span data-stu-id="21554-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="21554-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="21554-112">Attributes</span></span>

<span data-ttu-id="21554-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="21554-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21554-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="21554-114">Child Elements</span></span>

|<span data-ttu-id="21554-115">Element</span><span class="sxs-lookup"><span data-stu-id="21554-115">Element</span></span>|<span data-ttu-id="21554-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="21554-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21554-117">PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="21554-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21554-118">Optional element.</span></span><br /><br /> <span data-ttu-id="21554-119">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="21554-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="21554-120">ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="21554-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21554-121">Optional element.</span></span><br /><br /> <span data-ttu-id="21554-122">Anger skriptblocket som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="21554-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="21554-123">SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="21554-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21554-124">Optional element.</span></span><br /><br /> <span data-ttu-id="21554-125">Anger den uppsättning med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="21554-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="21554-126">TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="21554-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21554-127">Optional element.</span></span><br /><br /> <span data-ttu-id="21554-128">Anger ett .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="21554-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21554-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="21554-129">Parent Elements</span></span>

|<span data-ttu-id="21554-130">Element</span><span class="sxs-lookup"><span data-stu-id="21554-130">Element</span></span>|<span data-ttu-id="21554-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="21554-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21554-132">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="21554-133">Definierar vilka typer av .NET som använder den här wide posten eller villkor som måste finnas för den här posten som ska användas.</span><span class="sxs-lookup"><span data-stu-id="21554-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21554-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="21554-134">Remarks</span></span>

<span data-ttu-id="21554-135">Varje wide post måste ha minst ett namn, val av set eller Urvalsvillkoret som definierats.</span><span class="sxs-lookup"><span data-stu-id="21554-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="21554-136">När du definierar en urvalsvillkoret, gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="21554-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="21554-137">Urvalsvillkoret måste ange ett namn med minst en egenskap eller ett skriptblock, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="21554-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="21554-138">Urvalsvillkoret kan ange valfritt antal typer i .NET eller val av anger, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="21554-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="21554-139">Läs mer om hur du använder villkor för val av [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="21554-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="21554-140">Mer information om andra komponenter för en bred vy finns i [skapar en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="21554-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="21554-141">Se även</span><span class="sxs-lookup"><span data-stu-id="21554-141">See Also</span></span>

[<span data-ttu-id="21554-142">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="21554-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="21554-143">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="21554-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="21554-144">EntrySelectedBy Element för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="21554-145">PropertyName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="21554-146">ScriptBlock Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="21554-147">SelectionSetName Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="21554-148">TypeName-Element för SelectionCondition för EntrySelectedBy för WideEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="21554-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="21554-149">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="21554-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
