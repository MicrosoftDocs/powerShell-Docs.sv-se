---
title: EntrySelectedBy-element för TableRowEntry för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49623fcf-1238-4d20-a7ce-238d47d9d565
caps.latest.revision: 15
ms.openlocfilehash: 9302bfed0324773cb98d698acdcf608f34ee19c1
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354763"
---
# <a name="entryselectedby-element-for-tablerowentry--for-tablecontrol-format"></a><span data-ttu-id="c72cb-102">EntrySelectedBy-element för TableRowEntry  för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-102">EntrySelectedBy Element for TableRowEntry  for TableControl (Format)</span></span>

<span data-ttu-id="c72cb-103">Definierar de .NET-typer som använder den här definitionen av Tabellvy eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c72cb-103">Defines the .NET types that use this definition of the table view or the condition that must exist for this definition to be used.</span></span>

<span data-ttu-id="c72cb-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) EntrySelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) EntrySelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c72cb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c72cb-105">Syntax</span></span>

```xml
<EntrySelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>NameofSelectionSet</SelectionSetName>
  <SelectionCondition>...</SelectionCondition>
</EntrySelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c72cb-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c72cb-106">Attributes and Elements</span></span>

<span data-ttu-id="c72cb-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `EntrySelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="c72cb-107">The following sections describe attributes, child elements, and the parent element of the `EntrySelectedBy` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c72cb-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c72cb-108">Attributes</span></span>

<span data-ttu-id="c72cb-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c72cb-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c72cb-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c72cb-110">Child Elements</span></span>

|<span data-ttu-id="c72cb-111">Element</span><span class="sxs-lookup"><span data-stu-id="c72cb-111">Element</span></span>|<span data-ttu-id="c72cb-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c72cb-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c72cb-113">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-113">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c72cb-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c72cb-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c72cb-115">Definierar det villkor som måste finnas för att den här tabell visnings definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="c72cb-115">Defines the condition that must exist for this table view definition to be used.</span></span>|
|[<span data-ttu-id="c72cb-116">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-116">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c72cb-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c72cb-117">Optional element.</span></span><br /><br /> <span data-ttu-id="c72cb-118">Anger en uppsättning av .NET-typer som använder den här Table View-definitionen.</span><span class="sxs-lookup"><span data-stu-id="c72cb-118">Specifies a set of .NET types that use this table view definition.</span></span>|
|[<span data-ttu-id="c72cb-119">Elementet TypeName för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-119">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)|<span data-ttu-id="c72cb-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c72cb-120">Optional element.</span></span><br /><br /> <span data-ttu-id="c72cb-121">Anger en .NET-typ som använder den här Table View-definitionen.</span><span class="sxs-lookup"><span data-stu-id="c72cb-121">Specifies a .NET type that uses this table view definition.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c72cb-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c72cb-122">Parent Elements</span></span>

|<span data-ttu-id="c72cb-123">Element</span><span class="sxs-lookup"><span data-stu-id="c72cb-123">Element</span></span>|<span data-ttu-id="c72cb-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c72cb-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c72cb-125">TableRowEntry-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-125">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="c72cb-126">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="c72cb-126">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c72cb-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c72cb-127">Remarks</span></span>

<span data-ttu-id="c72cb-128">Du måste ange minst en typ, markerings uppsättning eller ett markerings villkor för en tabell visnings definition.</span><span class="sxs-lookup"><span data-stu-id="c72cb-128">You must specify at least one type, selection set, or selection condition for a table view definition.</span></span> <span data-ttu-id="c72cb-129">Det finns ingen övre gräns för antalet underordnade element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="c72cb-129">There is no maximum limit to the number of child elements that you can use.</span></span>

<span data-ttu-id="c72cb-130">Urvals villkor används för att definiera ett villkor som måste finnas för att definitionen ska kunna användas, till exempel när ett objekt har en speciell egenskap eller ett angivet egenskaps värde eller skript utvärderar till `true`.</span><span class="sxs-lookup"><span data-stu-id="c72cb-130">Selection conditions are used to define a condition that must exist for the definition to be used, such as when an object has a specific property or that a specific property value or script evaluates to `true`.</span></span> <span data-ttu-id="c72cb-131">Mer information om urvals villkor finns i [definiera villkor för när en visnings post eller ett objekt används](./defining-conditions-for-displaying-data.md).</span><span class="sxs-lookup"><span data-stu-id="c72cb-131">For more information about selection conditions, see [Defining Conditions for when a View Entry or Item is Used](./defining-conditions-for-displaying-data.md).</span></span>

<span data-ttu-id="c72cb-132">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c72cb-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c72cb-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="c72cb-133">Example</span></span>

<span data-ttu-id="c72cb-134">I följande exempel visas ett `TableRowEntry`-element som används för att visa egenskaperna för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="c72cb-134">The following example shows a `TableRowEntry` element that is used to display the properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c72cb-135">Se även</span><span class="sxs-lookup"><span data-stu-id="c72cb-135">See Also</span></span>

[<span data-ttu-id="c72cb-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="c72cb-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c72cb-137">SelectionCondition-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-137">SelectionCondition Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectioncondition-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c72cb-138">SelectionSetName-element för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-138">SelectionSetName Element for EntrySelectedBy for TableControl (Format)</span></span>](./selectionsetname-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c72cb-139">TableRowEntry-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-139">TableRowEntry Element for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="c72cb-140">Elementet TypeName för EntrySelectedBy för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c72cb-140">TypeName Element for EntrySelectedBy for TableControl (Format)</span></span>](./typename-element-for-entryselectedby-for-tablecontrol-format.md)

[<span data-ttu-id="c72cb-141">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="c72cb-141">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
