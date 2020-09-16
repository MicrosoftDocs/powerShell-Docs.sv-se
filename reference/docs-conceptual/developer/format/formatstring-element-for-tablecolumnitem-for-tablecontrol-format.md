---
title: FormatString-element för TableColumnItem för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 848583e697d0ab7bd5b017c14c47aba3c51a3c17
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781553"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="56338-102">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="56338-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="56338-103">Anger ett format mönster som definierar hur tabellens egenskaps-eller skript värde visas.</span><span class="sxs-lookup"><span data-stu-id="56338-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="56338-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem element (format) FormatString-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="56338-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="56338-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="56338-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="56338-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="56338-106">Attributes and Elements</span></span>

<span data-ttu-id="56338-107">I följande avsnitt beskrivs attribut, underordnade element och `FormatString` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="56338-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="56338-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="56338-108">Attributes</span></span>

<span data-ttu-id="56338-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="56338-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="56338-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="56338-110">Child Elements</span></span>

<span data-ttu-id="56338-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="56338-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="56338-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="56338-112">Parent Elements</span></span>

|<span data-ttu-id="56338-113">Element</span><span class="sxs-lookup"><span data-stu-id="56338-113">Element</span></span>|<span data-ttu-id="56338-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="56338-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="56338-115">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="56338-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="56338-116">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="56338-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="56338-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="56338-117">Text Value</span></span>

<span data-ttu-id="56338-118">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="56338-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="56338-119">Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [system. TimeSpan](/dotnet/api/System.TimeSpan): {0: MMM} {0: DD} {0: hh}: {0: mm}.</span><span class="sxs-lookup"><span data-stu-id="56338-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="56338-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="56338-120">Remarks</span></span>

<span data-ttu-id="56338-121">Format strängar kan användas för att skapa tabellvyer, listvyer, breda vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="56338-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="56338-122">Mer information om hur du formaterar ett värde som visas i en vy finns i [Formatera data som visas](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="56338-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="56338-123">Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="56338-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="56338-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="56338-124">Example</span></span>

<span data-ttu-id="56338-125">I följande exempel visas hur du definierar en format sträng för `StartTime` egenskapens värde.</span><span class="sxs-lookup"><span data-stu-id="56338-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="56338-126">Se även</span><span class="sxs-lookup"><span data-stu-id="56338-126">See Also</span></span>

[<span data-ttu-id="56338-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="56338-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="56338-128">Formatera data som visas</span><span class="sxs-lookup"><span data-stu-id="56338-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="56338-129">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="56338-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="56338-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="56338-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
