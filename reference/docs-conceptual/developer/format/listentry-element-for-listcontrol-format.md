---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntry-element för ListControl (format)
description: ListEntry-element för ListControl (format)
ms.openlocfilehash: 96ae5fcdd837d2491d6c7ff6a375fef1d83ae3e9
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666577"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="0ebcd-103">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-103">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="0ebcd-104">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-104">Provides a definition of the list view.</span></span>

<span data-ttu-id="0ebcd-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="0ebcd-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="0ebcd-106">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="0ebcd-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="0ebcd-107">Attributes and Elements</span></span>

<span data-ttu-id="0ebcd-108">I följande avsnitt beskrivs attributen, underordnade element och `ListEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="0ebcd-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="0ebcd-109">Attributes</span></span>

<span data-ttu-id="0ebcd-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="0ebcd-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="0ebcd-111">Child Elements</span></span>

|<span data-ttu-id="0ebcd-112">Element</span><span class="sxs-lookup"><span data-stu-id="0ebcd-112">Element</span></span>|<span data-ttu-id="0ebcd-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0ebcd-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ebcd-114">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-114">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0ebcd-115">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-115">Optional element.</span></span><br /><br /> <span data-ttu-id="0ebcd-116">Definierar de .NET-objekt som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-116">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="0ebcd-117">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-117">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="0ebcd-118">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-118">Required element.</span></span><br /><br /> <span data-ttu-id="0ebcd-119">Definierar egenskaper och skript vars värden visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-119">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="0ebcd-120">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="0ebcd-120">Parent Elements</span></span>

|<span data-ttu-id="0ebcd-121">Element</span><span class="sxs-lookup"><span data-stu-id="0ebcd-121">Element</span></span>|<span data-ttu-id="0ebcd-122">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="0ebcd-122">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="0ebcd-123">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-123">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="0ebcd-124">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-124">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="0ebcd-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="0ebcd-125">Remarks</span></span>

<span data-ttu-id="0ebcd-126">En listvy är ett List format som visar egenskaps värden eller skript värden för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="0ebcd-126">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="0ebcd-127">Mer information om listvyer finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="0ebcd-127">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="0ebcd-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="0ebcd-128">Example</span></span>

<span data-ttu-id="0ebcd-129">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="0ebcd-129">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>
        <ListItems>...</ListItems>
      </ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="0ebcd-130">Se även</span><span class="sxs-lookup"><span data-stu-id="0ebcd-130">See Also</span></span>

[<span data-ttu-id="0ebcd-131">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="0ebcd-131">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="0ebcd-132">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-132">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0ebcd-133">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-133">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="0ebcd-134">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="0ebcd-134">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="0ebcd-135">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="0ebcd-135">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
