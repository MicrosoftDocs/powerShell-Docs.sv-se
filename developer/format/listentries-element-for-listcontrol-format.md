---
title: ListEntries Element för ListControl (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: b62e81cc-4175-40fa-829f-634245b09f86
caps.latest.revision: 12
ms.openlocfilehash: aaf16702e485135b5299ccb43a2b62db2d9f5762
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847364"
---
# <a name="listentries-element-for-listcontrol-format"></a><span data-ttu-id="8f84b-102">ListEntries-element för ListControl (format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-102">ListEntries Element for ListControl (Format)</span></span>

<span data-ttu-id="8f84b-103">Innehåller definitioner i listvyn.</span><span class="sxs-lookup"><span data-stu-id="8f84b-103">Provides the definitions of the list view.</span></span> <span data-ttu-id="8f84b-104">Listvyn måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="8f84b-104">The list view must specify one or more definitions.</span></span>

<span data-ttu-id="8f84b-105">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl Element (Format) ListEntries konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format) ListEntries Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8f84b-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8f84b-106">Syntax</span></span>

```xml
<ListEntries>
  <ListEntry>...</ListEntry>
</ListEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8f84b-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8f84b-107">Attributes and Elements</span></span>

<span data-ttu-id="8f84b-108">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListEntries` element.</span><span class="sxs-lookup"><span data-stu-id="8f84b-108">The following sections describe the attributes, child elements, and the parent element of the `ListEntries` element.</span></span> <span data-ttu-id="8f84b-109">Du måste ange minst ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="8f84b-109">At least one child element must be specified.</span></span>

### <a name="attributes"></a><span data-ttu-id="8f84b-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8f84b-110">Attributes</span></span>

<span data-ttu-id="8f84b-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="8f84b-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8f84b-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8f84b-112">Child Elements</span></span>

|<span data-ttu-id="8f84b-113">Element</span><span class="sxs-lookup"><span data-stu-id="8f84b-113">Element</span></span>|<span data-ttu-id="8f84b-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8f84b-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f84b-115">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-115">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)|<span data-ttu-id="8f84b-116">Innehåller en definition av listvyn.</span><span class="sxs-lookup"><span data-stu-id="8f84b-116">Provides a definition of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8f84b-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8f84b-117">Parent Elements</span></span>

|<span data-ttu-id="8f84b-118">Element</span><span class="sxs-lookup"><span data-stu-id="8f84b-118">Element</span></span>|<span data-ttu-id="8f84b-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8f84b-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8f84b-120">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-120">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)|<span data-ttu-id="8f84b-121">Definierar ett listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="8f84b-121">Defines a list format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8f84b-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="8f84b-122">Remarks</span></span>

<span data-ttu-id="8f84b-123">Läs mer om listvyer [listvyn](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="8f84b-123">For more information about list views, see [List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="8f84b-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="8f84b-124">Example</span></span>

<span data-ttu-id="8f84b-125">Det här exemplet visar XML-element som definierar listvyn för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="8f84b-125">This example shows the XML elements that define the list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="8f84b-126">Se även</span><span class="sxs-lookup"><span data-stu-id="8f84b-126">See Also</span></span>

[<span data-ttu-id="8f84b-127">ListControl Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-127">ListControl Element (Format)</span></span>](./listcontrol-element-format.md)

[<span data-ttu-id="8f84b-128">ListEntry Element (Format)</span><span class="sxs-lookup"><span data-stu-id="8f84b-128">ListEntry Element (Format)</span></span>](./listentry-element-for-listcontrol-format.md)

[<span data-ttu-id="8f84b-129">Listvy</span><span class="sxs-lookup"><span data-stu-id="8f84b-129">List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="8f84b-130">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="8f84b-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
