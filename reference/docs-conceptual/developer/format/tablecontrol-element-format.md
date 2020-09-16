---
title: TableControl-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 34e20006a7501650f2a22f71a3d7e999fb8b2337
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785140"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="26910-102">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-102">TableControl Element (Format)</span></span>

<span data-ttu-id="26910-103">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="26910-103">Defines a table format for a view.</span></span>

<span data-ttu-id="26910-104">ViewDefinitions-element (format) Visa element (format) TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="26910-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="26910-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="26910-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="26910-106">Attributes and Elements</span></span>

<span data-ttu-id="26910-107">I följande avsnitt beskrivs attribut, underordnade element och `TableControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="26910-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="26910-108">Du måste ange raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="26910-108">You must specify the rows of the table.</span></span> <span data-ttu-id="26910-109">Alla andra underordnade element är valfria.</span><span class="sxs-lookup"><span data-stu-id="26910-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="26910-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="26910-110">Attributes</span></span>

<span data-ttu-id="26910-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="26910-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="26910-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="26910-112">Child Elements</span></span>

|<span data-ttu-id="26910-113">Element</span><span class="sxs-lookup"><span data-stu-id="26910-113">Element</span></span>|<span data-ttu-id="26910-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="26910-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26910-115">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="26910-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="26910-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="26910-116">Optional element.</span></span><br /><br /> <span data-ttu-id="26910-117">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="26910-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="26910-118">HideTableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="26910-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="26910-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="26910-119">Optional element.</span></span><br /><br /> <span data-ttu-id="26910-120">Anger om tabellens rubrik inte visas.</span><span class="sxs-lookup"><span data-stu-id="26910-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="26910-121">TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="26910-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="26910-122">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="26910-122">Required element.</span></span><br /><br /> <span data-ttu-id="26910-123">Definierar etiketter, bredder och justering för data för kolumnerna i Tabellvy.</span><span class="sxs-lookup"><span data-stu-id="26910-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="26910-124">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="26910-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="26910-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="26910-125">Optional element.</span></span><br /><br /> <span data-ttu-id="26910-126">Innehåller definitionerna för tabellvy.</span><span class="sxs-lookup"><span data-stu-id="26910-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="26910-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="26910-127">Parent Elements</span></span>

|<span data-ttu-id="26910-128">Element</span><span class="sxs-lookup"><span data-stu-id="26910-128">Element</span></span>|<span data-ttu-id="26910-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="26910-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="26910-130">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="26910-131">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="26910-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="26910-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="26910-132">Remarks</span></span>

<span data-ttu-id="26910-133">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="26910-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="26910-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="26910-134">Example</span></span>

<span data-ttu-id="26910-135">Det här exemplet visar ett- `TableControl` element som används för att visa egenskaperna för [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) -objektet.</span><span class="sxs-lookup"><span data-stu-id="26910-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="26910-136">Se även</span><span class="sxs-lookup"><span data-stu-id="26910-136">See Also</span></span>

[<span data-ttu-id="26910-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="26910-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="26910-138">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="26910-139">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="26910-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="26910-140">HideTableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="26910-141">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="26910-142">TableRowEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="26910-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="26910-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="26910-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
