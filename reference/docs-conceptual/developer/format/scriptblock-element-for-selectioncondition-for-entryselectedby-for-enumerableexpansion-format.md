---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: bd72a9bc914ea6543d8dab768b5e20e9a580ada7
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664902"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="77e4a-103">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="77e4a-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="77e4a-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="77e4a-104">Specifies the script that triggers the condition.</span></span>

<span data-ttu-id="77e4a-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="77e4a-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="77e4a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="77e4a-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="77e4a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="77e4a-107">Attributes and Elements</span></span>

<span data-ttu-id="77e4a-108">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="77e4a-108">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="77e4a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="77e4a-109">Attributes</span></span>

<span data-ttu-id="77e4a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="77e4a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="77e4a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="77e4a-111">Child Elements</span></span>

<span data-ttu-id="77e4a-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="77e4a-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="77e4a-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="77e4a-113">Parent Elements</span></span>

|<span data-ttu-id="77e4a-114">Element</span><span class="sxs-lookup"><span data-stu-id="77e4a-114">Element</span></span>|<span data-ttu-id="77e4a-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="77e4a-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="77e4a-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="77e4a-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="77e4a-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="77e4a-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="77e4a-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="77e4a-118">Text Value</span></span>

<span data-ttu-id="77e4a-119">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="77e4a-119">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="77e4a-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="77e4a-120">Remarks</span></span>

<span data-ttu-id="77e4a-121">Urvals villkoret måste innehålla minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="77e4a-121">The selection condition must specify at least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="77e4a-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="77e4a-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="77e4a-123">Se även</span><span class="sxs-lookup"><span data-stu-id="77e4a-123">See Also</span></span>

[<span data-ttu-id="77e4a-124">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="77e4a-124">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="77e4a-125">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="77e4a-125">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="77e4a-126">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="77e4a-126">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="77e4a-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="77e4a-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
