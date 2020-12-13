---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
description: PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 8e28118894661b50e90a5ccc86a36fbbe77e4b03
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665846"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7b5de-103">PropertyName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7b5de-103">PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7b5de-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7b5de-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="7b5de-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="7b5de-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="7b5de-106">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="7b5de-106">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b5de-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b5de-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b5de-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7b5de-108">Attributes and Elements</span></span>

<span data-ttu-id="7b5de-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7b5de-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b5de-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7b5de-110">Attributes</span></span>

<span data-ttu-id="7b5de-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="7b5de-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b5de-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7b5de-112">Child Elements</span></span>

<span data-ttu-id="7b5de-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="7b5de-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7b5de-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7b5de-114">Parent Elements</span></span>

|<span data-ttu-id="7b5de-115">Element</span><span class="sxs-lookup"><span data-stu-id="7b5de-115">Element</span></span>|<span data-ttu-id="7b5de-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7b5de-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b5de-117">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7b5de-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7b5de-118">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="7b5de-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7b5de-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="7b5de-119">Text Value</span></span>

<span data-ttu-id="7b5de-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="7b5de-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="7b5de-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7b5de-121">Remarks</span></span>

<span data-ttu-id="7b5de-122">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="7b5de-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="7b5de-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7b5de-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7b5de-124">Se även</span><span class="sxs-lookup"><span data-stu-id="7b5de-124">See Also</span></span>

[<span data-ttu-id="7b5de-125">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="7b5de-125">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="7b5de-126">ScriptBlock-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7b5de-126">ScriptBlock Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7b5de-127">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7b5de-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7b5de-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7b5de-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
