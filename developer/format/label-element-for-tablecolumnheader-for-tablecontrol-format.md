---
title: Etikettera Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 7196f039-2f6a-41fd-b252-5b1623ebb9f9
caps.latest.revision: 11
ms.openlocfilehash: 59dfd40b95d5088a711eb89cf101eb31a4b159f5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846874"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="76cbe-102">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="76cbe-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="76cbe-103">Definierar den etikett som visas överst i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="76cbe-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="76cbe-104">Det här elementet används när du definierar en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="76cbe-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="76cbe-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet för TableHeaders för TableControl (Format) etikett elementet för TableColumnHeader för TablControl (Format)</span><span class="sxs-lookup"><span data-stu-id="76cbe-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TablControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="76cbe-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="76cbe-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="76cbe-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="76cbe-107">Attributes and Elements</span></span>

<span data-ttu-id="76cbe-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Label` element.</span><span class="sxs-lookup"><span data-stu-id="76cbe-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="76cbe-109">Endast en etikett är tillåten för varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="76cbe-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="76cbe-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="76cbe-110">Attributes</span></span>

<span data-ttu-id="76cbe-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="76cbe-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="76cbe-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="76cbe-112">Child Elements</span></span>

<span data-ttu-id="76cbe-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="76cbe-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="76cbe-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="76cbe-114">Parent Elements</span></span>

|<span data-ttu-id="76cbe-115">Element</span><span class="sxs-lookup"><span data-stu-id="76cbe-115">Element</span></span>|<span data-ttu-id="76cbe-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="76cbe-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="76cbe-117">TableColumnHeader Element för TableHeaders för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="76cbe-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="76cbe-118">Definierar en etikett, bredd och justering av data för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="76cbe-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="76cbe-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="76cbe-119">Text Value</span></span>

<span data-ttu-id="76cbe-120">Ange vilken text som visas överst i kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="76cbe-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="76cbe-121">Det finns inga specialtecken för kolumnetiketten.</span><span class="sxs-lookup"><span data-stu-id="76cbe-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="76cbe-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="76cbe-122">Remarks</span></span>

<span data-ttu-id="76cbe-123">Om ingen etikett har angetts används namnet på egenskapen vars värde visas på raderna.</span><span class="sxs-lookup"><span data-stu-id="76cbe-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="76cbe-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="76cbe-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="76cbe-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="76cbe-125">Example</span></span>

<span data-ttu-id="76cbe-126">Det här exemplet visar en `TableColumnHeader` element vars etikett är ”kolumn 1”.</span><span class="sxs-lookup"><span data-stu-id="76cbe-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="76cbe-127">Se även</span><span class="sxs-lookup"><span data-stu-id="76cbe-127">See Also</span></span>

[<span data-ttu-id="76cbe-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="76cbe-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="76cbe-129">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="76cbe-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="76cbe-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="76cbe-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
