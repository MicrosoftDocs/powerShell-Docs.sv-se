---
ms.date: 09/13/2016
ms.topic: reference
title: TableRowEntries-element för TableControl (format)
description: TableRowEntries-element för TableControl (format)
ms.openlocfilehash: 1df63e645234da8276c7ccc5af34e81a56475e43
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651473"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="4e7ab-103">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-103">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="4e7ab-104">Definierar raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-104">Defines the rows of the table.</span></span>

<span data-ttu-id="4e7ab-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4e7ab-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4e7ab-106">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="4e7ab-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4e7ab-107">Attributes and Elements</span></span>

<span data-ttu-id="4e7ab-108">I följande avsnitt beskrivs attributen, underordnade element och `TableRowEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-108">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="4e7ab-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="4e7ab-109">Attributes</span></span>

<span data-ttu-id="4e7ab-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4e7ab-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4e7ab-111">Child Elements</span></span>

|<span data-ttu-id="4e7ab-112">Element</span><span class="sxs-lookup"><span data-stu-id="4e7ab-112">Element</span></span>|<span data-ttu-id="4e7ab-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e7ab-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e7ab-114">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-114">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="4e7ab-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-115">Required element.</span></span><br /><br /> <span data-ttu-id="4e7ab-116">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-116">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="4e7ab-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4e7ab-117">Parent Elements</span></span>

|<span data-ttu-id="4e7ab-118">Element</span><span class="sxs-lookup"><span data-stu-id="4e7ab-118">Element</span></span>|<span data-ttu-id="4e7ab-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4e7ab-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4e7ab-120">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-120">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="4e7ab-121">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-121">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="4e7ab-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="4e7ab-122">Remarks</span></span>

<span data-ttu-id="4e7ab-123">Du måste ange ett eller flera `TableRowEntry` element i vyn tabellvy.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-123">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="4e7ab-124">Det finns ingen övre gräns för antalet `TableRowEntry` element som kan läggas till eller som är deras inbördes ordning.</span><span class="sxs-lookup"><span data-stu-id="4e7ab-124">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="4e7ab-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4e7ab-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4e7ab-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="4e7ab-126">Example</span></span>

<span data-ttu-id="4e7ab-127">I följande exempel visas ett- `TableRowEntries` element som definierar en rad som visar värdena för två egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="4e7ab-127">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="4e7ab-128">Se även</span><span class="sxs-lookup"><span data-stu-id="4e7ab-128">See Also</span></span>

[<span data-ttu-id="4e7ab-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="4e7ab-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4e7ab-130">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="4e7ab-131">TableRowEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="4e7ab-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="4e7ab-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="4e7ab-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
