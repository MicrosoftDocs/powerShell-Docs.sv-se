---
ms.date: 09/13/2016
ms.topic: reference
title: EntrySelectedBy-element för TableRowEntry  för TableControl (format)
description: EntrySelectedBy-element för TableRowEntry  för TableControl (format)
ms.openlocfilehash: 1b7fc60b6fa9864b66e9edfebb3e4a86e287f3f8
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645895"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="0bd39-103">EntrySelectedBy-element för TableRowEntry  för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-103">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="0bd39-104">Definierar de .NET-typer som använder den här definitionen av Tabellvy eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0bd39-104">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="0bd39-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0bd39-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0bd39-106">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0bd39-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0bd39-107">Attributes and Elements</span></span>

<span data-ttu-id="0bd39-108">I följande avsnitt beskrivs attribut, underordnade element och `EntrySelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0bd39-108">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0bd39-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0bd39-109">Attributes</span></span>

<span data-ttu-id="0bd39-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="0bd39-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0bd39-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0bd39-111">Child Elements</span></span>

|<span data-ttu-id="0bd39-112">Element</span><span class="sxs-lookup"><span data-stu-id="0bd39-112">Element</span></span>|<span data-ttu-id="0bd39-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0bd39-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bd39-114">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-114">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0bd39-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0bd39-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0bd39-116">Definierar det villkor som måste finnas för att den här tabell visnings definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0bd39-116">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="0bd39-117">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-117">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0bd39-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0bd39-118">Optional element.</span></span><br /><br /> <span data-ttu-id="0bd39-119">Anger en uppsättning av .NET-typer som använder den här Table View-definitionen.</span><span class="sxs-lookup"><span data-stu-id="0bd39-119">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="0bd39-120">TypeName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-120">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="0bd39-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0bd39-121">Optional element.</span></span><br /><br /> <span data-ttu-id="0bd39-122">Anger en .NET-typ som använder den här Table View-definitionen.</span><span class="sxs-lookup"><span data-stu-id="0bd39-122">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0bd39-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0bd39-123">Parent Elements</span></span>

|<span data-ttu-id="0bd39-124">Element</span><span class="sxs-lookup"><span data-stu-id="0bd39-124">Element</span></span>|<span data-ttu-id="0bd39-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0bd39-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0bd39-126">TableRowEntry-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-126">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="0bd39-127">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="0bd39-127">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0bd39-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0bd39-128">Remarks</span></span>

<span data-ttu-id="0bd39-129">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en tabell visnings definition.</span><span class="sxs-lookup"><span data-stu-id="0bd39-129">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="0bd39-130">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="0bd39-130">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="0bd39-131">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderas till `true` .</span><span class="sxs-lookup"><span data-stu-id="0bd39-131">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="0bd39-132">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="0bd39-132">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="0bd39-133">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0bd39-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0bd39-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="0bd39-134">Example</span></span>

<span data-ttu-id="0bd39-135">I följande exempel visas ett- `TableRowEntry` element som används för att visa egenskaperna för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="0bd39-135">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0bd39-136">Se även</span><span class="sxs-lookup"><span data-stu-id="0bd39-136">See Also</span></span>

[<span data-ttu-id="0bd39-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="0bd39-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0bd39-138">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-138">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0bd39-139">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-139">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0bd39-140">TableRowEntry-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-140">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="0bd39-141">TypeName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="0bd39-141">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="0bd39-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="0bd39-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
