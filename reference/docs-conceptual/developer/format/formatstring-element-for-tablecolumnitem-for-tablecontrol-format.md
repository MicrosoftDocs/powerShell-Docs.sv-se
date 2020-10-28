---
ms.date: 09/13/2016
ms.topic: reference
title: FormatString-element för TableColumnItem för TableControl (format)
description: FormatString-element för TableColumnItem för TableControl (format)
ms.openlocfilehash: 3d386e61ac321c05e0b298019c2298f76b391b21
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667903"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="20486-103">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="20486-103">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="20486-104">Anger ett format mönster som definierar hur tabellens egenskaps-eller skript värde visas.</span><span class="sxs-lookup"><span data-stu-id="20486-104">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="20486-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem element (format) FormatString-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="20486-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="20486-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="20486-106">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="20486-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="20486-107">Attributes and Elements</span></span>

<span data-ttu-id="20486-108">I följande avsnitt beskrivs attribut, underordnade element och `FormatString` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="20486-108">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="20486-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="20486-109">Attributes</span></span>

<span data-ttu-id="20486-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="20486-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="20486-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="20486-111">Child Elements</span></span>

<span data-ttu-id="20486-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="20486-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="20486-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="20486-113">Parent Elements</span></span>

|<span data-ttu-id="20486-114">Element</span><span class="sxs-lookup"><span data-stu-id="20486-114">Element</span></span>|<span data-ttu-id="20486-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="20486-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="20486-116">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="20486-116">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="20486-117">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="20486-117">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="20486-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="20486-118">Text Value</span></span>

<span data-ttu-id="20486-119">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="20486-119">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="20486-120">Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="20486-120">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="20486-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="20486-121">Remarks</span></span>

<span data-ttu-id="20486-122">Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="20486-122">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="20486-123">Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="20486-123">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="20486-124">Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="20486-124">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="20486-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="20486-125">Example</span></span>

<span data-ttu-id="20486-126">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="20486-126">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="20486-127">Se även</span><span class="sxs-lookup"><span data-stu-id="20486-127">See Also</span></span>

[<span data-ttu-id="20486-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="20486-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="20486-129">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="20486-129">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="20486-130">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="20486-130">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="20486-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="20486-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
