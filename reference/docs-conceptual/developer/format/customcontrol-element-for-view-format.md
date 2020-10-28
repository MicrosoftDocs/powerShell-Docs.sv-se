---
ms.date: 09/13/2016
ms.topic: reference
title: CustomControl-element för View (format)
description: CustomControl-element för View (format)
ms.openlocfilehash: 41352be55f0c03b2eaca0dbe2d7345e7cf804a7c
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92655469"
---
# <a name="customcontrol-element-for-view-format"></a><span data-ttu-id="635b0-103">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-103">CustomControl Element for View (Format)</span></span>

<span data-ttu-id="635b0-104">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="635b0-104">Defines a custom control format for the view.</span></span>

<span data-ttu-id="635b0-105">Konfigurations element (format) ViewDefinitions element (format) Visa element (format) CustomControl-element (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="635b0-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="635b0-106">Syntax</span></span>

```xml
<CustomControl>
  <CustomEntries>...</CustomEntries>
</CustomControl>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="635b0-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="635b0-107">Attributes and Elements</span></span>

<span data-ttu-id="635b0-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomControl` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="635b0-108">The following sections describe attributes, child elements, and the parent element of the `CustomControl` element.</span></span> <span data-ttu-id="635b0-109">Du måste ange ett underordnat element.</span><span class="sxs-lookup"><span data-stu-id="635b0-109">You must specify one child element.</span></span>

### <a name="attributes"></a><span data-ttu-id="635b0-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="635b0-110">Attributes</span></span>

<span data-ttu-id="635b0-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="635b0-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="635b0-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="635b0-112">Child Elements</span></span>

|<span data-ttu-id="635b0-113">Element</span><span class="sxs-lookup"><span data-stu-id="635b0-113">Element</span></span>|<span data-ttu-id="635b0-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="635b0-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="635b0-115">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-115">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)|<span data-ttu-id="635b0-116">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="635b0-116">Required element.</span></span><br /><br /> <span data-ttu-id="635b0-117">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="635b0-117">Provides the definitions of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="635b0-118">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="635b0-118">Parent Elements</span></span>

|<span data-ttu-id="635b0-119">Element</span><span class="sxs-lookup"><span data-stu-id="635b0-119">Element</span></span>|<span data-ttu-id="635b0-120">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="635b0-120">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="635b0-121">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-121">View Element (Format)</span></span>](./view-element-format.md)|<span data-ttu-id="635b0-122">Definierar en vy som används för att visa ett eller flera .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="635b0-122">Defines a view that is used to display one or more .NET objects.</span></span>|

## <a name="remarks"></a><span data-ttu-id="635b0-123">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="635b0-123">Remarks</span></span>

<span data-ttu-id="635b0-124">I de flesta fall krävs bara en definition för varje kontroll, men det är möjligt att ange flera definitioner om du vill använda samma vy för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="635b0-124">In most cases, only one definition is required for each control view, but it is possible to provide multiple definitions if you want to use the same view to display different .NET objects.</span></span> <span data-ttu-id="635b0-125">I dessa fall kan du ange en separat definition för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="635b0-125">In those cases, you can provide a separate definition for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="635b0-126">Se även</span><span class="sxs-lookup"><span data-stu-id="635b0-126">See Also</span></span>

[<span data-ttu-id="635b0-127">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-127">CustomEntries Element for CustomControl for View (Format)</span></span>](./customentries-element-for-customcontrol-for-view-format.md)

[<span data-ttu-id="635b0-128">View-element (format)</span><span class="sxs-lookup"><span data-stu-id="635b0-128">View Element (Format)</span></span>](./view-element-format.md)

[<span data-ttu-id="635b0-129">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="635b0-129">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
