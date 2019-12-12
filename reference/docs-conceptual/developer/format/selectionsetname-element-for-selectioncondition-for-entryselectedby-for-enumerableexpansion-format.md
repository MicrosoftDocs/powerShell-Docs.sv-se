---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7b7af0b2-68e6-43c3-adcc-7c58007fced8
caps.latest.revision: 13
ms.openlocfilehash: 6f7c8d9af3c1c2fbda0208148b0088161701fdbe
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353818"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="c7b95-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="c7b95-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="c7b95-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="c7b95-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="c7b95-104">När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.</span><span class="sxs-lookup"><span data-stu-id="c7b95-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="c7b95-105">DefaultSettings-element för konfigurations element (format) EnumerableExpansions-element (format) EnumerableExpansions-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="c7b95-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7b95-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7b95-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7b95-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c7b95-107">Attributes and Elements</span></span>

<span data-ttu-id="c7b95-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="c7b95-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7b95-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c7b95-109">Attributes</span></span>

<span data-ttu-id="c7b95-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c7b95-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7b95-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c7b95-111">Child Elements</span></span>

<span data-ttu-id="c7b95-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c7b95-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c7b95-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c7b95-113">Parent Elements</span></span>

|<span data-ttu-id="c7b95-114">Element</span><span class="sxs-lookup"><span data-stu-id="c7b95-114">Element</span></span>|<span data-ttu-id="c7b95-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7b95-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7b95-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="c7b95-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="c7b95-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="c7b95-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c7b95-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c7b95-118">Text Value</span></span>

<span data-ttu-id="c7b95-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="c7b95-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="c7b95-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c7b95-120">Remarks</span></span>

<span data-ttu-id="c7b95-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="c7b95-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="c7b95-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c7b95-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c7b95-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="c7b95-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="c7b95-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="c7b95-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="c7b95-125">Se även</span><span class="sxs-lookup"><span data-stu-id="c7b95-125">See Also</span></span>

[<span data-ttu-id="c7b95-126">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="c7b95-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="c7b95-127">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="c7b95-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="c7b95-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c7b95-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
