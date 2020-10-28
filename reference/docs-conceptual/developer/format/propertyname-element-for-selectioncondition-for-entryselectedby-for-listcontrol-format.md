---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)
description: PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: 1e318e3a29f07b157b9ae7343ba08759db8efbb5
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665829"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="d1242-103">PropertyName-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="d1242-103">PropertyName Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="d1242-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="d1242-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="d1242-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och list posten används.</span><span class="sxs-lookup"><span data-stu-id="d1242-105">When this property is present or when it evaluates to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="d1242-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy för ListEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="d1242-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d1242-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="d1242-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d1242-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d1242-108">Attributes and Elements</span></span>

<span data-ttu-id="d1242-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d1242-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d1242-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="d1242-110">Attributes</span></span>

<span data-ttu-id="d1242-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="d1242-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d1242-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d1242-112">Child Elements</span></span>

<span data-ttu-id="d1242-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="d1242-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="d1242-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d1242-114">Parent Elements</span></span>

|<span data-ttu-id="d1242-115">Element</span><span class="sxs-lookup"><span data-stu-id="d1242-115">Element</span></span>|<span data-ttu-id="d1242-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d1242-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d1242-117">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d1242-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="d1242-118">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="d1242-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="d1242-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="d1242-119">Text Value</span></span>

<span data-ttu-id="d1242-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="d1242-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="d1242-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d1242-121">Remarks</span></span>

<span data-ttu-id="d1242-122">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="d1242-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="d1242-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="d1242-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="d1242-124">Mer information om andra komponenter i en listvy finns i [skapa listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="d1242-124">For more information about other components of a list view, see [Creating List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="d1242-125">Se även</span><span class="sxs-lookup"><span data-stu-id="d1242-125">See Also</span></span>

[<span data-ttu-id="d1242-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="d1242-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="d1242-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="d1242-127">Defining Conditions for When Data is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="d1242-128">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="d1242-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="d1242-129">Script block-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d1242-129">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="d1242-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d1242-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
