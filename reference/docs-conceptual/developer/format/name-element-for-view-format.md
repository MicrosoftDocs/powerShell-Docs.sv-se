---
title: Namn element för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 670b089f850fa4b39b7b100ca1e1ce45b05ea72d
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87773240"
---
# <a name="name-element-for-view-format"></a><span data-ttu-id="c443d-102">Name-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="c443d-102">Name Element for View (Format)</span></span>

<span data-ttu-id="c443d-103">Anger namnet som används för att identifiera vyn.</span><span class="sxs-lookup"><span data-stu-id="c443d-103">Specifies the name that is used to identify the view.</span></span>

<span data-ttu-id="c443d-104">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) namn element (format)</span><span class="sxs-lookup"><span data-stu-id="c443d-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Name Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c443d-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="c443d-105">Syntax</span></span>

```xml
<Name>ViewName</Name>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c443d-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c443d-106">Attributes and Elements</span></span>

<span data-ttu-id="c443d-107">I följande avsnitt beskrivs attribut, underordnade element och `Name` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c443d-107">The following sections describe attributes, child elements, and the parent element of the `Name` element.</span></span> <span data-ttu-id="c443d-108">Endast ett- `Name` element tillåts för varje vy.</span><span class="sxs-lookup"><span data-stu-id="c443d-108">Only one `Name` element is allowed for each view.</span></span>

### <a name="attributes"></a><span data-ttu-id="c443d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="c443d-109">Attributes</span></span>

<span data-ttu-id="c443d-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="c443d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c443d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c443d-111">Child Elements</span></span>

<span data-ttu-id="c443d-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="c443d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="c443d-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c443d-113">Parent Elements</span></span>

|<span data-ttu-id="c443d-114">Element</span><span class="sxs-lookup"><span data-stu-id="c443d-114">Element</span></span>|<span data-ttu-id="c443d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c443d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c443d-116">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="c443d-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="c443d-117">Definierar en vy som används för att visa medlemmar i ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="c443d-117">Defines a view that is used to display the members of one or more .NET objects.</span></span>|

## <a name="text-value"></a><span data-ttu-id="c443d-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="c443d-118">Text Value</span></span>

<span data-ttu-id="c443d-119">Ange ett unikt eget namn för vyn.</span><span class="sxs-lookup"><span data-stu-id="c443d-119">Specify a unique friendly name for the view.</span></span> <span data-ttu-id="c443d-120">Det här namnet kan innehålla en referens till typen av vy (till exempel en tabellvy eller listvy), vilket objekt eller en uppsättning objekt som använder vyn, vilket kommando returnerar objekten eller en kombination av dessa.</span><span class="sxs-lookup"><span data-stu-id="c443d-120">This name can include a reference to the type of the view (such as a table view or list view), which object or set of objects use the view, what command returns the objects, or a combination of these.</span></span>

## <a name="remarks"></a><span data-ttu-id="c443d-121">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c443d-121">Remarks</span></span>

<span data-ttu-id="c443d-122">Mer information om olika typer av vyer finns i följande avsnitt: [tabellvy](./creating-a-table-view.md), [listvy](./creating-a-list-view.md), [bred vy](./creating-a-wide-view.md)och [anpassad vy](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="c443d-122">For more information about the different types of views, see the following topics: [Table View](./creating-a-table-view.md), [List View](./creating-a-list-view.md), [Wide View](./creating-a-wide-view.md), and [Custom View](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="c443d-123">Exempel</span><span class="sxs-lookup"><span data-stu-id="c443d-123">Example</span></span>

<span data-ttu-id="c443d-124">I följande exempel visas ett- `View` element som definierar en tabellvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="c443d-124">The following example shows a `View` element that defines a table view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span> <span data-ttu-id="c443d-125">Namnet på vyn är "tjänst".</span><span class="sxs-lookup"><span data-stu-id="c443d-125">The name of the view is "service".</span></span>

```xml
<View>
  <Name>service</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <TableControl>...</TableControl>
</View>

```

## <a name="see-also"></a><span data-ttu-id="c443d-126">Se även</span><span class="sxs-lookup"><span data-stu-id="c443d-126">See Also</span></span>

[<span data-ttu-id="c443d-127">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="c443d-127">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c443d-128">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="c443d-128">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="c443d-129">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="c443d-129">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="c443d-130">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="c443d-130">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="c443d-131">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="c443d-131">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="c443d-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="c443d-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
