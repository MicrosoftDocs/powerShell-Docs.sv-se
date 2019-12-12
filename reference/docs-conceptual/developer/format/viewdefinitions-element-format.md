---
title: ViewDefinitions-element (format) | Microsoft Docs
ms.custom: ''
ms.date: 09/13/2016
ms.reviewer: ''
ms.suite: ''
ms.tgt_pltfrm: ''
ms.topic: article
ms.assetid: 29840c10-2b30-4bb1-a8a0-ddf84d19c2d0
caps.latest.revision: 18
ms.openlocfilehash: c5ec80350c7707ccd41112ab5e1952e5dc198cca
ms.sourcegitcommit: debd2b38fb8070a7357bf1a4bf9cc736f3702f31
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/05/2019
ms.locfileid: "72353419"
---
# <a name="viewdefinitions-element-format"></a><span data-ttu-id="ef514-102">ViewDefinitions-element (format)</span><span class="sxs-lookup"><span data-stu-id="ef514-102">ViewDefinitions Element (Format)</span></span>

<span data-ttu-id="ef514-103">Definierar de vyer som används för att visa .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ef514-103">Defines the views used to display .NET objects.</span></span> <span data-ttu-id="ef514-104">Dessa vyer kan visa egenskaper och skript värden för ett objekt i tabell format, list format, brett format och anpassat kontroll format.</span><span class="sxs-lookup"><span data-stu-id="ef514-104">These views can display the properties and script values of an object  in a table format, list format, wide format, and custom control format.</span></span>

<span data-ttu-id="ef514-105">Konfigurations element (format) ViewDefinitions-element (format-XML)</span><span class="sxs-lookup"><span data-stu-id="ef514-105">Configuration Element (Format) ViewDefinitions (Format XML) Element</span></span>

## <a name="syntax"></a><span data-ttu-id="ef514-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="ef514-106">Syntax</span></span>

```xml

<ViewDefinitions>
  <View>...</View>
</ViewDefinitions>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="ef514-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="ef514-107">Attributes and Elements</span></span>

<span data-ttu-id="ef514-108">I följande avsnitt beskrivs attributen, underordnade element och det överordnade elementet i `ViewDefinitions`-elementet.</span><span class="sxs-lookup"><span data-stu-id="ef514-108">The following sections describe the attributes, child elements, and parent element of the `ViewDefinitions` element.</span></span> <span data-ttu-id="ef514-109">Det finns ingen gräns för antalet vyer som kan definieras i en formateringsinformation och de kan läggas till i vilken ordning som helst.</span><span class="sxs-lookup"><span data-stu-id="ef514-109">There is no limit to the number of views that can be defined in a formatting file, and they can be added in any order.</span></span>

### <a name="attributes"></a><span data-ttu-id="ef514-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="ef514-110">Attributes</span></span>

<span data-ttu-id="ef514-111">Ingen.</span><span class="sxs-lookup"><span data-stu-id="ef514-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="ef514-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="ef514-112">Child Elements</span></span>

|<span data-ttu-id="ef514-113">Element</span><span class="sxs-lookup"><span data-stu-id="ef514-113">Element</span></span>|<span data-ttu-id="ef514-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ef514-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef514-115">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="ef514-115">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="ef514-116">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="ef514-116">Defines a view that is used to display one or more .NET objects.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="ef514-117">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="ef514-117">Parent Elements</span></span>

|<span data-ttu-id="ef514-118">Element</span><span class="sxs-lookup"><span data-stu-id="ef514-118">Element</span></span>|<span data-ttu-id="ef514-119">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="ef514-119">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="ef514-120">Konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="ef514-120">Configuration Element (Format)</span></span>](./configuration-element-format.md)|<span data-ttu-id="ef514-121">Representerar det översta elementet i en textfil.</span><span class="sxs-lookup"><span data-stu-id="ef514-121">Represents the top-level element of a formatting file.</span></span>|

## <a name="remarks"></a><span data-ttu-id="ef514-122">Anmärkningar</span><span class="sxs-lookup"><span data-stu-id="ef514-122">Remarks</span></span>

<span data-ttu-id="ef514-123">Mer information om komponenterna i de olika typerna av vyer finns i följande avsnitt:</span><span class="sxs-lookup"><span data-stu-id="ef514-123">For more information about the components of the different types of views, see the following topics:</span></span>

- [<span data-ttu-id="ef514-124">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="ef514-124">Creating a Table View</span></span>](./creating-a-table-view.md)

- [<span data-ttu-id="ef514-125">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="ef514-125">Creating a List View</span></span>](./creating-a-list-view.md)

- [<span data-ttu-id="ef514-126">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="ef514-126">Creating a Wide View</span></span>](./creating-a-wide-view.md)

- [<span data-ttu-id="ef514-127">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="ef514-127">Custom Controls</span></span>](./creating-custom-controls.md)

## <a name="example"></a><span data-ttu-id="ef514-128">Exempel</span><span class="sxs-lookup"><span data-stu-id="ef514-128">Example</span></span>

<span data-ttu-id="ef514-129">I det här exemplet visas ett `ViewDefinitions`-element som innehåller de överordnade elementen för en tabellvy och en listvy.</span><span class="sxs-lookup"><span data-stu-id="ef514-129">This example shows a `ViewDefinitions` element that contains the parent elements for a table view and a list view.</span></span>

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

## <a name="see-also"></a><span data-ttu-id="ef514-130">Se även</span><span class="sxs-lookup"><span data-stu-id="ef514-130">See Also</span></span>

[<span data-ttu-id="ef514-131">Konfigurations element (format)</span><span class="sxs-lookup"><span data-stu-id="ef514-131">Configuration Element (Format)</span></span>](./configuration-element-format.md)

[<span data-ttu-id="ef514-132">Visa element (format)</span><span class="sxs-lookup"><span data-stu-id="ef514-132">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="ef514-133">Skapa en tabellvy</span><span class="sxs-lookup"><span data-stu-id="ef514-133">Creating a Table View</span></span>](./creating-a-table-view.md)

[<span data-ttu-id="ef514-134">Skapa en listvy</span><span class="sxs-lookup"><span data-stu-id="ef514-134">Creating a List View</span></span>](./creating-a-list-view.md)

[<span data-ttu-id="ef514-135">Skapa en bred vy</span><span class="sxs-lookup"><span data-stu-id="ef514-135">Creating a Wide View</span></span>](./creating-a-wide-view.md)

[<span data-ttu-id="ef514-136">Anpassade kontroller</span><span class="sxs-lookup"><span data-stu-id="ef514-136">Custom Controls</span></span>](./creating-custom-controls.md)

[<span data-ttu-id="ef514-137">Skriva en fil med PowerShell-formatering</span><span class="sxs-lookup"><span data-stu-id="ef514-137">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
