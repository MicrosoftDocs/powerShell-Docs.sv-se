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
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847427"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="dc499-102">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="dc499-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="dc499-103">Definierar rubrikerna för kolumner i en tabell.</span><span class="sxs-lookup"><span data-stu-id="dc499-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="dc499-104">ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dc499-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dc499-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dc499-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="dc499-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="dc499-106">Attributes and Elements</span></span>

<span data-ttu-id="dc499-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade element i den `TableHeaders` element.</span><span class="sxs-lookup"><span data-stu-id="dc499-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="dc499-108">Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="dc499-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="dc499-109">Kolumninformation för rubriken visas i nämnd av underordnade element.</span><span class="sxs-lookup"><span data-stu-id="dc499-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="dc499-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="dc499-110">Attributes</span></span>

<span data-ttu-id="dc499-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="dc499-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dc499-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="dc499-112">Child Elements</span></span>

|<span data-ttu-id="dc499-113">Element</span><span class="sxs-lookup"><span data-stu-id="dc499-113">Element</span></span>|<span data-ttu-id="dc499-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc499-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc499-115">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="dc499-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="dc499-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="dc499-116">Optional element.</span></span><br /><br /> <span data-ttu-id="dc499-117">Definierar etiketten, bredd och justering av data för en kolumn med en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="dc499-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="dc499-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="dc499-118">Parent Elements</span></span>

|<span data-ttu-id="dc499-119">Element</span><span class="sxs-lookup"><span data-stu-id="dc499-119">Element</span></span>|<span data-ttu-id="dc499-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dc499-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dc499-121">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="dc499-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="dc499-122">Definierar ett tabellformat för en vy.</span><span class="sxs-lookup"><span data-stu-id="dc499-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="dc499-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="dc499-123">Remarks</span></span>

<span data-ttu-id="dc499-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="dc499-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dc499-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="dc499-125">Example</span></span>

<span data-ttu-id="dc499-126">Det här exemplet visar en `TableHeaders` -element som definierar två kolumnrubriker.</span><span class="sxs-lookup"><span data-stu-id="dc499-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="dc499-127">Se även</span><span class="sxs-lookup"><span data-stu-id="dc499-127">See Also</span></span>

[<span data-ttu-id="dc499-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="dc499-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="dc499-129">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="dc499-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="dc499-130">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="dc499-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="dc499-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="dc499-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
