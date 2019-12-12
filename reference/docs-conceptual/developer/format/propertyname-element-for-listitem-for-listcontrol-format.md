---
title: PropertyName-element för ListItem för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 01ae8cbe-acdc-4043-bd6e-1118a5691a55
caps.latest.revision: 12
ms.openlocfilehash: 405184f7bdbf1955f1df7766bf2723c244dcc27f
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354091"
---
# <a name="propertyname-element-for-listitem-for-listcontrol-format"></a><span data-ttu-id="67f99-102">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67f99-102">PropertyName Element for ListItem for ListControl (Format)</span></span>

<span data-ttu-id="67f99-103">Anger den .NET-egenskap vars värde visas i listan.</span><span class="sxs-lookup"><span data-stu-id="67f99-103">Specifies the .NET property whose value is displayed in the list.</span></span>

<span data-ttu-id="67f99-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry element (format) ListItems element (format) ListItem element (format) PropertyName-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="67f99-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format) ListItems Element (Format) ListItem Element (Format) PropertyName Element for ListItem (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67f99-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="67f99-105">Syntax</span></span>

```xml
<PropertyName>.NetTypeProperty</PropertyName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67f99-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="67f99-106">Attributes and Elements</span></span>

<span data-ttu-id="67f99-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `PropertyName`-elementet.</span><span class="sxs-lookup"><span data-stu-id="67f99-107">The following sections describe the attributes, child elements, and the parent element of the `PropertyName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="67f99-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="67f99-108">Attributes</span></span>

<span data-ttu-id="67f99-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="67f99-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="67f99-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="67f99-110">Child Elements</span></span>

<span data-ttu-id="67f99-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="67f99-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="67f99-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="67f99-112">Parent Elements</span></span>

|<span data-ttu-id="67f99-113">Element</span><span class="sxs-lookup"><span data-stu-id="67f99-113">Element</span></span>|<span data-ttu-id="67f99-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67f99-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67f99-115">ListItem-element (format)</span><span class="sxs-lookup"><span data-stu-id="67f99-115">ListItem Element (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="67f99-116">Definierar egenskapen eller skriptet vars värde visas i raden i listvyn.</span><span class="sxs-lookup"><span data-stu-id="67f99-116">Defines the property or script whose value is displayed in the row of the list view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="67f99-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="67f99-117">Text Value</span></span>

<span data-ttu-id="67f99-118">Ange namnet på den egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="67f99-118">Specify the name of the property whose value is displayed.</span></span>

## <a name="remarks"></a><span data-ttu-id="67f99-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="67f99-119">Remarks</span></span>

<span data-ttu-id="67f99-120">När det här elementet har angetts kan du inte ange [script block](./scriptblock-element-for-listitem-for-listcontrol-format.md) -elementet.</span><span class="sxs-lookup"><span data-stu-id="67f99-120">When this element is specified, you cannot specify the [ScriptBlock](./scriptblock-element-for-listitem-for-listcontrol-format.md) element.</span></span>

<span data-ttu-id="67f99-121">Förutom att Visa egenskap svärdet kan du också ange en etikett för värdet eller en format sträng som kan användas för att ändra visningen av värdet.</span><span class="sxs-lookup"><span data-stu-id="67f99-121">In addition to displaying the property value, you can also specify a label for the value or a format string that can be used to change the display of the value.</span></span> <span data-ttu-id="67f99-122">Mer information om hur du anger data i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="67f99-122">For more information about specifying data in a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67f99-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="67f99-123">Example</span></span>

<span data-ttu-id="67f99-124">I följande exempel visas hur du anger den etikett och egenskap vars värde visas.</span><span class="sxs-lookup"><span data-stu-id="67f99-124">The following example shows how to specify the label and property whose value is displayed.</span></span>

```xml
ListItem>
  <Label>NameOfProperty</Label>
  <PropertyName>.NetTypeProperty</PropertyName>
</ListItem>

```

## <a name="see-also"></a><span data-ttu-id="67f99-125">Se även</span><span class="sxs-lookup"><span data-stu-id="67f99-125">See Also</span></span>

[<span data-ttu-id="67f99-126">Script block-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67f99-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="67f99-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="67f99-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="67f99-128">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67f99-128">ListItem Element for ListControl(Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="67f99-129">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="67f99-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
