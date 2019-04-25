---
title: TableHeaders Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075417"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="c0d26-102">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="c0d26-103">Definierar rubrikerna för kolumner i en tabell.</span><span class="sxs-lookup"><span data-stu-id="c0d26-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="c0d26-104">ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c0d26-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c0d26-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="c0d26-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c0d26-106">Attributes and Elements</span></span>

<span data-ttu-id="c0d26-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade element i den `TableHeaders` element.</span><span class="sxs-lookup"><span data-stu-id="c0d26-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="c0d26-108">Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="c0d26-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="c0d26-109">Kolumninformation för rubriken visas i nämnd av underordnade element.</span><span class="sxs-lookup"><span data-stu-id="c0d26-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c0d26-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="c0d26-110">Attributes</span></span>

<span data-ttu-id="c0d26-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c0d26-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c0d26-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c0d26-112">Child Elements</span></span>

|<span data-ttu-id="c0d26-113">Element</span><span class="sxs-lookup"><span data-stu-id="c0d26-113">Element</span></span>|<span data-ttu-id="c0d26-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c0d26-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0d26-115">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="c0d26-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c0d26-116">Optional element.</span></span><br /><br /> <span data-ttu-id="c0d26-117">Definierar etiketten, bredd och justering av data för en kolumn med en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="c0d26-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c0d26-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c0d26-118">Parent Elements</span></span>

|<span data-ttu-id="c0d26-119">Element</span><span class="sxs-lookup"><span data-stu-id="c0d26-119">Element</span></span>|<span data-ttu-id="c0d26-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c0d26-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c0d26-121">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="c0d26-122">Definierar ett tabellformat för en vy.</span><span class="sxs-lookup"><span data-stu-id="c0d26-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c0d26-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c0d26-123">Remarks</span></span>

<span data-ttu-id="c0d26-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c0d26-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c0d26-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="c0d26-125">Example</span></span>

<span data-ttu-id="c0d26-126">Det här exemplet visar en `TableHeaders` -element som definierar två kolumnrubriker.</span><span class="sxs-lookup"><span data-stu-id="c0d26-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c0d26-127">Se även</span><span class="sxs-lookup"><span data-stu-id="c0d26-127">See Also</span></span>

[<span data-ttu-id="c0d26-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="c0d26-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c0d26-129">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="c0d26-130">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c0d26-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="c0d26-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="c0d26-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
