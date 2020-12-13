---
ms.date: 09/13/2016
ms.topic: reference
title: ViewDefinitions-element (format)
description: ViewDefinitions-element (format)
ms.openlocfilehash: fceef0e5ec91e8c59a7b2b90fd31ca422ff0c94d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92664577"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="86993-103">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="86993-103">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="86993-104">Definierar de vyer som används för att visa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="86993-104">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="86993-105">Dessa vyer kan visa egenskaper och skript värden för ett objekt i tabell format, list format, brett format och anpassat kontroll format.</span><span class="sxs-lookup"><span data-stu-id="86993-105">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="86993-106">Konfigurations element (format) ViewDefinitions-element (format-XML)</span><span class="sxs-lookup"><span data-stu-id="86993-106">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="86993-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="86993-107">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="86993-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="86993-108">Attributes and Elements</span></span>

<span data-ttu-id="86993-109">I följande avsnitt beskrivs attributen, underordnade element och `ViewDefinitions` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="86993-109">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="86993-110">Det finns ingen gräns för antalet vyer som kan definieras i en formateringsinformation och de kan läggas till i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="86993-110">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="86993-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="86993-111">Attributes</span></span>

<span data-ttu-id="86993-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="86993-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="86993-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="86993-113">Child Elements</span></span>

|<span data-ttu-id="86993-114">Element</span><span class="sxs-lookup"><span data-stu-id="86993-114">Element</span></span>|<span data-ttu-id="86993-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86993-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86993-116">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="86993-116">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="86993-117">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="86993-117">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="86993-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="86993-118">Parent Elements</span></span>

|<span data-ttu-id="86993-119">Element</span><span class="sxs-lookup"><span data-stu-id="86993-119">Element</span></span>|<span data-ttu-id="86993-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="86993-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="86993-121">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="86993-121">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="86993-122">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="86993-122">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="86993-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="86993-123">Remarks</span></span>

<span data-ttu-id="86993-124">Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="86993-124">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="86993-125">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="86993-125">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="86993-126">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="86993-126">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="86993-127">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="86993-127">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="86993-128">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="86993-128">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="86993-129">Exempel</span><span class="sxs-lookup"><span data-stu-id="86993-129">Example</span></span>

<span data-ttu-id="86993-130">Det här exemplet visar ett `ViewDefinitions` element som innehåller de överordnade elementen för en tabellvy och en listvy.</span><span class="sxs-lookup"><span data-stu-id="86993-130">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="86993-131">Se även</span><span class="sxs-lookup"><span data-stu-id="86993-131">See Also</span></span>

[<span data-ttu-id="86993-132">Configuration-element (format)</span><span class="sxs-lookup"><span data-stu-id="86993-132">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="86993-133">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="86993-133">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="86993-134">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="86993-134">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="86993-135">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="86993-135">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="86993-136">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="86993-136">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="86993-137">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="86993-137">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="86993-138">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="86993-138">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
