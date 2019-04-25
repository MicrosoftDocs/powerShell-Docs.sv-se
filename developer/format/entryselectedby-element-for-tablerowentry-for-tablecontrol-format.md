---
title: EntrySelectedBy Element för TableRowEntry för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62066166"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="84245-102">EntrySelectedBy-element för TableRowEntry  för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="84245-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="84245-103">Definierar vilka typer av .NET som använder den här definitionen av tabellvyn eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="84245-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="84245-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84245-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="84245-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84245-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="84245-106">Attributes and Elements</span></span>

<span data-ttu-id="84245-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `EntrySelectedBy` element.</span><span class="sxs-lookup"><span data-stu-id="84245-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84245-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="84245-108">Attributes</span></span>

<span data-ttu-id="84245-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="84245-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84245-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="84245-110">Child Elements</span></span>

|<span data-ttu-id="84245-111">Element</span><span class="sxs-lookup"><span data-stu-id="84245-111">Element</span></span>|<span data-ttu-id="84245-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84245-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84245-113">SelectionCondition Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="84245-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="84245-114">Optional element.</span></span><br /><br /> <span data-ttu-id="84245-115">Definierar de villkor som måste finnas för den här tabellen vydefinitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="84245-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="84245-116">SelectionSetName Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="84245-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="84245-117">Optional element.</span></span><br /><br /> <span data-ttu-id="84245-118">Anger en uppsättning med .NET-typer som använder den här tabellen vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="84245-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="84245-119">TypeName-Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="84245-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="84245-120">Optional element.</span></span><br /><br /> <span data-ttu-id="84245-121">Anger ett .NET-typ som använder den här tabellen vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="84245-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="84245-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="84245-122">Parent Elements</span></span>

|<span data-ttu-id="84245-123">Element</span><span class="sxs-lookup"><span data-stu-id="84245-123">Element</span></span>|<span data-ttu-id="84245-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84245-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84245-125">TableRowEntry Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="84245-126">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="84245-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="84245-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="84245-127">Remarks</span></span>

<span data-ttu-id="84245-128">Du måste ange minst en typ, val av set eller urvalsvillkoret för en tabell vydefinitionen.</span><span class="sxs-lookup"><span data-stu-id="84245-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="84245-129">Det finns ingen högsta gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="84245-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="84245-130">Val av villkor används för att definiera ett villkor som måste finnas för definitionen som ska användas, till exempel när ett objekt har en specifik egenskap eller som en specifik egenskapsvärde eller ett skript som utvärderas till `true`.</span><span class="sxs-lookup"><span data-stu-id="84245-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="84245-131">Mer information om val av villkor finns i [definiera villkor för när en post i vyn eller objektet används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="84245-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="84245-132">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="84245-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="84245-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="84245-133">Example</span></span>

<span data-ttu-id="84245-134">I följande exempel visas en `TableRowEntry` element som används för att visa egenskaperna för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="84245-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntry>
  <EntrySelectedBy>
    <TypeName>System.Diagnostics.Process</TypeName>
  </EntrySelectedBy>
  <TableColumnItems>
    <TableColumnItem>
      <PropertyName>PropertyForFirstColumn</PropertyName>
    </TableColumnItem>
    <TableColumnItem>
      <PropertyName>PropertyForSecondColumn</PropertyName>
    </TableColumnItem>
  </TableColumnItems>
</TableRowEntry>
```

## <a name="see-also"></a><span data-ttu-id="84245-135">Se även</span><span class="sxs-lookup"><span data-stu-id="84245-135">See Also</span></span>

[<span data-ttu-id="84245-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="84245-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="84245-137">SelectionCondition Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="84245-138">SelectionSetName Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="84245-139">TableRowEntry Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="84245-140">TypeName-Element för EntrySelectedBy för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="84245-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="84245-141">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="84245-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
