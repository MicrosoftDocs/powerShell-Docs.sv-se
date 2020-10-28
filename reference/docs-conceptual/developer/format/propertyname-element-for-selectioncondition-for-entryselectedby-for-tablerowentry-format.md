---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)
description: PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)
ms.openlocfilehash: dcb59fc438ae217870566f09204fb16b8f031614
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665795"
---
# <a name="propertyname-element-for-selectioncondition-for-entryselectedby-for-tablerowentry-format"></a><span data-ttu-id="c9225-103">PropertyName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c9225-103">PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

<span data-ttu-id="c9225-104">Anger den .NET-egenskap som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c9225-104">Specifies the .NET property that triggers the condition.</span></span> <span data-ttu-id="c9225-105">När den här egenskapen finns eller när den utvärderas `true` , uppfylls villkoret och tabell posten används.</span><span class="sxs-lookup"><span data-stu-id="c9225-105">When this property is present or when it evaluates to `true`, the condition is met, and the table entry is used.</span></span>

<span data-ttu-id="c9225-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy för TableRowEntry (format) PropertyName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="c9225-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) PropertyName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c9225-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c9225-107">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c9225-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c9225-108">Attributes and Elements</span></span>

<span data-ttu-id="c9225-109">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c9225-109">The following sections describe attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c9225-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c9225-110">Attributes</span></span>

<span data-ttu-id="c9225-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="c9225-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c9225-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c9225-112">Child Elements</span></span>

<span data-ttu-id="c9225-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="c9225-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c9225-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c9225-114">Parent Elements</span></span>

|<span data-ttu-id="c9225-115">Element</span><span class="sxs-lookup"><span data-stu-id="c9225-115">Element</span></span>|<span data-ttu-id="c9225-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c9225-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c9225-117">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c9225-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c9225-118">Definierar det villkor som måste finnas för att den här tabell posten ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c9225-118">Defines the condition that must exist for this table entry to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c9225-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c9225-119">Text Value</span></span>

<span data-ttu-id="c9225-120">Ange .NET-egenskaps namnet.</span><span class="sxs-lookup"><span data-stu-id="c9225-120">Specify the .NET property name.</span></span>

## <a name="remarks"></a><span data-ttu-id="c9225-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c9225-121">Remarks</span></span>

<span data-ttu-id="c9225-122">Urvals villkoret måste innehålla minst ett egenskaps namn eller ett skript block, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="c9225-122">The selection condition must specify at least one property name or a script block, but cannot specify both.</span></span> <span data-ttu-id="c9225-123">Mer information om hur urvals villkor kan användas finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c9225-123">For more information about how selection conditions can be used, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c9225-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c9225-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c9225-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c9225-125">See Also</span></span>

[<span data-ttu-id="c9225-126">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="c9225-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c9225-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="c9225-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="c9225-128">Script block-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c9225-128">ScriptBlock Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./scriptblock-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c9225-129">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="c9225-129">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c9225-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c9225-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
