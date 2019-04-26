---
title: Justering Element för TableColumnHeader för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ff85e83a-c9c2-4c37-accc-e6a27c182f3c
caps.latest.revision: 19
ms.openlocfilehash: 16b41535109ca503e679a135f5ba30054e33de5b
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62067016"
---
# <a name="alignment-element-for-tablecolumnheader-for-tablecontrol-format"></a><span data-ttu-id="f5328-102">Alignment-element för TableColumnHeader för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f5328-102">Alignment Element for TableColumnHeader for TableControl (Format)</span></span>

<span data-ttu-id="f5328-103">Definierar hur data i en kolumnrubrik visas.</span><span class="sxs-lookup"><span data-stu-id="f5328-103">Defines how the data in a column header is displayed.</span></span>

<span data-ttu-id="f5328-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) justering konfigurationselement för TableColumnHeader (Format)</span><span class="sxs-lookup"><span data-stu-id="f5328-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableHeaders Element (Format) TableColumnHeader Element (Format) Alignment Element for TableColumnHeader (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f5328-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f5328-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f5328-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f5328-106">Attributes and Elements</span></span>

<span data-ttu-id="f5328-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `Alignment` element.</span><span class="sxs-lookup"><span data-stu-id="f5328-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f5328-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f5328-108">Attributes</span></span>

<span data-ttu-id="f5328-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5328-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f5328-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f5328-110">Child Elements</span></span>

<span data-ttu-id="f5328-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f5328-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f5328-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f5328-112">Parent Elements</span></span>

|<span data-ttu-id="f5328-113">Element</span><span class="sxs-lookup"><span data-stu-id="f5328-113">Element</span></span>|<span data-ttu-id="f5328-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f5328-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f5328-115">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f5328-115">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)|<span data-ttu-id="f5328-116">Definierar en etikett, bredd och justering av data för en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="f5328-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f5328-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f5328-117">Text Value</span></span>

<span data-ttu-id="f5328-118">Ange ett av följande värden.</span><span class="sxs-lookup"><span data-stu-id="f5328-118">Specify one of the following values.</span></span> <span data-ttu-id="f5328-119">Dessa värden är inte skiftlägeskänsliga.</span><span class="sxs-lookup"><span data-stu-id="f5328-119">These values are not case-sensitive.</span></span>

<span data-ttu-id="f5328-120">Vänsterjusterar data som visas i kolumnen till vänster detta är standardvärdet om det här elementet inte har angetts.</span><span class="sxs-lookup"><span data-stu-id="f5328-120">Left Aligns the data displayed in the column on the left This is the default if this element is not specified.</span></span>

<span data-ttu-id="f5328-121">Högerjusterar data visas i kolumnen till höger.</span><span class="sxs-lookup"><span data-stu-id="f5328-121">Right Aligns the data displayed in the column on the right.</span></span>

<span data-ttu-id="f5328-122">Center Datacenter data som visas i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="f5328-122">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="f5328-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f5328-123">Remarks</span></span>

<span data-ttu-id="f5328-124">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f5328-124">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f5328-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="f5328-125">Example</span></span>

<span data-ttu-id="f5328-126">Det här exemplet visar en `TableColumnHeader` element vars data justeras till vänster.</span><span class="sxs-lookup"><span data-stu-id="f5328-126">This example shows a `TableColumnHeader` element whose data is aligned on the left.</span></span>

```xml
<TableColumnHeader>
  <Label>Column 1</Label)
  <Width>16</Width>
  <Alignment>Left</Alignment>
</TableColumnHeader>
```

## <a name="see-also"></a><span data-ttu-id="f5328-127">Se även</span><span class="sxs-lookup"><span data-stu-id="f5328-127">See Also</span></span>

[<span data-ttu-id="f5328-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="f5328-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f5328-129">TableColumnHeader Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f5328-129">TableColumnHeader Element (Format)</span></span>](./tablecolumnheader-element-format.md)

[<span data-ttu-id="f5328-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="f5328-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
