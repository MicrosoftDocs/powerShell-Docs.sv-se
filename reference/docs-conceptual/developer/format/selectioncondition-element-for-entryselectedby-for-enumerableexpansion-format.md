---
title: SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d5858145e092dc962174a776889a4f62db366d71
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785344"
---
# <a name="selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7e353-102">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-102">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7e353-103">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="7e353-103">Defines the condition that must exist to expand the collection objects of this definition.</span></span>

<span data-ttu-id="7e353-104">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-104">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7e353-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7e353-105">Syntax</span></span>

```xml
<SelectionCondition>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <PropertyName>.NetTypeProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</SelectionCondition>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7e353-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7e353-106">Attributes and Elements</span></span>

<span data-ttu-id="7e353-107">I följande avsnitt beskrivs attribut, underordnade element och `SelectionCondition` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7e353-107">The following sections describe attributes, child elements, and the parent element of the `SelectionCondition` element.</span></span> <span data-ttu-id="7e353-108">Du måste ange ett enskilt `PropertyName` eller- `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="7e353-108">You must specify a single `PropertyName` or `ScriptBlock` element.</span></span> <span data-ttu-id="7e353-109">`SelectionSetName` `TypeName` Elementen och är valfria.</span><span class="sxs-lookup"><span data-stu-id="7e353-109">The `SelectionSetName` and `TypeName` elements are optional.</span></span> <span data-ttu-id="7e353-110">Du kan ange ett av båda elementen.</span><span class="sxs-lookup"><span data-stu-id="7e353-110">You can specify one of either element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7e353-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="7e353-111">Attributes</span></span>

<span data-ttu-id="7e353-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="7e353-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7e353-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7e353-113">Child Elements</span></span>

|<span data-ttu-id="7e353-114">Element</span><span class="sxs-lookup"><span data-stu-id="7e353-114">Element</span></span>|<span data-ttu-id="7e353-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e353-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e353-116">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-116">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7e353-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7e353-117">Optional element.</span></span><br /><br /> <span data-ttu-id="7e353-118">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7e353-118">Specifies the .NET property that triggers the condition.</span></span>|
|[<span data-ttu-id="7e353-119">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-119">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7e353-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7e353-120">Optional element.</span></span><br /><br /> <span data-ttu-id="7e353-121">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7e353-121">Specifies the script that triggers the condition.</span></span>|
|[<span data-ttu-id="7e353-122">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-122">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7e353-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7e353-123">Optional element.</span></span><br /><br /> <span data-ttu-id="7e353-124">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7e353-124">Specifies the set of .NET types that triggers the condition.</span></span>|
|[<span data-ttu-id="7e353-125">TypeName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-125">TypeName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7e353-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7e353-126">Optional element.</span></span><br /><br /> <span data-ttu-id="7e353-127">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7e353-127">Specifies a .NET type that triggers the condition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7e353-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7e353-128">Parent Elements</span></span>

|<span data-ttu-id="7e353-129">Element</span><span class="sxs-lookup"><span data-stu-id="7e353-129">Element</span></span>|<span data-ttu-id="7e353-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7e353-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7e353-131">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7e353-131">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="7e353-132">Definierar vilka .NET-samlings objekt som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="7e353-132">Defines which .NET collection objects are expanded by this definition.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7e353-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7e353-133">Remarks</span></span>

<span data-ttu-id="7e353-134">Varje definition måste ha minst ett typ namn, en urvals uppsättning eller ett urvals villkor definierat.</span><span class="sxs-lookup"><span data-stu-id="7e353-134">Each definition must have at least one type name, selection set, or selection condition defined.</span></span>

<span data-ttu-id="7e353-135">När du definierar ett urvals villkor gäller följande krav:</span><span class="sxs-lookup"><span data-stu-id="7e353-135">When you are defining a selection condition, the following requirements apply:</span></span>

- <span data-ttu-id="7e353-136">Markerings villkoret måste ange minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="7e353-136">The selection condition must specify a least one property name or a script block, but cannot specify both.</span></span>

- <span data-ttu-id="7e353-137">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="7e353-137">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span>

<span data-ttu-id="7e353-138">Mer information om hur du använder urvals villkor finns i [definiera villkor för Diplaying-data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7e353-138">For more information about how to use selection conditions, see [Defining Conditions for Diplaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7e353-139">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="7e353-139">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7e353-140">Se även</span><span class="sxs-lookup"><span data-stu-id="7e353-140">See Also</span></span>

[<span data-ttu-id="7e353-141">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="7e353-141">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7e353-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7e353-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
