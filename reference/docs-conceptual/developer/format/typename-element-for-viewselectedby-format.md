---
title: Elementet TypeName för ViewSelectedBy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: e9a391565c3e66041dd9a340455dccfce9ce929b
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87780040"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="75152-102">TypeName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="75152-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="75152-103">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="75152-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="75152-104">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ViewSelectedBy-element (format) element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="75152-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="75152-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="75152-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="75152-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="75152-106">Attributes and Elements</span></span>

<span data-ttu-id="75152-107">I följande avsnitt beskrivs attribut, underordnade element och `TypeName` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="75152-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="75152-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="75152-108">Attributes</span></span>

<span data-ttu-id="75152-109">Inga.</span><span class="sxs-lookup"><span data-stu-id="75152-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="75152-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="75152-110">Child Elements</span></span>

<span data-ttu-id="75152-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="75152-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="75152-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="75152-112">Parent Elements</span></span>

|<span data-ttu-id="75152-113">Element</span><span class="sxs-lookup"><span data-stu-id="75152-113">Element</span></span>|<span data-ttu-id="75152-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="75152-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="75152-115">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="75152-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="75152-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="75152-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="75152-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="75152-117">Text Value</span></span>

<span data-ttu-id="75152-118">Ange det fullständigt kvalificerade namnet för .NET-typen, t `System.IO.DirectoryInfo` . ex..</span><span class="sxs-lookup"><span data-stu-id="75152-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="75152-119">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="75152-119">Remarks</span></span>

<span data-ttu-id="75152-120">Mer information om hur det här elementet används i olika vyer finns i [skapa en tabellvy](./creating-a-table-view.md), [skapa en listvy](./creating-a-list-view.md), [skapa en bred vy](./creating-a-wide-view.md)och [Anpassa View-komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="75152-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="75152-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="75152-121">Example</span></span>

<span data-ttu-id="75152-122">I följande exempel visas hur du anger objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) för en listvy.</span><span class="sxs-lookup"><span data-stu-id="75152-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="75152-123">Samma schema används för tabeller, breda och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="75152-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="75152-124">Se även</span><span class="sxs-lookup"><span data-stu-id="75152-124">See Also</span></span>

[<span data-ttu-id="75152-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="75152-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="75152-126">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="75152-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="75152-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="75152-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="75152-128">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="75152-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="75152-129">ViewSelectedBy-element (format)</span><span class="sxs-lookup"><span data-stu-id="75152-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="75152-130">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="75152-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
