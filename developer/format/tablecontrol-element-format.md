---
title: TableControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 1550b068-dfbc-4ae0-9aa1-72c9a680ec59
caps.latest.revision: 15
ms.openlocfilehash: dd48e82452e83f93e2e005c9db53bbc51d8b2eb4
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848855"
---
# <a name="tablecontrol-element-format"></a><span data-ttu-id="0dbd0-102">TableControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-102">TableControl Element (Format)</span></span>

<span data-ttu-id="0dbd0-103">Definierar ett tabellformat för en vy.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-103">Defines a table format for a view.</span></span>

<span data-ttu-id="0dbd0-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-104">ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0dbd0-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="0dbd0-105">Syntax</span></span>

```xml
<TableControl>
  <AutoSize/>
  <HideTableHeaders/>
  <TableHeaders>...</TableHeaders>
  <TableRowEntries>...</TableRowEntries>
</TableControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="0dbd0-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0dbd0-106">Attributes and Elements</span></span>

<span data-ttu-id="0dbd0-107">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `TableControl` element.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-107">The following sections describe attributes, child elements, and parent element of the `TableControl` element.</span></span> <span data-ttu-id="0dbd0-108">Du måste ange raderna i tabellen.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-108">You must specify the rows of the table.</span></span> <span data-ttu-id="0dbd0-109">Alla andra underordnade element är valfria.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-109">All other child elements are optional.</span></span>

### <a name="attributes"></a><span data-ttu-id="0dbd0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="0dbd0-110">Attributes</span></span>

<span data-ttu-id="0dbd0-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0dbd0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0dbd0-112">Child Elements</span></span>

|<span data-ttu-id="0dbd0-113">Element</span><span class="sxs-lookup"><span data-stu-id="0dbd0-113">Element</span></span>|<span data-ttu-id="0dbd0-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0dbd0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dbd0-115">AutoSize-Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-115">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)|<span data-ttu-id="0dbd0-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-116">Optional element.</span></span><br /><br /> <span data-ttu-id="0dbd0-117">Anger om kolumnstorlek och antalet kolumner justeras beroende på storleken på data.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-117">Specifies whether the column size and the number of columns are adjusted based on the size of the data.</span></span>|
|[<span data-ttu-id="0dbd0-118">HideTableHeaders Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-118">HideTableHeaders Element for TableControl (Format)</span></span>](./hidetableheaders-element-format.md)|<span data-ttu-id="0dbd0-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-119">Optional element.</span></span><br /><br /> <span data-ttu-id="0dbd0-120">Anger om rubriken för tabellen inte ska visas.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-120">Indicates whether the header of the table is not displayed.</span></span>|
|[<span data-ttu-id="0dbd0-121">TableHeaders Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-121">TableHeaders Element for TableControl (Format)</span></span>](./tableheaders-element-format.md)|<span data-ttu-id="0dbd0-122">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-122">Required element.</span></span><br /><br /> <span data-ttu-id="0dbd0-123">Definierar etiketter, bredderna och justering av data för kolumner i tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-123">Defines the labels, the widths, and the alignment of the data for the columns of the table view.</span></span>|
|[<span data-ttu-id="0dbd0-124">TableRowEntries Element för TableCotrol (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-124">TableRowEntries Element for TableCotrol (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)|<span data-ttu-id="0dbd0-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-125">Optional element.</span></span><br /><br /> <span data-ttu-id="0dbd0-126">Innehåller definitioner av tabellvyn.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-126">Provides the definitions of the table view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0dbd0-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0dbd0-127">Parent Elements</span></span>

|<span data-ttu-id="0dbd0-128">Element</span><span class="sxs-lookup"><span data-stu-id="0dbd0-128">Element</span></span>|<span data-ttu-id="0dbd0-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0dbd0-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0dbd0-130">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-130">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="0dbd0-131">Definierar en vy som används för att visa medlemmarna i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-131">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0dbd0-132">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="0dbd0-132">Remarks</span></span>

<span data-ttu-id="0dbd0-133">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="0dbd0-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0dbd0-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="0dbd0-134">Example</span></span>

<span data-ttu-id="0dbd0-135">Det här exemplet visar en `TableControl` element som används för att visa egenskaperna för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="0dbd0-135">This example shows a `TableControl` element that is used to display the properties of the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="0dbd0-136">Se även</span><span class="sxs-lookup"><span data-stu-id="0dbd0-136">See Also</span></span>

[<span data-ttu-id="0dbd0-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="0dbd0-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="0dbd0-138">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-138">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="0dbd0-139">AutoSize-Element för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-139">AutoSize Element for TableControl (Format)</span></span>](./autosize-element-for-tablecontrol-format.md)

[<span data-ttu-id="0dbd0-140">HideTableHeaders Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-140">HideTableHeaders Element (Format)</span></span>](./hidetableheaders-element-format.md)

[<span data-ttu-id="0dbd0-141">TableHeaders Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-141">TableHeaders Element (Format)</span></span>](./tableheaders-element-format.md)

[<span data-ttu-id="0dbd0-142">TableRowEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="0dbd0-142">TableRowEntries Element (Format)</span></span>](./tablerowentries-element-for-tablecontrol-format.md)

[<span data-ttu-id="0dbd0-143">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="0dbd0-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
