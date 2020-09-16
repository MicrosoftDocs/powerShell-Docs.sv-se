---
title: TableColumnItem-element för TableColumnItems för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: beadf771f02519394d799a03db374050e3302321
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785174"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="ef119-102">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="ef119-103">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="ef119-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="ef119-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element för TableControl (format) TableRowEntry-element för TableRowEntries för TableControl (format) TableColumnItems-element för TableControlEntry (format) TableControl-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ef119-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef119-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <FormatString>FormatPattern</FormatString>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef119-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ef119-106">Attributes and Elements</span></span>

<span data-ttu-id="ef119-107">I följande avsnitt beskrivs attributen, underordnade element och `TableColumnItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ef119-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef119-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="ef119-108">Attributes</span></span>

<span data-ttu-id="ef119-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="ef119-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef119-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ef119-110">Child Elements</span></span>

|<span data-ttu-id="ef119-111">Element</span><span class="sxs-lookup"><span data-stu-id="ef119-111">Element</span></span>|<span data-ttu-id="ef119-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ef119-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef119-113">Alignment-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ef119-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ef119-114">Optional element.</span></span><br /><br /> <span data-ttu-id="ef119-115">Definierar hur data i en kolumn i raden visas.</span><span class="sxs-lookup"><span data-stu-id="ef119-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="ef119-116">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ef119-117">Anger ett format mönster som används för att formatera data i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="ef119-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="ef119-118">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ef119-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ef119-119">Optional element.</span></span><br /><br /> <span data-ttu-id="ef119-120">Anger namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="ef119-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="ef119-121">ScriptBlock-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="ef119-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ef119-122">Optional element.</span></span><br /><br /> <span data-ttu-id="ef119-123">Anger det skript vars värde visas i kolumnen i en rad.</span><span class="sxs-lookup"><span data-stu-id="ef119-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef119-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ef119-124">Parent Elements</span></span>

|<span data-ttu-id="ef119-125">Element</span><span class="sxs-lookup"><span data-stu-id="ef119-125">Element</span></span>|<span data-ttu-id="ef119-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ef119-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef119-127">TableColumnItems-element för TableControlEntry för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="ef119-128">Definierar de egenskaper eller skript vars värden visas på raden.</span><span class="sxs-lookup"><span data-stu-id="ef119-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef119-129">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ef119-129">Remarks</span></span>

<span data-ttu-id="ef119-130">Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="ef119-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="ef119-131">Om inga underordnade element anges, är objektet en plats hållare och inga data visas.</span><span class="sxs-lookup"><span data-stu-id="ef119-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="ef119-132">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="ef119-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ef119-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="ef119-133">Example</span></span>

<span data-ttu-id="ef119-134">Det här exemplet visar ett- `TableColumnItem` element som visar värdet på `Status` egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="ef119-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="ef119-135">Se även</span><span class="sxs-lookup"><span data-stu-id="ef119-135">See Also</span></span>

[<span data-ttu-id="ef119-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="ef119-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ef119-137">Alignment-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ef119-138">TableColumnItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="ef119-139">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ef119-140">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ef119-141">ScriptBlock-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="ef119-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="ef119-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ef119-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
