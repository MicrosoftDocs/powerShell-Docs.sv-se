---
title: ListControl Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 37beeb0b-7a81-4747-becb-e309e17278fb
caps.latest.revision: 12
ms.openlocfilehash: 7a117c25b0d117dc846ba8e060e31e838b5edd52
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56847833"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="5c31e-102">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-102">ListControl Element (Format)</span></span>

<span data-ttu-id="5c31e-103">Definierar ett listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="5c31e-103">Defines a list format for the view.</span></span>

<span data-ttu-id="5c31e-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="5c31e-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="5c31e-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="5c31e-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="5c31e-106">Attributes and Elements</span></span>

<span data-ttu-id="5c31e-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListControl` element.</span><span class="sxs-lookup"><span data-stu-id="5c31e-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="5c31e-108">Det här elementet måste innehålla en enda underelement.</span><span class="sxs-lookup"><span data-stu-id="5c31e-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="5c31e-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="5c31e-109">Attributes</span></span>

<span data-ttu-id="5c31e-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="5c31e-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="5c31e-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="5c31e-111">Child Elements</span></span>

|<span data-ttu-id="5c31e-112">Element</span><span class="sxs-lookup"><span data-stu-id="5c31e-112">Element</span></span>|<span data-ttu-id="5c31e-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5c31e-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c31e-114">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="5c31e-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="5c31e-115">Required element.</span></span><br /><br /> <span data-ttu-id="5c31e-116">Innehåller definitioner i listvyn.</span><span class="sxs-lookup"><span data-stu-id="5c31e-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="5c31e-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="5c31e-117">Parent Elements</span></span>

|<span data-ttu-id="5c31e-118">Element</span><span class="sxs-lookup"><span data-stu-id="5c31e-118">Element</span></span>|<span data-ttu-id="5c31e-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="5c31e-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="5c31e-120">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="5c31e-121">Definierar en vy som används för att visa medlemmarna i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="5c31e-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="5c31e-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="5c31e-122">Remarks</span></span>

<span data-ttu-id="5c31e-123">Läs mer om hur du skapar en listvy [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="5c31e-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="5c31e-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="5c31e-124">Example</span></span>

<span data-ttu-id="5c31e-125">Det här exemplet visar en listvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="5c31e-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

```
<View>
  <Name>System.ServiceProcess.ServiceController</Name>
  <ViewSelectedBy>
    <TypeName>System.ServiceProcess.ServiceController</TypeName>
  </ViewSelectedBy>
  <ListControl>
    <ListEntries>
      <ListEntry>...</ListEntry>
    </ListEntries>
  </ListControl>
</View>
```

## <a name="see-also"></a><span data-ttu-id="5c31e-126">Se även</span><span class="sxs-lookup"><span data-stu-id="5c31e-126">See Also</span></span>

[<span data-ttu-id="5c31e-127">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="5c31e-128">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="5c31e-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="5c31e-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="5c31e-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="5c31e-130">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="5c31e-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
