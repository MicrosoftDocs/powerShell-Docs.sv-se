---
title: TableRowEntries-element för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d10b68ca-256c-4c58-b503-73f7777b39ae
caps.latest.revision: 15
ms.openlocfilehash: 88de19be02de4933f892e02093403a82ccdd5788
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358786"
---
# <a name="tablerowentries-element-for-tablecontrol-format"></a><span data-ttu-id="db750-102">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="db750-102">TableRowEntries Element for TableControl (Format)</span></span>

<span data-ttu-id="db750-103">Definierar raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="db750-103">Defines the rows of the table.</span></span>

<span data-ttu-id="db750-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="db750-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="db750-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="db750-105">Syntax</span></span>

```xml
<TableRowEntries>
  <TableRowEntry>...</TableRowEntry>
</TableRowEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="db750-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="db750-106">Attributes and Elements</span></span>

<span data-ttu-id="db750-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `TableRowEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="db750-107">The following sections describe the attributes, child elements, and parent element of the `TableRowEntries` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="db750-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="db750-108">Attributes</span></span>

<span data-ttu-id="db750-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="db750-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="db750-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="db750-110">Child Elements</span></span>

|<span data-ttu-id="db750-111">Element</span><span class="sxs-lookup"><span data-stu-id="db750-111">Element</span></span>|<span data-ttu-id="db750-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="db750-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db750-113">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="db750-113">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)|<span data-ttu-id="db750-114">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="db750-114">Required element.</span></span><br /><br /> <span data-ttu-id="db750-115">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="db750-115">Defines the data that is displayed in a row of the table.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="db750-116">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="db750-116">Parent Elements</span></span>

|<span data-ttu-id="db750-117">Element</span><span class="sxs-lookup"><span data-stu-id="db750-117">Element</span></span>|<span data-ttu-id="db750-118">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="db750-118">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="db750-119">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="db750-119">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)|<span data-ttu-id="db750-120">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="db750-120">Defines a table format for a view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="db750-121">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="db750-121">Remarks</span></span>

<span data-ttu-id="db750-122">Du måste ange ett eller flera `TableRowEntry` element för tabellvy.</span><span class="sxs-lookup"><span data-stu-id="db750-122">You must specify one or more `TableRowEntry` elements for the table view.</span></span> <span data-ttu-id="db750-123">Det finns ingen övre gräns för antalet `TableRowEntry`-element som kan läggas till eller är deras inbördes ordning.</span><span class="sxs-lookup"><span data-stu-id="db750-123">There is no maximum limit to the number of `TableRowEntry` elements that can be added nor is their order significant.</span></span>

<span data-ttu-id="db750-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="db750-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="db750-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="db750-125">Example</span></span>

<span data-ttu-id="db750-126">I följande exempel visas ett `TableRowEntries`-element som definierar en rad som visar värdena för två egenskaper för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="db750-126">The following example shows a `TableRowEntries` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="db750-127">Se även</span><span class="sxs-lookup"><span data-stu-id="db750-127">See Also</span></span>

[<span data-ttu-id="db750-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="db750-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="db750-129">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="db750-129">TableControl Element (Format)</span></span>](./tablecontrol-element-format.md)

[<span data-ttu-id="db750-130">TableRowEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="db750-130">TableRowEntry Element (Format)</span></span>](./tablerowentry-element-for-tablerowentries-for-tablecontrol-format.md)

[<span data-ttu-id="db750-131">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="db750-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
