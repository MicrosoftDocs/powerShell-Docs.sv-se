---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e18c74bb95c658f2c3e7b7454628f78d523f7609
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787503"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="581eb-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="581eb-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="581eb-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="581eb-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="581eb-104">När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.</span><span class="sxs-lookup"><span data-stu-id="581eb-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="581eb-105">DefaultSettings-element för konfigurations element (format) EnumerableExpansions-element (format) EnumerableExpansions-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="581eb-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="581eb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="581eb-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="581eb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="581eb-107">Attributes and Elements</span></span>

<span data-ttu-id="581eb-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="581eb-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="581eb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="581eb-109">Attributes</span></span>

<span data-ttu-id="581eb-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="581eb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="581eb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="581eb-111">Child Elements</span></span>

<span data-ttu-id="581eb-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="581eb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="581eb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="581eb-113">Parent Elements</span></span>

|<span data-ttu-id="581eb-114">Element</span><span class="sxs-lookup"><span data-stu-id="581eb-114">Element</span></span>|<span data-ttu-id="581eb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="581eb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="581eb-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="581eb-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="581eb-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="581eb-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="581eb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="581eb-118">Text Value</span></span>

<span data-ttu-id="581eb-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="581eb-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="581eb-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="581eb-120">Remarks</span></span>

<span data-ttu-id="581eb-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="581eb-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="581eb-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="581eb-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="581eb-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="581eb-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="581eb-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="581eb-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="581eb-125">Se även</span><span class="sxs-lookup"><span data-stu-id="581eb-125">See Also</span></span>

[<span data-ttu-id="581eb-126">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="581eb-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="581eb-127">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="581eb-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="581eb-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="581eb-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
