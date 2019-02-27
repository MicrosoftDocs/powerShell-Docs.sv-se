---
title: Etikettera Element för ListItem för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56845957"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="dd63b-102">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="dd63b-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="dd63b-103">Anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden.</span><span class="sxs-lookup"><span data-stu-id="dd63b-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="dd63b-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListItems ListControl (Format) som finns för ListEntry för ListControl Element ( Format) ListItem Element för ListItems som finns för ListControl (Format) etikett elementet för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dd63b-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="dd63b-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="dd63b-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="dd63b-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="dd63b-106">Attributes and Elements</span></span>

<span data-ttu-id="dd63b-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `Label` element.</span><span class="sxs-lookup"><span data-stu-id="dd63b-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="dd63b-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="dd63b-108">Attributes</span></span>

<span data-ttu-id="dd63b-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="dd63b-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="dd63b-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="dd63b-110">Child Elements</span></span>

<span data-ttu-id="dd63b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="dd63b-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="dd63b-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="dd63b-112">Parent Elements</span></span>

|<span data-ttu-id="dd63b-113">Element</span><span class="sxs-lookup"><span data-stu-id="dd63b-113">Element</span></span>|<span data-ttu-id="dd63b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="dd63b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="dd63b-115">ListItem Element för ListItems som finns för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="dd63b-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="dd63b-116">Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="dd63b-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="dd63b-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="dd63b-117">Text Value</span></span>

<span data-ttu-id="dd63b-118">Ange etiketten ska visas till vänster om värdet för egenskapen eller skript.</span><span class="sxs-lookup"><span data-stu-id="dd63b-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="dd63b-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="dd63b-119">Remarks</span></span>

<span data-ttu-id="dd63b-120">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="dd63b-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="dd63b-121">Läs mer om hur du använder etiketter i en listvy [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="dd63b-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="dd63b-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="dd63b-122">Example</span></span>

<span data-ttu-id="dd63b-123">I följande exempel visas hur du lägger till en etikett till en rad.</span><span class="sxs-lookup"><span data-stu-id="dd63b-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="dd63b-124">Se även</span><span class="sxs-lookup"><span data-stu-id="dd63b-124">See Also</span></span>

[<span data-ttu-id="dd63b-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="dd63b-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="dd63b-126">ListItem Element (Format)</span><span class="sxs-lookup"><span data-stu-id="dd63b-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="dd63b-127">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="dd63b-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
