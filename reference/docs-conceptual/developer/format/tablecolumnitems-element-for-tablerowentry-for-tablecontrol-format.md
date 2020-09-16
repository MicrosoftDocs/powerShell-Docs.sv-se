---
title: TableColumnItems-element för TableRowEntry för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 661b938e8db0e68e10dc05f552e4f3a14608bc55
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785157"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="5c448-102">TableColumnItems-element för TableRowEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="5c448-103">Definierar de egenskaper eller skript vars värden visas i en rad.</span><span class="sxs-lookup"><span data-stu-id="5c448-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="5c448-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c448-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c448-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c448-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5c448-106">Attributes and Elements</span></span>

<span data-ttu-id="5c448-107">I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItems` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5c448-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c448-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="5c448-108">Attributes</span></span>

<span data-ttu-id="5c448-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="5c448-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c448-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5c448-110">Child Elements</span></span>

|<span data-ttu-id="5c448-111">Element</span><span class="sxs-lookup"><span data-stu-id="5c448-111">Element</span></span>|<span data-ttu-id="5c448-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5c448-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c448-113">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="5c448-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="5c448-114">Required element.</span></span><br /><br /> <span data-ttu-id="5c448-115">Definierar egenskapen eller skriptet vars värde visas i en kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="5c448-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c448-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5c448-116">Parent Elements</span></span>

|<span data-ttu-id="5c448-117">Element</span><span class="sxs-lookup"><span data-stu-id="5c448-117">Element</span></span>|<span data-ttu-id="5c448-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5c448-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c448-119">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="5c448-120">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="5c448-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c448-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5c448-121">Remarks</span></span>

<span data-ttu-id="5c448-122">Ett `TableColumnItem` element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="5c448-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="5c448-123">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="5c448-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="5c448-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="5c448-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c448-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="5c448-125">Example</span></span>

<span data-ttu-id="5c448-126">I följande exempel visas ett- `TableColumnItems` element som definierar tre egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="5c448-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="5c448-127">Se även</span><span class="sxs-lookup"><span data-stu-id="5c448-127">See Also</span></span>

[<span data-ttu-id="5c448-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="5c448-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="5c448-129">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="5c448-130">TableRowEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="5c448-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="5c448-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5c448-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
