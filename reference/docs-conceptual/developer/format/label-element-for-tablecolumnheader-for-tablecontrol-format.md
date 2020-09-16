---
title: Etikett element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: b7b1d6825d3bca0e36b230415d19c2ac48377a46
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785752"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="67bb3-102">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="67bb3-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="67bb3-103">Definierar etiketten som visas överst i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="67bb3-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="67bb3-104">Det här elementet används när du definierar en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="67bb3-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="67bb3-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element för TableHeaders för TableControl (format) etikett element för TableColumnHeader (format)</span><span class="sxs-lookup"><span data-stu-id="67bb3-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67bb3-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="67bb3-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="67bb3-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="67bb3-107">Attributes and Elements</span></span>

<span data-ttu-id="67bb3-108">I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="67bb3-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="67bb3-109">Endast en etikett tillåts för varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="67bb3-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="67bb3-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="67bb3-110">Attributes</span></span>

<span data-ttu-id="67bb3-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="67bb3-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67bb3-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="67bb3-112">Child Elements</span></span>

<span data-ttu-id="67bb3-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="67bb3-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67bb3-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="67bb3-114">Parent Elements</span></span>

|<span data-ttu-id="67bb3-115">Element</span><span class="sxs-lookup"><span data-stu-id="67bb3-115">Element</span></span>|<span data-ttu-id="67bb3-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67bb3-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67bb3-117">TableColumnHeader-element för TableHeaders för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="67bb3-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="67bb3-118">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="67bb3-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67bb3-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="67bb3-119">Text Value</span></span>

<span data-ttu-id="67bb3-120">Ange texten som visas överst i kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="67bb3-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="67bb3-121">Det finns inga begränsade tecken för kolumn etiketten.</span><span class="sxs-lookup"><span data-stu-id="67bb3-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="67bb3-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="67bb3-122">Remarks</span></span>

<span data-ttu-id="67bb3-123">Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.</span><span class="sxs-lookup"><span data-stu-id="67bb3-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="67bb3-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="67bb3-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67bb3-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="67bb3-125">Example</span></span>

<span data-ttu-id="67bb3-126">Det här exemplet visar ett `TableColumnHeader` element vars etikett är "kolumn 1".</span><span class="sxs-lookup"><span data-stu-id="67bb3-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="67bb3-127">Se även</span><span class="sxs-lookup"><span data-stu-id="67bb3-127">See Also</span></span>

[<span data-ttu-id="67bb3-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="67bb3-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="67bb3-129">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="67bb3-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="67bb3-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="67bb3-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
