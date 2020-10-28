---
ms.date: 09/13/2016
ms.topic: reference
title: ViewSelectedBy-element (format)
description: ViewSelectedBy-element (format)
ms.openlocfilehash: ac3c7de299b3009a067a476a024c6a6fcb5dce02
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667716"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="6a451-103">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-103">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="6a451-104">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="6a451-104">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="6a451-105">Varje vy måste innehålla minst ett .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="6a451-105">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="6a451-106">ViewDefinitions-element (format) Visa element (format) ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-106">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="6a451-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="6a451-107">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="6a451-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="6a451-108">Attributes and Elements</span></span>

<span data-ttu-id="6a451-109">I följande avsnitt beskrivs attributen, underordnade element och `ViewSelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="6a451-109">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="6a451-110">Elementet måste innehålla minst ett `TypeName` eller `SelectionSetName` underordnat element.</span><span class="sxs-lookup"><span data-stu-id="6a451-110">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="6a451-111">Det finns ingen gräns för antalet underordnade element som kan anges eller som är deras inbördes ordning.</span><span class="sxs-lookup"><span data-stu-id="6a451-111">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="6a451-112">Attribut</span><span class="sxs-lookup"><span data-stu-id="6a451-112">Attributes</span></span>

<span data-ttu-id="6a451-113">Inga.</span><span class="sxs-lookup"><span data-stu-id="6a451-113">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="6a451-114">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="6a451-114">Child Elements</span></span>

|<span data-ttu-id="6a451-115">Element</span><span class="sxs-lookup"><span data-stu-id="6a451-115">Element</span></span>|<span data-ttu-id="6a451-116">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a451-116">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a451-117">TypeName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-117">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="6a451-118">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6a451-118">Optional element.</span></span><br /><br /> <span data-ttu-id="6a451-119">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="6a451-119">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="6a451-120">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-120">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="6a451-121">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="6a451-121">Optional element.</span></span><br /><br /> <span data-ttu-id="6a451-122">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="6a451-122">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="6a451-123">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="6a451-123">Parent Elements</span></span>

|<span data-ttu-id="6a451-124">Element</span><span class="sxs-lookup"><span data-stu-id="6a451-124">Element</span></span>|<span data-ttu-id="6a451-125">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="6a451-125">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="6a451-126">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-126">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="6a451-127">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="6a451-127">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="6a451-128">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="6a451-128">Remarks</span></span>

<span data-ttu-id="6a451-129">Mer information om hur det här elementet används i olika vyer finns i [tabellvy komponenter](./creating-a-table-view.md), [list Visa](./creating-a-list-view.md)komponenter, [wide View-komponenter](./creating-a-wide-view.md)och [anpassade kontroll komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="6a451-129">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="6a451-130">`SelectionSetName`Elementet används när format filen definierar en uppsättning objekt som visas av flera vyer.</span><span class="sxs-lookup"><span data-stu-id="6a451-130">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="6a451-131">Mer information om hur urvals uppsättningar definieras och refereras till finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="6a451-131">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="6a451-132">Exempel</span><span class="sxs-lookup"><span data-stu-id="6a451-132">Example</span></span>

<span data-ttu-id="6a451-133">I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy.</span><span class="sxs-lookup"><span data-stu-id="6a451-133">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="6a451-134">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="6a451-134">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="6a451-135">Se även</span><span class="sxs-lookup"><span data-stu-id="6a451-135">See Also</span></span>

[<span data-ttu-id="6a451-136">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="6a451-136">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="6a451-137">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="6a451-137">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="6a451-138">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="6a451-138">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="6a451-139">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="6a451-139">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="6a451-140">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="6a451-140">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="6a451-141">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-141">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="6a451-142">Elementet TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="6a451-142">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="6a451-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="6a451-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
