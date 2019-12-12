---
title: Script block-element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 74e30938-00ef-46fd-84e5-f0a83706a50e
caps.latest.revision: 11
ms.openlocfilehash: 76b600256af3f957f7fe0578f9fef810262aa5d5
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72355792"
---
# <a name="scriptblock-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="e0506-102">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0506-102">ScriptBlock Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="e0506-103">Anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="e0506-103">Specifies the script whose value is displayed in the row.</span></span>

<span data-ttu-id="e0506-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListEntries för ListControl (format) ListItems-element för ListEntry för ListControl (format) ListItem-elementet för ListItems för ListControl (format) script block-elementet för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0506-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListEntries for ListControl (Format) ListItems Element for ListEntry for ListControl (Format) ListItem Element for ListItems for ListControl (Format) ScriptBlock Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e0506-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="e0506-105">Syntax</span></span>

```xml
<ScriptBlock>ScriptToEvaluate</ScriptBlock>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e0506-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e0506-106">Attributes and Elements</span></span>

<span data-ttu-id="e0506-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ScriptBlock`-elementet.</span><span class="sxs-lookup"><span data-stu-id="e0506-107">The following sections describe the attributes, child elements, and the parent element of the `ScriptBlock` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="e0506-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="e0506-108">Attributes</span></span>

<span data-ttu-id="e0506-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e0506-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e0506-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e0506-110">Child Elements</span></span>

<span data-ttu-id="e0506-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="e0506-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e0506-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e0506-112">Parent Elements</span></span>

|<span data-ttu-id="e0506-113">Element</span><span class="sxs-lookup"><span data-stu-id="e0506-113">Element</span></span>|<span data-ttu-id="e0506-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e0506-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e0506-115">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="e0506-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="e0506-116">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="e0506-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e0506-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e0506-117">Text Value</span></span>

<span data-ttu-id="e0506-118">Ange det skript vars värde visas på raden.</span><span class="sxs-lookup"><span data-stu-id="e0506-118">Specify the script whose value is displayed in the row.</span></span>

## <a name="remarks"></a><span data-ttu-id="e0506-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="e0506-119">Remarks</span></span>

<span data-ttu-id="e0506-120">När det här elementet har angetts kan du inte ange elementet [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) .</span><span class="sxs-lookup"><span data-stu-id="e0506-120">When this element is specified, you cannot specify the [PropertyName](./propertyname-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="e0506-121">Mer information om hur du anger skript i listvyn finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="e0506-121">For more information about specifying scripts in a list view, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="e0506-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="e0506-122">Example</span></span>

<span data-ttu-id="e0506-123">I följande exempel visas hur du anger den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="e0506-123">The following example shows how to specify the property whose value is displayed.</span></span>

```xml
<ListItem>
  <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="e0506-124">Se även</span><span class="sxs-lookup"><span data-stu-id="e0506-124">See Also</span></span>

[<span data-ttu-id="e0506-125">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0506-125">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="e0506-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="e0506-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e0506-127">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="e0506-127">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="e0506-128">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="e0506-128">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
