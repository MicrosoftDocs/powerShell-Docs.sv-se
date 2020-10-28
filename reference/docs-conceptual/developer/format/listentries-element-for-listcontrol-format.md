---
ms.date: 09/13/2016
ms.topic: reference
title: ListEntries-element för ListControl (format)
description: ListEntries-element för ListControl (format)
ms.openlocfilehash: d4d6625bb92ea27863fc30d5bf5625f9275e4f69
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666611"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="c694c-103">ListEntries-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-103">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="c694c-104">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="c694c-104">Provides the definitions of the list view.</span></span> <span data-ttu-id="c694c-105">Listvyn måste innehålla en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="c694c-105">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="c694c-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) element för ListEntries (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="c694c-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="c694c-107">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="c694c-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="c694c-108">Attributes and Elements</span></span>

<span data-ttu-id="c694c-109">I följande avsnitt beskrivs attributen, underordnade element och `ListEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="c694c-109">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="c694c-110">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="c694c-110">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="c694c-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="c694c-111">Attributes</span></span>

<span data-ttu-id="c694c-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="c694c-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="c694c-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="c694c-113">Child Elements</span></span>

|<span data-ttu-id="c694c-114">Element</span><span class="sxs-lookup"><span data-stu-id="c694c-114">Element</span></span>|<span data-ttu-id="c694c-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c694c-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c694c-116">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-116">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="c694c-117">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="c694c-117">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="c694c-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="c694c-118">Parent Elements</span></span>

|<span data-ttu-id="c694c-119">Element</span><span class="sxs-lookup"><span data-stu-id="c694c-119">Element</span></span>|<span data-ttu-id="c694c-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="c694c-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="c694c-121">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-121">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="c694c-122">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="c694c-122">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="c694c-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="c694c-123">Remarks</span></span>

<span data-ttu-id="c694c-124">Mer information om listvyer finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="c694c-124">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="c694c-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="c694c-125">Example</span></span>

<span data-ttu-id="c694c-126">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="c694c-126">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="c694c-127">Se även</span><span class="sxs-lookup"><span data-stu-id="c694c-127">See Also</span></span>

[<span data-ttu-id="c694c-128">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-128">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="c694c-129">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="c694c-129">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="c694c-130">Listvy</span><span class="sxs-lookup"><span data-stu-id="c694c-130">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="c694c-131">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="c694c-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
