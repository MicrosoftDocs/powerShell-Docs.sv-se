---
ms.date: 09/13/2016
ms.topic: reference
title: ScriptBlock-element för ListItem för ListControl (format)
description: ScriptBlock-element för ListItem för ListControl (format)
ms.openlocfilehash: 0635ac2622cc203a2dc895873621901d956f87da
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92664974"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="92eb8-103">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="92eb8-103">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="92eb8-104">Anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="92eb8-104">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="92eb8-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems element for ListEntry for ListControl (format) ListItem element for ListItems for ListControl (format) script block element for ListItem for ListControl for (format)</span><span class="sxs-lookup"><span data-stu-id="92eb8-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="92eb8-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="92eb8-106">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="92eb8-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="92eb8-107">Attributes and Elements</span></span>

<span data-ttu-id="92eb8-108">I följande avsnitt beskrivs attributen, underordnade element och `ScriptBlock` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="92eb8-108">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="92eb8-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="92eb8-109">Attributes</span></span>

<span data-ttu-id="92eb8-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="92eb8-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="92eb8-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="92eb8-111">Child Elements</span></span>

<span data-ttu-id="92eb8-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="92eb8-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="92eb8-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="92eb8-113">Parent Elements</span></span>

|<span data-ttu-id="92eb8-114">Element</span><span class="sxs-lookup"><span data-stu-id="92eb8-114">Element</span></span>|<span data-ttu-id="92eb8-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="92eb8-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="92eb8-116">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="92eb8-116">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="92eb8-117">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="92eb8-117">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="92eb8-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="92eb8-118">Text Value</span></span>

<span data-ttu-id="92eb8-119">Ange det skript vars värde visas på raden.</span><span class="sxs-lookup"><span data-stu-id="92eb8-119">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="92eb8-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="92eb8-120">Remarks</span></span>

<span data-ttu-id="92eb8-121">När det här elementet har angetts kan du inte ange elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="92eb8-121">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="92eb8-122">Mer information om hur du anger skript i listvyn finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="92eb8-122">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="92eb8-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="92eb8-123">Example</span></span>

<span data-ttu-id="92eb8-124">I följande exempel visas hur du anger den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="92eb8-124">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="92eb8-125">Se även</span><span class="sxs-lookup"><span data-stu-id="92eb8-125">See Also</span></span>

[<span data-ttu-id="92eb8-126">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="92eb8-126">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="92eb8-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="92eb8-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="92eb8-128">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="92eb8-128">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="92eb8-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="92eb8-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
