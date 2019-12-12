---
title: Etikett element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: c693ff46-d1ad-4dc7-93ac-41ff2fc6c103
caps.latest.revision: 9
ms.openlocfilehash: c1293d5a1f942704ac01388c66bd9009fd340e82
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354448"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="84e76-102">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="84e76-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="84e76-103">Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.</span><span class="sxs-lookup"><span data-stu-id="84e76-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="84e76-104">Konfigurations element (format) ViewDefinitions element (format) View element (format) ListControl element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems för ListEntry för ListControl-element ( Format) ListItem-element för ListItems for ListControl (format)-elementet för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="84e76-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="84e76-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="84e76-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="84e76-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="84e76-106">Attributes and Elements</span></span>

<span data-ttu-id="84e76-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `Label`-elementet.</span><span class="sxs-lookup"><span data-stu-id="84e76-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="84e76-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="84e76-108">Attributes</span></span>

<span data-ttu-id="84e76-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="84e76-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="84e76-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="84e76-110">Child Elements</span></span>

<span data-ttu-id="84e76-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="84e76-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="84e76-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="84e76-112">Parent Elements</span></span>

|<span data-ttu-id="84e76-113">Element</span><span class="sxs-lookup"><span data-stu-id="84e76-113">Element</span></span>|<span data-ttu-id="84e76-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="84e76-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="84e76-115">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="84e76-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="84e76-116">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="84e76-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="84e76-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="84e76-117">Text Value</span></span>

<span data-ttu-id="84e76-118">Ange etiketten som ska visas till vänster om egenskapen eller värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="84e76-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="84e76-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="84e76-119">Remarks</span></span>

<span data-ttu-id="84e76-120">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="84e76-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="84e76-121">Mer information om hur du använder etiketter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="84e76-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="84e76-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="84e76-122">Example</span></span>

<span data-ttu-id="84e76-123">I följande exempel visas hur du lägger till en etikett till en rad.</span><span class="sxs-lookup"><span data-stu-id="84e76-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="84e76-124">Se även</span><span class="sxs-lookup"><span data-stu-id="84e76-124">See Also</span></span>

[<span data-ttu-id="84e76-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="84e76-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="84e76-126">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="84e76-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="84e76-127">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="84e76-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
