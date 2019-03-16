---
title: TableRowEntries Element för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58055741"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="7b426-102">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="7b426-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="7b426-103">Definierar raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7b426-103">Defines the rows of the table.</span></span>

<span data-ttu-id="7b426-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7b426-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7b426-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7b426-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7b426-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7b426-106">Attributes and Elements</span></span>

<span data-ttu-id="7b426-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableRowEntries` element.</span><span class="sxs-lookup"><span data-stu-id="7b426-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="7b426-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="7b426-108">Attributes</span></span>

<span data-ttu-id="7b426-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="7b426-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7b426-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7b426-110">Child Elements</span></span>

|<span data-ttu-id="7b426-111">Element</span><span class="sxs-lookup"><span data-stu-id="7b426-111">Element</span></span>|<span data-ttu-id="7b426-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7b426-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b426-113">TableRowEntry Element för TableRowEntries för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="7b426-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="7b426-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="7b426-114">Required element.</span></span><br /><br /> <span data-ttu-id="7b426-115">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="7b426-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7b426-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7b426-116">Parent Elements</span></span>

|<span data-ttu-id="7b426-117">Element</span><span class="sxs-lookup"><span data-stu-id="7b426-117">Element</span></span>|<span data-ttu-id="7b426-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7b426-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7b426-119">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7b426-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="7b426-120">Definierar ett tabellformat för en vy.</span><span class="sxs-lookup"><span data-stu-id="7b426-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7b426-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="7b426-121">Remarks</span></span>

<span data-ttu-id="7b426-122">Du måste ange en eller flera `TableRowEntry` -element för tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="7b426-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="7b426-123">Det finns ingen högsta gräns för hur många `TableRowEntry` element som du kan lägga till och kan inte heller deras inbördes ordning betydande.</span><span class="sxs-lookup"><span data-stu-id="7b426-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="7b426-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="7b426-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7b426-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="7b426-125">Example</span></span>

<span data-ttu-id="7b426-126">I följande exempel visas en `TableRowEntries` element som definierar en rad som visar värdena för två egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="7b426-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>
    <EntrySelectedBy>
      <TypeName>System.Diagnostics.Process</TypeName>
    </EntrySelectedBy>
    <TableColumnItems>
      <TableColumnItem>
        <PropertyName> Property for first column</PropertyName>
      </TableColumnItem>
      <TableColumnItem>
        <PropertyName> Property for second column</PropertyName>
      </TableColumnItem>
    </TableColumnItems>
  </TableRowEntry>
</TableRowEntries>

```

## <a name="see-also"></a><span data-ttu-id="7b426-127">Se även</span><span class="sxs-lookup"><span data-stu-id="7b426-127">See Also</span></span>

[<span data-ttu-id="7b426-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="7b426-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="7b426-129">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7b426-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="7b426-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="7b426-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="7b426-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="7b426-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
