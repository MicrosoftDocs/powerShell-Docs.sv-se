---
title: Justerings element för TableColumnItem för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b07a53df-64f1-49b0-8cea-c993b3f1f76b
caps.latest.revision: 10
ms.openlocfilehash: 1bc936b94ee6fd6239e9e3c4afcdb8f14fbe36eb
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72359120"
---
# <a name="alignment-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="f7fa6-102">Alignment-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-102">Alignment Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="f7fa6-103">Definierar hur data i en kolumn i raden visas.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-103">Defines how the data in a column of the row is displayed.</span></span>

<span data-ttu-id="f7fa6-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem-element (format) Justerings element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) Alignment Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f7fa6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f7fa6-105">Syntax</span></span>

```xml
<Alignment>AlignmentType</Alignment>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f7fa6-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f7fa6-106">Attributes and Elements</span></span>

<span data-ttu-id="f7fa6-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Alignment`-elementet.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-107">The following sections describe the attributes, child elements, and parent element of the `Alignment` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f7fa6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="f7fa6-108">Attributes</span></span>

<span data-ttu-id="f7fa6-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f7fa6-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f7fa6-110">Child Elements</span></span>

<span data-ttu-id="f7fa6-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f7fa6-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f7fa6-112">Parent Elements</span></span>

|<span data-ttu-id="f7fa6-113">Element</span><span class="sxs-lookup"><span data-stu-id="f7fa6-113">Element</span></span>|<span data-ttu-id="f7fa6-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f7fa6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f7fa6-115">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="f7fa6-116">Definierar en etikett, bredd och justering för data i en kolumn i tabellen.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-116">Defines a label, the width, and the alignment of the data for a column of the table.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f7fa6-117">Text värde</span><span class="sxs-lookup"><span data-stu-id="f7fa6-117">Text Value</span></span>

<span data-ttu-id="f7fa6-118">Ange ett av följande värden.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-118">Specify one of the following values.</span></span> <span data-ttu-id="f7fa6-119">(Dessa värden är inte Skift läges känsliga.)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-119">(These values are not case-sensitive.)</span></span>

<span data-ttu-id="f7fa6-120">Vänster flyttar data som visas i kolumnen till vänster.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-120">Left Shifts the data displayed in the column to the left.</span></span> <span data-ttu-id="f7fa6-121">(Detta är standardvärdet om det här elementet inte anges.)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-121">(This is the default if this element is not specified.)</span></span>

<span data-ttu-id="f7fa6-122">Höger växlar data som visas i kolumnen till höger.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-122">Right Shifts the data displayed in the column to the right.</span></span>

<span data-ttu-id="f7fa6-123">Center centrerar de data som visas i kolumnen.</span><span class="sxs-lookup"><span data-stu-id="f7fa6-123">Center Centers the data displayed in the column.</span></span>

## <a name="remarks"></a><span data-ttu-id="f7fa6-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f7fa6-124">Remarks</span></span>

<span data-ttu-id="f7fa6-125">Mer information om komponenterna i en tabellvy finns i [tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="f7fa6-125">For more information about the components of a table view, see [Table View](./creating-a-table-view.md).</span></span>

## <a name="see-also"></a><span data-ttu-id="f7fa6-126">Se även</span><span class="sxs-lookup"><span data-stu-id="f7fa6-126">See Also</span></span>

[<span data-ttu-id="f7fa6-127">Tabellvy</span><span class="sxs-lookup"><span data-stu-id="f7fa6-127">Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f7fa6-128">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="f7fa6-128">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)
