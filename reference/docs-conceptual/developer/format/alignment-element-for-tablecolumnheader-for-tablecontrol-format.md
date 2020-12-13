---
ms.date: 09/13/2016
ms.topic: reference
title: Alignment-element för TableColumnHeader för TableControl (format)
description: Alignment-element för TableColumnHeader för TableControl (format)
ms.openlocfilehash: cf8b90c12c28951283b5870186e2c88d427318a5
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666832"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="600c8-103">Alignment-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="600c8-103">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="600c8-104">Definierar hur data i en kolumn rubrik visas.</span><span class="sxs-lookup"><span data-stu-id="600c8-104">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="600c8-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders element (format) TableColumnHeader element (format) justerings element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="600c8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="600c8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="600c8-106">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="600c8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="600c8-107">Attributes and Elements</span></span>

<span data-ttu-id="600c8-108">I följande avsnitt beskrivs attributen, underordnade element och `Alignment` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="600c8-108">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="600c8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="600c8-109">Attributes</span></span>

<span data-ttu-id="600c8-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="600c8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="600c8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="600c8-111">Child Elements</span></span>

<span data-ttu-id="600c8-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="600c8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="600c8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="600c8-113">Parent Elements</span></span>

|<span data-ttu-id="600c8-114">Element</span><span class="sxs-lookup"><span data-stu-id="600c8-114">Element</span></span>|<span data-ttu-id="600c8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="600c8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="600c8-116">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="600c8-116">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="600c8-117">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="600c8-117">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="600c8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="600c8-118">Text Value</span></span>

<span data-ttu-id="600c8-119">Ange ett av följande värden.</span><span class="sxs-lookup"><span data-stu-id="600c8-119">Specify one of the following values.</span></span> <span data-ttu-id="600c8-120">De här värdena är inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="600c8-120">These values are not case-sensitive.</span></span>

<span data-ttu-id="600c8-121">Vänster justerar data som visas i kolumnen till vänster detta är standardvärdet om det här elementet inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="600c8-121">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="600c8-122">Högerjusterar de data som visas i kolumnen till höger.</span><span class="sxs-lookup"><span data-stu-id="600c8-122">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="600c8-123">Center centrerar de data som visas i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="600c8-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="600c8-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="600c8-124">Remarks</span></span>

<span data-ttu-id="600c8-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="600c8-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="600c8-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="600c8-126">Example</span></span>

<span data-ttu-id="600c8-127">I det här exemplet visas ett `TableColumnHeader` element vars data justeras till vänster.</span><span class="sxs-lookup"><span data-stu-id="600c8-127">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="600c8-128">Se även</span><span class="sxs-lookup"><span data-stu-id="600c8-128">See Also</span></span>

[<span data-ttu-id="600c8-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="600c8-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="600c8-130">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="600c8-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="600c8-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="600c8-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
