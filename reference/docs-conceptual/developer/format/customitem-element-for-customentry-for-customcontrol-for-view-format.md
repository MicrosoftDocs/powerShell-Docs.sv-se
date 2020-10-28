---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för CustomControl för View (format)
description: CustomItem-element för CustomEntry för CustomControl för View (format)
ms.openlocfilehash: 9090a3ada5316ba5ddb4a9c46eee37c11982ae6e
ms.sourcegitcommit: 488a940c7c828820b36a6ba56c119f64614afc29
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 10/27/2020
ms.locfileid: "92666747"
---
# <a name="customitem-element-for-customentry-for-customcontrol-for-view-format"></a><span data-ttu-id="96707-103">CustomItem-element för CustomEntry för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-103">CustomItem Element for CustomEntry for CustomControl for View (Format)</span></span>

<span data-ttu-id="96707-104">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="96707-104">Defines what data is displayed by the custom control view and how it is displayed.</span></span> <span data-ttu-id="96707-105">Det här elementet används när du definierar en anpassad kontrol vy.</span><span class="sxs-lookup"><span data-stu-id="96707-105">This element is used when defining a custom control view.</span></span>

<span data-ttu-id="96707-106">Konfigurations element (format) ViewDefinitions element (format) View element (format) CustomControl element (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för View (format) CustomItem-element för CustomEntry för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-106">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) CustomControl Element (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for View (Format) CustomItem Element for CustomEntry for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="96707-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="96707-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <Frame>...</Frame>
  <NewLine/>
  <Text>TextToDisplay</Text>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="96707-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="96707-108">Attributes and Elements</span></span>

<span data-ttu-id="96707-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="96707-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span>

### <a name="attributes"></a><span data-ttu-id="96707-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="96707-110">Attributes</span></span>

<span data-ttu-id="96707-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="96707-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="96707-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="96707-112">Child Elements</span></span>

|<span data-ttu-id="96707-113">Element</span><span class="sxs-lookup"><span data-stu-id="96707-113">Element</span></span>|<span data-ttu-id="96707-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96707-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96707-115">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-115">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="96707-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="96707-116">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="96707-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="96707-118">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-118">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="96707-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="96707-119">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-120">Definierar vilka data som visas i vyn anpassad kontroll och hur den visas.</span><span class="sxs-lookup"><span data-stu-id="96707-120">Defines what data is displayed by the custom control view and how it is displayed.</span></span>|
|[<span data-ttu-id="96707-121">Rad matnings element för CustomItem för anpassad kontroll för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96707-121">NewLine Element for CustomItem for Custom Control for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)|<span data-ttu-id="96707-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="96707-122">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="96707-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="96707-124">Text element för CustomItem för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96707-124">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)|<span data-ttu-id="96707-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="96707-125">Optional element.</span></span><br /><br /> <span data-ttu-id="96707-126">Anger ytterligare text för de data som visas i kontrollen.</span><span class="sxs-lookup"><span data-stu-id="96707-126">Specifies additional text to the data displayed by the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="96707-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="96707-127">Parent Elements</span></span>

|<span data-ttu-id="96707-128">Element</span><span class="sxs-lookup"><span data-stu-id="96707-128">Element</span></span>|<span data-ttu-id="96707-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="96707-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="96707-130">CustomEntry-element för CustomEntries för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-130">CustomEntry Element for CustomEntries for CustomControl for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)|<span data-ttu-id="96707-131">Innehåller en definition av den anpassade kontrollen.</span><span class="sxs-lookup"><span data-stu-id="96707-131">Provides a definition of the custom control view.</span></span>|

## <a name="remarks"></a><span data-ttu-id="96707-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="96707-132">Remarks</span></span>

## <a name="see-also"></a><span data-ttu-id="96707-133">Se även</span><span class="sxs-lookup"><span data-stu-id="96707-133">See Also</span></span>

[<span data-ttu-id="96707-134">CustomEntry-element för CustomEntries för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96707-134">CustomEntry Element for CustomEntries for View (Format)</span></span>](./customentry-element-for-customentries-for-customcontrol-for-view-format.md)

[<span data-ttu-id="96707-135">ExpressionBinding-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-135">ExpressionBinding Element for CustomItem for CustomControl for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="96707-136">Frame-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-136">Frame Element for CustomItem for CustomControl for View (Format)</span></span>](./frame-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="96707-137">NewLine-element för CustomItem för CustomControl för View (format)</span><span class="sxs-lookup"><span data-stu-id="96707-137">NewLine Element for CustomItem for CustomControl for View (Format)</span></span>](./newline-element-for-customitem-for-customcontrol-for-view-format.md)

[<span data-ttu-id="96707-138">Text element för CustomItem för CustomControl för vy (format)</span><span class="sxs-lookup"><span data-stu-id="96707-138">Text Element for CustomItem for CustomControl for View (Format)</span></span>](./text-element-for-customitem-for-customview-for-view-format.md)

[<span data-ttu-id="96707-139">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="96707-139">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
