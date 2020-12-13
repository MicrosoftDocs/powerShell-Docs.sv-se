---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItems-element för TableRowEntry för TableControl (format)
description: TableColumnItems-element för TableRowEntry för TableControl (format)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92667767"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="d2e2a-103">TableColumnItems-element för TableRowEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-103">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="d2e2a-104">Definierar de egenskaper eller skript vars värden visas i en rad.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-104">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="d2e2a-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2e2a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2e2a-106">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2e2a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d2e2a-107">Attributes and Elements</span></span>

<span data-ttu-id="d2e2a-108">I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItems` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2e2a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2e2a-109">Attributes</span></span>

<span data-ttu-id="d2e2a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2e2a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d2e2a-111">Child Elements</span></span>

|<span data-ttu-id="d2e2a-112">Element</span><span class="sxs-lookup"><span data-stu-id="d2e2a-112">Element</span></span>|<span data-ttu-id="d2e2a-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2e2a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2e2a-114">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-114">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="d2e2a-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-115">Required element.</span></span><br /><br /> <span data-ttu-id="d2e2a-116">Definierar egenskapen eller skriptet vars värde visas i en kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-116">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d2e2a-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d2e2a-117">Parent Elements</span></span>

|<span data-ttu-id="d2e2a-118">Element</span><span class="sxs-lookup"><span data-stu-id="d2e2a-118">Element</span></span>|<span data-ttu-id="d2e2a-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2e2a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2e2a-120">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-120">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="d2e2a-121">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-121">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2e2a-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d2e2a-122">Remarks</span></span>

<span data-ttu-id="d2e2a-123">Ett `TableColumnItem` element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-123">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="d2e2a-124">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="d2e2a-124">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="d2e2a-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d2e2a-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2e2a-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2e2a-126">Example</span></span>

<span data-ttu-id="d2e2a-127">I följande exempel visas ett- `TableColumnItems` element som definierar tre egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="d2e2a-127">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItems>
  <TableColumnItem>
    <PropertyName>Status</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>Name</PropertyName>
  </TableColumnItem>
  <TableColumnItem>
    <PropertyName>DisplayName</PropertyName>
  </TableColumnItem>
</TableColumnItems>

```

## <a name="see-also"></a><span data-ttu-id="d2e2a-128">Se även</span><span class="sxs-lookup"><span data-stu-id="d2e2a-128">See Also</span></span>

[<span data-ttu-id="d2e2a-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="d2e2a-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d2e2a-130">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="d2e2a-131">TableRowEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2e2a-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="d2e2a-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d2e2a-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
