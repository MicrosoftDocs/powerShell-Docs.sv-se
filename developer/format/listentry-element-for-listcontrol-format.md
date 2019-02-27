---
title: ListEntry Element för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 6d16bca8-d025-432d-aa84-8b607b8af3ae
caps.latest.revision: 12
ms.openlocfilehash: 1a3bafd4ca94aee70e869c699f7a4ef8befc5511
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851186"
---
# <a name="listentry-element-for-listcontrol-format"></a><span data-ttu-id="b7ced-102">ListEntry-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-102">ListEntry Element for ListControl (Format)</span></span>

<span data-ttu-id="b7ced-103">Innehåller en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="b7ced-103">Provides a definition of the list view.</span></span>

<span data-ttu-id="b7ced-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format) ListEntry Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="b7ced-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="b7ced-105">Syntax</span></span>

```xml
<ListEntry>
  <EntrySelectedBy>...</EntrySelectedBy>
  <ListItems>...</ListItems>
</ListEntry>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="b7ced-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="b7ced-106">Attributes and Elements</span></span>

<span data-ttu-id="b7ced-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListEntry` element.</span><span class="sxs-lookup"><span data-stu-id="b7ced-107">The following sections describe the attributes, child elements, and the parent element of the `ListEntry` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="b7ced-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="b7ced-108">Attributes</span></span>

<span data-ttu-id="b7ced-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="b7ced-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="b7ced-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="b7ced-110">Child Elements</span></span>

|<span data-ttu-id="b7ced-111">Element</span><span class="sxs-lookup"><span data-stu-id="b7ced-111">Element</span></span>|<span data-ttu-id="b7ced-112">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7ced-112">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ced-113">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-113">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b7ced-114">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="b7ced-114">Optional element.</span></span><br /><br /> <span data-ttu-id="b7ced-115">Definierar de .NET-objekt som använder den här listan vydefinitionen eller villkor som måste finnas för den här definitionen som ska användas.</span><span class="sxs-lookup"><span data-stu-id="b7ced-115">Defines the .NET objects that use this list view definition or the condition that must exist for this definition to be used.</span></span>|
|[<span data-ttu-id="b7ced-116">ListItems som finns Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-116">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)|<span data-ttu-id="b7ced-117">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="b7ced-117">Required element.</span></span><br /><br /> <span data-ttu-id="b7ced-118">Definierar egenskaperna och skript vars värden visas i listvyn.</span><span class="sxs-lookup"><span data-stu-id="b7ced-118">Defines the properties and scripts whose values are displayed by the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="b7ced-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="b7ced-119">Parent Elements</span></span>

|<span data-ttu-id="b7ced-120">Element</span><span class="sxs-lookup"><span data-stu-id="b7ced-120">Element</span></span>|<span data-ttu-id="b7ced-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="b7ced-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="b7ced-122">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-122">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="b7ced-123">Innehåller definitioner i listvyn.</span><span class="sxs-lookup"><span data-stu-id="b7ced-123">Provides the definitions of the list view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="b7ced-124">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="b7ced-124">Remarks</span></span>

<span data-ttu-id="b7ced-125">En listvy är ett listformat som visar egenskapsvärden eller skript värden för varje objekt.</span><span class="sxs-lookup"><span data-stu-id="b7ced-125">A list view is a list format that displays property values or script values for each object.</span></span> <span data-ttu-id="b7ced-126">Läs mer om listvyer [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="b7ced-126">For more information about list views, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="b7ced-127">Exempel</span><span class="sxs-lookup"><span data-stu-id="b7ced-127">Example</span></span>

<span data-ttu-id="b7ced-128">Det här exemplet visar XML-element som definierar listvyn för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="b7ced-128">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b7ced-129">Se även</span><span class="sxs-lookup"><span data-stu-id="b7ced-129">See Also</span></span>

[<span data-ttu-id="b7ced-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="b7ced-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="b7ced-131">EntrySelectedBy Element för ListEntry (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-131">EntrySelectedBy Element for ListEntry (Format)</span></span>](./entryselectedby-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b7ced-132">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-132">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="b7ced-133">ListItems som finns Element (Format)</span><span class="sxs-lookup"><span data-stu-id="b7ced-133">ListItems Element (Format)</span></span>](./listitems-element-for-listentry-for-listcontrol-format.md)

[<span data-ttu-id="b7ced-134">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="b7ced-134">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
