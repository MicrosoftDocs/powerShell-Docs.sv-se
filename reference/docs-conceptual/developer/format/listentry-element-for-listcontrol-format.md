---
title: ListEntry-element för ListControl (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: d98f0b5215eea7668f866d2733214ade79d748f1
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785701"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="839be-102">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="839be-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="839be-103">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="839be-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="839be-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="839be-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="839be-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="839be-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="839be-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="839be-106">Attributes and Elements</span></span>

<span data-ttu-id="839be-107">I följande avsnitt beskrivs attributen, underordnade element och `ListEntry` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="839be-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="839be-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="839be-108">Attributes</span></span>

<span data-ttu-id="839be-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="839be-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="839be-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="839be-110">Child Elements</span></span>

|<span data-ttu-id="839be-111">Element</span><span class="sxs-lookup"><span data-stu-id="839be-111">Element</span></span>|<span data-ttu-id="839be-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="839be-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="839be-113">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="839be-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="839be-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="839be-114">Optional element.</span></span><br /><br /> <span data-ttu-id="839be-115">Definierar de .NET-objekt som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="839be-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="839be-116">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="839be-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="839be-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="839be-117">Required element.</span></span><br /><br /> <span data-ttu-id="839be-118">Definierar egenskaper och skript vars värden visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="839be-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="839be-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="839be-119">Parent Elements</span></span>

|<span data-ttu-id="839be-120">Element</span><span class="sxs-lookup"><span data-stu-id="839be-120">Element</span></span>|<span data-ttu-id="839be-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="839be-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="839be-122">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="839be-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="839be-123">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="839be-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="839be-124">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="839be-124">Remarks</span></span>

<span data-ttu-id="839be-125">En listvy är ett List format som visar egenskaps värden eller skript värden för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="839be-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="839be-126">Mer information om listvyer finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="839be-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="839be-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="839be-127">Example</span></span>

<span data-ttu-id="839be-128">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="839be-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="839be-129">Se även</span><span class="sxs-lookup"><span data-stu-id="839be-129">See Also</span></span>

[<span data-ttu-id="839be-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="839be-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="839be-131">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="839be-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="839be-132">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="839be-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="839be-133">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="839be-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="839be-134">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="839be-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
