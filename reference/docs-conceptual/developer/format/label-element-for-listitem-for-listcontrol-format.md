---
ms.date: 09/13/2016
ms.topic: reference
title: Label-element för ListItem för ListControl (format)
description: Label-element för ListItem för ListControl (format)
ms.openlocfilehash: 01ff34c4129abe2c76a0a21794e756b77bff12bf
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666662"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="73856-103">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="73856-103">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="73856-104">Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.</span><span class="sxs-lookup"><span data-stu-id="73856-104">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="73856-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems för ListEntry för ListControl-element (format) ListItem element for ListItems for ListControl (format) ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="73856-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="73856-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="73856-106">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="73856-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="73856-107">Attributes and Elements</span></span>

<span data-ttu-id="73856-108">I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="73856-108">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="73856-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="73856-109">Attributes</span></span>

<span data-ttu-id="73856-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="73856-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="73856-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="73856-111">Child Elements</span></span>

<span data-ttu-id="73856-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="73856-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="73856-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="73856-113">Parent Elements</span></span>

|<span data-ttu-id="73856-114">Element</span><span class="sxs-lookup"><span data-stu-id="73856-114">Element</span></span>|<span data-ttu-id="73856-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="73856-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="73856-116">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="73856-116">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="73856-117">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="73856-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="73856-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="73856-118">Text Value</span></span>

<span data-ttu-id="73856-119">Ange etiketten som ska visas till vänster om egenskapen eller värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="73856-119">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="73856-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="73856-120">Remarks</span></span>

<span data-ttu-id="73856-121">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="73856-121">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="73856-122">Mer information om hur du använder etiketter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="73856-122">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="73856-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="73856-123">Example</span></span>

<span data-ttu-id="73856-124">I följande exempel visas hur du lägger till en etikett till en rad.</span><span class="sxs-lookup"><span data-stu-id="73856-124">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="73856-125">Se även</span><span class="sxs-lookup"><span data-stu-id="73856-125">See Also</span></span>

[<span data-ttu-id="73856-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="73856-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="73856-127">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="73856-127">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="73856-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="73856-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
