---
ms.date: 09/13/2016
ms.topic: reference
title: CustomItem-element för CustomEntry för Controls för Configuration (format)
description: CustomItem-element för CustomEntry för Controls för Configuration (format)
ms.openlocfilehash: 06c399e982b6ac0fba9c11e20c468fe8bef6f694
ms.sourcegitcommit: ba7315a496986451cfc1296b659d73ea2373d3f0
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 12/10/2020
ms.locfileid: "92666781"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="be025-103">CustomItem-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-103">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="be025-104">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="be025-104">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="be025-105">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="be025-105">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="be025-106">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="be025-106">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="be025-107">Syntax</span><span class="sxs-lookup"><span data-stu-id="be025-107">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="be025-108">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="be025-108">Attributes and Elements</span></span>

<span data-ttu-id="be025-109">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="be025-109">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="be025-110">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="be025-110">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="be025-111">Attribut</span><span class="sxs-lookup"><span data-stu-id="be025-111">Attributes</span></span>

<span data-ttu-id="be025-112">Inga.</span><span class="sxs-lookup"><span data-stu-id="be025-112">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="be025-113">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="be025-113">Child Elements</span></span>

|<span data-ttu-id="be025-114">Element</span><span class="sxs-lookup"><span data-stu-id="be025-114">Element</span></span>|<span data-ttu-id="be025-115">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="be025-115">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be025-116">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-116">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="be025-117">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="be025-117">Optional element.</span></span><br /><br /> <span data-ttu-id="be025-118">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="be025-118">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="be025-119">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-119">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="be025-120">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="be025-120">Optional element.</span></span><br /><br /> <span data-ttu-id="be025-121">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="be025-121">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="be025-122">NewLine-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-122">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="be025-123">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="be025-123">Optional element.</span></span><br /><br /> <span data-ttu-id="be025-124">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="be025-124">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="be025-125">Text-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-125">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="be025-126">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="be025-126">Optional element.</span></span><br /><br /> <span data-ttu-id="be025-127">Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.</span><span class="sxs-lookup"><span data-stu-id="be025-127">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="be025-128">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="be025-128">Parent Elements</span></span>

|<span data-ttu-id="be025-129">Element</span><span class="sxs-lookup"><span data-stu-id="be025-129">Element</span></span>|<span data-ttu-id="be025-130">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="be025-130">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="be025-131">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-131">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="be025-132">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="be025-132">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="be025-133">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="be025-133">Remarks</span></span>

<span data-ttu-id="be025-134">`CustomItem`Tänk på följande när du anger elementets underordnade element:</span><span class="sxs-lookup"><span data-stu-id="be025-134">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="be025-135">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding` , `NewLine` , `Text` och `Frame` .</span><span class="sxs-lookup"><span data-stu-id="be025-135">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="be025-136">Det finns ingen övre gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="be025-136">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="be025-137">I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding` element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="be025-137">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="be025-138">Se även</span><span class="sxs-lookup"><span data-stu-id="be025-138">See Also</span></span>

[<span data-ttu-id="be025-139">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-139">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="be025-140">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-140">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="be025-141">NewLine-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-141">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="be025-142">Text-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="be025-142">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="be025-143">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="be025-143">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
