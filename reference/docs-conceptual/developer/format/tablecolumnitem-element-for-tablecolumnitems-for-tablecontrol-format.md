---
ms.date: 09/13/2016
ms.topic: reference
title: TableColumnItem-element för TableColumnItems för TableControl (format)
description: TableColumnItem-element för TableColumnItems för TableControl (format)
ms.openlocfilehash: 8ef5158c9bb9f074d5c58190d4d3b20c10c83744
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92659849"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="2ce3a-103">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-103">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="2ce3a-104">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-104">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="2ce3a-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format) TableControl-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2ce3a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2ce3a-106">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2ce3a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2ce3a-107">Attributes and Elements</span></span>

<span data-ttu-id="2ce3a-108">I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-108">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2ce3a-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2ce3a-109">Attributes</span></span>

<span data-ttu-id="2ce3a-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2ce3a-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2ce3a-111">Child Elements</span></span>

|<span data-ttu-id="2ce3a-112">Element</span><span class="sxs-lookup"><span data-stu-id="2ce3a-112">Element</span></span>|<span data-ttu-id="2ce3a-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ce3a-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ce3a-114">Alignment-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-114">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="2ce3a-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-115">Optional element.</span></span><br /><br /> <span data-ttu-id="2ce3a-116">Definierar hur data i en kolumn i raden visas.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-116">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="2ce3a-117">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-117">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="2ce3a-118">Anger ett format mönster som används för att formatera data i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-118">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="2ce3a-119">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-119">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="2ce3a-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-120">Optional element.</span></span><br /><br /> <span data-ttu-id="2ce3a-121">Anger namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-121">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="2ce3a-122">ScriptBlock-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-122">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="2ce3a-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-123">Optional element.</span></span><br /><br /> <span data-ttu-id="2ce3a-124">Anger det skript vars värde visas i kolumnen i en rad.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-124">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="2ce3a-125">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2ce3a-125">Parent Elements</span></span>

|<span data-ttu-id="2ce3a-126">Element</span><span class="sxs-lookup"><span data-stu-id="2ce3a-126">Element</span></span>|<span data-ttu-id="2ce3a-127">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2ce3a-127">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2ce3a-128">TableColumnItems-element för TableControlEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-128">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="2ce3a-129">Definierar de egenskaper eller skript vars värden visas på raden.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-129">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="2ce3a-130">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2ce3a-130">Remarks</span></span>

<span data-ttu-id="2ce3a-131">Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-131">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="2ce3a-132">Om inga underordnade element anges, är objektet en plats hållare och inga data visas.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-132">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="2ce3a-133">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2ce3a-133">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2ce3a-134">Exempel</span><span class="sxs-lookup"><span data-stu-id="2ce3a-134">Example</span></span>

<span data-ttu-id="2ce3a-135">Det här exemplet visar ett- `TableColumnItem` element som visar värdet på `Status` egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="2ce3a-135">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="2ce3a-136">Se även</span><span class="sxs-lookup"><span data-stu-id="2ce3a-136">See Also</span></span>

[<span data-ttu-id="2ce3a-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="2ce3a-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2ce3a-138">Alignment-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-138">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="2ce3a-139">TableColumnItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-139">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="2ce3a-140">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-140">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="2ce3a-141">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-141">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="2ce3a-142">ScriptBlock-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2ce3a-142">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="2ce3a-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2ce3a-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
