---
title: ViewDefinitions Element (Format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: b6871f21bd666f9cd71dd336bb3f844cf472b56c
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 02/03/2019
ms.locfileid: "56851074"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="aa05a-102">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="aa05a-103">Definierar de vyer som används för att visa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="aa05a-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="aa05a-104">Vyerna kan visa egenskaperna och värdena för skript för ett objekt i ett tabellformat, lista, brett format och anpassad kontroll format.</span><span class="sxs-lookup"><span data-stu-id="aa05a-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="aa05a-105">Konfigurationselementet Element (Format) ViewDefinitions (XML-Format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="aa05a-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="aa05a-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="aa05a-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="aa05a-107">Attributes and Elements</span></span>

<span data-ttu-id="aa05a-108">I följande avsnitt beskrivs de attribut och underordnade element överordnade elementet i den `ViewDefinitions` element.</span><span class="sxs-lookup"><span data-stu-id="aa05a-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="aa05a-109">Det finns ingen gräns för antal vyer som kan definieras i en fil med formatering och de kan läggas till i valfri ordning.</span><span class="sxs-lookup"><span data-stu-id="aa05a-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="aa05a-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="aa05a-110">Attributes</span></span>

<span data-ttu-id="aa05a-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="aa05a-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="aa05a-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="aa05a-112">Child Elements</span></span>

|<span data-ttu-id="aa05a-113">Element</span><span class="sxs-lookup"><span data-stu-id="aa05a-113">Element</span></span>|<span data-ttu-id="aa05a-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aa05a-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa05a-115">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="aa05a-116">Definierar en vy som används för att visa en eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="aa05a-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="aa05a-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="aa05a-117">Parent Elements</span></span>

|<span data-ttu-id="aa05a-118">Element</span><span class="sxs-lookup"><span data-stu-id="aa05a-118">Element</span></span>|<span data-ttu-id="aa05a-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="aa05a-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="aa05a-120">Konfigurationselementet (Format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="aa05a-121">Representerar det översta elementet i en formatering fil.</span><span class="sxs-lookup"><span data-stu-id="aa05a-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="aa05a-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="aa05a-122">Remarks</span></span>

<span data-ttu-id="aa05a-123">Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="aa05a-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="aa05a-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="aa05a-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="aa05a-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="aa05a-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="aa05a-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="aa05a-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="aa05a-127">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="aa05a-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="aa05a-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="aa05a-128">Example</span></span>

<span data-ttu-id="aa05a-129">Det här exemplet visar en `ViewDefinitions` element som innehåller de överordnade element för en tabell och en listvy.</span><span class="sxs-lookup"><span data-stu-id="aa05a-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

```xml
<Configuration>
  <ViewDefinitions>
    <View>
      <TableControl>...</TableControl>
    </View>
    <View>
      <ListControl>...</ListControl>
    </View>
  </ViewDefinitions>
</Configuration>
```

## <a name="see-also"></a><span data-ttu-id="aa05a-130">Se även</span><span class="sxs-lookup"><span data-stu-id="aa05a-130">See Also</span></span>

[<span data-ttu-id="aa05a-131">Konfigurationselementet (Format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="aa05a-132">Visa Element (Format)</span><span class="sxs-lookup"><span data-stu-id="aa05a-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="aa05a-133">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="aa05a-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="aa05a-134">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="aa05a-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="aa05a-135">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="aa05a-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="aa05a-136">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="aa05a-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="aa05a-137">Skriva ett PowerShell formatering fil</span><span class="sxs-lookup"><span data-stu-id="aa05a-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
