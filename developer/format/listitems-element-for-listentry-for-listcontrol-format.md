---
title: ListItems som finns Element för ListEntry för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: d2c1da6d-acc7-4fe8-9e7d-6dcddc2787cd
caps.latest.revision: 9
ms.openlocfilehash: c25f18489d9c7abd8889758499dbbacd6ee29304
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848624"
---
# <a name="listitems-element-for-listentry-for-listcontrol-format"></a><span data-ttu-id="ab389-102">ListItems-element för ListEntry för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="ab389-102">ListItems Element for ListEntry for ListControl (Format)</span></span>

<span data-ttu-id="ab389-103">Definierar egenskaperna och skript vars värden visas i raderna i listvyn.</span><span class="sxs-lookup"><span data-stu-id="ab389-103">Defines the properties and scripts whose values are displayed in the rows of the list view.</span></span>

<span data-ttu-id="ab389-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för listan kontroll (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab389-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for List Control (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ab389-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="ab389-105">Syntax</span></span>

```xml
<ListItems>
  <ListItem>...</ListItem>
</ListItems>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ab389-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ab389-106">Attributes and Elements</span></span>

<span data-ttu-id="ab389-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ListItems` element.</span><span class="sxs-lookup"><span data-stu-id="ab389-107">The following sections describe the attributes, child elements, and parent element of the `ListItems` element.</span></span> <span data-ttu-id="ab389-108">Det finns ingen gräns för antalet underordnade element som kan anges.</span><span class="sxs-lookup"><span data-stu-id="ab389-108">There is no limit to the number of child elements that can be specified.</span></span> <span data-ttu-id="ab389-109">Ordningen på de underordnade elementen definierar ordningen att värden visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="ab389-109">The order of the child elements defines the order that values are displayed in the list view.</span></span>

### <a name="attributes"></a><span data-ttu-id="ab389-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ab389-110">Attributes</span></span>

<span data-ttu-id="ab389-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ab389-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ab389-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ab389-112">Child Elements</span></span>

|<span data-ttu-id="ab389-113">Element</span><span class="sxs-lookup"><span data-stu-id="ab389-113">Element</span></span>|<span data-ttu-id="ab389-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab389-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab389-115">ListItem Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab389-115">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)|<span data-ttu-id="ab389-116">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="ab389-116">Required element.</span></span><br /><br /> <span data-ttu-id="ab389-117">Definierar egenskapen eller skript som vars värde visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="ab389-117">Defines the property or script whose value is displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ab389-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ab389-118">Parent Elements</span></span>

|<span data-ttu-id="ab389-119">Element</span><span class="sxs-lookup"><span data-stu-id="ab389-119">Element</span></span>|<span data-ttu-id="ab389-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ab389-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ab389-121">ListEntry Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab389-121">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="ab389-122">Innehåller en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="ab389-122">Provides a definition of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ab389-123">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ab389-123">Remarks</span></span>

<span data-ttu-id="ab389-124">Mer information om den här typen av vy finns i [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="ab389-124">For more information about this type of view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="ab389-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="ab389-125">Example</span></span>

<span data-ttu-id="ab389-126">Det här exemplet visar XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="ab389-126">This example shows the XML elements that define three rows of the list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ab389-127">Se även</span><span class="sxs-lookup"><span data-stu-id="ab389-127">See Also</span></span>

[<span data-ttu-id="ab389-128">ListEntry Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab389-128">ListEntry Element for ListControl (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="ab389-129">ListItem Element för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="ab389-129">ListItem Element for ListControl (Format)</span></span>](./listitem-element-for-listitems-for-listcontrol-format.md)

[<span data-ttu-id="ab389-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="ab389-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ab389-131">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="ab389-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
