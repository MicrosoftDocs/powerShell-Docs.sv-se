---
ms.date: 09/13/2016
ms.topic: reference
title: TableHeaders-element (format)
description: TableHeaders-element (format)
ms.openlocfilehash: 5ac4dccae746c167ebf95add9f3d18030a2b3a99
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92659823"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="28a2e-103">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-103">TableHeaders Element (Format)</span></span>

<span data-ttu-id="28a2e-104">Definierar rubrikerna för kolumnerna i en tabell.</span><span class="sxs-lookup"><span data-stu-id="28a2e-104">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="28a2e-105">ViewDefinitions-element (format) View-element (format) TableControl-element (format) TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="28a2e-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="28a2e-106">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="28a2e-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="28a2e-107">Attributes and Elements</span></span>

<span data-ttu-id="28a2e-108">I följande avsnitt beskrivs attributen, underordnade element och `TableHeaders` elementens överordnade element.</span><span class="sxs-lookup"><span data-stu-id="28a2e-108">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="28a2e-109">Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="28a2e-109">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="28a2e-110">Kolumn rubrik informationen visas i den ordning som de underordnade elementen har angetts.</span><span class="sxs-lookup"><span data-stu-id="28a2e-110">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="28a2e-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="28a2e-111">Attributes</span></span>

<span data-ttu-id="28a2e-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="28a2e-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="28a2e-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="28a2e-113">Child Elements</span></span>

|<span data-ttu-id="28a2e-114">Element</span><span class="sxs-lookup"><span data-stu-id="28a2e-114">Element</span></span>|<span data-ttu-id="28a2e-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28a2e-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28a2e-116">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="28a2e-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="28a2e-117">Optional element.</span></span><br /><br /> <span data-ttu-id="28a2e-118">Definierar etiketten, bredden och data justeringen för en kolumn i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="28a2e-118">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="28a2e-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="28a2e-119">Parent Elements</span></span>

|<span data-ttu-id="28a2e-120">Element</span><span class="sxs-lookup"><span data-stu-id="28a2e-120">Element</span></span>|<span data-ttu-id="28a2e-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="28a2e-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="28a2e-122">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-122">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="28a2e-123">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="28a2e-123">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="28a2e-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="28a2e-124">Remarks</span></span>

<span data-ttu-id="28a2e-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="28a2e-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="28a2e-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="28a2e-126">Example</span></span>

<span data-ttu-id="28a2e-127">Det här exemplet visar ett `TableHeaders` element som definierar två kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="28a2e-127">This example shows a `TableHeaders` element that defines two column headers.</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>
    <Label>Column 1</Label)
    <Width>16</Width>
    <Alignment>Left</Alignment>
  </TableColumnHeader>
  <TableColumnHeader>
    <Label>Column 2</Label)
    <Width>10</Width>
    <Alignment>Centered</Alignment>
  </TableColumnHeader>
</TableHeaders>
```

## <a name="see-also"></a><span data-ttu-id="28a2e-128">Se även</span><span class="sxs-lookup"><span data-stu-id="28a2e-128">See Also</span></span>

[<span data-ttu-id="28a2e-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="28a2e-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="28a2e-130">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="28a2e-131">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="28a2e-131">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="28a2e-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="28a2e-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
