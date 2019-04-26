---
title: SelectionSetName Element för SelectionCondition för EntrySelectedBy för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 17ae4d6b-dc95-4a1d-8e32-31ff084a951f
caps.latest.revision: 10
ms.openlocfilehash: edb163f2b0b5129bd741677dce882888d9bbfd89
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064058"
---
# <a name="selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="5b554-102">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="5b554-102">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="5b554-103">Anger uppsättningen med .NET-typer som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="5b554-103">Specifies the set of .NET types that trigger the condition.</span></span> <span data-ttu-id="5b554-104">När någon av typerna i den här uppsättningen finns villkoret uppfylls och objektet visas med hjälp av den här definitionen av tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="5b554-104">When any of the types in this set are present, the condition is met, and the object is displayed by using this definition of the table view.</span></span>

<span data-ttu-id="5b554-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement för TableRowEntry (Format) SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format) SelectionSetName elementet för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5b554-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5b554-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="5b554-106">Syntax</span></span>

```xml
<SelectionSetName>NameofSelectionSet</SelectionSetName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5b554-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5b554-107">Attributes and Elements</span></span>

<span data-ttu-id="5b554-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `SelectionSetName` element.</span><span class="sxs-lookup"><span data-stu-id="5b554-108">The following sections describe attributes, child elements, and the parent element of the `SelectionSetName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5b554-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5b554-109">Attributes</span></span>

<span data-ttu-id="5b554-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b554-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5b554-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5b554-111">Child Elements</span></span>

<span data-ttu-id="5b554-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5b554-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5b554-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5b554-113">Parent Elements</span></span>

|<span data-ttu-id="5b554-114">Element</span><span class="sxs-lookup"><span data-stu-id="5b554-114">Element</span></span>|<span data-ttu-id="5b554-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5b554-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5b554-116">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5b554-116">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="5b554-117">Definierar de villkor som måste finnas för att använda för den här definitionen av tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="5b554-117">Defines the condition that must exist to use for this definition of the table view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5b554-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="5b554-118">Text Value</span></span>

<span data-ttu-id="5b554-119">Ange namnet på val av uppsättningen.</span><span class="sxs-lookup"><span data-stu-id="5b554-119">Specify the name of the selection set.</span></span>

## <a name="remarks"></a><span data-ttu-id="5b554-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5b554-120">Remarks</span></span>

<span data-ttu-id="5b554-121">Urvalsvillkoret kan ange en uppsättning för val av eller en .NET-typ, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="5b554-121">The selection condition can specify a selection set or .NET type, but cannot specify both.</span></span> <span data-ttu-id="5b554-122">Läs mer om hur du använder villkor för val av [definiera villkor för när Data visas](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="5b554-122">For more information about how to use selection conditions, see [Defining Conditions for when Data is Displayed](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="5b554-123">Val av som är vanliga grupper av .NET-objekt som kan användas av en vy som definierar filen formatering.</span><span class="sxs-lookup"><span data-stu-id="5b554-123">Selection sets are common groups of .NET objects that can be used by any view that the formatting file defines.</span></span> <span data-ttu-id="5b554-124">Läs mer om att skapa och refererar till val av uppsättningar [definiera anger av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="5b554-124">For more information about creating and referencing selection sets, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

<span data-ttu-id="5b554-125">Mer information om andra komponenter för en bred vy finns i [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5b554-125">For more information about other components of a wide view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="5b554-126">Se även</span><span class="sxs-lookup"><span data-stu-id="5b554-126">See Also</span></span>

[<span data-ttu-id="5b554-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="5b554-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5b554-128">Definiera villkor för när Data visas</span><span class="sxs-lookup"><span data-stu-id="5b554-128">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="5b554-129">TypeName-Element för SelectionCondition för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5b554-129">TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5b554-130">SelectionCondition Element för EntrySelectedBy för TableRowEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="5b554-130">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="5b554-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="5b554-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
