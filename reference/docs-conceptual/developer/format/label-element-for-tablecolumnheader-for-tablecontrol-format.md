---
title: Etikett element för TableColumnHeader för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72356044"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="4fed2-102">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4fed2-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="4fed2-103">Definierar etiketten som visas överst i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="4fed2-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="4fed2-104">Det här elementet används när du definierar en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="4fed2-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="4fed2-105">Konfigurations element (format) ViewDefinitions element (format) View element (format) TableControl element (format) TableHeaders-element för TableControl (format) TableColumnHeader element för TableHeaders för TableControl (format) etikett element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4fed2-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="4fed2-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="4fed2-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="4fed2-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="4fed2-107">Attributes and Elements</span></span>

<span data-ttu-id="4fed2-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `Label`.</span><span class="sxs-lookup"><span data-stu-id="4fed2-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="4fed2-109">Endast en etikett tillåts för varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="4fed2-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="4fed2-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="4fed2-110">Attributes</span></span>

<span data-ttu-id="4fed2-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4fed2-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="4fed2-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="4fed2-112">Child Elements</span></span>

<span data-ttu-id="4fed2-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="4fed2-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="4fed2-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="4fed2-114">Parent Elements</span></span>

|<span data-ttu-id="4fed2-115">Element</span><span class="sxs-lookup"><span data-stu-id="4fed2-115">Element</span></span>|<span data-ttu-id="4fed2-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="4fed2-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="4fed2-117">TableColumnHeader-element för TableHeaders för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="4fed2-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="4fed2-118">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4fed2-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="4fed2-119">Text värde</span><span class="sxs-lookup"><span data-stu-id="4fed2-119">Text Value</span></span>

<span data-ttu-id="4fed2-120">Ange texten som visas överst i kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="4fed2-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="4fed2-121">Det finns inga begränsade tecken för kolumn etiketten.</span><span class="sxs-lookup"><span data-stu-id="4fed2-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="4fed2-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="4fed2-122">Remarks</span></span>

<span data-ttu-id="4fed2-123">Om ingen etikett anges används namnet på den egenskap vars värde visas i raderna.</span><span class="sxs-lookup"><span data-stu-id="4fed2-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="4fed2-124">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="4fed2-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="4fed2-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="4fed2-125">Example</span></span>

<span data-ttu-id="4fed2-126">Det här exemplet visar ett `TableColumnHeader`-element vars etikett är "kolumn 1".</span><span class="sxs-lookup"><span data-stu-id="4fed2-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="4fed2-127">Se även</span><span class="sxs-lookup"><span data-stu-id="4fed2-127">See Also</span></span>

[<span data-ttu-id="4fed2-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="4fed2-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="4fed2-129">TableColumnHeader-element (format)</span><span class="sxs-lookup"><span data-stu-id="4fed2-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="4fed2-130">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="4fed2-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
