---
ms.date: 09/13/2016
ms.topic: reference
title: Label-element för TableColumnHeader för TableControl (format)
description: Label-element för TableColumnHeader för TableControl (format)
ms.openlocfilehash: fe4c209903c04e683b44e2bdcbf381adb6874ace
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667801"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="b26a2-103">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b26a2-103">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="b26a2-104">Definierar etiketten som visas överst i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="b26a2-104">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="b26a2-105">Det här elementet används när du definierar en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="b26a2-105">This element is used when defining a table view.</span></span>

<span data-ttu-id="b26a2-106">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element för TableHeaders för TableControl (format) etikett element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="b26a2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b26a2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="b26a2-107">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="b26a2-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b26a2-108">Attributes and Elements</span></span>

<span data-ttu-id="b26a2-109">I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="b26a2-109">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="b26a2-110">Endast en etikett tillåts för varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="b26a2-110">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="b26a2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="b26a2-111">Attributes</span></span>

<span data-ttu-id="b26a2-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="b26a2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b26a2-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b26a2-113">Child Elements</span></span>

<span data-ttu-id="b26a2-114">Inga.</span><span class="sxs-lookup"><span data-stu-id="b26a2-114">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="b26a2-115">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b26a2-115">Parent Elements</span></span>

|<span data-ttu-id="b26a2-116">Element</span><span class="sxs-lookup"><span data-stu-id="b26a2-116">Element</span></span>|<span data-ttu-id="b26a2-117">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b26a2-117">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b26a2-118">TableColumnHeader-element för TableHeaders för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="b26a2-118">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="b26a2-119">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b26a2-119">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="b26a2-120">Textvärde</span><span class="sxs-lookup"><span data-stu-id="b26a2-120">Text Value</span></span>

<span data-ttu-id="b26a2-121">Ange texten som visas överst i kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="b26a2-121">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="b26a2-122">Det finns inga begränsade tecken för kolumn etiketten.</span><span class="sxs-lookup"><span data-stu-id="b26a2-122">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="b26a2-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="b26a2-123">Remarks</span></span>

<span data-ttu-id="b26a2-124">Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.</span><span class="sxs-lookup"><span data-stu-id="b26a2-124">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="b26a2-125">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="b26a2-125">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b26a2-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="b26a2-126">Example</span></span>

<span data-ttu-id="b26a2-127">Det här exemplet visar ett `TableColumnHeader` element vars etikett är "kolumn 1".</span><span class="sxs-lookup"><span data-stu-id="b26a2-127">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="b26a2-128">Se även</span><span class="sxs-lookup"><span data-stu-id="b26a2-128">See Also</span></span>

[<span data-ttu-id="b26a2-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="b26a2-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="b26a2-130">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="b26a2-130">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="b26a2-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="b26a2-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
