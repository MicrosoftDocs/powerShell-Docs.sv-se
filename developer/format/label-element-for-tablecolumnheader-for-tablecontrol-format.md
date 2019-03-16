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
ms.openlocfilehash: 09183a538c179f19347c3f1ed45b4ad38c2ca451
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58054517"
---
# <a name="label-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="608ac-102">Label-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="608ac-102">Label Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="608ac-103">Definierar den etikett som visas överst i en kolumn.</span><span class="sxs-lookup"><span data-stu-id="608ac-103">Defines the label that is displayed at the top of a column.</span></span> <span data-ttu-id="608ac-104">Det här elementet används när du definierar en tabellvy.</span><span class="sxs-lookup"><span data-stu-id="608ac-104">This element is used when defining a table view.</span></span>

<span data-ttu-id="608ac-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders konfigurationselement för TableControl (Format) TableColumnHeader elementet för TableHeaders för TableControl (Format) etikett elementet för TableColumnHeader för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="608ac-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element for TableControl (Format) TableColumnHeader Element for TableHeaders for TableControl (Format) Label Element  for TableColumnHeader for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="608ac-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="608ac-106">Syntax</span></span>

```xml
<Label>DisplayedLabel</Label>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="608ac-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="608ac-107">Attributes and Elements</span></span>

<span data-ttu-id="608ac-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Label` element.</span><span class="sxs-lookup"><span data-stu-id="608ac-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span> <span data-ttu-id="608ac-109">Endast en etikett är tillåten för varje kolumn.</span><span class="sxs-lookup"><span data-stu-id="608ac-109">Only one label is allowed for each column.</span></span>

### <a name="attributes"></a><span data-ttu-id="608ac-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="608ac-110">Attributes</span></span>

<span data-ttu-id="608ac-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="608ac-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="608ac-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="608ac-112">Child Elements</span></span>

<span data-ttu-id="608ac-113">Ingen.</span><span class="sxs-lookup"><span data-stu-id="608ac-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="608ac-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="608ac-114">Parent Elements</span></span>

|<span data-ttu-id="608ac-115">Element</span><span class="sxs-lookup"><span data-stu-id="608ac-115">Element</span></span>|<span data-ttu-id="608ac-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="608ac-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="608ac-117">TableColumnHeader Element för TableHeaders för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="608ac-117">TableColumnHeader Element for TableHeaders for TableControl  (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="608ac-118">Definierar en etikett, bredd och justering av data för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="608ac-118">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="608ac-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="608ac-119">Text Value</span></span>

<span data-ttu-id="608ac-120">Ange vilken text som visas överst i kolumnen i tabellen.</span><span class="sxs-lookup"><span data-stu-id="608ac-120">Specify the text that is displayed at the top of the column of the table.</span></span> <span data-ttu-id="608ac-121">Det finns inga specialtecken för kolumnetiketten.</span><span class="sxs-lookup"><span data-stu-id="608ac-121">There are no restricted characters for the column label.</span></span>

## <a name="remarks"></a><span data-ttu-id="608ac-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="608ac-122">Remarks</span></span>

<span data-ttu-id="608ac-123">Om ingen etikett har angetts används namnet på egenskapen vars värde visas på raderna.</span><span class="sxs-lookup"><span data-stu-id="608ac-123">If no label is specified, the name of the property whose value is displayed in the rows is used.</span></span>

<span data-ttu-id="608ac-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="608ac-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="608ac-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="608ac-125">Example</span></span>

<span data-ttu-id="608ac-126">Det här exemplet visar en `TableColumnHeader` element vars etikett är ”kolumn 1”.</span><span class="sxs-lookup"><span data-stu-id="608ac-126">This example shows a `TableColumnHeader` element whose label is "Column 1".</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="608ac-127">Se även</span><span class="sxs-lookup"><span data-stu-id="608ac-127">See Also</span></span>

[<span data-ttu-id="608ac-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="608ac-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="608ac-129">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="608ac-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="608ac-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="608ac-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
