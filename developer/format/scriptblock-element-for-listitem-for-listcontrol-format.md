---
title: ScriptBlock Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56846503"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="70958-102">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="70958-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="70958-103">Anger skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="70958-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="70958-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListEntries för ListControl (Format) ListItems som finns elementet för ListEntry för ListControl (Format) ListItem elementet för ListItems som finns för ListControl (Format) ScriptBlock elementet för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="70958-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="70958-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="70958-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="70958-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="70958-106">Attributes and Elements</span></span>

<span data-ttu-id="70958-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ScriptBlock` element.</span><span class="sxs-lookup"><span data-stu-id="70958-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="70958-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="70958-108">Attributes</span></span>

<span data-ttu-id="70958-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="70958-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="70958-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="70958-110">Child Elements</span></span>

<span data-ttu-id="70958-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="70958-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="70958-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="70958-112">Parent Elements</span></span>

|<span data-ttu-id="70958-113">Element</span><span class="sxs-lookup"><span data-stu-id="70958-113">Element</span></span>|<span data-ttu-id="70958-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="70958-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="70958-115">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="70958-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="70958-116">Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="70958-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="70958-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="70958-117">Text Value</span></span>

<span data-ttu-id="70958-118">Ange skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="70958-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="70958-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="70958-119">Remarks</span></span>

<span data-ttu-id="70958-120">När det här elementet har angetts ska du inte ange den [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span><span class="sxs-lookup"><span data-stu-id="70958-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="70958-121">Läs mer om hur du anger skript i en listvy [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="70958-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="70958-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="70958-122">Example</span></span>

<span data-ttu-id="70958-123">I följande exempel visas hur du anger egenskapen vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="70958-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="70958-124">Se även</span><span class="sxs-lookup"><span data-stu-id="70958-124">See Also</span></span>

[<span data-ttu-id="70958-125">PropertyName-Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="70958-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="70958-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="70958-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="70958-127">ListItem Element för ListItems som finns för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="70958-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="70958-128">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="70958-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
