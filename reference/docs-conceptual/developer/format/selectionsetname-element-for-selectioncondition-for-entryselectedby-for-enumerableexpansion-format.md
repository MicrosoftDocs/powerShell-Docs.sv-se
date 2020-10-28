---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)
ms.openlocfilehash: 0c9372113a79f75cfbda67acf869164fde894ee3
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651599"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="53d2c-103">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="53d2c-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="53d2c-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="53d2c-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="53d2c-105">När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.</span><span class="sxs-lookup"><span data-stu-id="53d2c-105">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="53d2c-106">DefaultSettings-element för konfigurations element (format) EnumerableExpansions-element (format) EnumerableExpansions-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="53d2c-106">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="53d2c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="53d2c-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="53d2c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="53d2c-108">Attributes and Elements</span></span>

<span data-ttu-id="53d2c-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="53d2c-109">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="53d2c-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="53d2c-110">Attributes</span></span>

<span data-ttu-id="53d2c-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="53d2c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="53d2c-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="53d2c-112">Child Elements</span></span>

<span data-ttu-id="53d2c-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="53d2c-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="53d2c-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="53d2c-114">Parent Elements</span></span>

|<span data-ttu-id="53d2c-115">Element</span><span class="sxs-lookup"><span data-stu-id="53d2c-115">Element</span></span>|<span data-ttu-id="53d2c-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="53d2c-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="53d2c-117">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="53d2c-117">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="53d2c-118">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="53d2c-118">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="53d2c-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="53d2c-119">Text Value</span></span>

<span data-ttu-id="53d2c-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="53d2c-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="53d2c-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="53d2c-121">Remarks</span></span>

<span data-ttu-id="53d2c-122">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="53d2c-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="53d2c-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="53d2c-123">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="53d2c-124">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="53d2c-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="53d2c-125">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="53d2c-125">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="53d2c-126">Se även</span><span class="sxs-lookup"><span data-stu-id="53d2c-126">See Also</span></span>

[<span data-ttu-id="53d2c-127">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="53d2c-127">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="53d2c-128">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="53d2c-128">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="53d2c-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="53d2c-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
