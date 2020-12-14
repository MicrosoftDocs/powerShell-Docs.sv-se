---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för TableColumnItem för TableControl (format)
description: PropertyName-element för TableColumnItem för TableControl (format)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92665591"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="e5657-103">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="e5657-103">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="e5657-104">Anger den egenskap vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="e5657-104">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="e5657-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem element (format) PropertyName-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="e5657-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e5657-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e5657-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e5657-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e5657-107">Attributes and Elements</span></span>

<span data-ttu-id="e5657-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e5657-108">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e5657-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="e5657-109">Attributes</span></span>

<span data-ttu-id="e5657-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="e5657-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e5657-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e5657-111">Child Elements</span></span>

<span data-ttu-id="e5657-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="e5657-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e5657-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e5657-113">Parent Elements</span></span>

|<span data-ttu-id="e5657-114">Element</span><span class="sxs-lookup"><span data-stu-id="e5657-114">Element</span></span>|<span data-ttu-id="e5657-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e5657-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e5657-116">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="e5657-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="e5657-117">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="e5657-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e5657-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e5657-118">Text Value</span></span>

<span data-ttu-id="e5657-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="e5657-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="e5657-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e5657-120">Remarks</span></span>

<span data-ttu-id="e5657-121">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="e5657-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e5657-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="e5657-122">Example</span></span>

<span data-ttu-id="e5657-123">Det här exemplet visar ett- `TableColumnItem` element som anger `Status` egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="e5657-123">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="e5657-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e5657-124">See Also</span></span>

[<span data-ttu-id="e5657-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="e5657-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e5657-126">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="e5657-126">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="e5657-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e5657-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
