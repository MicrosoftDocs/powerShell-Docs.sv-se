---
title: ListItems-element för ListEntry för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 03b89a3df2ab0498533d0c00f303f643e0039b25
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87781145"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="7d846-102">ListItems-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="7d846-103">Definierar de egenskaper och skript vars värden visas i raderna i listvyn.</span><span class="sxs-lookup"><span data-stu-id="7d846-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="7d846-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl element (format) element för List kontroll (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="7d846-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="7d846-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="7d846-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="7d846-106">Attributes and Elements</span></span>

<span data-ttu-id="7d846-107">I följande avsnitt beskrivs attributen, underordnade element och `ListItems` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="7d846-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="7d846-108">Det finns ingen gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="7d846-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="7d846-109">Ordningen på underordnade element definierar i vilken ordning värdena visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="7d846-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="7d846-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="7d846-110">Attributes</span></span>

<span data-ttu-id="7d846-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="7d846-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="7d846-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="7d846-112">Child Elements</span></span>

|<span data-ttu-id="7d846-113">Element</span><span class="sxs-lookup"><span data-stu-id="7d846-113">Element</span></span>|<span data-ttu-id="7d846-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d846-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d846-115">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="7d846-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="7d846-116">Required element.</span></span><br /><br /> <span data-ttu-id="7d846-117">Definierar egenskapen eller skriptet vars värde visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="7d846-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="7d846-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="7d846-118">Parent Elements</span></span>

|<span data-ttu-id="7d846-119">Element</span><span class="sxs-lookup"><span data-stu-id="7d846-119">Element</span></span>|<span data-ttu-id="7d846-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="7d846-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="7d846-121">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="7d846-122">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="7d846-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="7d846-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="7d846-123">Remarks</span></span>

<span data-ttu-id="7d846-124">Mer information om den här typen av vy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="7d846-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="7d846-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="7d846-125">Example</span></span>

<span data-ttu-id="7d846-126">I det här exemplet visas de XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="7d846-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="7d846-127">Se även</span><span class="sxs-lookup"><span data-stu-id="7d846-127">See Also</span></span>

[<span data-ttu-id="7d846-128">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="7d846-129">ListItem-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="7d846-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="7d846-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="7d846-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="7d846-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="7d846-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
