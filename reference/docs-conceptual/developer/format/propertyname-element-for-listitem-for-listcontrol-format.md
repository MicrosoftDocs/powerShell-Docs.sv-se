---
title: PropertyName-element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 9ee466d7f73e53b129f8d46f49a21549683bb32c
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780839"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="a67b4-102">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a67b4-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="a67b4-103">Anger den .NET-egenskap vars värde visas i listan.</span><span class="sxs-lookup"><span data-stu-id="a67b4-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="a67b4-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format) ListItems element (format) ListItem element (format) PropertyName-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="a67b4-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="a67b4-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="a67b4-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="a67b4-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="a67b4-106">Attributes and Elements</span></span>

<span data-ttu-id="a67b4-107">I följande avsnitt beskrivs attributen, underordnade element och `PropertyName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="a67b4-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="a67b4-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="a67b4-108">Attributes</span></span>

<span data-ttu-id="a67b4-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="a67b4-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="a67b4-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="a67b4-110">Child Elements</span></span>

<span data-ttu-id="a67b4-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="a67b4-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="a67b4-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="a67b4-112">Parent Elements</span></span>

|<span data-ttu-id="a67b4-113">Element</span><span class="sxs-lookup"><span data-stu-id="a67b4-113">Element</span></span>|<span data-ttu-id="a67b4-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="a67b4-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="a67b4-115">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="a67b4-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="a67b4-116">Definierar egenskapen eller skriptet vars värde visas i raden i listvyn.</span><span class="sxs-lookup"><span data-stu-id="a67b4-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="a67b4-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="a67b4-117">Text Value</span></span>

<span data-ttu-id="a67b4-118">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="a67b4-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="a67b4-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="a67b4-119">Remarks</span></span>

<span data-ttu-id="a67b4-120">När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="a67b4-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="a67b4-121">Förutom att Visa egenskap svärdet kan du också ange en etikett för värdet eller en format sträng som kan användas för att ändra visningen av värdet.</span><span class="sxs-lookup"><span data-stu-id="a67b4-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="a67b4-122">Mer information om hur du anger data i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="a67b4-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="a67b4-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="a67b4-123">Example</span></span>

<span data-ttu-id="a67b4-124">I följande exempel visas hur du anger den etikett och egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="a67b4-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="a67b4-125">Se även</span><span class="sxs-lookup"><span data-stu-id="a67b4-125">See Also</span></span>

[<span data-ttu-id="a67b4-126">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a67b4-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="a67b4-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="a67b4-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="a67b4-128">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="a67b4-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="a67b4-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="a67b4-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
