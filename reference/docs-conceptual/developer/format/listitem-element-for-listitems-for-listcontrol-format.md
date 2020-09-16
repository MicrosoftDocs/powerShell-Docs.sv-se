---
title: ListItem-element för ListItems för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e72a887e8bd1f93bacb663e3079eeaec34bdfa51
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785684"
---
# <a name="listitem-element-for-listitems-for-listcontrol-format"></a><span data-ttu-id="67caf-102">ListItem-element för ListItems för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-102">ListItem Element for ListItems for ListControl (Format)</span></span>

<span data-ttu-id="67caf-103">Definierar egenskapen eller skriptet vars värde visas i en rad i list visningen.</span><span class="sxs-lookup"><span data-stu-id="67caf-103">Defines the property or script whose value is displayed in a row of the list view.</span></span>

<span data-ttu-id="67caf-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element för ListControl (format) ListEntry-element för ListControl (format) ListItems-element för ListControl (format) ListItem för ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element for ListControl (Format) ListEntry Element for ListControl (Format) ListItems Element for ListControl (Format) ListItem for ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="67caf-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="67caf-105">Syntax</span></span>

```xml
<ListItem>
  <PropertyName>PropertyToDisplay</PropertyName>
  <ScriptBlock>ScriptToExecute</ScriptBlock>
  <Label>LabelToDisplay</Label>
  <FormatString>FormatPattern</FormatString>
  <ItemSelectionCondition>...</ItemSelectionCondition>
</ListItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="67caf-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="67caf-106">Attributes and Elements</span></span>

<span data-ttu-id="67caf-107">I följande avsnitt beskrivs attributen, underordnade element och `ListItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="67caf-107">The following sections describe the attributes, child elements, and parent element of the `ListItem` element.</span></span> <span data-ttu-id="67caf-108">Det går bara att ange en egenskap eller ett skript.</span><span class="sxs-lookup"><span data-stu-id="67caf-108">Only one property or script can be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="67caf-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="67caf-109">Attributes</span></span>

<span data-ttu-id="67caf-110">Inget</span><span class="sxs-lookup"><span data-stu-id="67caf-110">None</span></span>

### <a name="child-elements"></a><span data-ttu-id="67caf-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="67caf-111">Child Elements</span></span>

|<span data-ttu-id="67caf-112">Element</span><span class="sxs-lookup"><span data-stu-id="67caf-112">Element</span></span>|<span data-ttu-id="67caf-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67caf-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67caf-114">FormatString-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-114">FormatString Element for ListItem for ListControl (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="67caf-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67caf-115">Optional element.</span></span><br /><br /> <span data-ttu-id="67caf-116">Anger en format sträng som definierar hur egenskapen eller skriptets värde visas.</span><span class="sxs-lookup"><span data-stu-id="67caf-116">Specifies a format string that defines how the property or script value is displayed.</span></span>|
|[<span data-ttu-id="67caf-117">ItemSelectionCondition-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-117">ItemSelectionCondition Element for ListItem for ListControl (Format)</span></span>](./itemselectioncondition-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="67caf-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67caf-118">Optional element.</span></span><br /><br /> <span data-ttu-id="67caf-119">Definierar det villkor som måste finnas för att listobjektet ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="67caf-119">Defines the condition that must exist for this list item to be used.</span></span>|
|[<span data-ttu-id="67caf-120">Label-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-120">Label Element for ListItem for ListControl (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="67caf-121">Valfritt element</span><span class="sxs-lookup"><span data-stu-id="67caf-121">Optional element</span></span><br /><br /> <span data-ttu-id="67caf-122">Anger etiketten som visas till vänster om egenskapen eller skriptets värde på raden.</span><span class="sxs-lookup"><span data-stu-id="67caf-122">Specifies the label that is displayed to the left of the property or script value in the row.</span></span>|
|[<span data-ttu-id="67caf-123">PropertyName-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-123">PropertyName Element for ListItem for ListControl (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="67caf-124">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67caf-124">Optional element.</span></span><br /><br /> <span data-ttu-id="67caf-125">Anger den .NET-egenskap vars värde visas på raden.</span><span class="sxs-lookup"><span data-stu-id="67caf-125">Specifies the .NET property whose value is displayed in the row.</span></span>|
|[<span data-ttu-id="67caf-126">ScriptBlock-element för ListItem för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-126">ScriptBlock Element for ListItem for ListControl (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)|<span data-ttu-id="67caf-127">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="67caf-127">Optional element.</span></span><br /><br /> <span data-ttu-id="67caf-128">Anger det skript vars värde visas i raden.</span><span class="sxs-lookup"><span data-stu-id="67caf-128">Specifies the script whose value is displayed in the row.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="67caf-129">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="67caf-129">Parent Elements</span></span>

|<span data-ttu-id="67caf-130">Element</span><span class="sxs-lookup"><span data-stu-id="67caf-130">Element</span></span>|<span data-ttu-id="67caf-131">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="67caf-131">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="67caf-132">ListItems-element för List kontroll (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-132">ListItems Element for List Control (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="67caf-133">Definierar egenskaper och skript vars värden visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="67caf-133">Defines the properties and scripts whose values are displayed in the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="67caf-134">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="67caf-134">Remarks</span></span>

<span data-ttu-id="67caf-135">Mer information om komponenterna i en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="67caf-135">For more information about the components of a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="67caf-136">Exempel</span><span class="sxs-lookup"><span data-stu-id="67caf-136">Example</span></span>

<span data-ttu-id="67caf-137">I det här exemplet visas de XML-element som definierar tre rader i listvyn.</span><span class="sxs-lookup"><span data-stu-id="67caf-137">This example shows the XML elements that define three rows of the list view.</span></span> <span data-ttu-id="67caf-138">De två första raderna visar värdet för en .NET-egenskap och den sista raden visar ett värde som skapats av ett skript.</span><span class="sxs-lookup"><span data-stu-id="67caf-138">The first two rows display the value of a .NET property, and the last row displays a value generated by a script.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="67caf-139">Se även</span><span class="sxs-lookup"><span data-stu-id="67caf-139">See Also</span></span>

[<span data-ttu-id="67caf-140">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-140">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="67caf-141">FormatString-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-141">FormatString Element for ListItem (Format)</span></span>](./formatstring-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="67caf-142">Etikett element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-142">Label Element for ListItem (Format)</span></span>](./label-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="67caf-143">PropertyName-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-143">PropertyName Element for ListItem (Format)</span></span>](./propertyname-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="67caf-144">Script block-element för ListItem (format)</span><span class="sxs-lookup"><span data-stu-id="67caf-144">ScriptBlock Element for ListItem (Format)</span></span>](./scriptblock-element-for-listitem-for-listcontrol-format.md)

[<span data-ttu-id="67caf-145">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="67caf-145">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="67caf-146">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="67caf-146">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
