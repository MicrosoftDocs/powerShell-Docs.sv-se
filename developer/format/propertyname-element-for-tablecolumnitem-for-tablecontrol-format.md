---
title: PropertyName-Element för TableColumnItem för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62064622"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="99d7f-102">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="99d7f-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="99d7f-103">Anger egenskapen vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="99d7f-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="99d7f-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem konfigurationselement (Format) PropertyName-Element för TableColumnItem (Format)</span><span class="sxs-lookup"><span data-stu-id="99d7f-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="99d7f-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="99d7f-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="99d7f-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="99d7f-106">Attributes and Elements</span></span>

<span data-ttu-id="99d7f-107">I följande avsnitt beskrivs attribut, underordnade element och överordnade elementet i den `PropertyName` element.</span><span class="sxs-lookup"><span data-stu-id="99d7f-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="99d7f-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="99d7f-108">Attributes</span></span>

<span data-ttu-id="99d7f-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="99d7f-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="99d7f-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="99d7f-110">Child Elements</span></span>

<span data-ttu-id="99d7f-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="99d7f-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="99d7f-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="99d7f-112">Parent Elements</span></span>

|<span data-ttu-id="99d7f-113">Element</span><span class="sxs-lookup"><span data-stu-id="99d7f-113">Element</span></span>|<span data-ttu-id="99d7f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="99d7f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="99d7f-115">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="99d7f-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="99d7f-116">Definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="99d7f-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="99d7f-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="99d7f-117">Text Value</span></span>

<span data-ttu-id="99d7f-118">Ange namnet på egenskapen vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="99d7f-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="99d7f-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="99d7f-119">Remarks</span></span>

<span data-ttu-id="99d7f-120">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="99d7f-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="99d7f-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="99d7f-121">Example</span></span>

<span data-ttu-id="99d7f-122">Det här exemplet visar en `TableColumnItem` element som anger den `Status` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="99d7f-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="99d7f-123">Se även</span><span class="sxs-lookup"><span data-stu-id="99d7f-123">See Also</span></span>

[<span data-ttu-id="99d7f-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="99d7f-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="99d7f-125">TableColumnItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="99d7f-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="99d7f-126">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="99d7f-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
