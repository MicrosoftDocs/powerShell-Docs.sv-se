---
title: ListEntry-element för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72354350"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="3aa0d-102">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="3aa0d-103">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="3aa0d-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) ListEntries-element (format) ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3aa0d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="3aa0d-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3aa0d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3aa0d-106">Attributes and Elements</span></span>

<span data-ttu-id="3aa0d-107">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet för elementet `ListEntry`.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3aa0d-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="3aa0d-108">Attributes</span></span>

<span data-ttu-id="3aa0d-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3aa0d-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3aa0d-110">Child Elements</span></span>

|<span data-ttu-id="3aa0d-111">Element</span><span class="sxs-lookup"><span data-stu-id="3aa0d-111">Element</span></span>|<span data-ttu-id="3aa0d-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3aa0d-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aa0d-113">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3aa0d-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-114">Optional element.</span></span><br /><br /> <span data-ttu-id="3aa0d-115">Definierar de .NET-objekt som använder den här List vydefinitionen eller det villkor som måste finnas för att den här definitionen ska kunna användas.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="3aa0d-116">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="3aa0d-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-117">Required element.</span></span><br /><br /> <span data-ttu-id="3aa0d-118">Definierar egenskaper och skript vars värden visas i list visningen.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3aa0d-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3aa0d-119">Parent Elements</span></span>

|<span data-ttu-id="3aa0d-120">Element</span><span class="sxs-lookup"><span data-stu-id="3aa0d-120">Element</span></span>|<span data-ttu-id="3aa0d-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3aa0d-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3aa0d-122">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="3aa0d-123">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3aa0d-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="3aa0d-124">Remarks</span></span>

<span data-ttu-id="3aa0d-125">En listvy är ett List format som visar egenskaps värden eller skript värden för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="3aa0d-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="3aa0d-126">Mer information om listvyer finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="3aa0d-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="3aa0d-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="3aa0d-127">Example</span></span>

<span data-ttu-id="3aa0d-128">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="3aa0d-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="3aa0d-129">Se även</span><span class="sxs-lookup"><span data-stu-id="3aa0d-129">See Also</span></span>

[<span data-ttu-id="3aa0d-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="3aa0d-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="3aa0d-131">EntrySelectedBy-element för ListEntry (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3aa0d-132">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="3aa0d-133">ListItems-element (format)</span><span class="sxs-lookup"><span data-stu-id="3aa0d-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="3aa0d-134">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="3aa0d-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
