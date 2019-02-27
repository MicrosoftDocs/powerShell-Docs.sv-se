---
title: TypeName-Element för ViewSelectedBy (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 0ad807a9-d7d8-4e96-b799-9c6a7677cc2d
caps.latest.revision: 12
ms.openlocfilehash: e2028c479103cc414295dc24a0f9bb69190bfc66
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56848141"
---
# <a name="typename-element-for-viewselectedby-format"></a><span data-ttu-id="2fb92-102">TypeName-element för ViewSelectedBy (format)</span><span class="sxs-lookup"><span data-stu-id="2fb92-102">TypeName Element for ViewSelectedBy (Format)</span></span>

<span data-ttu-id="2fb92-103">Anger ett .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2fb92-103">Specifies a .NET object that is displayed by the view.</span></span>

<span data-ttu-id="2fb92-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ViewSelectedBy Element (Format) TypeName konfigurationselement för ViewSelectedBy (Format)</span><span class="sxs-lookup"><span data-stu-id="2fb92-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ViewSelectedBy Element (Format) TypeName Element for ViewSelectedBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="2fb92-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="2fb92-105">Syntax</span></span>

```xml
<TypeName>FullyQualifiedTypeName</TypeName>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="2fb92-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="2fb92-106">Attributes and Elements</span></span>

<span data-ttu-id="2fb92-107">I följande avsnitt beskrivs attribut, underordnade element och de överordnade element i den `TypeName` element.</span><span class="sxs-lookup"><span data-stu-id="2fb92-107">The following sections describe attributes, child elements, and the parent elements of the `TypeName` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="2fb92-108">Attribut</span><span class="sxs-lookup"><span data-stu-id="2fb92-108">Attributes</span></span>

<span data-ttu-id="2fb92-109">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2fb92-109">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="2fb92-110">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="2fb92-110">Child Elements</span></span>

<span data-ttu-id="2fb92-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="2fb92-111">None.</span></span>

### <a name="parent-elements"></a><span data-ttu-id="2fb92-112">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="2fb92-112">Parent Elements</span></span>

|<span data-ttu-id="2fb92-113">Element</span><span class="sxs-lookup"><span data-stu-id="2fb92-113">Element</span></span>|<span data-ttu-id="2fb92-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="2fb92-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="2fb92-115">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2fb92-115">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)|<span data-ttu-id="2fb92-116">Definierar de .NET-objekt som visas i vyn.</span><span class="sxs-lookup"><span data-stu-id="2fb92-116">Defines the .NET objects that are displayed by the view.</span></span>|

## <a name="text-value"></a><span data-ttu-id="2fb92-117">Textvärde</span><span class="sxs-lookup"><span data-stu-id="2fb92-117">Text Value</span></span>

<span data-ttu-id="2fb92-118">Ange det fullständigt kvalificerade namnet för .NET-typ, till exempel `System.IO.DirectoryInfo`.</span><span class="sxs-lookup"><span data-stu-id="2fb92-118">Specify the fully qualified name of the .NET type, such as `System.IO.DirectoryInfo`.</span></span>

## <a name="remarks"></a><span data-ttu-id="2fb92-119">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="2fb92-119">Remarks</span></span>

<span data-ttu-id="2fb92-120">Mer information om hur det här elementet används i olika vyer finns i [skapar en tabellvy](./creating-a-table-view.md), [skapar en listvy](./creating-a-list-view.md), [skapar en bred vy](./creating-a-wide-view.md), och [ Anpassad vy komponenter](./creating-custom-controls.md).</span><span class="sxs-lookup"><span data-stu-id="2fb92-120">For more information about how this element is used in different views, see [Creating a Table View](./creating-a-table-view.md), [Creating a List View](./creating-a-list-view.md), [Creating a Wide View](./creating-a-wide-view.md), and [Custom View Components](./creating-custom-controls.md).</span></span>

## <a name="example"></a><span data-ttu-id="2fb92-121">Exempel</span><span class="sxs-lookup"><span data-stu-id="2fb92-121">Example</span></span>

<span data-ttu-id="2fb92-122">I följande exempel visas hur du anger den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt för en listvy.</span><span class="sxs-lookup"><span data-stu-id="2fb92-122">The following example shows how to specify the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object for a list view.</span></span> <span data-ttu-id="2fb92-123">Samma schema används för tabellen, bred och anpassade vyer.</span><span class="sxs-lookup"><span data-stu-id="2fb92-123">The same schema is used for table, wide, and custom views.</span></span>

```xml
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>...</ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="2fb92-124">Se även</span><span class="sxs-lookup"><span data-stu-id="2fb92-124">See Also</span></span>

[<span data-ttu-id="2fb92-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="2fb92-125">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="2fb92-126">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="2fb92-126">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="2fb92-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="2fb92-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="2fb92-128">Skapa anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="2fb92-128">Creating Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="2fb92-129">ViewSelectedBy Element (Format)</span><span class="sxs-lookup"><span data-stu-id="2fb92-129">ViewSelectedBy Element (Format)</span></span>](./viewselectedby-element-format.md)

[<span data-ttu-id="2fb92-130">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="2fb92-130">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
