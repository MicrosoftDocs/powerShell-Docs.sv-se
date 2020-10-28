---
ms.date: 09/13/2016
ms.topic: reference
title: TypeName-element för ViewSelectedBy (format)
description: TypeName-element för ViewSelectedBy (format)
ms.openlocfilehash: 62edc2fe4b4c1c5f1b17dd2f8b0943f28ff5dfb7
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92667733"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="f324d-103">TypeName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="f324d-103">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="f324d-104">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f324d-104">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="f324d-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="f324d-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f324d-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="f324d-106">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="f324d-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f324d-107">Attributes and Elements</span></span>

<span data-ttu-id="f324d-108">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="f324d-108">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f324d-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f324d-109">Attributes</span></span>

<span data-ttu-id="f324d-110">Inga.</span><span class="sxs-lookup"><span data-stu-id="f324d-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f324d-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f324d-111">Child Elements</span></span>

<span data-ttu-id="f324d-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="f324d-112">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="f324d-113">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f324d-113">Parent Elements</span></span>

|<span data-ttu-id="f324d-114">Element</span><span class="sxs-lookup"><span data-stu-id="f324d-114">Element</span></span>|<span data-ttu-id="f324d-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f324d-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f324d-116">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="f324d-116">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="f324d-117">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="f324d-117">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="f324d-118">Textvärde</span><span class="sxs-lookup"><span data-stu-id="f324d-118">Text Value</span></span>

<span data-ttu-id="f324d-119">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="f324d-119">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="f324d-120">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="f324d-120">Remarks</span></span>

<span data-ttu-id="f324d-121">Mer information om hur det här elementet används i olika vyer finns i [skapa en tabellvy](./creating-a-table-view.md), [skapa en listvy](./creating-a-list-view.md), [skapa en bred vy](./creating-a-wide-view.md)och [Anpassa View-komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="f324d-121">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="f324d-122">Exempel</span><span class="sxs-lookup"><span data-stu-id="f324d-122">Example</span></span>

<span data-ttu-id="f324d-123">I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy.</span><span class="sxs-lookup"><span data-stu-id="f324d-123">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="f324d-124">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="f324d-124">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="f324d-125">Se även</span><span class="sxs-lookup"><span data-stu-id="f324d-125">See Also</span></span>

[<span data-ttu-id="f324d-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="f324d-126">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f324d-127">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="f324d-127">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="f324d-128">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="f324d-128">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="f324d-129">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="f324d-129">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="f324d-130">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="f324d-130">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="f324d-131">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="f324d-131">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
