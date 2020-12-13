---
ms.date: 09/13/2016
ms.topic: reference
title: ListItems-element för ListEntry för ListControl (format)
description: ListItems-element för ListEntry för ListControl (format)
ms.openlocfilehash: 1553c81bc559020223a3c1fea10336baf017c9a0
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666543"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="524fc-103">ListItems-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-103">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="524fc-104">Definierar de egenskaper och skript vars värden visas i raderna i listvyn.</span><span class="sxs-lookup"><span data-stu-id="524fc-104">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="524fc-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) element för List kontroll (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="524fc-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="524fc-106">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="524fc-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="524fc-107">Attributes and Elements</span></span>

<span data-ttu-id="524fc-108">I följande avsnitt beskrivs attributen, underordnade element och `ListItems` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="524fc-108">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="524fc-109">Det finns ingen gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="524fc-109">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="524fc-110">Ordningen på underordnade element definierar i vilken ordning värdena visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="524fc-110">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="524fc-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="524fc-111">Attributes</span></span>

<span data-ttu-id="524fc-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="524fc-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="524fc-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="524fc-113">Child Elements</span></span>

|<span data-ttu-id="524fc-114">Element</span><span class="sxs-lookup"><span data-stu-id="524fc-114">Element</span></span>|<span data-ttu-id="524fc-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="524fc-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="524fc-116">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-116">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="524fc-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="524fc-117">Required element.</span></span><br /><br /> <span data-ttu-id="524fc-118">Definierar egenskapen eller skriptet vars värde visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="524fc-118">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="524fc-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="524fc-119">Parent Elements</span></span>

|<span data-ttu-id="524fc-120">Element</span><span class="sxs-lookup"><span data-stu-id="524fc-120">Element</span></span>|<span data-ttu-id="524fc-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="524fc-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="524fc-122">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-122">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="524fc-123">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="524fc-123">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="524fc-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="524fc-124">Remarks</span></span>

<span data-ttu-id="524fc-125">Mer information om den här typen av vy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="524fc-125">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="524fc-126">Exempel</span><span class="sxs-lookup"><span data-stu-id="524fc-126">Example</span></span>

<span data-ttu-id="524fc-127">I det här exemplet visas de XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="524fc-127">This example shows the XML elements that define three rows of the list view.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>.NetTypeProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>.NetTypeProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
  </ListEntry>
```

## <a name="see-also"></a><span data-ttu-id="524fc-128">Se även</span><span class="sxs-lookup"><span data-stu-id="524fc-128">See Also</span></span>

[<span data-ttu-id="524fc-129">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-129">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="524fc-130">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="524fc-130">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="524fc-131">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="524fc-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="524fc-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="524fc-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
