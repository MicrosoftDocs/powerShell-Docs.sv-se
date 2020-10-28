---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
description: PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)
ms.openlocfilehash: bda34b0c1e97fb85536132bedcec3986072801b7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665710"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-wideentry-format"></a><span data-ttu-id="92541-103">PropertyName-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="92541-103">PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

<span data-ttu-id="92541-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="92541-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="92541-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och definitionen används.</span><span class="sxs-lookup"><span data-stu-id="92541-105">When this property is present or when it evaluates to `true`, the condition is met, and the definition is used.</span></span>

<span data-ttu-id="92541-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) WideControl-element (format) WideEntries-element (format) WideEntry-element (format) EntrySelectedBy-element för WideEntry (format) SelectionCondition element for EntrySelectedBy för WideEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="92541-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) WideControl Element (Format) WideEntries Element (Format) WideEntry Element (Format) EntrySelectedBy Element for WideEntry (Format) SelectionCondition Element for EntrySelectedBy for WideEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92541-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="92541-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

```csharp

```

## <a name="attributes-and-elements"></a><span data-ttu-id="92541-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="92541-108">Attributes and Elements</span></span>

<span data-ttu-id="92541-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="92541-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92541-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="92541-110">Attributes</span></span>

<span data-ttu-id="92541-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="92541-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92541-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="92541-112">Child Elements</span></span>

<span data-ttu-id="92541-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="92541-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92541-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="92541-114">Parent Elements</span></span>

|<span data-ttu-id="92541-115">Element</span><span class="sxs-lookup"><span data-stu-id="92541-115">Element</span></span>|<span data-ttu-id="92541-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="92541-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92541-117">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="92541-117">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)|<span data-ttu-id="92541-118">Definierar det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="92541-118">Defines the condition that must exist for this definition to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92541-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="92541-119">Text Value</span></span>

<span data-ttu-id="92541-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="92541-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="92541-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="92541-121">Remarks</span></span>

<span data-ttu-id="92541-122">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="92541-122">The selection condition must specify at least one property name or a script to evaluate, but cannot specify both.</span></span> <span data-ttu-id="92541-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="92541-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="92541-124">Mer information om andra komponenter i en bred vy finns i [wide View](./creating-a-wide-view.md).</span><span class="sxs-lookup"><span data-stu-id="92541-124">For more information about other components of a wide view, see [Wide View](./creating-a-wide-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="92541-125">Se även</span><span class="sxs-lookup"><span data-stu-id="92541-125">See Also</span></span>

[<span data-ttu-id="92541-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="92541-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="92541-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="92541-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="92541-128">Script block-element för SelectionCondition för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="92541-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for WideEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="92541-129">SelectionCondition-element för EntrySelectedBy för WideEntry (format)</span><span class="sxs-lookup"><span data-stu-id="92541-129">SelectionCondition Element for EntrySelectedBy for WideEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-widecontrol-format.md)

[<span data-ttu-id="92541-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="92541-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
