---
title: TableColumnHeader Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 49ff3062-6396-4aa8-919b-3fd3ac60899a
caps.latest.revision: 19
ms.openlocfilehash: d3ad7fa563def17d43ce4dc64d155b65b650521f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58057883"
---
# <a name="tablecolumnheader-element-format"></a><span data-ttu-id="7586d-102">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="7586d-102">TableColumnHeader Element (Format)</span></span>

<span data-ttu-id="7586d-103">Definierar etiketten, bredden på kolumnen och justering för etiketten för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7586d-103">Defines the label, the width of the column, and the alignment of the label for a column of the table.</span></span>

<span data-ttu-id="7586d-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet för TableHeaders för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7586d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7586d-105">Syntax</span></span>

```xml
<TableColumnHeader>
  <Label>DisplayedLabel</Label>
  <Width>NumberOfCharacters</Width>
  <Alignment>Left, Right, or Centered</Alignment>
</TableColumnHeader>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7586d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7586d-106">Attributes and Elements</span></span>

<span data-ttu-id="7586d-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `TableColumnHeader` element.</span><span class="sxs-lookup"><span data-stu-id="7586d-107">The following sections describe attributes, child elements, and the parent element of the `TableColumnHeader` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7586d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7586d-108">Attributes</span></span>

<span data-ttu-id="7586d-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7586d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7586d-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7586d-110">Child Elements</span></span>

|<span data-ttu-id="7586d-111">Element</span><span class="sxs-lookup"><span data-stu-id="7586d-111">Element</span></span>|<span data-ttu-id="7586d-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7586d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7586d-113">Etikettelement för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-113">Label Element For TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7586d-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7586d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="7586d-115">Definierar den etikett som visas överst i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="7586d-115">Defines the label that is displayed at the top of the column.</span></span> <span data-ttu-id="7586d-116">Om ingen etikett har angetts används namnet på egenskapen vars värde visas på raderna.</span><span class="sxs-lookup"><span data-stu-id="7586d-116">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>|
|[<span data-ttu-id="7586d-117">Bredd-Element för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-117">Width Element for TableColumnHeader for TableControl (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7586d-118">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="7586d-118">Required element.</span></span><br /><br /> <span data-ttu-id="7586d-119">Anger bredden (i antal tecken) för kolumnen.</span><span class="sxs-lookup"><span data-stu-id="7586d-119">Specifies the width (in characters) of the column.</span></span>|
|[<span data-ttu-id="7586d-120">Justering Element för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-120">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)|<span data-ttu-id="7586d-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="7586d-121">Optional element.</span></span><br /><br /> <span data-ttu-id="7586d-122">Anger hur kolumnen etiketten ska visas.</span><span class="sxs-lookup"><span data-stu-id="7586d-122">Specifies how the label of the column is displayed.</span></span> <span data-ttu-id="7586d-123">Om ingen justering anges justeras etiketten till vänster.</span><span class="sxs-lookup"><span data-stu-id="7586d-123">If no alignment is specified, the label is aligned on the left.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7586d-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7586d-124">Parent Elements</span></span>

|<span data-ttu-id="7586d-125">Element</span><span class="sxs-lookup"><span data-stu-id="7586d-125">Element</span></span>|<span data-ttu-id="7586d-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7586d-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7586d-127">TableHeaders Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-127">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="7586d-128">Definierar kolumner i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="7586d-128">Defines the columns of a table view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7586d-129">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7586d-129">Remarks</span></span>

<span data-ttu-id="7586d-130">Ange en rubrik för varje kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7586d-130">Specify a header for each column of the table.</span></span> <span data-ttu-id="7586d-131">Kolumnerna i ordningen som de `TableColumnHeader` element har definierats.</span><span class="sxs-lookup"><span data-stu-id="7586d-131">The columns are displayed in the order in which the `TableColumnHeader` elements are defined.</span></span>

<span data-ttu-id="7586d-132">En tabell måste ha samma antal `TableColumnHeader` element som `TableRowEntry` element.</span><span class="sxs-lookup"><span data-stu-id="7586d-132">A table must have the same number of `TableColumnHeader` elements as `TableRowEntry` elements.</span></span> <span data-ttu-id="7586d-133">Kolumnrubriken definierar hur texten längst upp i tabellen visas.</span><span class="sxs-lookup"><span data-stu-id="7586d-133">The column header defines how the text at the top of the table is displayed.</span></span> <span data-ttu-id="7586d-134">Rad posterna definierar vilka data som visas i raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7586d-134">The row entries define what data is displayed in the rows of the table.</span></span>

<span data-ttu-id="7586d-135">Läs mer om komponenterna i en tabellvy, [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7586d-135">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7586d-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="7586d-136">Example</span></span>

<span data-ttu-id="7586d-137">I följande exempel visas två `TableColumnHeader` element.</span><span class="sxs-lookup"><span data-stu-id="7586d-137">The following example shows two `TableColumnHeader` elements.</span></span> <span data-ttu-id="7586d-138">Det första elementet definierar en kolumn vars etikett är ”kolumn 1”, har en bredd på 16 tecken och vars etikett har justerats till vänster.</span><span class="sxs-lookup"><span data-stu-id="7586d-138">The first element defines a column whose label is "Column 1", has a width of 16 characters, and whose label is aligned on the left.</span></span> <span data-ttu-id="7586d-139">Det andra elementet definierar en kolumn vars etikett är ”kolumn 2”, bredd är 10 tecken och vars etikett centreras i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="7586d-139">The second element defines a column whose label is "Column 2", has a width of 10 characters, and whose label is centered in the column.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7586d-140">Se även</span><span class="sxs-lookup"><span data-stu-id="7586d-140">See Also</span></span>

[<span data-ttu-id="7586d-141">Justering Element för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-141">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7586d-142">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="7586d-142">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7586d-143">Etikettelement för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-143">Label Element for TableColumnHeader for TableControl (Format)</span></span>](./label-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7586d-144">TableHeaders Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-144">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="7586d-145">Bredden för TableColumnHeader för TableControl elementet (Format)</span><span class="sxs-lookup"><span data-stu-id="7586d-145">Width for TableColumnHeader for TableControl Element (Format)</span></span>](./width-element-for-tablecolumnheader-for-tablecontrol-format.md)

[<span data-ttu-id="7586d-146">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="7586d-146">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
