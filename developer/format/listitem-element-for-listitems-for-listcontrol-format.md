---
title: ListItem Element för ListItems som finns för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0f96f4f5-8bd5-43ed-95e7-a7358115999a
caps.latest.revision: 11
ms.openlocfilehash: 1e0a1b2d20853650328b8cfd1513a08f7e167cd6
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065775"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="c5438-102">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="c5438-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="c5438-103">Definierar egenskapen eller skript som vars värde visas i en rad i listvyn.</span><span class="sxs-lookup"><span data-stu-id="c5438-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="c5438-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement för ListControl (Format) ListEntry elementet för ListControl (Format) ListItems som finns Element för ListControl (Format) ListItem för ListControl elementet (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c5438-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c5438-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c5438-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c5438-106">Attributes and Elements</span></span>

<span data-ttu-id="c5438-107">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ListItem` element.</span><span class="sxs-lookup"><span data-stu-id="c5438-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="c5438-108">Endast en egenskap eller skript kan anges.</span><span class="sxs-lookup"><span data-stu-id="c5438-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c5438-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c5438-109">Attributes</span></span>

<span data-ttu-id="c5438-110">Inga</span><span class="sxs-lookup"><span data-stu-id="c5438-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="c5438-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c5438-111">Child Elements</span></span>

|<span data-ttu-id="c5438-112">Element</span><span class="sxs-lookup"><span data-stu-id="c5438-112">Element</span></span>|<span data-ttu-id="c5438-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c5438-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5438-114">FormatString-Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c5438-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c5438-115">Optional element.</span></span><br /><br /> <span data-ttu-id="c5438-116">Anger en formatsträng som definierar hur värdet för egenskapen eller ett skript ska visas.</span><span class="sxs-lookup"><span data-stu-id="c5438-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="c5438-117">ItemSelectionCondition Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c5438-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c5438-118">Optional element.</span></span><br /><br /> <span data-ttu-id="c5438-119">Definierar de villkor som måste finnas för det här objektet i listan som ska användas.</span><span class="sxs-lookup"><span data-stu-id="c5438-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="c5438-120">Etikettelement för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c5438-121">Valfritt element</span><span class="sxs-lookup"><span data-stu-id="c5438-121">Optional element</span></span><br /><br /> <span data-ttu-id="c5438-122">Anger etiketten som visas till vänster om värdet för egenskapen eller skript på raden.</span><span class="sxs-lookup"><span data-stu-id="c5438-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="c5438-123">PropertyName-Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c5438-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c5438-124">Optional element.</span></span><br /><br /> <span data-ttu-id="c5438-125">Anger egenskapen .NET vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="c5438-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="c5438-126">ScriptBlock Element för ListItem för ListControl (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="c5438-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="c5438-127">Optional element.</span></span><br /><br /> <span data-ttu-id="c5438-128">Anger skriptet vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="c5438-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c5438-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c5438-129">Parent Elements</span></span>

|<span data-ttu-id="c5438-130">Element</span><span class="sxs-lookup"><span data-stu-id="c5438-130">Element</span></span>|<span data-ttu-id="c5438-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c5438-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c5438-132">ListItems som finns Element för listkontroll (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="c5438-133">Definierar egenskaperna och skript vars värden visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="c5438-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c5438-134">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="c5438-134">Remarks</span></span>

<span data-ttu-id="c5438-135">Läs mer om komponenterna i en listvy, [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c5438-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c5438-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="c5438-136">Example</span></span>

<span data-ttu-id="c5438-137">Det här exemplet visar XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="c5438-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="c5438-138">De två första raderna visa värdet för en egenskap för .NET och den sista raden visar ett värde av ett skript.</span><span class="sxs-lookup"><span data-stu-id="c5438-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

```xml
<ListEntry>
    <ListItems>
      <ListItem>
        <Label>Property1: </Label>
        <PropertyName>DotNetProperty1</PropertyName>
      </ListItem>
      <ListItem>
        <PropertyName>DotNetProperty2</PropertyName>
      </ListItem>
      <ListItem>
        <ScriptBlock>$_.ProcessName + ":" $_.Id</ScriptBlock>
      </ListItem>
    </ListItems>
</ListEntry>

```

## <a name="see-also"></a><span data-ttu-id="c5438-139">Se även</span><span class="sxs-lookup"><span data-stu-id="c5438-139">See Also</span></span>

[<span data-ttu-id="c5438-140">ListItems som finns Element (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="c5438-141">FormatString-Element för ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c5438-142">Etikettelement för ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c5438-143">PropertyName-Element för ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c5438-144">ScriptBlock Element för ListItem (Format)</span><span class="sxs-lookup"><span data-stu-id="c5438-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="c5438-145">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="c5438-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c5438-146">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="c5438-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
