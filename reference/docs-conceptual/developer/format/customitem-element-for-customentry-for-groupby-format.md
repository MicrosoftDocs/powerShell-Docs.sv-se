---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för GroupBy (format)
description: CustomItem-element för CustomEntry för GroupBy (format)
ms.openlocfilehash: 5db23ad4dad5bd66ea64b9c6e91b8224a4aa4eca
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92645990"
---
# <a name="customitem-element-for-customentry-for-groupby-format"></a><span data-ttu-id="3df98-103">CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-103">CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

<span data-ttu-id="3df98-104">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="3df98-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="3df98-105">Det här elementet används när du definierar hur en ny grupp av objekt visas.</span><span class="sxs-lookup"><span data-stu-id="3df98-105">This element is used when defining how a new group of objects is displayed.</span></span>

<span data-ttu-id="3df98-106">Konfigurations element (format) ViewDefinitions element (format) visnings element (format) GroupBy-element för View (format) CustomControl-element för GroupBy (format) CustomEntries-element för CustomControl for groupby (format) CustomItem-element för CustomEntry för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) GroupBy Element for View (Format) CustomControl Element for GroupBy (Format) CustomEntries Element for CustomControl for GroupBy (Format) CustomItem Element for CustomEntry for GroupBy (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="3df98-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="3df98-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="3df98-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="3df98-108">Attributes and Elements</span></span>

<span data-ttu-id="3df98-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="3df98-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="3df98-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="3df98-110">Attributes</span></span>

<span data-ttu-id="3df98-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="3df98-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="3df98-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="3df98-112">Child Elements</span></span>

|<span data-ttu-id="3df98-113">Element</span><span class="sxs-lookup"><span data-stu-id="3df98-113">Element</span></span>|<span data-ttu-id="3df98-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3df98-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3df98-115">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-115">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3df98-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3df98-116">Optional element.</span></span><br /><br /> <span data-ttu-id="3df98-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3df98-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="3df98-118">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-118">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3df98-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3df98-119">Optional element.</span></span><br /><br /> <span data-ttu-id="3df98-120">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="3df98-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="3df98-121">NewLine-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-121">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3df98-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3df98-122">Optional element.</span></span><br /><br /> <span data-ttu-id="3df98-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3df98-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="3df98-124">Text-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-124">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)|<span data-ttu-id="3df98-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="3df98-125">Optional element.</span></span><br /><br /> <span data-ttu-id="3df98-126">Anger ytterligare text för de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3df98-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="3df98-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="3df98-127">Parent Elements</span></span>

|<span data-ttu-id="3df98-128">Element</span><span class="sxs-lookup"><span data-stu-id="3df98-128">Element</span></span>|<span data-ttu-id="3df98-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="3df98-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="3df98-130">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-130">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)|<span data-ttu-id="3df98-131">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="3df98-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="3df98-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="3df98-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="3df98-133">Se även</span><span class="sxs-lookup"><span data-stu-id="3df98-133">See Also</span></span>

[<span data-ttu-id="3df98-134">CustomEntry-element för CustomControl för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-134">CustomEntry Element for CustomControl for GroupBy (Format)</span></span>](./customentry-element-for-customcontrol-for-groupby-format.md)

[<span data-ttu-id="3df98-135">ExpressionBinding-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-135">ExpressionBinding Element for CustomItem for GroupBy (Format)</span></span>](./expressionbinding-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="3df98-136">Frame-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-136">Frame Element for CustomItem for GroupBy (Format)</span></span>](./frame-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="3df98-137">NewLine-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-137">NewLine Element for CustomItem for GroupBy (Format)</span></span>](./newline-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="3df98-138">Text-element för CustomItem för GroupBy (format)</span><span class="sxs-lookup"><span data-stu-id="3df98-138">Text Element for CustomItem for GroupBy (Format)</span></span>](./text-element-for-customitem-for-groupby-format.md)

[<span data-ttu-id="3df98-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="3df98-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
