---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)
ms.openlocfilehash: f3193799e67706eb07f0fe1c2cd42cce83f7af57
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651535"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-listentry-format"></a><span data-ttu-id="a791b-103">SelectionSetName-element för SelectionCondition för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a791b-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

<span data-ttu-id="a791b-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a791b-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a791b-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="a791b-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the list view.</span></span>

<span data-ttu-id="a791b-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) EntrySelectedBy-element för ListEntry (format) SelectionCondition element for EntrySelectedBy for ListEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="a791b-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) EntrySelectedBy Element for ListEntry (Format) SelectionCondition Element for EntrySelectedBy for ListEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for ListEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a791b-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="a791b-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a791b-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a791b-108">Attributes and Elements</span></span>

<span data-ttu-id="a791b-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a791b-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a791b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="a791b-110">Attributes</span></span>

<span data-ttu-id="a791b-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a791b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a791b-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a791b-112">Child Elements</span></span>

<span data-ttu-id="a791b-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="a791b-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a791b-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a791b-114">Parent Elements</span></span>

|<span data-ttu-id="a791b-115">Element</span><span class="sxs-lookup"><span data-stu-id="a791b-115">Element</span></span>|<span data-ttu-id="a791b-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a791b-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a791b-117">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a791b-117">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)|<span data-ttu-id="a791b-118">Definierar det villkor som måste finnas för att använda den här definitionen av listvyn.</span><span class="sxs-lookup"><span data-stu-id="a791b-118">Defines the condition that must exist to use this definition of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a791b-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a791b-119">Text Value</span></span>

<span data-ttu-id="a791b-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="a791b-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a791b-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a791b-121">Remarks</span></span>

<span data-ttu-id="a791b-122">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="a791b-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a791b-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a791b-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a791b-124">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="a791b-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a791b-125">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a791b-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a791b-126">Mer information om andra komponenter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a791b-126">For more information about other components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a791b-127">Se även</span><span class="sxs-lookup"><span data-stu-id="a791b-127">See Also</span></span>

[<span data-ttu-id="a791b-128">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="a791b-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a791b-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="a791b-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a791b-130">SelectionCondition-element för EntrySelectedBy för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a791b-130">SelectionCondition Element for EntrySelectedBy for ListEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-listcontrol-format.md)

[<span data-ttu-id="a791b-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a791b-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
