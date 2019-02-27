---
title: TableColumnItems Element för TableRowEntry för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d43684ce-7c3d-4d14-8dbd-061c111ee805
caps.latest.revision: 12
ms.openlocfilehash: faa9ba78397e713400f6072df9915f20d966bb37
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56849226"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="d2584-102">TableColumnItems-element för TableRowEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="d2584-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="d2584-103">Definierar egenskaper eller skript som vars värden visas i en rad.</span><span class="sxs-lookup"><span data-stu-id="d2584-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="d2584-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format) TableColumnItems Element för TableControlEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d2584-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="d2584-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="d2584-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="d2584-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="d2584-106">Attributes and Elements</span></span>

<span data-ttu-id="d2584-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableColumnItems` element.</span><span class="sxs-lookup"><span data-stu-id="d2584-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="d2584-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="d2584-108">Attributes</span></span>

<span data-ttu-id="d2584-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="d2584-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="d2584-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="d2584-110">Child Elements</span></span>

|<span data-ttu-id="d2584-111">Element</span><span class="sxs-lookup"><span data-stu-id="d2584-111">Element</span></span>|<span data-ttu-id="d2584-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2584-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2584-113">TableColumnItem Element för TableColumnItems för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d2584-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="d2584-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="d2584-114">Required element.</span></span><br /><br /> <span data-ttu-id="d2584-115">Definierar egenskapen eller skript som vars värde visas i en kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2584-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="d2584-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="d2584-116">Parent Elements</span></span>

|<span data-ttu-id="d2584-117">Element</span><span class="sxs-lookup"><span data-stu-id="d2584-117">Element</span></span>|<span data-ttu-id="d2584-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="d2584-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="d2584-119">TableRowEntry Element för TableRowEntries för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="d2584-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="d2584-120">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="d2584-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="d2584-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="d2584-121">Remarks</span></span>

<span data-ttu-id="d2584-122">En `TableColumnItem` element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="d2584-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="d2584-123">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="d2584-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="d2584-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="d2584-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="d2584-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="d2584-125">Example</span></span>

<span data-ttu-id="d2584-126">I följande exempel visas en `TableColumnItems` element som definierar tre egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="d2584-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="d2584-127">Se även</span><span class="sxs-lookup"><span data-stu-id="d2584-127">See Also</span></span>

[<span data-ttu-id="d2584-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="d2584-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="d2584-129">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d2584-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="d2584-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="d2584-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="d2584-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="d2584-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
