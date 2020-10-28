---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItems-element för TableRowEntry för TableControl (format)
description: TableColumnItems-element för TableRowEntry för TableControl (format)
ms.openlocfilehash: 4d600a366d2be1c453f05b301bdf575351dd51c1
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667767"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="d2a1b-103">TableColumnItems-element för TableRowEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-103">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="d2a1b-104">Definierar de egenskaper eller skript vars värden visas i en rad.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-104">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="d2a1b-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2a1b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2a1b-106">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2a1b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d2a1b-107">Attributes and Elements</span></span>

<span data-ttu-id="d2a1b-108">I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItems` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2a1b-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2a1b-109">Attributes</span></span>

<span data-ttu-id="d2a1b-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2a1b-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d2a1b-111">Child Elements</span></span>

|<span data-ttu-id="d2a1b-112">Element</span><span class="sxs-lookup"><span data-stu-id="d2a1b-112">Element</span></span>|<span data-ttu-id="d2a1b-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2a1b-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2a1b-114">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-114">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="d2a1b-115">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-115">Required element.</span></span><br /><br /> <span data-ttu-id="d2a1b-116">Definierar egenskapen eller skriptet vars värde visas i en kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-116">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d2a1b-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d2a1b-117">Parent Elements</span></span>

|<span data-ttu-id="d2a1b-118">Element</span><span class="sxs-lookup"><span data-stu-id="d2a1b-118">Element</span></span>|<span data-ttu-id="d2a1b-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2a1b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2a1b-120">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-120">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="d2a1b-121">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-121">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2a1b-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="d2a1b-122">Remarks</span></span>

<span data-ttu-id="d2a1b-123">Ett `TableColumnItem` element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-123">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="d2a1b-124">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="d2a1b-124">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="d2a1b-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d2a1b-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2a1b-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2a1b-126">Example</span></span>

<span data-ttu-id="d2a1b-127">I följande exempel visas ett- `TableColumnItems` element som definierar tre egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="d2a1b-127">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2a1b-128">Se även</span><span class="sxs-lookup"><span data-stu-id="d2a1b-128">See Also</span></span>

[<span data-ttu-id="d2a1b-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="d2a1b-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d2a1b-130">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="d2a1b-131">TableRowEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="d2a1b-131">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="d2a1b-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="d2a1b-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
