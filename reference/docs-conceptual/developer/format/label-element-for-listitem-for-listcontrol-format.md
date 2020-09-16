---
title: Etikett element för ListItem för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: ad80cc0478e7567b12d264ab661d843248ba48e1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87783644"
---
# <a name="label-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="98b81-102">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="98b81-102">Label Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="98b81-103">Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.</span><span class="sxs-lookup"><span data-stu-id="98b81-103">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>

<span data-ttu-id="98b81-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems för ListEntry för ListControl-element (format) ListItem element for ListItems for ListControl (format) ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="98b81-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems for ListEntry for ListControl Element (Format) ListItem Element for ListItems for ListControl (Format) Label Element for ListItem for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="98b81-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="98b81-105">Syntax</span></span>

```xml
<Label>Label for displayed value</Label>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="98b81-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="98b81-106">Attributes and Elements</span></span>

<span data-ttu-id="98b81-107">I följande avsnitt beskrivs attributen, underordnade element och `Label` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="98b81-107">The following sections describe the attributes, child elements, and the parent element of the `Label` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="98b81-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="98b81-108">Attributes</span></span>

<span data-ttu-id="98b81-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="98b81-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="98b81-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="98b81-110">Child Elements</span></span>

<span data-ttu-id="98b81-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="98b81-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="98b81-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="98b81-112">Parent Elements</span></span>

|<span data-ttu-id="98b81-113">Element</span><span class="sxs-lookup"><span data-stu-id="98b81-113">Element</span></span>|<span data-ttu-id="98b81-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="98b81-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="98b81-115">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="98b81-115">ListItem Element for ListItems for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="98b81-116">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="98b81-116">Defines the property or script whose value is displayed in a row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="98b81-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="98b81-117">Text Value</span></span>

<span data-ttu-id="98b81-118">Ange etiketten som ska visas till vänster om egenskapen eller värdet för skriptet.</span><span class="sxs-lookup"><span data-stu-id="98b81-118">Specify the label to be display to the left of the property or script value.</span></span>

## <a name="remarks"></a><span data-ttu-id="98b81-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="98b81-119">Remarks</span></span>

<span data-ttu-id="98b81-120">Om en etikett inte anges visas namnet på egenskapen eller skriptet.</span><span class="sxs-lookup"><span data-stu-id="98b81-120">If a label is not specified, the name of the property or the script is displayed.</span></span> <span data-ttu-id="98b81-121">Mer information om hur du använder etiketter i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="98b81-121">For more information about using labels in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="98b81-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="98b81-122">Example</span></span>

<span data-ttu-id="98b81-123">I följande exempel visas hur du lägger till en etikett till en rad.</span><span class="sxs-lookup"><span data-stu-id="98b81-123">The following example shows how to add a label to a row.</span></span>

```xml
<ListItem>
  <Label>Property1: </Label>
  <PropertyName>DotNetProperty1</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="98b81-124">Se även</span><span class="sxs-lookup"><span data-stu-id="98b81-124">See Also</span></span>

[<span data-ttu-id="98b81-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="98b81-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="98b81-126">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="98b81-126">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="98b81-127">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="98b81-127">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
