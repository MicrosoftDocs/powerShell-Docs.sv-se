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
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353818"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-enumerableexpansion-format"></a><span data-ttu-id="7ce16-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7ce16-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

<span data-ttu-id="7ce16-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="7ce16-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="7ce16-104">När någon av typerna i den här uppsättningen är närvarande uppfylls villkoret.</span><span class="sxs-lookup"><span data-stu-id="7ce16-104">When any of the types in this set are present, the condition is met.</span></span>

<span data-ttu-id="7ce16-105">DefaultSettings-element för konfigurations element (format) EnumerableExpansions-element (format) EnumerableExpansions-element (format) EntrySelectedBy-element för EnumerableExpansion (format) SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7ce16-105">Configuration Element DefaultSettings Element (Format) EnumerableExpansions Element (Format) EnumerableExpansions Element (Format) EntrySelectedBy Element for EnumerableExpansion (Format) SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for EnumerableExpansion (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7ce16-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="7ce16-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7ce16-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7ce16-107">Attributes and Elements</span></span>

<span data-ttu-id="7ce16-108">I följande avsnitt beskrivs attribut, underordnade element och ett överordnat element för elementet `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="7ce16-108">The following sections describe attributes, child elements, and parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7ce16-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="7ce16-109">Attributes</span></span>

<span data-ttu-id="7ce16-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7ce16-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7ce16-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7ce16-111">Child Elements</span></span>

<span data-ttu-id="7ce16-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7ce16-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="7ce16-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7ce16-113">Parent Elements</span></span>

|<span data-ttu-id="7ce16-114">Element</span><span class="sxs-lookup"><span data-stu-id="7ce16-114">Element</span></span>|<span data-ttu-id="7ce16-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7ce16-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7ce16-116">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7ce16-116">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)|<span data-ttu-id="7ce16-117">Definierar det villkor som måste finnas för att expandera samlings objekt i den här definitionen.</span><span class="sxs-lookup"><span data-stu-id="7ce16-117">Defines the condition that must exist to expand the collection objects of this definition.</span></span>|

## <a name="text-value"></a><span data-ttu-id="7ce16-118">Text värde</span><span class="sxs-lookup"><span data-stu-id="7ce16-118">Text Value</span></span>

<span data-ttu-id="7ce16-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="7ce16-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="7ce16-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7ce16-120">Remarks</span></span>

<span data-ttu-id="7ce16-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="7ce16-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="7ce16-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för att visa data](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="7ce16-122">For more information about how to use selection conditions, see [Defining Conditions for Displaying Data](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="7ce16-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="7ce16-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="7ce16-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera urvals uppsättningar](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="7ce16-124">For more information about creating and referencing selection sets, see [Defining Selection Sets](./defining-selection-sets.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="7ce16-125">Se även</span><span class="sxs-lookup"><span data-stu-id="7ce16-125">See Also</span></span>

[<span data-ttu-id="7ce16-126">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="7ce16-126">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="7ce16-127">SelectionCondition-element för EntrySelectedBy för EnumerableExpansion (format)</span><span class="sxs-lookup"><span data-stu-id="7ce16-127">SelectionCondition Element for EntrySelectedBy for EnumerableExpansion (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-enumerableexpansion-format.md)

[<span data-ttu-id="7ce16-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="7ce16-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
