---
title: FormatString-Element för TableColumnItem för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 8a150731-d4b4-4d63-8db5-f14d463c8c37
caps.latest.revision: 13
ms.openlocfilehash: b7e1d0adc43254141056a729e1c1cc9699b6ac9b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065645"
---
# <a name="formatstring-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="634ac-102">FormatString-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="634ac-102">FormatString Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="634ac-103">Anger ett formatmönster som definierar hur värdet för egenskapen eller ett skript för tabellen visas.</span><span class="sxs-lookup"><span data-stu-id="634ac-103">Specifies a format pattern that defines how the property or script value of the table is displayed.</span></span>

<span data-ttu-id="634ac-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem konfigurationselement (Format) FormatString-Element för TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="634ac-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) FormatString Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="634ac-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="634ac-105">Syntax</span></span>

```xml
<FormatString>FormatPattern</FormatString>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="634ac-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="634ac-106">Attributes and Elements</span></span>

<span data-ttu-id="634ac-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `FormatString` element.</span><span class="sxs-lookup"><span data-stu-id="634ac-107">The following sections describe attributes, child elements, and the parent element of the `FormatString` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="634ac-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="634ac-108">Attributes</span></span>

<span data-ttu-id="634ac-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="634ac-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="634ac-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="634ac-110">Child Elements</span></span>

<span data-ttu-id="634ac-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="634ac-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="634ac-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="634ac-112">Parent Elements</span></span>

|<span data-ttu-id="634ac-113">Element</span><span class="sxs-lookup"><span data-stu-id="634ac-113">Element</span></span>|<span data-ttu-id="634ac-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="634ac-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="634ac-115">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="634ac-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="634ac-116">Definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="634ac-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="634ac-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="634ac-117">Text Value</span></span>

<span data-ttu-id="634ac-118">Ange mönstret som används för att formatera data.</span><span class="sxs-lookup"><span data-stu-id="634ac-118">Specify the pattern that is used to format the data.</span></span> <span data-ttu-id="634ac-119">Det här mönstret kan till exempel användas för att formatera värdet för en egenskap som är av typen [System.Timespan](/dotnet/api/System.TimeSpan): {0: MMM} {0:dd} {0:HH}: {0:mm}.</span><span class="sxs-lookup"><span data-stu-id="634ac-119">For example, this pattern can be used to format the value of any property that is of type [System.Timespan](/dotnet/api/System.TimeSpan): {0:MMM}{0:dd}{0:HH}:{0:mm}.</span></span>

## <a name="remarks"></a><span data-ttu-id="634ac-120">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="634ac-120">Remarks</span></span>

<span data-ttu-id="634ac-121">Formatsträngar kan användas när du skapar tabellvyer, listvyer, brett vyer eller anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="634ac-121">Format strings can be used when creating table views, list views, wide views, or custom views.</span></span> <span data-ttu-id="634ac-122">Mer information om hur du formaterar ett värde som visas i en vy finns i [formatering visas Data](./formatting-displayed-data.md).</span><span class="sxs-lookup"><span data-stu-id="634ac-122">For more information about formatting a value displayed in a view, see [Formatting Displayed Data](./formatting-displayed-data.md).</span></span>

<span data-ttu-id="634ac-123">Läs mer om komponenterna i en tabellvy, [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="634ac-123">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="634ac-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="634ac-124">Example</span></span>

<span data-ttu-id="634ac-125">I följande exempel visas hur du definierar en formateringssträngen för värdet för den `StartTime` egenskapen.</span><span class="sxs-lookup"><span data-stu-id="634ac-125">The following example shows how to define a formatting string for the value of the `StartTime` property.</span></span>

```xml
<TableColumnItem>
  <PropertyName>StartTime</PropertyName>
  <FormatString>{0:MMM} (0:DD) (0:HH):(0:MM)</FormatString>
</TableColumnItem>
```

## <a name="see-also"></a><span data-ttu-id="634ac-126">Se även</span><span class="sxs-lookup"><span data-stu-id="634ac-126">See Also</span></span>

[<span data-ttu-id="634ac-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="634ac-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="634ac-128">Formatering visas Data</span><span class="sxs-lookup"><span data-stu-id="634ac-128">Formatting Displayed Data</span></span>](./formatting-displayed-data.md)

[<span data-ttu-id="634ac-129">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="634ac-129">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="634ac-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="634ac-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
