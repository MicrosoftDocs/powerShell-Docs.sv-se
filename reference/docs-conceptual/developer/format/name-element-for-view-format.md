---
ms.date: 09/13/2016
ms.topic: reference
title: Name-element för View (format)
description: Name-element för View (format)
ms.openlocfilehash: 5781bcdf7a0e1eb5e9c7e97bb6acc0a383dc0262
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666473"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="e82c0-103">Name-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="e82c0-103">Name Element for View (Format)</span></span>

<span data-ttu-id="e82c0-104">Anger namnet som används för att identifiera vyn.</span><span class="sxs-lookup"><span data-stu-id="e82c0-104">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="e82c0-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) namn element (format)</span><span class="sxs-lookup"><span data-stu-id="e82c0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="e82c0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="e82c0-106">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="e82c0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="e82c0-107">Attributes and Elements</span></span>

<span data-ttu-id="e82c0-108">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="e82c0-108">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="e82c0-109">Endast ett- `Name` element tillåts för varje vy.</span><span class="sxs-lookup"><span data-stu-id="e82c0-109">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="e82c0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="e82c0-110">Attributes</span></span>

<span data-ttu-id="e82c0-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="e82c0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="e82c0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="e82c0-112">Child Elements</span></span>

<span data-ttu-id="e82c0-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="e82c0-113">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="e82c0-114">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="e82c0-114">Parent Elements</span></span>

|<span data-ttu-id="e82c0-115">Element</span><span class="sxs-lookup"><span data-stu-id="e82c0-115">Element</span></span>|<span data-ttu-id="e82c0-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="e82c0-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="e82c0-117">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e82c0-117">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="e82c0-118">Definierar en vy som används för att visa medlemmar i ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="e82c0-118">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="e82c0-119">Textvärde</span><span class="sxs-lookup"><span data-stu-id="e82c0-119">Text Value</span></span>

<span data-ttu-id="e82c0-120">Ange ett unikt eget namn för vyn.</span><span class="sxs-lookup"><span data-stu-id="e82c0-120">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="e82c0-121">Det här namnet kan innehålla en referens till typen av vy (till exempel en tabellvy eller listvy), vilket objekt eller en uppsättning objekt som använder vyn, vilket kommando returnerar objekten eller en kombination av dessa.</span><span class="sxs-lookup"><span data-stu-id="e82c0-121">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="e82c0-122">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="e82c0-122">Remarks</span></span>

<span data-ttu-id="e82c0-123">Mer information om olika typer av vyer finns i följande avsnitt: [tabellvy](./creating-a-table-view.md), [listvy](./creating-a-list-view.md), [bred vy](./creating-a-wide-view.md)och [anpassad vy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="e82c0-123">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="e82c0-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="e82c0-124">Example</span></span>

<span data-ttu-id="e82c0-125">I följande exempel visas ett- `View` element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="e82c0-125">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="e82c0-126">Namnet på vyn är "tjänst".</span><span class="sxs-lookup"><span data-stu-id="e82c0-126">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="e82c0-127">Se även</span><span class="sxs-lookup"><span data-stu-id="e82c0-127">See Also</span></span>

[<span data-ttu-id="e82c0-128">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="e82c0-128">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="e82c0-129">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="e82c0-129">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="e82c0-130">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="e82c0-130">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="e82c0-131">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="e82c0-131">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="e82c0-132">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="e82c0-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="e82c0-133">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="e82c0-133">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
