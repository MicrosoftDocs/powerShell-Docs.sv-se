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
ms.openlocfilehash: d05437aaa9652e7f81d0854d1a746acffe145699
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056914"
---
# <a name="tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format"></a><span data-ttu-id="b5502-102">TableColumnItems-element för TableRowEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b5502-102">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>

<span data-ttu-id="b5502-103">Definierar egenskaper eller skript som vars värden visas i en rad.</span><span class="sxs-lookup"><span data-stu-id="b5502-103">Defines the properties or scripts whose values are displayed in a row.</span></span>

<span data-ttu-id="b5502-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format) TableColumnItems Element för TableControlEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b5502-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b5502-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b5502-105">Syntax</span></span>

```xml
TableColumnItems>
  <TableColumnItem>...</TableColumnItem>
</TableColumnItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b5502-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b5502-106">Attributes and Elements</span></span>

<span data-ttu-id="b5502-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableColumnItems` element.</span><span class="sxs-lookup"><span data-stu-id="b5502-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItems` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b5502-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b5502-108">Attributes</span></span>

<span data-ttu-id="b5502-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b5502-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b5502-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b5502-110">Child Elements</span></span>

|<span data-ttu-id="b5502-111">Element</span><span class="sxs-lookup"><span data-stu-id="b5502-111">Element</span></span>|<span data-ttu-id="b5502-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5502-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5502-113">TableColumnItem Element för TableColumnItems för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b5502-113">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="b5502-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="b5502-114">Required element.</span></span><br /><br /> <span data-ttu-id="b5502-115">Definierar egenskapen eller skript som vars värde visas i en kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="b5502-115">Defines the property or script whose value is displayed in a column of the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b5502-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b5502-116">Parent Elements</span></span>

|<span data-ttu-id="b5502-117">Element</span><span class="sxs-lookup"><span data-stu-id="b5502-117">Element</span></span>|<span data-ttu-id="b5502-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b5502-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b5502-119">TableRowEntry Element för TableRowEntries för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="b5502-119">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="b5502-120">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b5502-120">Defines the data that is displayed in a row of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b5502-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b5502-121">Remarks</span></span>

<span data-ttu-id="b5502-122">En `TableColumnItem` element krävs för varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="b5502-122">A `TableColumnItem` element is required for each column of the row.</span></span> <span data-ttu-id="b5502-123">Den första posten visas i första kolumnen, den andra posten i den andra kolumnen och så vidare.</span><span class="sxs-lookup"><span data-stu-id="b5502-123">The first entry is displayed in first column, the second entry in the second column, and so on.</span></span>

<span data-ttu-id="b5502-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b5502-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b5502-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="b5502-125">Example</span></span>

<span data-ttu-id="b5502-126">I följande exempel visas en `TableColumnItems` element som definierar tre egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="b5502-126">The following example shows a `TableColumnItems` element that defines three properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b5502-127">Se även</span><span class="sxs-lookup"><span data-stu-id="b5502-127">See Also</span></span>

[<span data-ttu-id="b5502-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="b5502-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b5502-129">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b5502-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="b5502-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b5502-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="b5502-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="b5502-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
