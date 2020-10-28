---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för TableColumnItem för TableControl (format)
description: PropertyName-element för TableColumnItem för TableControl (format)
ms.openlocfilehash: e83bbdb96d2755013cb9fe065cb98731ba44917f
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665591"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="b2150-103">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b2150-103">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="b2150-104">Anger den egenskap vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="b2150-104">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="b2150-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem element (format) PropertyName-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="b2150-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b2150-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="b2150-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b2150-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b2150-107">Attributes and Elements</span></span>

<span data-ttu-id="b2150-108">I följande avsnitt beskrivs attribut, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b2150-108">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b2150-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="b2150-109">Attributes</span></span>

<span data-ttu-id="b2150-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="b2150-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b2150-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b2150-111">Child Elements</span></span>

<span data-ttu-id="b2150-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="b2150-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b2150-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b2150-113">Parent Elements</span></span>

|<span data-ttu-id="b2150-114">Element</span><span class="sxs-lookup"><span data-stu-id="b2150-114">Element</span></span>|<span data-ttu-id="b2150-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b2150-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b2150-116">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="b2150-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="b2150-117">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="b2150-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b2150-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b2150-118">Text Value</span></span>

<span data-ttu-id="b2150-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="b2150-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="b2150-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b2150-120">Remarks</span></span>

<span data-ttu-id="b2150-121">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b2150-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b2150-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="b2150-122">Example</span></span>

<span data-ttu-id="b2150-123">Det här exemplet visar ett- `TableColumnItem` element som anger `Status` egenskapen för [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) -objektet.</span><span class="sxs-lookup"><span data-stu-id="b2150-123">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="b2150-124">Se även</span><span class="sxs-lookup"><span data-stu-id="b2150-124">See Also</span></span>

[<span data-ttu-id="b2150-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="b2150-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b2150-126">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="b2150-126">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="b2150-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b2150-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
