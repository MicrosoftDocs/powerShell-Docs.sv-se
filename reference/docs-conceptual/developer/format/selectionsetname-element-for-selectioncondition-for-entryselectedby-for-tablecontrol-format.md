---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: db751c40b22db52985bc7cd9f8f4296a64a523f0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87787469"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="a77af-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="a77af-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="a77af-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="a77af-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="a77af-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="a77af-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="a77af-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition element for EntrySelectedBy for TableRowEntry (format) SelectionSetName-element för SelectionCondition för EntrySelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="a77af-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a77af-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a77af-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a77af-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a77af-107">Attributes and Elements</span></span>

<span data-ttu-id="a77af-108">I följande avsnitt beskrivs attribut, underordnade element och `SelectionSetName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a77af-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a77af-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a77af-109">Attributes</span></span>

<span data-ttu-id="a77af-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="a77af-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a77af-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a77af-111">Child Elements</span></span>

<span data-ttu-id="a77af-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="a77af-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a77af-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a77af-113">Parent Elements</span></span>

|<span data-ttu-id="a77af-114">Element</span><span class="sxs-lookup"><span data-stu-id="a77af-114">Element</span></span>|<span data-ttu-id="a77af-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a77af-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a77af-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a77af-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="a77af-117">Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="a77af-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a77af-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a77af-118">Text Value</span></span>

<span data-ttu-id="a77af-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="a77af-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="a77af-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a77af-120">Remarks</span></span>

<span data-ttu-id="a77af-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="a77af-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="a77af-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="a77af-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="a77af-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="a77af-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="a77af-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="a77af-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="a77af-125">Mer information om andra komponenter i en bred vy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a77af-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="a77af-126">Se även</span><span class="sxs-lookup"><span data-stu-id="a77af-126">See Also</span></span>

[<span data-ttu-id="a77af-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="a77af-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a77af-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="a77af-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="a77af-129">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a77af-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a77af-130">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="a77af-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="a77af-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a77af-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
