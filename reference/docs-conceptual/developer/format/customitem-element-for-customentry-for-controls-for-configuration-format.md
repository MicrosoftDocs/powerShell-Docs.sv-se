---
title: CustomItem-element för CustomEntry för kontroll av konfiguration (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: bb8124242496f192717127f201674bc1428e5de0
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785871"
---
# <a name="customitem-element-for-customentry-for-controls-for-configuration-format"></a><span data-ttu-id="bc2fa-102">CustomItem-element för CustomEntry för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-102">CustomItem Element for CustomEntry for Controls for Configuration (Format)</span></span>

<span data-ttu-id="bc2fa-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="bc2fa-104">Det här elementet används när du definierar en gemensam kontroll som kan användas av alla vyer i format filen.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-104">This element is used when defining a common control that can be used by all the views in the formatting file.</span></span>

<span data-ttu-id="bc2fa-105">Konfigurations element (format) styr element i konfigurations-(format)-kontroll element för Controls (format) CustomControl-element för Control för Configuration (format) CustomEntries-element för CustomControl för Configuration (format) CustomEntry-element för CustomControl för Controls (format) CustomItem-element för CustomEntry för kontroller för konfiguration</span><span class="sxs-lookup"><span data-stu-id="bc2fa-105">Configuration Element (Format) Controls Element of Configuration (Format) Control Element for Controls for Configuration (Format) CustomControl Element for Control for Configuration (Format) CustomEntries Element for CustomControl for Configuration (Format) CustomEntry Element for CustomControl for Controls for Configuration (Format) CustomItem Element for CustomEntry for Controls for Configuration</span></span>

## <a name="syntax"></a><span data-ttu-id="bc2fa-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="bc2fa-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...</Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="bc2fa-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="bc2fa-107">Attributes and Elements</span></span>

<span data-ttu-id="bc2fa-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="bc2fa-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="bc2fa-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="bc2fa-110">Attributes</span></span>

<span data-ttu-id="bc2fa-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="bc2fa-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="bc2fa-112">Child Elements</span></span>

|<span data-ttu-id="bc2fa-113">Element</span><span class="sxs-lookup"><span data-stu-id="bc2fa-113">Element</span></span>|<span data-ttu-id="bc2fa-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bc2fa-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc2fa-115">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-115">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bc2fa-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-116">Optional element.</span></span><br /><br /> <span data-ttu-id="bc2fa-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="bc2fa-118">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-118">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bc2fa-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-119">Optional element.</span></span><br /><br /> <span data-ttu-id="bc2fa-120">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="bc2fa-121">NewLine-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-121">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bc2fa-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-122">Optional element.</span></span><br /><br /> <span data-ttu-id="bc2fa-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="bc2fa-124">Text-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-124">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)|<span data-ttu-id="bc2fa-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-125">Optional element.</span></span><br /><br /> <span data-ttu-id="bc2fa-126">Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="bc2fa-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="bc2fa-127">Parent Elements</span></span>

|<span data-ttu-id="bc2fa-128">Element</span><span class="sxs-lookup"><span data-stu-id="bc2fa-128">Element</span></span>|<span data-ttu-id="bc2fa-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="bc2fa-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="bc2fa-130">CustomEntry-element för CustomControl för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-130">CustomEntry Element for CustomControl for Controls for Configuration (Format)</span></span>](./customentry-element-for-customcontrol-for-controls-for-configuration-format.md)|<span data-ttu-id="bc2fa-131">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="bc2fa-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="bc2fa-132">Remarks</span></span>

<span data-ttu-id="bc2fa-133">`CustomItem`Tänk på följande när du anger elementets underordnade element:</span><span class="sxs-lookup"><span data-stu-id="bc2fa-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="bc2fa-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding` , `NewLine` , `Text` och `Frame` .</span><span class="sxs-lookup"><span data-stu-id="bc2fa-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="bc2fa-135">Det finns ingen övre gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="bc2fa-136">I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding` element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="bc2fa-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="bc2fa-137">Se även</span><span class="sxs-lookup"><span data-stu-id="bc2fa-137">See Also</span></span>

[<span data-ttu-id="bc2fa-138">ExpressionBinding-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-138">ExpressionBinding Element for CustomItem for Controls for Configuration (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc2fa-139">Frame-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-139">Frame Element for CustomItem for Controls for Configuration (Format)</span></span>](./frame-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc2fa-140">NewLine-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-140">NewLine Element for CustomItem for Controls for Configuration (Format)</span></span>](./newline-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc2fa-141">Text-element för CustomItem för Controls för Configuration (format)</span><span class="sxs-lookup"><span data-stu-id="bc2fa-141">Text Element for CustomItem for Controls for Configuration (Format)</span></span>](./text-element-for-customitem-for-controls-for-configuration-format.md)

[<span data-ttu-id="bc2fa-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="bc2fa-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
