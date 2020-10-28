---
ms.date: 09/13/2016
ms.topic: reference
title: Width-element för TableColumnHeader för TableControl (format)
description: Width-element för TableColumnHeader för TableControl (format)
ms.openlocfilehash: bde84f1d33b3d6b3b8c4462f870f978611cb434b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92658264"
---
# <a name="width-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="2f712-103">Width-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2f712-103">Width Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="2f712-104">Definierar bredden (i tecken) för en kolumn.</span><span class="sxs-lookup"><span data-stu-id="2f712-104">Defines the width (in characters) of a column.</span></span>

<span data-ttu-id="2f712-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element TableHeaders för TableControl (format) width-element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="2f712-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element TableHeaders for TableControl (Format) Width Element for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2f712-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="2f712-106">Syntax</span></span>

```xml
<Width>NumberOfCharacters</Width>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2f712-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2f712-107">Attributes and Elements</span></span>

<span data-ttu-id="2f712-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för det `Width` element som används när kolumn rubriker definieras.</span><span class="sxs-lookup"><span data-stu-id="2f712-108">The following sections describe the attributes, child elements, and parent element of the `Width` element used when defining column headers.</span></span>

### <a name="attributes"></a><span data-ttu-id="2f712-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="2f712-109">Attributes</span></span>

<span data-ttu-id="2f712-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="2f712-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2f712-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2f712-111">Child Elements</span></span>

<span data-ttu-id="2f712-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="2f712-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2f712-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2f712-113">Parent Elements</span></span>

|<span data-ttu-id="2f712-114">Element</span><span class="sxs-lookup"><span data-stu-id="2f712-114">Element</span></span>|<span data-ttu-id="2f712-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2f712-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2f712-116">TableColumnHeader-element för TableHeaders för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2f712-116">TableColumnHeader Element for TableHeaders for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="2f712-117">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="2f712-117">Defines a label, width, and alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2f712-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2f712-118">Text Value</span></span>

<span data-ttu-id="2f712-119">När som helst kan du ange en bredd (i tecken) som är större än längden på de visade egenskapsvärdena.</span><span class="sxs-lookup"><span data-stu-id="2f712-119">When at all possible, specify a width (in characters) that is greater than the length of the displayed property values.</span></span>

## <a name="remarks"></a><span data-ttu-id="2f712-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="2f712-120">Remarks</span></span>

<span data-ttu-id="2f712-121">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="2f712-121">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="2f712-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="2f712-122">Example</span></span>

<span data-ttu-id="2f712-123">I följande exempel visas ett `TableColumnHeader` element vars bredd är 16 tecken.</span><span class="sxs-lookup"><span data-stu-id="2f712-123">The following example shows a `TableColumnHeader` element whose width is 16 characters.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="2f712-124">Se även</span><span class="sxs-lookup"><span data-stu-id="2f712-124">See Also</span></span>

[<span data-ttu-id="2f712-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="2f712-125">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2f712-126">TableColumnHeader-element för TableHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="2f712-126">TableColumnHeader Element for TableHeader for TableControl (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="2f712-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="2f712-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
