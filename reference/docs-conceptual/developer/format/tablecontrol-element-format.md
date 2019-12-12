---
title: TableControl-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: 3942c008e026b0b99db3c77af4a0152b50fffc4e
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72358795"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="415bb-102">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-102">TableControl Element (Format)</span></span>

<span data-ttu-id="415bb-103">Definierar ett tabell format för en vy.</span><span class="sxs-lookup"><span data-stu-id="415bb-103">Defines a table format for a view.</span></span>

<span data-ttu-id="415bb-104">ViewDefinitions-element (format) Visa element (format) TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="415bb-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="415bb-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="415bb-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="415bb-106">Attributes and Elements</span></span>

<span data-ttu-id="415bb-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `TableControl`-elementet.</span><span class="sxs-lookup"><span data-stu-id="415bb-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="415bb-108">Du måste ange raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="415bb-108">You must specify the rows of the table.</span></span> <span data-ttu-id="415bb-109">Alla andra underordnade element är valfria.</span><span class="sxs-lookup"><span data-stu-id="415bb-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="415bb-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="415bb-110">Attributes</span></span>

<span data-ttu-id="415bb-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="415bb-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="415bb-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="415bb-112">Child Elements</span></span>

|<span data-ttu-id="415bb-113">Element</span><span class="sxs-lookup"><span data-stu-id="415bb-113">Element</span></span>|<span data-ttu-id="415bb-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="415bb-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="415bb-115">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="415bb-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="415bb-116">Optional element.</span></span><br /><br /> <span data-ttu-id="415bb-117">Anger om kolumn storleken och antalet kolumner justeras baserat på data storleken.</span><span class="sxs-lookup"><span data-stu-id="415bb-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="415bb-118">HideTableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="415bb-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="415bb-119">Optional element.</span></span><br /><br /> <span data-ttu-id="415bb-120">Anger om tabellens rubrik inte visas.</span><span class="sxs-lookup"><span data-stu-id="415bb-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="415bb-121">TableHeaders-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="415bb-122">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="415bb-122">Required element.</span></span><br /><br /> <span data-ttu-id="415bb-123">Definierar etiketter, bredder och justering för data för kolumnerna i Tabellvy.</span><span class="sxs-lookup"><span data-stu-id="415bb-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="415bb-124">TableRowEntries-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-124">TableRowEntries Element for TableControl (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="415bb-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="415bb-125">Optional element.</span></span><br /><br /> <span data-ttu-id="415bb-126">Innehåller definitionerna för tabellvy.</span><span class="sxs-lookup"><span data-stu-id="415bb-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="415bb-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="415bb-127">Parent Elements</span></span>

|<span data-ttu-id="415bb-128">Element</span><span class="sxs-lookup"><span data-stu-id="415bb-128">Element</span></span>|<span data-ttu-id="415bb-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="415bb-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="415bb-130">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="415bb-131">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="415bb-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="415bb-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="415bb-132">Remarks</span></span>

<span data-ttu-id="415bb-133">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="415bb-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="415bb-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="415bb-134">Example</span></span>

<span data-ttu-id="415bb-135">I det här exemplet visas ett `TableControl`-element som används för att visa egenskaperna för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="415bb-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="415bb-136">Se även</span><span class="sxs-lookup"><span data-stu-id="415bb-136">See Also</span></span>

[<span data-ttu-id="415bb-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="415bb-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="415bb-138">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="415bb-139">AutoSize-element för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="415bb-140">HideTableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="415bb-141">TableHeaders-element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="415bb-142">TableRowEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="415bb-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="415bb-143">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="415bb-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
