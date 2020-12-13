---
ms.date: 09/13/2016
ms.topic: reference
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
description: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: 2fb09e27eef1ce5d6e864c72edb595817d91f729
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92655042"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="ef56d-103">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef56d-103">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="ef56d-104">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="ef56d-104">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="ef56d-105">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="ef56d-105">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="ef56d-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy for TableRowEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ef56d-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef56d-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef56d-107">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef56d-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ef56d-108">Attributes and Elements</span></span>

<span data-ttu-id="ef56d-109">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ef56d-109">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef56d-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ef56d-110">Attributes</span></span>

<span data-ttu-id="ef56d-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="ef56d-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef56d-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ef56d-112">Child Elements</span></span>

<span data-ttu-id="ef56d-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="ef56d-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="ef56d-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ef56d-114">Parent Elements</span></span>

|<span data-ttu-id="ef56d-115">Element</span><span class="sxs-lookup"><span data-stu-id="ef56d-115">Element</span></span>|<span data-ttu-id="ef56d-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ef56d-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef56d-117">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ef56d-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="ef56d-118">Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="ef56d-118">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="ef56d-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="ef56d-119">Text Value</span></span>

<span data-ttu-id="ef56d-120">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="ef56d-120">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="ef56d-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ef56d-121">Remarks</span></span>

<span data-ttu-id="ef56d-122">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="ef56d-122">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="ef56d-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="ef56d-123">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="ef56d-124">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="ef56d-124">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="ef56d-125">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ef56d-125">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="ef56d-126">Mer information om andra komponenter i en bred vy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ef56d-126">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="ef56d-127">Se även</span><span class="sxs-lookup"><span data-stu-id="ef56d-127">See Also</span></span>

[<span data-ttu-id="ef56d-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="ef56d-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ef56d-129">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="ef56d-129">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="ef56d-130">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ef56d-130">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ef56d-131">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="ef56d-131">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="ef56d-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ef56d-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
