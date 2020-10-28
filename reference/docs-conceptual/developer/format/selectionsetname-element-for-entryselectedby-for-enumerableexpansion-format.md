---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)
description: SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 074f810f5a3cbad61ee8be69408967758f0591df
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651886"
---
# <a name="selectionsetname-element-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="2a7d3-103">SelectionSetName-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2a7d3-103">SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="2a7d3-104">Anger den uppsättning av .NET-typer som expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-104">Specifies the set of .NET types that are expanded by this definition.</span></span>

<span data-ttu-id="2a7d3-105">Konfigurations element (format) DefaultSettings-element (format) EnumerableExpansions-element (format) EnumerableExpansion-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionSetName-element för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="2a7d3-105">Configuration Element (Format) DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansion Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionSetName Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2a7d3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2a7d3-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="2a7d3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2a7d3-107">Attributes and Elements</span></span>

<span data-ttu-id="2a7d3-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2a7d3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2a7d3-109">Attributes</span></span>

<span data-ttu-id="2a7d3-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2a7d3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2a7d3-111">Child Elements</span></span>

<span data-ttu-id="2a7d3-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2a7d3-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2a7d3-113">Parent Elements</span></span>

|<span data-ttu-id="2a7d3-114">Element</span><span class="sxs-lookup"><span data-stu-id="2a7d3-114">Element</span></span>|<span data-ttu-id="2a7d3-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2a7d3-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2a7d3-116">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2a7d3-116">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)|<span data-ttu-id="2a7d3-117">Definierar de .NET-samlings objekt som ska expanderas av den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-117">Defines the .NET collection objects that are expanded by this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2a7d3-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2a7d3-118">Text Value</span></span>

<span data-ttu-id="2a7d3-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="2a7d3-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2a7d3-120">Remarks</span></span>

<span data-ttu-id="2a7d3-121">Varje definition måste ange ett eller flera typnamn, en markerings uppsättning eller ett markerings villkor.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-121">Each definition must specify one or more type names, a selection set, or a selection condition.</span></span>

<span data-ttu-id="2a7d3-122">Urvals uppsättningar används vanligt vis när du vill definiera en grupp objekt som används i flera vyer.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-122">Selection sets are typically used when you want to define a group of objects that are used in multiple views.</span></span> <span data-ttu-id="2a7d3-123">Du kanske till exempel vill skapa en tabellvy och en listvy för samma uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="2a7d3-123">For example, you might want to create a table view and a list view for the same set of objects.</span></span> <span data-ttu-id="2a7d3-124">Mer information om hur du definierar urvals uppsättningar finns i [definiera uppsättningar av objekt för en vy](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="2a7d3-124">For more information about defining selection sets, see [Defining Sets of Objects for a View](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="2a7d3-125">Se även</span><span class="sxs-lookup"><span data-stu-id="2a7d3-125">See Also</span></span>

[<span data-ttu-id="2a7d3-126">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="2a7d3-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="2a7d3-127">EntrySelectedBy-element för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="2a7d3-127">EntrySelectedBy Element for EnumerableExpansion (Format)</span></span>](./entryselectedby-element-for-enumerableexpansion-format.md)

[<span data-ttu-id="2a7d3-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2a7d3-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
