---
title: SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353769"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="38622-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="38622-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="38622-103">Anger den uppsättning av .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="38622-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="38622-104">När någon av typerna i den här uppsättningen finns, uppfylls villkoret och objektet visas med hjälp av den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="38622-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="38622-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) SelectionSetName-elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="38622-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="38622-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="38622-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="38622-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="38622-107">Attributes and Elements</span></span>

<span data-ttu-id="38622-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `SelectionSetName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="38622-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="38622-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="38622-109">Attributes</span></span>

<span data-ttu-id="38622-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="38622-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="38622-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="38622-111">Child Elements</span></span>

<span data-ttu-id="38622-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="38622-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="38622-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="38622-113">Parent Elements</span></span>

|<span data-ttu-id="38622-114">Element</span><span class="sxs-lookup"><span data-stu-id="38622-114">Element</span></span>|<span data-ttu-id="38622-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="38622-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="38622-116">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="38622-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="38622-117">Definierar det villkor som måste finnas för att användas för den här definitionen av tabellvy.</span><span class="sxs-lookup"><span data-stu-id="38622-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="38622-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="38622-118">Text Value</span></span>

<span data-ttu-id="38622-119">Ange namnet på urvals uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="38622-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="38622-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="38622-120">Remarks</span></span>

<span data-ttu-id="38622-121">Urvals villkoret kan ange en urvals uppsättning eller en .NET-typ, men det går inte att ange båda.</span><span class="sxs-lookup"><span data-stu-id="38622-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="38622-122">Mer information om hur du använder urvals villkor finns i [definiera villkor för när data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="38622-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="38622-123">Urvals uppsättningar är vanliga grupper av .NET-objekt som kan användas av alla vyer som format filen definierar.</span><span class="sxs-lookup"><span data-stu-id="38622-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="38622-124">Mer information om hur du skapar och refererar till urvals uppsättningar finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="38622-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="38622-125">Mer information om andra komponenter i en bred vy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="38622-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="38622-126">Se även</span><span class="sxs-lookup"><span data-stu-id="38622-126">See Also</span></span>

[<span data-ttu-id="38622-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="38622-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="38622-128">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="38622-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="38622-129">Elementet TypeName för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="38622-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="38622-130">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="38622-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="38622-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="38622-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
