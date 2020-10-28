---
ms.date: 09/13/2016
ms.topic: reference
title: PropertyName-element för ListItem för ListControl (format)
description: PropertyName-element för ListItem för ListControl (format)
ms.openlocfilehash: 30cd48f9549e1a091776cd5f8395e1a71314ea1b
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92665982"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="a8aeb-103">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a8aeb-103">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="a8aeb-104">Anger den .NET-egenskap vars värde visas i listan.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-104">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="a8aeb-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) ListItems element (format) ListItem element (format) PropertyName-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="a8aeb-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a8aeb-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="a8aeb-106">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a8aeb-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a8aeb-107">Attributes and Elements</span></span>

<span data-ttu-id="a8aeb-108">I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-108">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a8aeb-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="a8aeb-109">Attributes</span></span>

<span data-ttu-id="a8aeb-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a8aeb-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a8aeb-111">Child Elements</span></span>

<span data-ttu-id="a8aeb-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a8aeb-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a8aeb-113">Parent Elements</span></span>

|<span data-ttu-id="a8aeb-114">Element</span><span class="sxs-lookup"><span data-stu-id="a8aeb-114">Element</span></span>|<span data-ttu-id="a8aeb-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a8aeb-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a8aeb-116">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="a8aeb-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="a8aeb-117">Definierar egenskapen eller skriptet vars värde visas i raden i listvyn.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-117">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a8aeb-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a8aeb-118">Text Value</span></span>

<span data-ttu-id="a8aeb-119">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-119">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a8aeb-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a8aeb-120">Remarks</span></span>

<span data-ttu-id="a8aeb-121">När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-121">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="a8aeb-122">Förutom att Visa egenskap svärdet kan du också ange en etikett för värdet eller en format sträng som kan användas för att ändra visningen av värdet.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-122">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="a8aeb-123">Mer information om hur du anger data i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a8aeb-123">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a8aeb-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="a8aeb-124">Example</span></span>

<span data-ttu-id="a8aeb-125">I följande exempel visas hur du anger den etikett och egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="a8aeb-125">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="a8aeb-126">Se även</span><span class="sxs-lookup"><span data-stu-id="a8aeb-126">See Also</span></span>

[<span data-ttu-id="a8aeb-127">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a8aeb-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="a8aeb-128">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="a8aeb-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a8aeb-129">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a8aeb-129">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="a8aeb-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a8aeb-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
