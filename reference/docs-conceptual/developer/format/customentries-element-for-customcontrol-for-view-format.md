---
ms.date: 09/13/2016
ms.topic: reference
title: CustomEntries-element för CustomControl för View (format)
description: CustomEntries-element för CustomControl för View (format)
ms.openlocfilehash: 6e757bccdface2503667f8786462a2b43134a07d
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92649974"
---
# <a name="customentries-element-for-customcontrol-for-view-format"></a><span data-ttu-id="13da2-103">CustomEntries-element för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-103">CustomEntries Element for CustomControl for View (Format)</span></span>

<span data-ttu-id="13da2-104">Innehåller definitionerna för vyn anpassad kontroll.</span><span class="sxs-lookup"><span data-stu-id="13da2-104">Provides the definitions of the custom control view.</span></span> <span data-ttu-id="13da2-105">Vyn anpassad kontroll måste ange en eller flera definitioner.</span><span class="sxs-lookup"><span data-stu-id="13da2-105">The custom control view must specify one or more definitions.</span></span>

<span data-ttu-id="13da2-106">Konfigurations element (format) ViewDefinitions element (format) View-element (format) CustomControl-element (format) element (format) CustomEntries-element för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="13da2-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="13da2-107">Syntax</span></span>

```xml
<CustomEntries>
  <CustomEntry>...</CustomEntry>
</CustomEntries>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="13da2-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="13da2-108">Attributes and Elements</span></span>

<span data-ttu-id="13da2-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomControlEntries` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="13da2-109">The following sections describe attributes, child elements, and the parent element of the `CustomControlEntries` element.</span></span> <span data-ttu-id="13da2-110">Du måste ange ett eller flera underordnade element.</span><span class="sxs-lookup"><span data-stu-id="13da2-110">You must specify one or more child elements.</span></span>

### <a name="attributes"></a><span data-ttu-id="13da2-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="13da2-111">Attributes</span></span>

<span data-ttu-id="13da2-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="13da2-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="13da2-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="13da2-113">Child Elements</span></span>

|<span data-ttu-id="13da2-114">Element</span><span class="sxs-lookup"><span data-stu-id="13da2-114">Element</span></span>|<span data-ttu-id="13da2-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13da2-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13da2-116">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-116">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="13da2-117">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="13da2-117">Required element.</span></span><br /><br /> <span data-ttu-id="13da2-118">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="13da2-118">Provides a definition of the custom control view.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="13da2-119">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="13da2-119">Parent Elements</span></span>

|<span data-ttu-id="13da2-120">Element</span><span class="sxs-lookup"><span data-stu-id="13da2-120">Element</span></span>|<span data-ttu-id="13da2-121">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="13da2-121">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="13da2-122">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-122">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)|<span data-ttu-id="13da2-123">Nödvändigt element.</span><span class="sxs-lookup"><span data-stu-id="13da2-123">Required element.</span></span><br /><br /> <span data-ttu-id="13da2-124">Definierar ett anpassat kontroll format för vyn.</span><span class="sxs-lookup"><span data-stu-id="13da2-124">Defines a custom control format for the view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="13da2-125">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="13da2-125">Remarks</span></span>

<span data-ttu-id="13da2-126">I de flesta fall har en kontroll bara en definition som definieras i ett enda `CustomEntry` element.</span><span class="sxs-lookup"><span data-stu-id="13da2-126">In most cases, a control has only one definition, which is defined in a single `CustomEntry` element.</span></span> <span data-ttu-id="13da2-127">Det är dock möjligt att ha flera definitioner om du vill använda samma kontroll för att visa olika .NET-objekt.</span><span class="sxs-lookup"><span data-stu-id="13da2-127">However it is possible to have multiple definitions if you want to use the same control to display different .NET objects.</span></span> <span data-ttu-id="13da2-128">I dessa fall kan du definiera ett- `CustomEntry` element för varje objekt eller uppsättning objekt.</span><span class="sxs-lookup"><span data-stu-id="13da2-128">In those cases, you can define a `CustomEntry` element for each object or set of objects.</span></span>

## <a name="see-also"></a><span data-ttu-id="13da2-129">Se även</span><span class="sxs-lookup"><span data-stu-id="13da2-129">See Also</span></span>

[<span data-ttu-id="13da2-130">CustomControl-element för View (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-130">CustomControl Element for View (Format)</span></span>](./customcontrol-element-for-view-format.md)

[<span data-ttu-id="13da2-131">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="13da2-131">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="13da2-132">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="13da2-132">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
