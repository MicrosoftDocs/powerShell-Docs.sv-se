---
title: ListEntries-element för ListControl (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72354357"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="cc475-102">ListEntries-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="cc475-103">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="cc475-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="cc475-104">Listvyn måste innehålla en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="cc475-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="cc475-105">Konfigurations element (format) ViewDefinitions element (format) View-element (format) ListControl-element (format) element för ListEntries (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="cc475-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="cc475-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="cc475-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="cc475-107">Attributes and Elements</span></span>

<span data-ttu-id="cc475-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ListEntries`-elementet.</span><span class="sxs-lookup"><span data-stu-id="cc475-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="cc475-109">Minst ett underordnat element måste anges.</span><span class="sxs-lookup"><span data-stu-id="cc475-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="cc475-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="cc475-110">Attributes</span></span>

<span data-ttu-id="cc475-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="cc475-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="cc475-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="cc475-112">Child Elements</span></span>

|<span data-ttu-id="cc475-113">Element</span><span class="sxs-lookup"><span data-stu-id="cc475-113">Element</span></span>|<span data-ttu-id="cc475-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cc475-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc475-115">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="cc475-116">Ger en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="cc475-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="cc475-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="cc475-117">Parent Elements</span></span>

|<span data-ttu-id="cc475-118">Element</span><span class="sxs-lookup"><span data-stu-id="cc475-118">Element</span></span>|<span data-ttu-id="cc475-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="cc475-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="cc475-120">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="cc475-121">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="cc475-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="cc475-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="cc475-122">Remarks</span></span>

<span data-ttu-id="cc475-123">Mer information om listvyer finns i [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="cc475-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="cc475-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="cc475-124">Example</span></span>

<span data-ttu-id="cc475-125">I det här exemplet visas de XML-element som definierar listvyn för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="cc475-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cc475-126">Se även</span><span class="sxs-lookup"><span data-stu-id="cc475-126">See Also</span></span>

[<span data-ttu-id="cc475-127">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="cc475-128">ListEntry-element (format)</span><span class="sxs-lookup"><span data-stu-id="cc475-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="cc475-129">Listvy</span><span class="sxs-lookup"><span data-stu-id="cc475-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="cc475-130">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="cc475-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
