---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)
description: ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)
ms.openlocfilehash: ec7691358d0ff3758411317a349221e1704a1895
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659905"
---
# <a name="scriptblock-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format"></a><span data-ttu-id="225d5-103">ScriptBlock-element för SelectionCondition för EntrySelectedBy för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-103">ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListControl (Format)</span></span>

<span data-ttu-id="225d5-104">Anger det skript som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="225d5-104">Specifies the script that triggers the condition.</span></span> <span data-ttu-id="225d5-105">När det här skriptet utvärderas `true` , uppfylls villkoret och list posten används.</span><span class="sxs-lookup"><span data-stu-id="225d5-105">When this script is evaluated to `true`, the condition is met, and the list entry is used.</span></span>

<span data-ttu-id="225d5-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) script block-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) ScriptBlock Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="225d5-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="225d5-107">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="225d5-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="225d5-108">Attributes and Elements</span></span>

<span data-ttu-id="225d5-109">I följande avsnitt beskrivs attribut, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="225d5-109">The following sections describe attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="225d5-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="225d5-110">Attributes</span></span>

<span data-ttu-id="225d5-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="225d5-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="225d5-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="225d5-112">Child Elements</span></span>

<span data-ttu-id="225d5-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="225d5-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="225d5-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="225d5-114">Parent Elements</span></span>

|<span data-ttu-id="225d5-115">Element</span><span class="sxs-lookup"><span data-stu-id="225d5-115">Element</span></span>|<span data-ttu-id="225d5-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="225d5-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="225d5-117">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="225d5-118">Definierar det villkor som måste finnas för att den här List posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="225d5-118">Defines the condition that must exist for this list entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="225d5-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="225d5-119">Text Value</span></span>

<span data-ttu-id="225d5-120">Ange det skript som utvärderas.</span><span class="sxs-lookup"><span data-stu-id="225d5-120">Specify the script that is evaluated.</span></span>

## <a name="remarks"></a><span data-ttu-id="225d5-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="225d5-121">Remarks</span></span>

<span data-ttu-id="225d5-122">Urvals villkoret måste ange minst ett skript eller egenskaps namn som ska utvärderas, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="225d5-122">The selection condition must specify a least one script or property name to evaluate, but cannot specify both.</span></span> <span data-ttu-id="225d5-123">(Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).)</span><span class="sxs-lookup"><span data-stu-id="225d5-123">(For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).)</span></span>

<span data-ttu-id="225d5-124">Mer information om de andra komponenterna i en listvy finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="225d5-124">For more information about the other components of a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="225d5-125">Se även</span><span class="sxs-lookup"><span data-stu-id="225d5-125">See Also</span></span>

[<span data-ttu-id="225d5-126">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-126">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="225d5-127">PropertyName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-127">PropertyName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>](./propertyname-element-for-selectioncondition-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="225d5-128">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="225d5-128">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="225d5-129">Listvy</span><span class="sxs-lookup"><span data-stu-id="225d5-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="225d5-130">Definiera villkor för när en visnings post eller ett objekt används</span><span class="sxs-lookup"><span data-stu-id="225d5-130">Defining Conditions for when a View Entry or Item is Used</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="225d5-131">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="225d5-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
