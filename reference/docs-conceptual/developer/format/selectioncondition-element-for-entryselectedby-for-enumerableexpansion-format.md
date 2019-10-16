---
title: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8c012115-9241-4851-9015-841eb508faf3
caps.latest.revision: 10
ms.openlocfilehash: d6adf2fa62384d671fd6a07dd185a941daa44cec
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353832"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="b77ed-102">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="b77ed-103">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="b77ed-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="b77ed-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b77ed-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b77ed-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b77ed-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b77ed-106">Attributes and Elements</span></span>

<span data-ttu-id="b77ed-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet för elementet `SelectionCondition`.</span><span class="sxs-lookup"><span data-stu-id="b77ed-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="b77ed-108">Du måste ange ett enskilt `PropertyName`-eller `ScriptBlock`-element.</span><span class="sxs-lookup"><span data-stu-id="b77ed-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="b77ed-109">Elementen `SelectionSetName` och `TypeName` är valfria.</span><span class="sxs-lookup"><span data-stu-id="b77ed-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="b77ed-110">Du kan ange ett av båda elementen.</span><span class="sxs-lookup"><span data-stu-id="b77ed-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b77ed-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b77ed-111">Attributes</span></span>

<span data-ttu-id="b77ed-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b77ed-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b77ed-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b77ed-113">Child Elements</span></span>

|<span data-ttu-id="b77ed-114">Element</span><span class="sxs-lookup"><span data-stu-id="b77ed-114">Element</span></span>|<span data-ttu-id="b77ed-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b77ed-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b77ed-116">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b77ed-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b77ed-117">Optional element.</span></span><br /><br /> <span data-ttu-id="b77ed-118">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b77ed-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="b77ed-119">Script block-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b77ed-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b77ed-120">Optional element.</span></span><br /><br /> <span data-ttu-id="b77ed-121">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b77ed-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="b77ed-122">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b77ed-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b77ed-123">Optional element.</span></span><br /><br /> <span data-ttu-id="b77ed-124">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b77ed-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="b77ed-125">Elementet TypeName för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="b77ed-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b77ed-126">Optional element.</span></span><br /><br /> <span data-ttu-id="b77ed-127">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="b77ed-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b77ed-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b77ed-128">Parent Elements</span></span>

|<span data-ttu-id="b77ed-129">Element</span><span class="sxs-lookup"><span data-stu-id="b77ed-129">Element</span></span>|<span data-ttu-id="b77ed-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b77ed-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b77ed-131">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="b77ed-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="b77ed-132">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="b77ed-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b77ed-133">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b77ed-133">Remarks</span></span>

<span data-ttu-id="b77ed-134">Varje definition måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="b77ed-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="b77ed-135">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="b77ed-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="b77ed-136">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b77ed-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="b77ed-137">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="b77ed-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="b77ed-138">Mer information om hur du använder urvals villkor finns i [definiera villkor för Diplaying-data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="b77ed-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="b77ed-139">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="b77ed-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="b77ed-140">Se även</span><span class="sxs-lookup"><span data-stu-id="b77ed-140">See Also</span></span>

[<span data-ttu-id="b77ed-141">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="b77ed-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="b77ed-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="b77ed-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
