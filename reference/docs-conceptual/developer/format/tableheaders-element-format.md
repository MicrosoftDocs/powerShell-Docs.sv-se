---
title: TableHeaders-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: f9fa2b6f-b99a-42de-9779-44e9cb583f71
caps.latest.revision: 15
ms.openlocfilehash: bd44fcf4878c858afe81fb071ce72f627ac465dc
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72353699"
---
# <a name="tableheaders-element-format"></a><span data-ttu-id="bc0da-102">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-102">TableHeaders Element (Format)</span></span>

<span data-ttu-id="bc0da-103">Definierar rubrikerna för kolumnerna i en tabell.</span><span class="sxs-lookup"><span data-stu-id="bc0da-103">Defines the headers for the columns of a table.</span></span>

<span data-ttu-id="bc0da-104">ViewDefinitions-element (format) View-element (format) TableControl-element (format) TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="bc0da-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc0da-105">Syntax</span></span>

```xml
<TableHeaders>
  <TableColumnHeader>...</TableColumnHeader>
</TableHeaders>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc0da-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bc0da-106">Attributes and Elements</span></span>

<span data-ttu-id="bc0da-107">I följande avsnitt beskrivs attributen, underordnade element och överordnade element i `TableHeaders`-elementet.</span><span class="sxs-lookup"><span data-stu-id="bc0da-107">The following sections describe the attributes, child elements, and parent elements of the `TableHeaders` element.</span></span> <span data-ttu-id="bc0da-108">Det måste finnas ett underordnat element för varje egenskap i objektet som ska visas.</span><span class="sxs-lookup"><span data-stu-id="bc0da-108">There must be a child element for each property of the object that is to be displayed.</span></span> <span data-ttu-id="bc0da-109">Kolumn rubrik informationen visas i den ordning som de underordnade elementen har angetts.</span><span class="sxs-lookup"><span data-stu-id="bc0da-109">The column header information is displayed in the order that the child elements are specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc0da-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="bc0da-110">Attributes</span></span>

<span data-ttu-id="bc0da-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="bc0da-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc0da-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bc0da-112">Child Elements</span></span>

|<span data-ttu-id="bc0da-113">Element</span><span class="sxs-lookup"><span data-stu-id="bc0da-113">Element</span></span>|<span data-ttu-id="bc0da-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bc0da-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc0da-115">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="bc0da-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bc0da-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bc0da-117">Definierar etiketten, bredden och data justeringen för en kolumn i en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="bc0da-117">Defines the label, the width, and the alignment of the data for a column of a table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc0da-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bc0da-118">Parent Elements</span></span>

|<span data-ttu-id="bc0da-119">Element</span><span class="sxs-lookup"><span data-stu-id="bc0da-119">Element</span></span>|<span data-ttu-id="bc0da-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bc0da-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc0da-121">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-121">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="bc0da-122">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="bc0da-122">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc0da-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="bc0da-123">Remarks</span></span>

<span data-ttu-id="bc0da-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="bc0da-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="bc0da-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="bc0da-125">Example</span></span>

<span data-ttu-id="bc0da-126">Det här exemplet visar ett `TableHeaders`-element som definierar två kolumn rubriker.</span><span class="sxs-lookup"><span data-stu-id="bc0da-126">This example shows a `TableHeaders` element that defines two column headers.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="bc0da-127">Se även</span><span class="sxs-lookup"><span data-stu-id="bc0da-127">See Also</span></span>

[<span data-ttu-id="bc0da-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="bc0da-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="bc0da-129">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="bc0da-130">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="bc0da-130">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="bc0da-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="bc0da-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
