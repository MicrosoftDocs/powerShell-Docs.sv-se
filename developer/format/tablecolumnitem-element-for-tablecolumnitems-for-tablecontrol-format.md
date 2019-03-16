---
title: TableColumnItem Element för TableColumnItems för TableControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: ef8395aa-4b31-48c0-a0b8-b481fd0b3738
caps.latest.revision: 15
ms.openlocfilehash: 159f943f6bfb33c5403b5714380631351523789f
ms.sourcegitcommit: caac7d098a448232304c9d6728e7340ec7517a71
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 03/16/2019
ms.locfileid: "58056999"
---
# <a name="tablecolumnitem-element-for-tablecolumnitems-for-tablecontrol-format"></a><span data-ttu-id="c7ef2-102">TableColumnItem-element för TableColumnItems för TableControl (format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-102">TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

<span data-ttu-id="c7ef2-103">Definierar egenskapen eller skript som vars värde visas i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-103">Defines the property or script whose value is displayed in the column of the row.</span></span>

<span data-ttu-id="c7ef2-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) TableControl Element (Format) TableRowEntries konfigurationselement för TableControl (Format) TableRowEntry elementet för TableRowEntries för TableControl (Format) TableColumnItems Element för TableControlEntry för TableControl (Format) TableColumnItem elementet för TableColumnItems för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) TableControl Element (Format) TableRowEntries Element for TableControl (Format) TableRowEntry Element for TableRowEntries for TableControl (Format) TableColumnItems Element for TableControlEntry for TableControl (Format) TableColumnItem Element for TableColumnItems for TableControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c7ef2-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c7ef2-105">Syntax</span></span>

```xml
<TableColumnItem>
  <Alignment>Left, Right, or Center</Alignment>
  <PropertyName>Nameof.NetProperty</PropertyName>
  <ScriptBlock>ScriptToEvaluate</ScriptBlock>
</TableColumnItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c7ef2-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c7ef2-106">Attributes and Elements</span></span>

<span data-ttu-id="c7ef2-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `TableColumnItem` element.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-107">The following sections describe the attributes, child elements, and parent element of the `TableColumnItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="c7ef2-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="c7ef2-108">Attributes</span></span>

<span data-ttu-id="c7ef2-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c7ef2-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c7ef2-110">Child Elements</span></span>

|<span data-ttu-id="c7ef2-111">Element</span><span class="sxs-lookup"><span data-stu-id="c7ef2-111">Element</span></span>|<span data-ttu-id="c7ef2-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7ef2-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7ef2-113">Justering Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-113">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c7ef2-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-114">Optional element.</span></span><br /><br /> <span data-ttu-id="c7ef2-115">Definierar hur data i en kolumn i raden visas.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-115">Defines how the data in a column of the row is displayed.</span></span>|
|[<span data-ttu-id="c7ef2-116">FormatString-Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-116">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c7ef2-117">Anger ett formatmönster som används för att formatera data i kolumnen i raden.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-117">Specifies a format pattern that is used to format the data in the column of the row.</span></span>|
|[<span data-ttu-id="c7ef2-118">PropertyName-Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-118">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c7ef2-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-119">Optional element.</span></span><br /><br /> <span data-ttu-id="c7ef2-120">Anger namnet på egenskapen vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-120">Specifies the name of the property whose value is displayed.</span></span>|
|[<span data-ttu-id="c7ef2-121">ScriptBlock Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-121">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)|<span data-ttu-id="c7ef2-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-122">Optional element.</span></span><br /><br /> <span data-ttu-id="c7ef2-123">Anger skriptet vars värde visas i kolumnen i en rad.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-123">Specifies the script whose value is displayed in the column of a row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c7ef2-124">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c7ef2-124">Parent Elements</span></span>

|<span data-ttu-id="c7ef2-125">Element</span><span class="sxs-lookup"><span data-stu-id="c7ef2-125">Element</span></span>|<span data-ttu-id="c7ef2-126">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c7ef2-126">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c7ef2-127">TableColumnItems Element för TableControlEntry för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-127">TableColumnItems Element for TableControlEntry for TableControl (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)|<span data-ttu-id="c7ef2-128">Definierar egenskaper eller skript som vars värden visas i raden.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-128">Defines the properties or scripts whose values are displayed in the row.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c7ef2-129">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c7ef2-129">Remarks</span></span>

<span data-ttu-id="c7ef2-130">Du kan ange en egenskap för ett objekt eller ett skript i varje kolumn i raden.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-130">You can specify a property of an object or a script in each column of the row.</span></span> <span data-ttu-id="c7ef2-131">Om inga underordnade element anges objektet är en platshållare och inga data visas.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-131">If no child elements are specified, the item is a placeholder, and no data is displayed.</span></span>

<span data-ttu-id="c7ef2-132">Läs mer om komponenterna i en tabellvy, [skapar en tabellvy](./creating-a-table-view.md).</span><span class="sxs-lookup"><span data-stu-id="c7ef2-132">For more information about the components of a table view, see [Creating a Table View](./creating-a-table-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c7ef2-133">Exempel</span><span class="sxs-lookup"><span data-stu-id="c7ef2-133">Example</span></span>

<span data-ttu-id="c7ef2-134">Det här exemplet visar en `TableColumnItem` element som visar värdet för den `Status` egenskapen för den [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) objekt.</span><span class="sxs-lookup"><span data-stu-id="c7ef2-134">This example shows a `TableColumnItem` element that displays the value of the `Status` property of the [System.Diagnostics.Process](/dotnet/api/System.Diagnostics.Process) object.</span></span>

```xml
<TableColumnItem>
   <Alignment>Centered</Alignment>
  <PropertyName>Status</PropertyName>
</TableColumnItem>

```

## <a name="see-also"></a><span data-ttu-id="c7ef2-135">Se även</span><span class="sxs-lookup"><span data-stu-id="c7ef2-135">See Also</span></span>

[<span data-ttu-id="c7ef2-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="c7ef2-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c7ef2-137">Justering Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-137">Alignment Element for TableColumnItem for TableControl (Format)</span></span>](./alignment-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c7ef2-138">TableColumnItems Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-138">TableColumnItems Element (Format)</span></span>](./tablecolumnitems-element-for-tablerowentry-for-tablecontrol-format.md)

[<span data-ttu-id="c7ef2-139">FormatString-Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-139">FormatString Element for TableColumnItem for TableControl (Format)</span></span>](./formatstring-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c7ef2-140">PropertyName-Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-140">PropertyName Element for TableColumnItem for TableControl (Format)</span></span>](./propertyname-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c7ef2-141">ScriptBlock Element för TableColumnItem för TableControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c7ef2-141">ScriptBlock Element for TableColumnItem for TableControl (Format)</span></span>](./scriptblock-element-for-tablecolumnitem-for-tablecontrol-format.md)

[<span data-ttu-id="c7ef2-142">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="c7ef2-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
