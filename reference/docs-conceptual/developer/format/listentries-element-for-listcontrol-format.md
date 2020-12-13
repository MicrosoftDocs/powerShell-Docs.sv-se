---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntries-element för ListControl (format)
description: ListEntries-element för ListControl (format)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666611"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="8067f-103">ListEntries-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="8067f-104">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="8067f-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="8067f-105">Listvyn måste innehålla en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="8067f-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="8067f-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) element för ListEntries (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8067f-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="8067f-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8067f-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8067f-108">Attributes and Elements</span></span>

<span data-ttu-id="8067f-109">I följande avsnitt beskrivs attributen, underordnade element och `ListEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8067f-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="8067f-110">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="8067f-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8067f-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="8067f-111">Attributes</span></span>

<span data-ttu-id="8067f-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="8067f-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8067f-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8067f-113">Child Elements</span></span>

|<span data-ttu-id="8067f-114">Element</span><span class="sxs-lookup"><span data-stu-id="8067f-114">Element</span></span>|<span data-ttu-id="8067f-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8067f-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8067f-116">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="8067f-117">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="8067f-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8067f-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8067f-118">Parent Elements</span></span>

|<span data-ttu-id="8067f-119">Element</span><span class="sxs-lookup"><span data-stu-id="8067f-119">Element</span></span>|<span data-ttu-id="8067f-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8067f-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8067f-121">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="8067f-122">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="8067f-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8067f-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8067f-123">Remarks</span></span>

<span data-ttu-id="8067f-124">Mer information om listvyer finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8067f-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8067f-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="8067f-125">Example</span></span>

<span data-ttu-id="8067f-126">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="8067f-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8067f-127">Se även</span><span class="sxs-lookup"><span data-stu-id="8067f-127">See Also</span></span>

[<span data-ttu-id="8067f-128">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="8067f-129">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="8067f-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8067f-130">Listvy</span><span class="sxs-lookup"><span data-stu-id="8067f-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8067f-131">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="8067f-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
