---
ms.date: 09/13/2016
ms.topic: reference
title: ListItem-element för ListItems för ListControl (format)
description: ListItem-element för ListItems för ListControl (format)
ms.openlocfilehash: 999491b7851aa4fa21667ad376d7e9853500ca08
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666560"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="f926f-103">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-103">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="f926f-104">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="f926f-104">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="f926f-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format) ListItem för ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f926f-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f926f-106">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f926f-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f926f-107">Attributes and Elements</span></span>

<span data-ttu-id="f926f-108">I följande avsnitt beskrivs attributen, underordnade element och `ListItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f926f-108">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="f926f-109">Det går bara att ange en egenskap eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="f926f-109">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="f926f-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="f926f-110">Attributes</span></span>

<span data-ttu-id="f926f-111">Inget</span><span class="sxs-lookup"><span data-stu-id="f926f-111">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="f926f-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f926f-112">Child Elements</span></span>

|<span data-ttu-id="f926f-113">Element</span><span class="sxs-lookup"><span data-stu-id="f926f-113">Element</span></span>|<span data-ttu-id="f926f-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f926f-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f926f-115">FormatString-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-115">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f926f-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f926f-116">Optional element.</span></span><br /><br /> <span data-ttu-id="f926f-117">Anger en format sträng som definierar hur egenskapen eller skriptets värde visas.</span><span class="sxs-lookup"><span data-stu-id="f926f-117">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="f926f-118">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-118">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f926f-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f926f-119">Optional element.</span></span><br /><br /> <span data-ttu-id="f926f-120">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="f926f-120">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="f926f-121">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-121">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f926f-122">Valfritt element</span><span class="sxs-lookup"><span data-stu-id="f926f-122">Optional element</span></span><br /><br /> <span data-ttu-id="f926f-123">Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.</span><span class="sxs-lookup"><span data-stu-id="f926f-123">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="f926f-124">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-124">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f926f-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f926f-125">Optional element.</span></span><br /><br /> <span data-ttu-id="f926f-126">Anger den .NET-egenskap vars värde visas på raden.</span><span class="sxs-lookup"><span data-stu-id="f926f-126">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="f926f-127">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-127">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="f926f-128">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="f926f-128">Optional element.</span></span><br /><br /> <span data-ttu-id="f926f-129">Anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="f926f-129">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f926f-130">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f926f-130">Parent Elements</span></span>

|<span data-ttu-id="f926f-131">Element</span><span class="sxs-lookup"><span data-stu-id="f926f-131">Element</span></span>|<span data-ttu-id="f926f-132">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f926f-132">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f926f-133">ListItems-element för List kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-133">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="f926f-134">Definierar egenskaper och skript vars värden visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="f926f-134">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f926f-135">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f926f-135">Remarks</span></span>

<span data-ttu-id="f926f-136">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f926f-136">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f926f-137">Exempel</span><span class="sxs-lookup"><span data-stu-id="f926f-137">Example</span></span>

<span data-ttu-id="f926f-138">I det här exemplet visas de XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="f926f-138">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="f926f-139">De två första raderna visar värdet för en .NET-egenskap och den sista raden visar ett värde som skapats av ett skript.</span><span class="sxs-lookup"><span data-stu-id="f926f-139">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f926f-140">Se även</span><span class="sxs-lookup"><span data-stu-id="f926f-140">See Also</span></span>

[<span data-ttu-id="f926f-141">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-141">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="f926f-142">FormatString-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-142">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f926f-143">Etikett element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-143">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f926f-144">PropertyName-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-144">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f926f-145">Script block-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="f926f-145">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="f926f-146">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="f926f-146">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f926f-147">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="f926f-147">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
