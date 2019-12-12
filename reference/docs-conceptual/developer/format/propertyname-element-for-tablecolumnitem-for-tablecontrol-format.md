---
title: PropertyName-element för TableColumnItem för TableControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: fb26d72c-2f77-4801-badf-0537ccc55e31
caps.latest.revision: 10
ms.openlocfilehash: 6e86b6a0874b385703121802bc8108a0410442cd
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354000"
---
# <a name="propertyname-element-for-tablecolumnitem-for-tablecontrol-format"></a><span data-ttu-id="a5dd6-102">PropertyName-element för TableColumnItem för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="a5dd6-102">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>

<span data-ttu-id="a5dd6-103">Anger den egenskap vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-103">Specifies the property whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="a5dd6-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) TableControl-element (format) TableRowEntries-element (format) TableRowEntry-element (format) TableColumnItems element (format) TableColumnItem-element (format) PropertyName-element för TableColumnItem (format)</span><span class="sxs-lookup"><span data-stu-id="a5dd6-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element (Format) TableRowEntry Element (Format) TableColumnItems Element (Format) TableColumnItem Element (Format) PropertyName Element for TableColumnItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a5dd6-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a5dd6-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a5dd6-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a5dd6-106">Attributes and Elements</span></span>

<span data-ttu-id="a5dd6-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-107">The following sections describe attributes, child elements, and parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a5dd6-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a5dd6-108">Attributes</span></span>

<span data-ttu-id="a5dd6-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a5dd6-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a5dd6-110">Child Elements</span></span>

<span data-ttu-id="a5dd6-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a5dd6-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a5dd6-112">Parent Elements</span></span>

|<span data-ttu-id="a5dd6-113">Element</span><span class="sxs-lookup"><span data-stu-id="a5dd6-113">Element</span></span>|<span data-ttu-id="a5dd6-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a5dd6-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a5dd6-115">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="a5dd6-115">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)|<span data-ttu-id="a5dd6-116">Definierar egenskapen eller skriptet vars värde visas i kolumnen på raden.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-116">Defines the property or script whose value is displayed in the column of the row.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a5dd6-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a5dd6-117">Text Value</span></span>

<span data-ttu-id="a5dd6-118">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="a5dd6-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a5dd6-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="a5dd6-119">Remarks</span></span>

<span data-ttu-id="a5dd6-120">Mer information om komponenterna i en tabellvy finns i [skapa en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="a5dd6-120">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a5dd6-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="a5dd6-121">Example</span></span>

<span data-ttu-id="a5dd6-122">I det här exemplet visas ett `TableColumnItem`-element som anger egenskapen `Status` för objektet [system. Diagnostics. process](/dotnet/api/System.Diagnostics.Process) .</span><span class="sxs-lookup"><span data-stu-id="a5dd6-122">This example shows a `TableColumnItem` element that specifies the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="a5dd6-123">Se även</span><span class="sxs-lookup"><span data-stu-id="a5dd6-123">See Also</span></span>

[<span data-ttu-id="a5dd6-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="a5dd6-124">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="a5dd6-125">TableColumnItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="a5dd6-125">TableColumnItem Element (Format)</span></span>](./tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format.md)

[<span data-ttu-id="a5dd6-126">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="a5dd6-126">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
