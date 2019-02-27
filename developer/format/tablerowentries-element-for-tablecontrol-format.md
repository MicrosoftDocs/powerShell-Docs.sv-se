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
ms.openlocfilehash: d93750f919c1075f173dc9ac70324cc003e36879
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851144"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="06328-102">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="06328-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="06328-103">Definierar raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="06328-103">Defines the rows of the table.</span></span>

<span data-ttu-id="06328-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="06328-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="06328-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="06328-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="06328-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="06328-106">Attributes and Elements</span></span>

<span data-ttu-id="06328-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableRowEntries` element.</span><span class="sxs-lookup"><span data-stu-id="06328-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="06328-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="06328-108">Attributes</span></span>

<span data-ttu-id="06328-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="06328-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="06328-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="06328-110">Child Elements</span></span>

|<span data-ttu-id="06328-111">Element</span><span class="sxs-lookup"><span data-stu-id="06328-111">Element</span></span>|<span data-ttu-id="06328-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="06328-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06328-113">TableRowEntry Element för TableRowEntries för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="06328-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)|<span data-ttu-id="06328-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="06328-114">Required element.</span></span><br /><br /> <span data-ttu-id="06328-115">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="06328-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="06328-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="06328-116">Parent Elements</span></span>

|<span data-ttu-id="06328-117">Element</span><span class="sxs-lookup"><span data-stu-id="06328-117">Element</span></span>|<span data-ttu-id="06328-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="06328-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="06328-119">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="06328-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="06328-120">Definierar ett tabellformat för en vy.</span><span class="sxs-lookup"><span data-stu-id="06328-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="06328-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="06328-121">Remarks</span></span>

<span data-ttu-id="06328-122">Du måste ange en eller flera `TableRowEntry` -element för tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="06328-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="06328-123">Det finns ingen högsta gräns för hur många `TableRowEntry` element som du kan lägga till och kan inte heller deras inbördes ordning betydande.</span><span class="sxs-lookup"><span data-stu-id="06328-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="06328-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="06328-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="06328-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="06328-125">Example</span></span>

<span data-ttu-id="06328-126">I följande exempel visas en `TableRowEntries` element som definierar en rad som visar värdena för två egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="06328-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="06328-127">Se även</span><span class="sxs-lookup"><span data-stu-id="06328-127">See Also</span></span>

[<span data-ttu-id="06328-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="06328-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="06328-129">TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="06328-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="06328-130">TableRowEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="06328-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentroes-for-tablecontrol-format.md)

[<span data-ttu-id="06328-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="06328-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
