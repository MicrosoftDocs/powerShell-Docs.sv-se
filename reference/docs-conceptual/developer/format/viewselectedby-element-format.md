---
title: ViewSelectedBy-element (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: c8704c1504c6e24c9cac6bc8bc25e92a0d9110cc
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785021"
---
# <a name="viewselectedby-element-format"></a><span data-ttu-id="ae259-102">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-102">ViewSelectedBy Element (Format)</span></span>

<span data-ttu-id="ae259-103">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ae259-103">Defines the .NET objects that are displayed by the view.</span></span> <span data-ttu-id="ae259-104">Varje vy måste innehålla minst ett .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ae259-104">Each view must specify at least one .NET object.</span></span>

<span data-ttu-id="ae259-105">ViewDefinitions-element (format) Visa element (format) ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-105">ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="ae259-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ae259-106">Syntax</span></span>

```xml
<ViewSelectedBy>
  <TypeName>Nameof.NetType</TypeName>
  <SelectionSetName>SelectionSet</SelectionSetName>
</ViewSelectedBy>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ae259-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ae259-107">Attributes and Elements</span></span>

<span data-ttu-id="ae259-108">I följande avsnitt beskrivs attributen, underordnade element och `ViewSelectedBy` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="ae259-108">The following sections describe the attributes, child elements, and parent element of the `ViewSelectedBy` element.</span></span> <span data-ttu-id="ae259-109">Elementet måste innehålla minst ett `TypeName` eller `SelectionSetName` underordnat element.</span><span class="sxs-lookup"><span data-stu-id="ae259-109">This element must contain at least one `TypeName` or `SelectionSetName` child element.</span></span> <span data-ttu-id="ae259-110">Det finns ingen gräns för antalet underordnade element som kan anges eller som är deras inbördes ordning.</span><span class="sxs-lookup"><span data-stu-id="ae259-110">There is no limit to the number of child elements that can be specified nor is their order significant.</span></span>

### <a name="attributes"></a><span data-ttu-id="ae259-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="ae259-111">Attributes</span></span>

<span data-ttu-id="ae259-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="ae259-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ae259-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ae259-113">Child Elements</span></span>

|<span data-ttu-id="ae259-114">Element</span><span class="sxs-lookup"><span data-stu-id="ae259-114">Element</span></span>|<span data-ttu-id="ae259-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ae259-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae259-116">TypeName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-116">TypeName Element for ViewSelectedBy (Format)</span></span>](./typename-element-for-viewselectedby-format.md)|<span data-ttu-id="ae259-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ae259-117">Optional element.</span></span><br /><br /> <span data-ttu-id="ae259-118">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ae259-118">Specifies a .NET object that is displayed by the view.</span></span>|
|[<span data-ttu-id="ae259-119">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-119">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)|<span data-ttu-id="ae259-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="ae259-120">Optional element.</span></span><br /><br /> <span data-ttu-id="ae259-121">Anger en uppsättning .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="ae259-121">Specifies a set of .NET objects that are displayed by the view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ae259-122">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ae259-122">Parent Elements</span></span>

|<span data-ttu-id="ae259-123">Element</span><span class="sxs-lookup"><span data-stu-id="ae259-123">Element</span></span>|<span data-ttu-id="ae259-124">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ae259-124">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ae259-125">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-125">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ae259-126">Definierar en vy som visar ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ae259-126">Defines a view that displays one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ae259-127">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="ae259-127">Remarks</span></span>

<span data-ttu-id="ae259-128">Mer information om hur det här elementet används i olika vyer finns i [tabellvy komponenter](./creating-a-table-view.md), [list Visa](./creating-a-list-view.md)komponenter, [wide View-komponenter](./creating-a-wide-view.md)och [anpassade kontroll komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="ae259-128">For more information about how this element is used in different views, see [Table View Components](./creating-a-table-view.md), [List View Components](./creating-a-list-view.md), [Wide View Components](./creating-a-wide-view.md), and [Custom Control Components](./creating-custom-controls.md).</span></span>

<span data-ttu-id="ae259-129">`SelectionSetName`Elementet används när format filen definierar en uppsättning objekt som visas av flera vyer.</span><span class="sxs-lookup"><span data-stu-id="ae259-129">The `SelectionSetName` element is used when the formatting file defines a set of objects that are displayed by multiple views.</span></span> <span data-ttu-id="ae259-130">Mer information om hur urvals uppsättningar definieras och refereras till finns i [definiera uppsättningar av objekt](./defining-selection-sets.md).</span><span class="sxs-lookup"><span data-stu-id="ae259-130">For more information about how selection sets are defined and referenced, see [Defining Sets of Objects](./defining-selection-sets.md).</span></span>

## <a name="example"></a><span data-ttu-id="ae259-131">Exempel</span><span class="sxs-lookup"><span data-stu-id="ae259-131">Example</span></span>

<span data-ttu-id="ae259-132">I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy.</span><span class="sxs-lookup"><span data-stu-id="ae259-132">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="ae259-133">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="ae259-133">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="ae259-134">Se även</span><span class="sxs-lookup"><span data-stu-id="ae259-134">See Also</span></span>

[<span data-ttu-id="ae259-135">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="ae259-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ae259-136">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="ae259-136">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ae259-137">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="ae259-137">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ae259-138">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="ae259-138">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ae259-139">Definiera valuppsättningar</span><span class="sxs-lookup"><span data-stu-id="ae259-139">Defining Selection Sets</span></span>](./defining-selection-sets.md)

[<span data-ttu-id="ae259-140">SelectionSetName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-140">SelectionSetName Element for ViewSelectedBy (Format)</span></span>](./selectionsetname-element-for-viewselectedby-format.md)

[<span data-ttu-id="ae259-141">Elementet TypeName (format)</span><span class="sxs-lookup"><span data-stu-id="ae259-141">TypeName Element (Format)</span></span>](./typename-element-for-viewselectedby-format.md)

[<span data-ttu-id="ae259-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="ae259-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
