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
ms.sourcegitcommit: e7445ba8203da304286c591ff513900ad1c244a4
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 04/23/2019
ms.locfileid: "62065265"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="f9cc3-102">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-102">ListControl Element (Format)</span></span>

<span data-ttu-id="f9cc3-103">Definierar ett listformat för vyn.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-103">Defines a list format for the view.</span></span>

<span data-ttu-id="f9cc3-104">Elementet (Format) ViewDefinitions Element (Format) visa Element (Format) ListControl konfigurationselement (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-104">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="f9cc3-105">Syntax</span><span class="sxs-lookup"><span data-stu-id="f9cc3-105">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="f9cc3-106">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="f9cc3-106">Attributes and Elements</span></span>

<span data-ttu-id="f9cc3-107">I följande avsnitt beskrivs attribut, underordnade element och det överordnade elementet i den `ListControl` element.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-107">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="f9cc3-108">Det här elementet måste innehålla en enda underelement.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-108">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="f9cc3-109">Attribut</span><span class="sxs-lookup"><span data-stu-id="f9cc3-109">Attributes</span></span>

<span data-ttu-id="f9cc3-110">Ingen.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-110">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="f9cc3-111">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="f9cc3-111">Child Elements</span></span>

|<span data-ttu-id="f9cc3-112">Element</span><span class="sxs-lookup"><span data-stu-id="f9cc3-112">Element</span></span>|<span data-ttu-id="f9cc3-113">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f9cc3-113">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9cc3-114">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-114">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="f9cc3-115">Element som krävs.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-115">Required element.</span></span><br /><br /> <span data-ttu-id="f9cc3-116">Innehåller definitioner i listvyn.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-116">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="f9cc3-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="f9cc3-117">Parent Elements</span></span>

|<span data-ttu-id="f9cc3-118">Element</span><span class="sxs-lookup"><span data-stu-id="f9cc3-118">Element</span></span>|<span data-ttu-id="f9cc3-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="f9cc3-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="f9cc3-120">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-120">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="f9cc3-121">Definierar en vy som används för att visa medlemmarna i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-121">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="f9cc3-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="f9cc3-122">Remarks</span></span>

<span data-ttu-id="f9cc3-123">Läs mer om hur du skapar en listvy [skapar en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="f9cc3-123">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="f9cc3-124">Exempel</span><span class="sxs-lookup"><span data-stu-id="f9cc3-124">Example</span></span>

<span data-ttu-id="f9cc3-125">Det här exemplet visar en listvy för den [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) objekt.</span><span class="sxs-lookup"><span data-stu-id="f9cc3-125">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="f9cc3-126">Se även</span><span class="sxs-lookup"><span data-stu-id="f9cc3-126">See Also</span></span>

[<span data-ttu-id="f9cc3-127">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-127">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="f9cc3-128">ListEntries Element (Format)</span><span class="sxs-lookup"><span data-stu-id="f9cc3-128">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="f9cc3-129">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="f9cc3-129">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="f9cc3-130">Skriva ett Windows PowerShell formatering och skriver fil</span><span class="sxs-lookup"><span data-stu-id="f9cc3-130">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
