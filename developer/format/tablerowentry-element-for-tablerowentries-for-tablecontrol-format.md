---
title: TableRowEntry Element för TableRowEntries för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 18d86af7-7ff9-4968-81be-2caa61937d49
caps.latest.revision: 10
ms.openlocfilehash: 946ffb3fe857503c02b9000238a86775969abbd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62075332"
---
# <a name="tablerowentry-element-for-tablerowentries-for-tablecontrol-format"></a><span data-ttu-id="82803-102">TableRowEntry-element för TableRowEntries för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="82803-102">TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

<span data-ttu-id="82803-103">Definierar de data som visas i en rad i tabellen.</span><span class="sxs-lookup"><span data-stu-id="82803-103">Defines the data that is displayed in a row of the table.</span></span>

<span data-ttu-id="82803-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="82803-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="82803-105">Syntax</span></span>

```xml
<TableRowEntry>
  <Wrap/>
  <EntrySelectedBy>...</EntrySelectedBy>
  <TableColumnItems>...</TableColumnItems>
</TableRowEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="82803-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="82803-106">Attributes and Elements</span></span>

<span data-ttu-id="82803-107">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `TableRowEntry` element.</span><span class="sxs-lookup"><span data-stu-id="82803-107">The following sections describe attributes, child elements, and parent element of the `TableRowEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="82803-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="82803-108">Attributes</span></span>

<span data-ttu-id="82803-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="82803-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="82803-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="82803-110">Child Elements</span></span>

|<span data-ttu-id="82803-111">Element</span><span class="sxs-lookup"><span data-stu-id="82803-111">Element</span></span>|<span data-ttu-id="82803-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82803-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82803-113">EntrySelectedBy Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-113">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="82803-114">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="82803-114">Required element.</span></span><br /><br /> <span data-ttu-id="82803-115">Definierar de objekt vars egenskapsvärden visas i raden.</span><span class="sxs-lookup"><span data-stu-id="82803-115">Defines the objects whose property values are displayed in the row.</span></span>|
|[<span data-ttu-id="82803-116">TableColumnItems Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-116">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="82803-117">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="82803-117">Required element.</span></span><br /><br /> <span data-ttu-id="82803-118">Definierar egenskaper eller skript som vars värden visas.</span><span class="sxs-lookup"><span data-stu-id="82803-118">Defines the properties or scripts whose values are displayed.</span></span>|
|[<span data-ttu-id="82803-119">Omsluta Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-119">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="82803-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="82803-120">Optional element.</span></span><br /><br /> <span data-ttu-id="82803-121">Anger att text som överskrider kolumnbredden visas på nästa rad.</span><span class="sxs-lookup"><span data-stu-id="82803-121">Specifies that text that exceeds the column width is displayed on the next line.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="82803-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="82803-122">Parent Elements</span></span>

|<span data-ttu-id="82803-123">Element</span><span class="sxs-lookup"><span data-stu-id="82803-123">Element</span></span>|<span data-ttu-id="82803-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="82803-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="82803-125">TableRowEntries Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="82803-126">Definierar raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="82803-126">Defines the rows of the table.</span></span>|

## <a name="remarks"></a><span data-ttu-id="82803-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="82803-127">Remarks</span></span>

<span data-ttu-id="82803-128">En `TableColumnItems` element och en `EntrySelectedBy` element måste anges.</span><span class="sxs-lookup"><span data-stu-id="82803-128">One `TableColumnItems` element and one `EntrySelectedBy` element must be specified.</span></span>

<span data-ttu-id="82803-129">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="82803-129">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="82803-130">Exempel</span><span class="sxs-lookup"><span data-stu-id="82803-130">Example</span></span>

<span data-ttu-id="82803-131">I följande exempel visas en `TableRowEntry` element som definierar en rad som visar värdena för två egenskaper för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="82803-131">The following example shows a `TableRowEntry` element that defines a row that displays the values of two properties of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
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
```

## <a name="see-also"></a><span data-ttu-id="82803-132">Se även</span><span class="sxs-lookup"><span data-stu-id="82803-132">See Also</span></span>

[<span data-ttu-id="82803-133">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="82803-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="82803-134">EntrySelectedBy Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-134">EntrySelectedBy Element for TableRowEntry for TableControl (Format)</span></span>](./entryselectedby-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="82803-135">TableColumnItems Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-135">TableColumnItems Element for TableRowEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="82803-136">TableRowEntries Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-136">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="82803-137">Omsluta Element för TableRowEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="82803-137">Wrap Element for TableRowEntry for TableControl (Format)</span></span>](./wrap-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="82803-138">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="82803-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
