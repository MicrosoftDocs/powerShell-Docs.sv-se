---
title: ViewSelectedBy-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: acdeef4d-3554-4f39-a7e6-a684e3848fd7
caps.latest.revision: 19
ms.openlocfilehash: efc1c5d1338889ecd0be7150b7733842ce78979e
ms.sourcegitcommit: 52a67bcd9d7bf3e8600ea4302d1fa8970ff9c998
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/15/2019
ms.locfileid: "72358732"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="21d1c-102">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="21d1c-103">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="21d1c-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="21d1c-104">Varje vy måste innehålla minst ett .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="21d1c-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="21d1c-105">ViewDefinitions-element (format) Visa element (format) ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="21d1c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="21d1c-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="21d1c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="21d1c-107">Attributes and Elements</span></span>

<span data-ttu-id="21d1c-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ViewSelectedBy`-elementet.</span><span class="sxs-lookup"><span data-stu-id="21d1c-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="21d1c-109">Det här elementet måste innehålla minst ett underordnat element `TypeName` eller `SelectionSetName`.</span><span class="sxs-lookup"><span data-stu-id="21d1c-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="21d1c-110">Det finns ingen gräns för antalet underordnade element som kan anges eller som är deras inbördes ordning.</span><span class="sxs-lookup"><span data-stu-id="21d1c-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="21d1c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="21d1c-111">Attributes</span></span>

<span data-ttu-id="21d1c-112">Ingen.</span><span class="sxs-lookup"><span data-stu-id="21d1c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="21d1c-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="21d1c-113">Child Elements</span></span>

|<span data-ttu-id="21d1c-114">Element</span><span class="sxs-lookup"><span data-stu-id="21d1c-114">Element</span></span>|<span data-ttu-id="21d1c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="21d1c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21d1c-116">Elementet TypeName för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="21d1c-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21d1c-117">Optional element.</span></span><br /><br /> <span data-ttu-id="21d1c-118">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="21d1c-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="21d1c-119">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="21d1c-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="21d1c-120">Optional element.</span></span><br /><br /> <span data-ttu-id="21d1c-121">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="21d1c-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="21d1c-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="21d1c-122">Parent Elements</span></span>

|<span data-ttu-id="21d1c-123">Element</span><span class="sxs-lookup"><span data-stu-id="21d1c-123">Element</span></span>|<span data-ttu-id="21d1c-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="21d1c-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="21d1c-125">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="21d1c-126">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="21d1c-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="21d1c-127">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="21d1c-127">Remarks</span></span>

<span data-ttu-id="21d1c-128">Mer information om hur det här elementet används i olika vyer finns i [tabellvy komponenter](./creating-a-table-view.md), [list Visa](./creating-a-list-view.md)komponenter, [wide View-komponenter](./creating-a-wide-view.md)och [anpassade kontroll komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="21d1c-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="21d1c-129">Elementet `SelectionSetName` används när format filen definierar en uppsättning objekt som visas av flera vyer.</span><span class="sxs-lookup"><span data-stu-id="21d1c-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="21d1c-130">Mer information om hur urvals uppsättningar definieras och refereras till finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="21d1c-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="21d1c-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="21d1c-131">Example</span></span>

<span data-ttu-id="21d1c-132">I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy.</span><span class="sxs-lookup"><span data-stu-id="21d1c-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="21d1c-133">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="21d1c-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="21d1c-134">Se även</span><span class="sxs-lookup"><span data-stu-id="21d1c-134">See Also</span></span>

[<span data-ttu-id="21d1c-135">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="21d1c-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="21d1c-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="21d1c-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="21d1c-137">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="21d1c-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="21d1c-138">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="21d1c-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="21d1c-139">Definiera urvals uppsättningar</span><span class="sxs-lookup"><span data-stu-id="21d1c-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="21d1c-140">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="21d1c-141">Elementet TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="21d1c-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="21d1c-142">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="21d1c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
