---
ms.date: 09/13/2016
ms.topic: reference
title: TableControl-element (format)
description: TableControl-element (format)
ms.openlocfilehash: 93e05e22d61504d7781b6f3c07f9a3fd0b3c9e8a
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92651460"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="e7c18-103">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-103">TableControl Element (Format)</span></span>

<span data-ttu-id="e7c18-104">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="e7c18-104">Defines a table format for a view.</span></span>

<span data-ttu-id="e7c18-105">ViewDefinitions-element (format) Visa element (format) TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-105">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e7c18-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e7c18-106">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="e7c18-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e7c18-107">Attributes and Elements</span></span>

<span data-ttu-id="e7c18-108">I följande avsnitt beskrivs attribut, underordnade element och `TableControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e7c18-108">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="e7c18-109">Du måste ange raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="e7c18-109">You must specify the rows of the table.</span></span> <span data-ttu-id="e7c18-110">Alla andra underordnade element är valfria.</span><span class="sxs-lookup"><span data-stu-id="e7c18-110">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="e7c18-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="e7c18-111">Attributes</span></span>

<span data-ttu-id="e7c18-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="e7c18-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e7c18-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e7c18-113">Child Elements</span></span>

|<span data-ttu-id="e7c18-114">Element</span><span class="sxs-lookup"><span data-stu-id="e7c18-114">Element</span></span>|<span data-ttu-id="e7c18-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e7c18-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7c18-116">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-116">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="e7c18-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e7c18-117">Optional element.</span></span><br /><br /> <span data-ttu-id="e7c18-118">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="e7c18-118">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="e7c18-119">HideTableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-119">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="e7c18-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e7c18-120">Optional element.</span></span><br /><br /> <span data-ttu-id="e7c18-121">Anger om tabellens rubrik inte visas.</span><span class="sxs-lookup"><span data-stu-id="e7c18-121">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="e7c18-122">TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-122">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="e7c18-123">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="e7c18-123">Required element.</span></span><br /><br /> <span data-ttu-id="e7c18-124">Definierar etiketter, bredder och justering för data för kolumnerna i Tabellvy.</span><span class="sxs-lookup"><span data-stu-id="e7c18-124">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="e7c18-125">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-125">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="e7c18-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="e7c18-126">Optional element.</span></span><br /><br /> <span data-ttu-id="e7c18-127">Innehåller definitionerna för tabellvy.</span><span class="sxs-lookup"><span data-stu-id="e7c18-127">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="e7c18-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e7c18-128">Parent Elements</span></span>

|<span data-ttu-id="e7c18-129">Element</span><span class="sxs-lookup"><span data-stu-id="e7c18-129">Element</span></span>|<span data-ttu-id="e7c18-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e7c18-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e7c18-131">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-131">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e7c18-132">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="e7c18-132">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="e7c18-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e7c18-133">Remarks</span></span>

<span data-ttu-id="e7c18-134">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e7c18-134">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e7c18-135">Exempel</span><span class="sxs-lookup"><span data-stu-id="e7c18-135">Example</span></span>

<span data-ttu-id="e7c18-136">Det här exemplet visar ett- `TableControl` element som används för att visa egenskaperna för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -objektet.</span><span class="sxs-lookup"><span data-stu-id="e7c18-136">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>
    <TableHeaders>...</TableHeaders>
    <TableRowEntries>...</TableRowEntries>
  </TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="e7c18-137">Se även</span><span class="sxs-lookup"><span data-stu-id="e7c18-137">See Also</span></span>

[<span data-ttu-id="e7c18-138">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="e7c18-138">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e7c18-139">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-139">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e7c18-140">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-140">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="e7c18-141">HideTableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-141">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="e7c18-142">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-142">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="e7c18-143">TableRowEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="e7c18-143">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="e7c18-144">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e7c18-144">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
