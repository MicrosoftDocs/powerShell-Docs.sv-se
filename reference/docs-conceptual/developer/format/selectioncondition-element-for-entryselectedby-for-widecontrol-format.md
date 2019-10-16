---
title: SelectionCondition-element för EntrySelectedBy för WideControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b7a9f086-b1ca-4400-9be7-9ec1ec8880f3
caps.latest.revision: 11
ms.openlocfilehash: f20679e3392b99a049c075f24c7712262bab08e1
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72355771"
---
# <a name="selectioncondition-element-for-entryselectedby-for-widecontrol-format"></a><span data-ttu-id="0f44f-102">SelectionCondition-element för EntrySelectedBy för WideControl (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-102">SelectionCondition Element for EntrySelectedBy for WideControl (Format)</span></span>

<span data-ttu-id="0f44f-103">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0f44f-103">Defines the condition that must exist for this definition to be used.</span></span> <span data-ttu-id="0f44f-104">Det finns ingen gräns för hur många urvals villkor som kan anges för en bred post definition.</span><span class="sxs-lookup"><span data-stu-id="0f44f-104">There is no limit to the number of selection conditions that can be specified for a wide entry definition.</span></span>

<span data-ttu-id="0f44f-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) WideControl-element (format) WideEntries-element (format) WideEntry element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0f44f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0f44f-106">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0f44f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0f44f-107">Attributes and Elements</span></span>

<span data-ttu-id="0f44f-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="0f44f-108">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="0f44f-109">Du måste ange ett enskilt `PropertyName`-eller `ScriptBlock`-element.</span><span class="sxs-lookup"><span data-stu-id="0f44f-109">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="0f44f-110">Elementen `SelectionSetName` och `TypeName` är valfria.</span><span class="sxs-lookup"><span data-stu-id="0f44f-110">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="0f44f-111">Du kan ange ett av båda elementen.</span><span class="sxs-lookup"><span data-stu-id="0f44f-111">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0f44f-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="0f44f-112">Attributes</span></span>

<span data-ttu-id="0f44f-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0f44f-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0f44f-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0f44f-114">Child Elements</span></span>

|<span data-ttu-id="0f44f-115">Element</span><span class="sxs-lookup"><span data-stu-id="0f44f-115">Element</span></span>|<span data-ttu-id="0f44f-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0f44f-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f44f-117">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-117">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0f44f-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0f44f-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0f44f-119">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0f44f-119">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="0f44f-120">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-120">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0f44f-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0f44f-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0f44f-122">Anger det skript block som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0f44f-122">Specifies the script block that triggers the condition.</span></span>|
|[<span data-ttu-id="0f44f-123">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-123">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)|<span data-ttu-id="0f44f-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0f44f-124">Optional element.</span></span><br /><br /> <span data-ttu-id="0f44f-125">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0f44f-125">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="0f44f-126">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-126">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="0f44f-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0f44f-127">Optional element.</span></span><br /><br /> <span data-ttu-id="0f44f-128">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="0f44f-128">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0f44f-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0f44f-129">Parent Elements</span></span>

|<span data-ttu-id="0f44f-130">Element</span><span class="sxs-lookup"><span data-stu-id="0f44f-130">Element</span></span>|<span data-ttu-id="0f44f-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0f44f-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0f44f-132">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-132">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)|<span data-ttu-id="0f44f-133">Definierar de .NET-typer som använder den här breda posten eller det villkor som måste finnas för att den här posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0f44f-133">Defines the .NET types that use this wide entry or the condition that must exist for this entry to be used.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0f44f-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0f44f-134">Remarks</span></span>

<span data-ttu-id="0f44f-135">Varje bred post måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="0f44f-135">Each wide entry must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="0f44f-136">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="0f44f-136">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="0f44f-137">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="0f44f-137">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="0f44f-138">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="0f44f-138">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="0f44f-139">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0f44f-139">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0f44f-140">Mer information om andra komponenter i en bred vy finns i [skapa en bred vy](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="0f44f-140">For more information about other components of a wide view, see [Creating a Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="0f44f-141">Se även</span><span class="sxs-lookup"><span data-stu-id="0f44f-141">See Also</span></span>

[<span data-ttu-id="0f44f-142">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="0f44f-142">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="0f44f-143">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="0f44f-143">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="0f44f-144">EntrySelectedBy-element för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-144">EntrySelectedBy Element for WideEntry (Format)</span></span>](./entryselectedby-element-for-wideentry-format.md)

[<span data-ttu-id="0f44f-145">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-145">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0f44f-146">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-146">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0f44f-147">SelectionSetName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-147">SelectionSetName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format.md)

[<span data-ttu-id="0f44f-148">Elementet TypeName för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0f44f-148">TypeName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="0f44f-149">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="0f44f-149">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
