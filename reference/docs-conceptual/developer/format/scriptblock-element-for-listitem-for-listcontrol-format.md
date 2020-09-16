---
title: Script block-element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 249d3e36b4246b7baa410815122f8e30340f1862
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785463"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="5ae02-102">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5ae02-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="5ae02-103">Anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="5ae02-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="5ae02-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems element for ListEntry for ListControl (format) ListItem element for ListItems for ListControl (format) script block element for ListItem for ListControl for (format)</span><span class="sxs-lookup"><span data-stu-id="5ae02-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5ae02-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5ae02-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="5ae02-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5ae02-106">Attributes and Elements</span></span>

<span data-ttu-id="5ae02-107">I följande avsnitt beskrivs attributen, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="5ae02-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5ae02-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="5ae02-108">Attributes</span></span>

<span data-ttu-id="5ae02-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="5ae02-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5ae02-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5ae02-110">Child Elements</span></span>

<span data-ttu-id="5ae02-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="5ae02-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="5ae02-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5ae02-112">Parent Elements</span></span>

|<span data-ttu-id="5ae02-113">Element</span><span class="sxs-lookup"><span data-stu-id="5ae02-113">Element</span></span>|<span data-ttu-id="5ae02-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5ae02-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5ae02-115">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="5ae02-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="5ae02-116">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="5ae02-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="5ae02-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="5ae02-117">Text Value</span></span>

<span data-ttu-id="5ae02-118">Ange det skript vars värde visas på raden.</span><span class="sxs-lookup"><span data-stu-id="5ae02-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="5ae02-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="5ae02-119">Remarks</span></span>

<span data-ttu-id="5ae02-120">När det här elementet har angetts kan du inte ange elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="5ae02-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="5ae02-121">Mer information om hur du anger skript i listvyn finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5ae02-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5ae02-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="5ae02-122">Example</span></span>

<span data-ttu-id="5ae02-123">I följande exempel visas hur du anger den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="5ae02-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="5ae02-124">Se även</span><span class="sxs-lookup"><span data-stu-id="5ae02-124">See Also</span></span>

[<span data-ttu-id="5ae02-125">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5ae02-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="5ae02-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="5ae02-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5ae02-127">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="5ae02-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="5ae02-128">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="5ae02-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
