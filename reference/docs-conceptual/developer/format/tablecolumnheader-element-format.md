---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnHeader-element (format)
description: TableColumnHeader-element (format)
ms.openlocfilehash: 30368512875b7c5c4cf3c686f3d09540dea1bd26
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92651518"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="b08b2-103">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-103">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="b08b2-104">Definierar etiketten, bredden på kolumnen och justeringen av etiketten för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-104">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="b08b2-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader-element för TableHeaders (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b08b2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b08b2-106">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b08b2-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b08b2-107">Attributes and Elements</span></span>

<span data-ttu-id="b08b2-108">I följande avsnitt beskrivs attribut, underordnade element och `TableColumnHeader` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-108">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b08b2-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b08b2-109">Attributes</span></span>

<span data-ttu-id="b08b2-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b08b2-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b08b2-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b08b2-111">Child Elements</span></span>

|<span data-ttu-id="b08b2-112">Element</span><span class="sxs-lookup"><span data-stu-id="b08b2-112">Element</span></span>|<span data-ttu-id="b08b2-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b08b2-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b08b2-114">Etikett element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-114">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b08b2-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-115">Optional element.</span></span><br /><br /> <span data-ttu-id="b08b2-116">Definierar etiketten som visas överst i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-116">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="b08b2-117">Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.</span><span class="sxs-lookup"><span data-stu-id="b08b2-117">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="b08b2-118">Width-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-118">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b08b2-119">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-119">Required element.</span></span><br /><br /> <span data-ttu-id="b08b2-120">Anger bredden (i tecken) för kolumnen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-120">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="b08b2-121">Alignment-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-121">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="b08b2-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="b08b2-123">Anger hur kolumnens etikett visas.</span><span class="sxs-lookup"><span data-stu-id="b08b2-123">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="b08b2-124">Om ingen justering anges justeras etiketten till vänster.</span><span class="sxs-lookup"><span data-stu-id="b08b2-124">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b08b2-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b08b2-125">Parent Elements</span></span>

|<span data-ttu-id="b08b2-126">Element</span><span class="sxs-lookup"><span data-stu-id="b08b2-126">Element</span></span>|<span data-ttu-id="b08b2-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b08b2-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b08b2-128">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-128">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="b08b2-129">Definierar kolumnerna i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="b08b2-129">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b08b2-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b08b2-130">Remarks</span></span>

<span data-ttu-id="b08b2-131">Ange ett sidhuvud för varje kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-131">Specify a header for each column of the table.</span></span> <span data-ttu-id="b08b2-132">Kolumnerna visas i den ordning som `TableColumnHeader` elementen definieras i.</span><span class="sxs-lookup"><span data-stu-id="b08b2-132">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="b08b2-133">En tabell måste ha samma antal `TableColumnHeader` element som `TableRowEntry` element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-133">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="b08b2-134">Kolumn rubriken definierar hur texten överst i tabellen visas.</span><span class="sxs-lookup"><span data-stu-id="b08b2-134">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="b08b2-135">Rad posterna definierar vilka data som visas i raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-135">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="b08b2-136">Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b08b2-136">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b08b2-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="b08b2-137">Example</span></span>

<span data-ttu-id="b08b2-138">I följande exempel visas två `TableColumnHeader` element.</span><span class="sxs-lookup"><span data-stu-id="b08b2-138">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="b08b2-139">Det första elementet definierar en kolumn vars etikett är "kolumn 1", har en bredd på 16 tecken och vars etikett är justerad till vänster.</span><span class="sxs-lookup"><span data-stu-id="b08b2-139">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="b08b2-140">Det andra elementet definierar en kolumn vars etikett är "kolumn 2", har en bredd på 10 tecken och vars etikett centreras i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="b08b2-140">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b08b2-141">Se även</span><span class="sxs-lookup"><span data-stu-id="b08b2-141">See Also</span></span>

[<span data-ttu-id="b08b2-142">Alignment-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-142">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b08b2-143">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="b08b2-143">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b08b2-144">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-144">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b08b2-145">TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-145">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="b08b2-146">Bredd för TableColumnHeader för TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="b08b2-146">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="b08b2-147">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b08b2-147">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
