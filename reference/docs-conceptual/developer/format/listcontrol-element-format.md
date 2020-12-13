---
ms.date: 09/13/2016
ms.topic: reference
title: ListControl-element (format)
description: ListControl-element (format)
ms.openlocfilehash: cd5687ac8e94e2245d1ae2de8b2206185e5b8ca4
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666594"
---
# <a name="listcontrol-element-format"></a><span data-ttu-id="00c46-103">ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-103">ListControl Element (Format)</span></span>

<span data-ttu-id="00c46-104">Definierar ett List format för vyn.</span><span class="sxs-lookup"><span data-stu-id="00c46-104">Defines a list format for the view.</span></span>

<span data-ttu-id="00c46-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) ListControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) ListControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="00c46-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="00c46-106">Syntax</span></span>

```xml
<ListControl>
  <ListEntries>...</ListEntries>
</ListControl>

```

## <a name="attributes-and-elements"></a><span data-ttu-id="00c46-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="00c46-107">Attributes and Elements</span></span>

<span data-ttu-id="00c46-108">I följande avsnitt beskrivs attributen, underordnade element och `ListControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="00c46-108">The following sections describe the attributes, child elements, and the parent element of the `ListControl` element.</span></span> <span data-ttu-id="00c46-109">Det här elementet får bara innehålla ett enda underordnat element.</span><span class="sxs-lookup"><span data-stu-id="00c46-109">This element must contain only a single child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="00c46-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="00c46-110">Attributes</span></span>

<span data-ttu-id="00c46-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="00c46-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="00c46-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="00c46-112">Child Elements</span></span>

|<span data-ttu-id="00c46-113">Element</span><span class="sxs-lookup"><span data-stu-id="00c46-113">Element</span></span>|<span data-ttu-id="00c46-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="00c46-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00c46-115">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-115">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)|<span data-ttu-id="00c46-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="00c46-116">Required element.</span></span><br /><br /> <span data-ttu-id="00c46-117">Innehåller definitionerna för listvyn.</span><span class="sxs-lookup"><span data-stu-id="00c46-117">Provides the definitions of the list view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="00c46-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="00c46-118">Parent Elements</span></span>

|<span data-ttu-id="00c46-119">Element</span><span class="sxs-lookup"><span data-stu-id="00c46-119">Element</span></span>|<span data-ttu-id="00c46-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="00c46-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="00c46-121">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="00c46-122">Definierar en vy som används för att visa medlemmar i ett eller flera objekt.</span><span class="sxs-lookup"><span data-stu-id="00c46-122">Defines a view that is used to display the members of one or more objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="00c46-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="00c46-123">Remarks</span></span>

<span data-ttu-id="00c46-124">Mer information om hur du skapar en listvy finns i [skapa en listvy](./creating-a-list-view.md).</span><span class="sxs-lookup"><span data-stu-id="00c46-124">For more information about creating a list view, see [Creating a List View](./creating-a-list-view.md).</span></span>

## <a name="example"></a><span data-ttu-id="00c46-125">Exempel</span><span class="sxs-lookup"><span data-stu-id="00c46-125">Example</span></span>

<span data-ttu-id="00c46-126">I det här exemplet visas en listvy för objektet [system. serviceprocess. ServiceController](/dotnet/api/System.ServiceProcess.ServiceController) .</span><span class="sxs-lookup"><span data-stu-id="00c46-126">This example shows a list view for the [System.Serviceprocess.Servicecontroller](/dotnet/api/System.ServiceProcess.ServiceController) object.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="00c46-127">Se även</span><span class="sxs-lookup"><span data-stu-id="00c46-127">See Also</span></span>

[<span data-ttu-id="00c46-128">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="00c46-129">ListEntries-element (format)</span><span class="sxs-lookup"><span data-stu-id="00c46-129">ListEntries Element (Format)</span></span>](./listentries-element-for-listcontrol-format.md)

[<span data-ttu-id="00c46-130">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="00c46-130">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="00c46-131">Skriva en Windows PowerShell-formatering och en typ fil</span><span class="sxs-lookup"><span data-stu-id="00c46-131">Writing a Windows PowerShell Formatting and Types File</span></span>](./writing-a-powershell-formatting-file.md)
