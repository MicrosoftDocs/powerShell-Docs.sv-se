---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
description: TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)
ms.openlocfilehash: 66e90ab33775cf35d5e98e45266996d2d1a622d7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659634"
---
# <a name="typename-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format"></a><span data-ttu-id="58115-103">TypeName-element för SelectionCondition för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="58115-103">TypeName Element for SelectionCondition for EntrySelectedBy for TableControl (Format)</span></span>

<span data-ttu-id="58115-104">Anger en .NET-typ som utlöser villkoret.</span><span class="sxs-lookup"><span data-stu-id="58115-104">Specifies a .NET type that triggers the condition.</span></span> <span data-ttu-id="58115-105">När den här typen är närvarande uppfylls villkoret och tabell raden används.</span><span class="sxs-lookup"><span data-stu-id="58115-105">When this type is present, the condition is met, and the table row is used.</span></span>

<span data-ttu-id="58115-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element för TableRowEntry (format) SelectionCondition-element för EntrySelectedBy för TableRowEntry (format) element för SelectionCondition (format)</span><span class="sxs-lookup"><span data-stu-id="58115-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element for TableRowEntry (Format) SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format) TypeName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="58115-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="58115-107">Syntax</span></span>

```xml
<TypeName>Nameof.NetType</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="58115-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="58115-108">Attributes and Elements</span></span>

<span data-ttu-id="58115-109">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="58115-109">The following sections describe attributes, child elements, and the parent element of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="58115-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="58115-110">Attributes</span></span>

<span data-ttu-id="58115-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="58115-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="58115-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="58115-112">Child Elements</span></span>

<span data-ttu-id="58115-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="58115-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="58115-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="58115-114">Parent Elements</span></span>

|<span data-ttu-id="58115-115">Element</span><span class="sxs-lookup"><span data-stu-id="58115-115">Element</span></span>|<span data-ttu-id="58115-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="58115-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="58115-117">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="58115-117">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="58115-118">Definierar det villkor som måste finnas för att den här tabell raden ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="58115-118">Defines the condition that must exist for this table row to be used.</span></span>|

## <a name="text-value"></a><span data-ttu-id="58115-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="58115-119">Text Value</span></span>

<span data-ttu-id="58115-120">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="58115-120">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="58115-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="58115-121">Remarks</span></span>

<span data-ttu-id="58115-122">Urvals villkoret kan ange valfritt antal .NET-typer eller markerings uppsättningar, men kan inte ange båda.</span><span class="sxs-lookup"><span data-stu-id="58115-122">The selection condition can specify any number of .NET types or selection sets, but cannot specify both.</span></span> <span data-ttu-id="58115-123">Mer information om hur du använder urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="58115-123">For more information about how to use selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="58115-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="58115-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="58115-125">Se även</span><span class="sxs-lookup"><span data-stu-id="58115-125">See Also</span></span>

[<span data-ttu-id="58115-126">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="58115-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="58115-127">Definiera villkor för när data visas</span><span class="sxs-lookup"><span data-stu-id="58115-127">Defining Conditions for When Data Is Displayed</span></span>](./defining-conditions-for-displaying-data.md)

[<span data-ttu-id="58115-128">SelectionCondition-element för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="58115-128">SelectionCondition Element for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="58115-129">SelectionSetName-element för SelectionCondition för EntrySelectedBy för TableRowEntry (format)</span><span class="sxs-lookup"><span data-stu-id="58115-129">SelectionSetName Element for SelectionCondition for EntrySelectedBy for TableRowEntry (Format)</span></span>](./selectionsetname-element-for-selectioncondition-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="58115-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="58115-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
