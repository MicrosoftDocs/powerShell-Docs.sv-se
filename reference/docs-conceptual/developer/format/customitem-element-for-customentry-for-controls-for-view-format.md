---
title: CustomItem-element för CustomEntry för kontroller för vy (format) | Microsoft Docs
ms.date: 09/13/2016
ms.openlocfilehash: 747ea14e7118be62ebee00e7d80af2dccb5c8353
ms.sourcegitcommit: 0907b8c6322d2c7c61b17f8168d53452c8964b41
ms.translationtype: MT
ms.contentlocale: sv-SE
ms.lasthandoff: 08/05/2020
ms.locfileid: "87785854"
---
# <a name="customitem-element-for-customentry-for-controls-for-view-format"></a><span data-ttu-id="8e63c-102">CustomItem-element för CustomEntry för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-102">CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

<span data-ttu-id="8e63c-103">Definierar vilka data som visas av kontrollen och hur de visas.</span><span class="sxs-lookup"><span data-stu-id="8e63c-103">Defines what data is displayed by the control and how it is displayed.</span></span> <span data-ttu-id="8e63c-104">Det här elementet används när du definierar kontroller som kan användas av en vy.</span><span class="sxs-lookup"><span data-stu-id="8e63c-104">This element is used when defining controls that can be used by a view.</span></span>

<span data-ttu-id="8e63c-105">Konfigurations element (format) ViewDefinitions element (format) (format) styr element (format) styr element (format) kontroll element för Controls (format) CustomControl-element för Control for View (format) CustomEntries-element för CustomControl för View (format) CustomEntry-element för CustomEntries för Controls (format) CustomItem-element för CustomEntry för Controls (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-105">Configuration Element (Format) ViewDefinitions Element (Format) View Element (Format) Controls Element (Format) Control Element for Controls for View (Format) CustomControl Element for Control for Controls for View (Format) CustomEntries Element for CustomControl for View (Format) CustomEntry Element for CustomEntries for Controls for View (Format) CustomItem Element for CustomEntry for Controls for View (Format)</span></span>

## <a name="syntax"></a><span data-ttu-id="8e63c-106">Syntax</span><span class="sxs-lookup"><span data-stu-id="8e63c-106">Syntax</span></span>

```xml
<CustomItem>
  <ExpressionBinding>...</ExpressionBinding>
  <NewLine/>
  <Text>TextToDisplay</Text>
  <Frame>...<Frame>
</CustomItem>
```

## <a name="attributes-and-elements"></a><span data-ttu-id="8e63c-107">Attribut och element</span><span class="sxs-lookup"><span data-stu-id="8e63c-107">Attributes and Elements</span></span>

<span data-ttu-id="8e63c-108">I följande avsnitt beskrivs attribut, underordnade element och `CustomItem` elementets överordnade element.</span><span class="sxs-lookup"><span data-stu-id="8e63c-108">The following sections describe attributes, child elements, and the parent element of the `CustomItem` element.</span></span> <span data-ttu-id="8e63c-109">Mer information finns i kommentarer.</span><span class="sxs-lookup"><span data-stu-id="8e63c-109">For more information, see Remarks.</span></span>

### <a name="attributes"></a><span data-ttu-id="8e63c-110">Attribut</span><span class="sxs-lookup"><span data-stu-id="8e63c-110">Attributes</span></span>

<span data-ttu-id="8e63c-111">Inga.</span><span class="sxs-lookup"><span data-stu-id="8e63c-111">None.</span></span>

### <a name="child-elements"></a><span data-ttu-id="8e63c-112">Underordnade element</span><span class="sxs-lookup"><span data-stu-id="8e63c-112">Child Elements</span></span>

|<span data-ttu-id="8e63c-113">Element</span><span class="sxs-lookup"><span data-stu-id="8e63c-113">Element</span></span>|<span data-ttu-id="8e63c-114">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e63c-114">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e63c-115">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-115">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8e63c-116">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e63c-116">Optional element.</span></span><br /><br /> <span data-ttu-id="8e63c-117">Definierar de data som visas av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8e63c-117">Defines the data that is displayed by the control.</span></span>|
|[<span data-ttu-id="8e63c-118">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-118">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8e63c-119">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e63c-119">Optional element.</span></span><br /><br /> <span data-ttu-id="8e63c-120">Definierar hur data visas, till exempel att flytta data till vänster eller höger.</span><span class="sxs-lookup"><span data-stu-id="8e63c-120">Defines how the data is displayed, such as shifting the data to the left or right.</span></span>|
|[<span data-ttu-id="8e63c-121">NewLine-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-121">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8e63c-122">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e63c-122">Optional element.</span></span><br /><br /> <span data-ttu-id="8e63c-123">Lägger till en tom rad i visningen av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8e63c-123">Adds a blank line to the display of the control.</span></span>|
|[<span data-ttu-id="8e63c-124">Text-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-124">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)|<span data-ttu-id="8e63c-125">Valfritt element.</span><span class="sxs-lookup"><span data-stu-id="8e63c-125">Optional element.</span></span><br /><br /> <span data-ttu-id="8e63c-126">Lägger till text, till exempel parenteser eller hakparenteser, för att Visa kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8e63c-126">Adds text, such as parentheses or brackets, to the display of the control.</span></span>|

### <a name="parent-elements"></a><span data-ttu-id="8e63c-127">Överordnade element</span><span class="sxs-lookup"><span data-stu-id="8e63c-127">Parent Elements</span></span>

|<span data-ttu-id="8e63c-128">Element</span><span class="sxs-lookup"><span data-stu-id="8e63c-128">Element</span></span>|<span data-ttu-id="8e63c-129">Beskrivning</span><span class="sxs-lookup"><span data-stu-id="8e63c-129">Description</span></span>|
|-------------|-----------------|
|[<span data-ttu-id="8e63c-130">CustomEntry-element för CustomEntries för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-130">CustomEntry Element for CustomEntries for Controls for View (Format)</span></span>](./customentry-element-for-customentries-for-controls-for-view-format.md)|<span data-ttu-id="8e63c-131">Ger en definition av kontrollen.</span><span class="sxs-lookup"><span data-stu-id="8e63c-131">Provides a definition of the control.</span></span>|

## <a name="remarks"></a><span data-ttu-id="8e63c-132">Kommentarer</span><span class="sxs-lookup"><span data-stu-id="8e63c-132">Remarks</span></span>

<span data-ttu-id="8e63c-133">`CustomItem`Tänk på följande när du anger elementets underordnade element:</span><span class="sxs-lookup"><span data-stu-id="8e63c-133">When specifying the child elements of the `CustomItem` element, keep the following in mind:</span></span>

- <span data-ttu-id="8e63c-134">De underordnade elementen måste läggas till i följande ordning: `ExpressionBinding` , `NewLine` , `Text` och `Frame` .</span><span class="sxs-lookup"><span data-stu-id="8e63c-134">The child elements must be added in the following sequence: `ExpressionBinding`, `NewLine`, `Text`, and `Frame`.</span></span>

- <span data-ttu-id="8e63c-135">Det finns ingen övre gräns för antalet sekvenser som du kan ange.</span><span class="sxs-lookup"><span data-stu-id="8e63c-135">There is no maximum limit to the number of sequences that you can specify.</span></span>

- <span data-ttu-id="8e63c-136">I varje sekvens finns det ingen övre gräns för antalet `ExpressionBinding` element som du kan använda.</span><span class="sxs-lookup"><span data-stu-id="8e63c-136">In each sequence, there is no maximum limit to the number of `ExpressionBinding` elements that you can use.</span></span>

## <a name="see-also"></a><span data-ttu-id="8e63c-137">Se även</span><span class="sxs-lookup"><span data-stu-id="8e63c-137">See Also</span></span>

[<span data-ttu-id="8e63c-138">ExpressionBinding-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-138">ExpressionBinding Element for CustomItem for Controls for View (Format)</span></span>](./expressionbinding-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8e63c-139">Frame-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-139">Frame Element for CustomItem for Controls for View (Format)</span></span>](./frame-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8e63c-140">NewLine-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-140">NewLine Element for CustomItem for Controls for View (Format)</span></span>](./newline-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8e63c-141">Text-element för CustomItem för Controls för View (format)</span><span class="sxs-lookup"><span data-stu-id="8e63c-141">Text Element for CustomItem for Controls for View (Format)</span></span>](./text-element-for-customitem-for-controls-for-view-format.md)

[<span data-ttu-id="8e63c-142">Skriva en PowerShell-formateringsfil</span><span class="sxs-lookup"><span data-stu-id="8e63c-142">Writing a PowerShell Formatting File</span></span>](./writing-a-powershell-formatting-file.md)
